---
name: diagram-d2
description: Create D2 architecture diagrams â system context, containers, dataflow, deployment. Use for HLD/LLD architecture visualization with SVG export. D2 is the primary architecture diagram tool.
---

# D2 Diagrams Skill

## Purpose
D2 is a modern diagram scripting language for creating professional architecture diagrams. Use as the **primary tool** for system architecture, HLD, LLD, and deployment diagrams with SVG export.

## When to Use
- System architecture diagrams (HLD)
- Container and component diagrams (LLD)
- Dataflow diagrams
- Deployment topology diagrams
- Cloud architecture (AWS, Cloudflare, GCP)
- Any diagram that needs SVG/PDF export

## Trigger Phrases
- "create architecture diagram"
- "D2 diagram"
- "system context diagram"
- "deployment diagram"
- "dataflow diagram"
- "HLD diagram"
- "LLD diagram"

## Basic Syntax

### System Context
```d2
direction: right

user: Customer {
  shape: person
}
storefront: Storefront {
  tooltip: "Next.js 15"
  style.fill: "#dbeafe"
}
auth_worker: Auth Worker {
  tooltip: "Hono + Cloudflare Worker"
  style.fill: "#fef3c7"
}
api_worker: API Worker {
  tooltip: "Hono + Cloudflare Worker"
  style.fill: "#fef3c7"
}
d1: D1 Database {
  shape: cylinder
  style.fill: "#dcfce7"
}
kv: KV Namespace {
  shape: cylinder
  style.fill: "#dcfce7"
}

user -> storefront: browses
storefront -> auth_worker: authenticates
storefront -> api_worker: fetches products
api_worker -> d1: queries
auth_worker -> d1: user store
auth_worker -> kv: token blacklist
```

### Container Diagram
```d2
direction: down

cf_edge: Cloudflare Edge {
  storefront: Storefront {
    tooltip: "Next.js 15"
    style.fill: "#dbeafe"
  }
  admin: Admin Dashboard {
    tooltip: "Next.js 15"
    style.fill: "#dbeafe"
  }
  merchant: Merchant Dashboard {
    tooltip: "Next.js 15"
    style.fill: "#dbeafe"
  }
  auth_api: Auth API {
    tooltip: "Hono Worker"
    style.fill: "#fef3c7"
  }
  ecom_api: Ecommerce API {
    tooltip: "Hono Worker"
    style.fill: "#fef3c7"
  }
}

data_layer: Data Layer {
  d1_auth: D1 Auth DB {
    shape: cylinder
    style.fill: "#dcfce7"
  }
  d1_ecom: D1 Ecom DB {
    shape: cylinder
    style.fill: "#dcfce7"
  }
  kv_auth: KV Namespace {
    shape: cylinder
    style.fill: "#dcfce7"
  }
}

storefront -> auth_api: JWT auth
admin -> auth_api: JWT auth
merchant -> auth_api: JWT auth
storefront -> ecom_api: REST
admin -> ecom_api: REST
merchant -> ecom_api: REST
auth_api -> d1_auth
ecom_api -> d1_ecom
auth_api -> kv_auth
```

### Dataflow
```d2
direction: right

customer: Customer {
  shape: person
}
storefront: Storefront {
  style.fill: "#dbeafe"
}
auth: Auth Worker {
  style.fill: "#fef3c7"
}
api: API Worker {
  style.fill: "#fef3c7"
}
d1: D1 Database {
  shape: cylinder
  style.fill: "#dcfce7"
}

customer -> storefront: 1. Browse products
storefront -> auth: 2. Check JWT
auth -> d1: 3. Verify user
d1 -> auth: 4. User data
auth -> storefront: 5. Valid token
storefront -> api: 6. GET /products
api -> d1: 7. Query products
d1 -> api: 8. Product list
api -> storefront: 9. JSON response
storefront -> customer: 10. Render page
```

### Styled Diagram
```d2
direction: right
style: {
  fill: transparent
  stroke: "#2563eb"
  font-color: "#1e293b"
}

frontend: Frontend {
  style.fill: "#dbeafe"
}
backend: Backend {
  style.fill: "#fef3c7"
}
database: Database {
  style.fill: "#dcfce7"
  shape: cylinder
}

frontend -> backend: HTTPS
backend -> database: SQL
```

## CLI Usage
```bash
# Install
npm install -g @terrastruct/d2

# Render to SVG
d2 diagram.d2 diagram.svg

# Render with layout engine
d2 --layout=elk diagram.d2 diagram.svg

# Watch mode
d2 --watch diagram.d2
```

## Best Practices
- Use `direction: right` for system context, `down` for container/deployment
- Use `shape: person` for human actors (NOT `icon: person`)
- Use `shape: cylinder` for databases
- Use `tooltip: "description"` for metadata (NOT `type:` which is invalid)
- Use `style.fill: "#hexcolor"` for color-coded components
- Group related components with nested blocks
- Keep diagrams under 15 components per level
- Export as SVG for docs, PNG for presentations

## CRITICAL â Common Mistakes That Cause Freeze/Hang
- **NEVER use `icon:` with bare names** like `icon: nextjs` or `icon: cloudflare`
  - `icon:` expects a URL (`https://icons.terrastruct.com/...`) or local file path
  - Bare names cause the renderer to hang trying to fetch a non-existent resource
  - If you don't have a URL, just omit `icon:` entirely and use `style.fill` for visual distinction
- **NEVER use `type:` as a field** â it is NOT a valid D2 keyword
  - It gets parsed as a nested shape, causing unexpected rendering behavior
  - Use `tooltip: "text"` instead for metadata annotations
- **NEVER use `icon: person`** for human actors
  - Use `shape: person` instead â it renders a person icon natively
- **NEVER use `label:` with commas** for multi-value labels
  - Use `tooltip: "comma, separated, values"` inside quotes instead

## Valid Icon URLs (from icons.terrastruct.com)
- Cloudflare: `https://icons.terrastruct.com/dev/cloudflare.svg`
- React: `https://icons.terrastruct.com/dev/react.svg`
- GitHub: `https://icons.terrastruct.com/dev/github.svg`
- Docker: `https://icons.terrastruct.com/dev/docker.svg`
- AWS: `https://icons.terrastruct.com/aws/...`
- Browse all: https://icons.terrastruct.com

## File Convention
- Save as `<name>.d2` in `docs/architecture/diagrams/`
- Export SVG to `docs/architecture/diagrams/<name>.svg`
- **`.d2` files contain raw D2 syntax only** â no markdown fences

