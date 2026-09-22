---
name: diagram-structurizr
description: Create Structurizr DSL diagrams â C4 model (context, container, component, code). Use for enterprise architecture and C4-compliant documentation.
---

# Structurizr Diagrams Skill

## Purpose
Create C4 model diagrams using Structurizr DSL. C4 (Context, Container, Component, Code) provides a structured approach to architecture documentation at multiple abstraction levels.

## When to Use
- Enterprise architecture documentation
- C4 model compliance (context, container, component, code levels)
- Organization-level system mapping
- When you need multi-level architecture views
- Stakeholder communication (context) vs developer detail (component)

## Trigger Phrases
- "C4 model"
- "structurizr"
- "context diagram"
- "container diagram"
- "component diagram"
- "enterprise architecture"

## C4 Levels

### Level 1 â System Context
```structurizr
workspace "ShopEdge Ecommerce" "Ecommerce platform architecture" {
    model {
        customer = person "Customer" "Browses and purchases products"
        merchant = person "Merchant" "Sells products on platform"
        admin = person "Admin" "Manages platform"

        storefront = softwareSystem "Storefront" "Customer-facing web app"
        adminDash = softwareSystem "Admin Dashboard" "Platform management"
        merchantDash = softwareSystem "Merchant Dashboard" "Merchant management"
        authSystem = softwareSystem "Auth Worker" "Authentication & RBAC"
        apiSystem = softwareSystem "API Worker" "Ecommerce REST API"

        customer -> storefront "Browses, purchases"
        merchant -> merchantDash "Manages products"
        admin -> adminDash "Manages platform"
        storefront -> authSystem "Authenticates"
        storefront -> apiSystem "Fetches products"
        adminDash -> authSystem "Authenticates"
        adminDash -> apiSystem "Manages data"
        merchantDash -> authSystem "Authenticates"
        merchantDash -> apiSystem "Manages products"
    }

    views {
        systemContext storefront "SystemContext" "System Context Diagram" {
            include *
            autoLayout
        }
    }
}
```

### Level 2 â Container
```structurizr
workspace "ShopEdge" {
    model {
        !identifiers structured

        customer = person "Customer"

        storefront = softwareSystem "Storefront" {
            web = container "Web App" "Next.js 15 storefront" "TypeScript"
        }

        authSystem = softwareSystem "Auth Worker" {
            hono = container "Hono API" "Auth API endpoints" "TypeScript"
            d1 = container "D1 Database" "User & role store" "SQLite"
            kv = container "KV Namespace" "Token blacklist" "Key-Value"
        }

        apiSystem = softwareSystem "API Worker" {
            api = container "Hono API" "Ecommerce REST API" "TypeScript"
            d1ecom = container "D1 Database" "Product & order store" "SQLite"
        }

        customer -> storefront.web "Uses"
        storefront.web -> authSystem.hono "JWT auth"
        storefront.web -> apiSystem.api "REST"
        authSystem.hono -> authSystem.d1 "Queries"
        authSystem.hono -> authSystem.kv "Token revocation"
        apiSystem.api -> apiSystem.d1ecom "Queries"
    }

    views {
        container storefront "ContainerView" "Container Diagram" {
            include *
            autoLayout
        }
    }
}
```

### Level 3 â Component
```structurizr
workspace "Auth Worker Components" {
    model {
        authSystem = softwareSystem "Auth Worker"

        authSystem.hono = container "Hono API"

        authController = component "Auth Controller" "Login, register, logout"
        adminController = component "Admin Controller" "Merchant approval, user management"
        rbacMiddleware = component "RBAC Middleware" "Role & approval enforcement"
        userModel = component "User Model" "User CRUD"
        roleModel = component "Role Model" "Role CRUD & assignment"
        jwtUtil = component "JWT Utility" "Token generation & verification"
        passwordUtil = component "Password Utility" "bcrypt hashing"

        authController -> rbacMiddleware
        adminController -> rbacMiddleware
        authController -> userModel
        authController -> jwtUtil
        authController -> passwordUtil
        adminController -> userModel
        adminController -> roleModel
        rbacMiddleware -> jwtUtil
    }

    views {
        component authSystem "ComponentView" "Component Diagram" {
            include *
            autoLayout
        }
    }
}
```

## CLI Usage
```bash
# Install Structurizr CLI
npm install -g structurizr-cli

# Export to PlantUML
structurizr export -workspace workspace.dsl -format plantuml

# Export to Mermaid
structurizr export -workspace workspace.dsl -format mermaid

# View in Structurizr Lite (Docker)
docker run -it --rm -p 8080:8080 -v $(pwd):/usr/local/structurizr structurizr/lite
```

## Best Practices
- Start with Level 1 (Context), then drill down to Level 2 (Container), then Level 3 (Component)
- Use `!identifiers structured` for hierarchical naming
- Keep model and views separate
- Use `autoLayout` for automatic positioning
- Export to PlantUML or Mermaid for Markdown rendering
- One workspace file per system

## File Convention
- Save as `workspace.dsl` in `docs/architecture/`
- Export diagrams to `docs/architecture/diagrams/`

