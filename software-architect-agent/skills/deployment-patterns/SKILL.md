---
name: deployment-patterns
description: Flujos de trabajo de despliegue, patrones de pipeline CI/CD, contenedorizaciÃ³n Docker, health checks, estrategias de rollback y listas de verificaciÃ³n de preparaciÃ³n para producciÃ³n de aplicaciones web.
---

# Patrones de Despliegue

Flujos de trabajo de despliegue en producciÃ³n y buenas prÃ¡cticas de CI/CD.

## CuÃ¡ndo Activar

- Configurar pipelines de CI/CD
- Contenedorizar una aplicaciÃ³n con Docker
- Planificar estrategia de despliegue (blue-green, canary, rolling)
- Implementar health checks y readiness probes
- Preparar un lanzamiento a producciÃ³n
- Configurar ajustes especÃ­ficos por entorno

## Estrategias de Despliegue

### Rolling Deployment (Por Defecto)

Reemplazar instancias gradualmente â las versiones vieja y nueva se ejecutan simultÃ¡neamente durante el despliegue.

```
Instancia 1: v1 â v2  (actualizar primero)
Instancia 2: v1        (aÃºn ejecutando v1)
Instancia 3: v1        (aÃºn ejecutando v1)

Instancia 1: v2
Instancia 2: v1 â v2  (actualizar segundo)
Instancia 3: v1

Instancia 1: v2
Instancia 2: v2
Instancia 3: v1 â v2  (actualizar Ãºltimo)
```

**Pros:** Zero downtime, despliegue gradual
**Contras:** Dos versiones se ejecutan simultÃ¡neamente â requiere cambios compatibles hacia atrÃ¡s
**Usar cuando:** Despliegues estÃ¡ndar, cambios compatibles hacia atrÃ¡s

### Blue-Green Deployment

Ejecutar dos entornos idÃ©nticos. Cambiar el trÃ¡fico de forma atÃ³mica.

```
Blue  (v1) â trÃ¡fico
Green (v2)   inactivo, ejecutando nueva versiÃ³n

# DespuÃ©s de la verificaciÃ³n:
Blue  (v1)   inactivo (se convierte en standby)
Green (v2) â trÃ¡fico
```

**Pros:** Rollback instantÃ¡neo (cambiar de vuelta a blue), corte limpio
**Contras:** Requiere 2x infraestructura durante el despliegue
**Usar cuando:** Servicios crÃ­ticos, tolerancia cero a problemas

### Canary Deployment

Enrutar un pequeÃ±o porcentaje del trÃ¡fico a la nueva versiÃ³n primero.

```
v1: 95% del trÃ¡fico
v2:  5% del trÃ¡fico  (canary)

# Si las mÃ©tricas se ven bien:
v1: 50% del trÃ¡fico
v2: 50% del trÃ¡fico

# Final:
v2: 100% del trÃ¡fico
```

**Pros:** Detecta problemas con trÃ¡fico real antes del despliegue completo
**Contras:** Requiere infraestructura de divisiÃ³n de trÃ¡fico, monitoreo
**Usar cuando:** Servicios de alto trÃ¡fico, cambios arriesgados, feature flags

## Docker

### Dockerfile Multi-Stage (Node.js)

```dockerfile
# Etapa 1: Instalar dependencias
FROM node:22-alpine AS deps
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --production=false

# Etapa 2: Build
FROM node:22-alpine AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
RUN npm run build
RUN npm prune --production

# Etapa 3: Imagen de producciÃ³n
FROM node:22-alpine AS runner
WORKDIR /app

RUN addgroup -g 1001 -S appgroup && adduser -S appuser -u 1001
USER appuser

COPY --from=builder --chown=appuser:appgroup /app/node_modules ./node_modules
COPY --from=builder --chown=appuser:appgroup /app/dist ./dist
COPY --from=builder --chown=appuser:appgroup /app/package.json ./

ENV NODE_ENV=production
EXPOSE 3000

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:3000/health || exit 1

CMD ["node", "dist/server.js"]
```

### Dockerfile Multi-Stage (Go)

```dockerfile
FROM golang:1.22-alpine AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o /server ./cmd/server

FROM alpine:3.19 AS runner
RUN apk --no-cache add ca-certificates
RUN adduser -D -u 1001 appuser
USER appuser

COPY --from=builder /server /server

EXPOSE 8080
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:8080/health || exit 1
CMD ["/server"]
```

### Dockerfile Multi-Stage (Python/Django)

```dockerfile
FROM python:3.12-slim AS builder
WORKDIR /app
RUN pip install --no-cache-dir uv
COPY requirements.txt .
RUN uv pip install --system --no-cache -r requirements.txt

FROM python:3.12-slim AS runner
WORKDIR /app

RUN useradd -r -u 1001 appuser
USER appuser

COPY --from=builder /usr/local/lib/python3.12/site-packages /usr/local/lib/python3.12/site-packages
COPY --from=builder /usr/local/bin /usr/local/bin
COPY . .

ENV PYTHONUNBUFFERED=1
EXPOSE 8000

HEALTHCHECK --interval=30s --timeout=3s CMD python -c "import urllib.request; urllib.request.urlopen('http://localhost:8000/health/')" || exit 1
CMD ["gunicorn", "config.wsgi:application", "--bind", "0.0.0.0:8000", "--workers", "4"]
```

### Buenas PrÃ¡cticas de Docker

```
# Buenas prÃ¡cticas
- Usar etiquetas de versiÃ³n especÃ­ficas (node:22-alpine, no node:latest)
- Builds multi-stage para minimizar el tamaÃ±o de imagen
- Ejecutar como usuario no-root
- Copiar archivos de dependencias primero (cache de capas)
- Usar .dockerignore para excluir node_modules, .git, tests
- Agregar instrucciÃ³n HEALTHCHECK
- Establecer lÃ­mites de recursos en docker-compose o k8s

# Malas prÃ¡cticas
- Ejecutar como root
- Usar etiquetas :latest
- Copiar todo el repositorio en una sola capa COPY
- Instalar dependencias de desarrollo en imagen de producciÃ³n
- Almacenar secretos en la imagen (usar variables de entorno o gestor de secretos)
```

## Pipeline CI/CD

### GitHub Actions (Pipeline EstÃ¡ndar)

```yaml
name: CI/CD

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 22
          cache: npm
      - run: npm ci
      - run: npm run lint
      - run: npm run typecheck
      - run: npm test -- --coverage
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: coverage
          path: coverage/

  build:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v4
      - uses: docker/setup-buildx-action@v3
      - uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
      - uses: docker/build-push-action@v5
        with:
          push: true
          tags: ghcr.io/${{ github.repository }}:${{ github.sha }}
          cache-from: type=gha
          cache-to: type=gha,mode=max

  deploy:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    environment: production
    steps:
      - name: Deploy to production
        run: |
          # Comando de despliegue especÃ­fico de plataforma
          # Railway: railway up
          # Vercel: vercel --prod
          # K8s: kubectl set image deployment/app app=ghcr.io/${{ github.repository }}:${{ github.sha }}
          echo "Deploying ${{ github.sha }}"
```

### Etapas del Pipeline

```
PR abierto:
  lint â typecheck â pruebas unitarias â pruebas de integraciÃ³n â despliegue preview

Merge a main:
  lint â typecheck â pruebas unitarias â pruebas de integraciÃ³n â build imagen â desplegar staging â smoke tests â desplegar producciÃ³n
```

## Health Checks

### Endpoint de Health Check

```typescript
// Health check simple
app.get("/health", (req, res) => {
  res.status(200).json({ status: "ok" });
});

// Health check detallado (para monitoreo interno)
app.get("/health/detailed", async (req, res) => {
  const checks = {
    database: await checkDatabase(),
    redis: await checkRedis(),
    externalApi: await checkExternalApi(),
  };

  const allHealthy = Object.values(checks).every(c => c.status === "ok");

  res.status(allHealthy ? 200 : 503).json({
    status: allHealthy ? "ok" : "degraded",
    timestamp: new Date().toISOString(),
    version: process.env.APP_VERSION || "unknown",
    uptime: process.uptime(),
    checks,
  });
});

async function checkDatabase(): Promise<HealthCheck> {
  try {
    await db.query("SELECT 1");
    return { status: "ok", latency_ms: 2 };
  } catch (err) {
    return { status: "error", message: "Database unreachable" };
  }
}
```

### Probes de Kubernetes

```yaml
livenessProbe:
  httpGet:
    path: /health
    port: 3000
  initialDelaySeconds: 10
  periodSeconds: 30
  failureThreshold: 3

readinessProbe:
  httpGet:
    path: /health
    port: 3000
  initialDelaySeconds: 5
  periodSeconds: 10
  failureThreshold: 2

startupProbe:
  httpGet:
    path: /health
    port: 3000
  initialDelaySeconds: 0
  periodSeconds: 5
  failureThreshold: 30    # 30 * 5s = 150s tiempo mÃ¡ximo de inicio
```

## ConfiguraciÃ³n de Entorno

### PatrÃ³n Twelve-Factor App

```bash
# Toda la configuraciÃ³n mediante variables de entorno â nunca en el cÃ³digo
DATABASE_URL=postgres://user:pass@host:5432/db
REDIS_URL=redis://host:6379/0
API_KEY=${API_KEY}           # inyectado por el gestor de secretos
LOG_LEVEL=info
PORT=3000

# Comportamiento especÃ­fico por entorno
NODE_ENV=production          # o staging, development
APP_ENV=production           # entorno de app explÃ­cito
```

### ValidaciÃ³n de ConfiguraciÃ³n

```typescript
import { z } from "zod";

const envSchema = z.object({
  NODE_ENV: z.enum(["development", "staging", "production"]),
  PORT: z.coerce.number().default(3000),
  DATABASE_URL: z.string().url(),
  REDIS_URL: z.string().url(),
  JWT_SECRET: z.string().min(32),
  LOG_LEVEL: z.enum(["debug", "info", "warn", "error"]).default("info"),
});

// Validar al inicio â fallar rÃ¡pido si la configuraciÃ³n es incorrecta
export const env = envSchema.parse(process.env);
```

## Estrategia de Rollback

### Rollback InstantÃ¡neo

```bash
# Docker/Kubernetes: apuntar a imagen anterior
kubectl rollout undo deployment/app

# Vercel: promover despliegue anterior
vercel rollback

# Railway: volver a desplegar commit anterior
railway up --commit <previous-sha>

# Base de datos: revertir migraciÃ³n (si es reversible)
npx prisma migrate resolve --rolled-back <migration-name>
```

### Lista de VerificaciÃ³n de Rollback

- [ ] La imagen/artefacto anterior estÃ¡ disponible y etiquetado
- [ ] Las migraciones de base de datos son compatibles hacia atrÃ¡s (sin cambios destructivos)
- [ ] Los feature flags pueden deshabilitar nuevas funciones sin despliegue
- [ ] Alertas de monitoreo configuradas para picos de tasa de error
- [ ] Rollback probado en staging antes del lanzamiento a producciÃ³n

## Lista de VerificaciÃ³n de PreparaciÃ³n para ProducciÃ³n

Antes de cualquier despliegue a producciÃ³n:

### AplicaciÃ³n
- [ ] Todas las pruebas pasan (unitarias, integraciÃ³n, E2E)
- [ ] Sin secretos hardcodeados en cÃ³digo o archivos de configuraciÃ³n
- [ ] El manejo de errores cubre todos los casos lÃ­mite
- [ ] El logging es estructurado (JSON) y no contiene PII
- [ ] El endpoint de health check retorna estado significativo

### Infraestructura
- [ ] La imagen Docker se construye de forma reproducible (versiones fijadas)
- [ ] Las variables de entorno estÃ¡n documentadas y validadas al inicio
- [ ] LÃ­mites de recursos establecidos (CPU, memoria)
- [ ] Escalado horizontal configurado (instancias mÃ­n/mÃ¡x)
- [ ] SSL/TLS habilitado en todos los endpoints

### Monitoreo
- [ ] MÃ©tricas de aplicaciÃ³n exportadas (tasa de requests, latencia, errores)
- [ ] Alertas configuradas para tasa de error > umbral
- [ ] AgregaciÃ³n de logs configurada (logs estructurados, con bÃºsqueda)
- [ ] Monitoreo de uptime en endpoint de health

### Seguridad
- [ ] Dependencias escaneadas en busca de CVEs
- [ ] CORS configurado solo para orÃ­genes permitidos
- [ ] Rate limiting habilitado en endpoints pÃºblicos
- [ ] AutenticaciÃ³n y autorizaciÃ³n verificadas
- [ ] Headers de seguridad establecidos (CSP, HSTS, X-Frame-Options)

### Operaciones
- [ ] Plan de rollback documentado y probado
- [ ] MigraciÃ³n de base de datos probada contra datos de tamaÃ±o de producciÃ³n
- [ ] Runbook para escenarios de fallo comunes
- [ ] RotaciÃ³n de on-call y ruta de escalaciÃ³n definida
