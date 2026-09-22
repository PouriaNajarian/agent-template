---
name: database-migrations
description: Buenas prÃ¡cticas de migraciÃ³n de base de datos para cambios de esquema, migraciones de datos, rollbacks y despliegues de tiempo cero en PostgreSQL, MySQL y ORMs comunes (Prisma, Drizzle, Kysely, Django, TypeORM, golang-migrate).
---

# Patrones de MigraciÃ³n de Base de Datos

Cambios de esquema de base de datos seguros y reversibles para sistemas de producciÃ³n.

## CuÃ¡ndo Activar

- Crear o alterar tablas de base de datos
- Agregar/eliminar columnas o Ã­ndices
- Ejecutar migraciones de datos (backfill, transformaciÃ³n)
- Planificar cambios de esquema de tiempo cero (zero-downtime)
- Configurar herramientas de migraciÃ³n para un nuevo proyecto

## Principios Fundamentales

1. **Cada cambio es una migraciÃ³n** â nunca alterar bases de datos de producciÃ³n manualmente
2. **Las migraciones son solo hacia adelante en producciÃ³n** â los rollbacks usan nuevas migraciones hacia adelante
3. **Las migraciones de esquema y de datos son separadas** â nunca mezclar DDL y DML en una migraciÃ³n
4. **Probar migraciones contra datos de tamaÃ±o de producciÃ³n** â una migraciÃ³n que funciona en 100 filas puede bloquear en 10M
5. **Las migraciones son inmutables una vez desplegadas** â nunca editar una migraciÃ³n que ya se ejecutÃ³ en producciÃ³n

## Lista de VerificaciÃ³n de Seguridad de MigraciÃ³n

Antes de aplicar cualquier migraciÃ³n:

- [ ] La migraciÃ³n tiene tanto UP como DOWN (o estÃ¡ marcada explÃ­citamente como irreversible)
- [ ] Sin bloqueos de tabla completa en tablas grandes (usar operaciones concurrentes)
- [ ] Las nuevas columnas tienen valores predeterminados o son nullable (nunca agregar NOT NULL sin valor predeterminado)
- [ ] Ãndices creados de forma concurrente (no en lÃ­nea con CREATE TABLE para tablas existentes)
- [ ] El backfill de datos es una migraciÃ³n separada del cambio de esquema
- [ ] Probado contra una copia de datos de producciÃ³n
- [ ] Plan de rollback documentado

## Patrones PostgreSQL

### Agregar una Columna de Forma Segura

```sql
-- BIEN: Columna nullable, sin bloqueo
ALTER TABLE users ADD COLUMN avatar_url TEXT;

-- BIEN: Columna con valor predeterminado (Postgres 11+ es instantÃ¡neo, sin reescritura)
ALTER TABLE users ADD COLUMN is_active BOOLEAN NOT NULL DEFAULT true;

-- MAL: NOT NULL sin valor predeterminado en tabla existente (requiere reescritura completa)
ALTER TABLE users ADD COLUMN role TEXT NOT NULL;
-- Esto bloquea la tabla y reescribe cada fila
```

### Agregar un Ãndice Sin Tiempo de Inactividad

```sql
-- MAL: Bloquea escrituras en tablas grandes
CREATE INDEX idx_users_email ON users (email);

-- BIEN: No bloqueante, permite escrituras concurrentes
CREATE INDEX CONCURRENTLY idx_users_email ON users (email);

-- Nota: CONCURRENTLY no puede ejecutarse dentro de un bloque de transacciÃ³n
-- La mayorÃ­a de herramientas de migraciÃ³n necesitan manejo especial para esto
```

### Renombrar una Columna (Zero-Downtime)

Nunca renombrar directamente en producciÃ³n. Usar el patrÃ³n expand-contract:

```sql
-- Paso 1: Agregar nueva columna (migraciÃ³n 001)
ALTER TABLE users ADD COLUMN display_name TEXT;

-- Paso 2: Backfill de datos (migraciÃ³n 002, migraciÃ³n de datos)
UPDATE users SET display_name = username WHERE display_name IS NULL;

-- Paso 3: Actualizar el cÃ³digo de la aplicaciÃ³n para leer/escribir ambas columnas
-- Desplegar cambios de aplicaciÃ³n

-- Paso 4: Dejar de escribir en la columna antigua, eliminarla (migraciÃ³n 003)
ALTER TABLE users DROP COLUMN username;
```

### Eliminar una Columna de Forma Segura

```sql
-- Paso 1: Eliminar todas las referencias de la aplicaciÃ³n a la columna
-- Paso 2: Desplegar la aplicaciÃ³n sin la referencia a la columna
-- Paso 3: Eliminar la columna en la prÃ³xima migraciÃ³n
ALTER TABLE orders DROP COLUMN legacy_status;

-- Para Django: usar SeparateDatabaseAndState para eliminar del modelo
-- sin generar DROP COLUMN (luego eliminar en la prÃ³xima migraciÃ³n)
```

### Migraciones de Datos Grandes

```sql
-- MAL: Actualiza todas las filas en una transacciÃ³n (bloquea la tabla)
UPDATE users SET normalized_email = LOWER(email);

-- BIEN: ActualizaciÃ³n en lotes con progreso
DO $$
DECLARE
  batch_size INT := 10000;
  rows_updated INT;
BEGIN
  LOOP
    UPDATE users
    SET normalized_email = LOWER(email)
    WHERE id IN (
      SELECT id FROM users
      WHERE normalized_email IS NULL
      LIMIT batch_size
      FOR UPDATE SKIP LOCKED
    );
    GET DIAGNOSTICS rows_updated = ROW_COUNT;
    RAISE NOTICE 'Updated % rows', rows_updated;
    EXIT WHEN rows_updated = 0;
    COMMIT;
  END LOOP;
END $$;
```

## Prisma (TypeScript/Node.js)

### Flujo de Trabajo

```bash
# Crear migraciÃ³n a partir de cambios de esquema
npx prisma migrate dev --name add_user_avatar

# Aplicar migraciones pendientes en producciÃ³n
npx prisma migrate deploy

# Resetear base de datos (solo desarrollo)
npx prisma migrate reset

# Generar cliente despuÃ©s de cambios de esquema
npx prisma generate
```

### Ejemplo de Esquema

```prisma
model User {
  id        String   @id @default(cuid())
  email     String   @unique
  name      String?
  avatarUrl String?  @map("avatar_url")
  createdAt DateTime @default(now()) @map("created_at")
  updatedAt DateTime @updatedAt @map("updated_at")
  orders    Order[]

  @@map("users")
  @@index([email])
}
```

### MigraciÃ³n SQL Personalizada

Para operaciones que Prisma no puede expresar (Ã­ndices concurrentes, backfills de datos):

```bash
# Crear migraciÃ³n vacÃ­a, luego editar el SQL manualmente
npx prisma migrate dev --create-only --name add_email_index
```

```sql
-- migrations/20240115_add_email_index/migration.sql
-- Prisma no puede generar CONCURRENTLY, por lo que se escribe manualmente
CREATE INDEX CONCURRENTLY IF NOT EXISTS idx_users_email ON users (email);
```

## Drizzle (TypeScript/Node.js)

### Flujo de Trabajo

```bash
# Generar migraciÃ³n a partir de cambios de esquema
npx drizzle-kit generate

# Aplicar migraciones
npx drizzle-kit migrate

# Hacer push del esquema directamente (solo desarrollo, sin archivo de migraciÃ³n)
npx drizzle-kit push
```

### Ejemplo de Esquema

```typescript
import { pgTable, text, timestamp, uuid, boolean } from "drizzle-orm/pg-core";

export const users = pgTable("users", {
  id: uuid("id").primaryKey().defaultRandom(),
  email: text("email").notNull().unique(),
  name: text("name"),
  isActive: boolean("is_active").notNull().default(true),
  createdAt: timestamp("created_at").notNull().defaultNow(),
  updatedAt: timestamp("updated_at").notNull().defaultNow(),
});
```

## Kysely (TypeScript/Node.js)

### Flujo de Trabajo (kysely-ctl)

```bash
# Inicializar archivo de configuraciÃ³n (kysely.config.ts)
kysely init

# Crear un nuevo archivo de migraciÃ³n
kysely migrate make add_user_avatar

# Aplicar todas las migraciones pendientes
kysely migrate latest

# Revertir la Ãºltima migraciÃ³n
kysely migrate down

# Mostrar estado de migraciones
kysely migrate list
```

### Archivo de MigraciÃ³n

```typescript
// migrations/2024_01_15_001_create_user_profile.ts
import { type Kysely, sql } from 'kysely'

// IMPORTANTE: Siempre usar Kysely<any>, no tu interfaz de DB tipada.
// Las migraciones estÃ¡n congeladas en el tiempo y no deben depender de los tipos de esquema actuales.
export async function up(db: Kysely<any>): Promise<void> {
  await db.schema
    .createTable('user_profile')
    .addColumn('id', 'serial', (col) => col.primaryKey())
    .addColumn('email', 'varchar(255)', (col) => col.notNull().unique())
    .addColumn('avatar_url', 'text')
    .addColumn('created_at', 'timestamp', (col) =>
      col.defaultTo(sql`now()`).notNull()
    )
    .execute()

  await db.schema
    .createIndex('idx_user_profile_avatar')
    .on('user_profile')
    .column('avatar_url')
    .execute()
}

export async function down(db: Kysely<any>): Promise<void> {
  await db.schema.dropTable('user_profile').execute()
}
```

### Migrador ProgramÃ¡tico

```typescript
import { Migrator, FileMigrationProvider } from 'kysely'
import { promises as fs } from 'fs'
import * as path from 'path'
// Solo ESM â CJS puede usar __dirname directamente
import { fileURLToPath } from 'url'
const migrationFolder = path.join(
  path.dirname(fileURLToPath(import.meta.url)),
  './migrations',
)

// `db` es tu instancia de base de datos Kysely<any>
const migrator = new Migrator({
  db,
  provider: new FileMigrationProvider({
    fs,
    path,
    migrationFolder,
  }),
  // ADVERTENCIA: Solo habilitar en desarrollo. Deshabilita la validaciÃ³n de
  // ordenamiento por timestamp, lo que puede causar deriva de esquema entre entornos.
  // allowUnorderedMigrations: true,
})

const { error, results } = await migrator.migrateToLatest()

results?.forEach((it) => {
  if (it.status === 'Success') {
    console.log(`migration "${it.migrationName}" executed successfully`)
  } else if (it.status === 'Error') {
    console.error(`failed to execute migration "${it.migrationName}"`)
  }
})

if (error) {
  console.error('migration failed', error)
  process.exit(1)
}
```

## Django (Python)

### Flujo de Trabajo

```bash
# Generar migraciÃ³n a partir de cambios de modelo
python manage.py makemigrations

# Aplicar migraciones
python manage.py migrate

# Mostrar estado de migraciones
python manage.py showmigrations

# Generar migraciÃ³n vacÃ­a para SQL personalizado
python manage.py makemigrations --empty app_name -n description
```

### MigraciÃ³n de Datos

```python
from django.db import migrations

def backfill_display_names(apps, schema_editor):
    User = apps.get_model("accounts", "User")
    batch_size = 5000
    users = User.objects.filter(display_name="")
    while users.exists():
        batch = list(users[:batch_size])
        for user in batch:
            user.display_name = user.username
        User.objects.bulk_update(batch, ["display_name"], batch_size=batch_size)

def reverse_backfill(apps, schema_editor):
    pass  # MigraciÃ³n de datos, no se necesita reversiÃ³n

class Migration(migrations.Migration):
    dependencies = [("accounts", "0015_add_display_name")]

    operations = [
        migrations.RunPython(backfill_display_names, reverse_backfill),
    ]
```

### SeparateDatabaseAndState

Eliminar una columna del modelo Django sin eliminarla de la base de datos inmediatamente:

```python
class Migration(migrations.Migration):
    operations = [
        migrations.SeparateDatabaseAndState(
            state_operations=[
                migrations.RemoveField(model_name="user", name="legacy_field"),
            ],
            database_operations=[],  # No tocar la DB todavÃ­a
        ),
    ]
```

## golang-migrate (Go)

### Flujo de Trabajo

```bash
# Crear par de migraciÃ³n
migrate create -ext sql -dir migrations -seq add_user_avatar

# Aplicar todas las migraciones pendientes
migrate -path migrations -database "$DATABASE_URL" up

# Revertir la Ãºltima migraciÃ³n
migrate -path migrations -database "$DATABASE_URL" down 1

# Forzar versiÃ³n (corregir estado sucio)
migrate -path migrations -database "$DATABASE_URL" force VERSION
```

### Archivos de MigraciÃ³n

```sql
-- migrations/000003_add_user_avatar.up.sql
ALTER TABLE users ADD COLUMN avatar_url TEXT;
CREATE INDEX CONCURRENTLY idx_users_avatar ON users (avatar_url) WHERE avatar_url IS NOT NULL;

-- migrations/000003_add_user_avatar.down.sql
DROP INDEX IF EXISTS idx_users_avatar;
ALTER TABLE users DROP COLUMN IF EXISTS avatar_url;
```

## Estrategia de MigraciÃ³n de Zero-Downtime

Para cambios crÃ­ticos de producciÃ³n, seguir el patrÃ³n expand-contract:

```
Fase 1: EXPAND (Expandir)
  - Agregar nueva columna/tabla (nullable o con valor predeterminado)
  - Desplegar: la app escribe en AMBAS, vieja y nueva
  - Backfill de datos existentes

Fase 2: MIGRATE (Migrar)
  - Desplegar: la app lee de la NUEVA, escribe en AMBAS
  - Verificar consistencia de datos

Fase 3: CONTRACT (Contraer)
  - Desplegar: la app solo usa la NUEVA
  - Eliminar columna/tabla antigua en migraciÃ³n separada
```

### Ejemplo de LÃ­nea de Tiempo

```
DÃ­a 1: MigraciÃ³n agrega columna new_status (nullable)
DÃ­a 1: Desplegar app v2 â escribe en status y new_status
DÃ­a 2: Ejecutar migraciÃ³n de backfill para filas existentes
DÃ­a 3: Desplegar app v3 â lee solo de new_status
DÃ­a 7: MigraciÃ³n elimina columna status antigua
```

## Anti-Patrones

| Anti-PatrÃ³n | Por QuÃ© Falla | Mejor Enfoque |
|-------------|-------------|-----------------|
| SQL manual en producciÃ³n | Sin historial de auditorÃ­a, no repetible | Siempre usar archivos de migraciÃ³n |
| Editar migraciones desplegadas | Causa deriva entre entornos | Crear nueva migraciÃ³n en su lugar |
| NOT NULL sin valor predeterminado | Bloquea tabla, reescribe todas las filas | Agregar nullable, backfill, luego agregar restricciÃ³n |
| Ãndice en lÃ­nea en tabla grande | Bloquea escrituras durante la construcciÃ³n | CREATE INDEX CONCURRENTLY |
| Esquema + datos en una migraciÃ³n | DifÃ­cil de revertir, transacciones largas | Migraciones separadas |
| Eliminar columna antes de eliminar cÃ³digo | Errores de aplicaciÃ³n por columna faltante | Eliminar cÃ³digo primero, eliminar columna en el prÃ³ximo despliegue |
