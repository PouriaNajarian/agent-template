---
name: diagram-mermaid
description: Create professional Mermaid diagrams â flowcharts, sequence, class, ER, C4, state, Gantt, git graph. Use for README docs, architecture docs, and inline Markdown rendering.
---

# Mermaid Diagrams Skill

## Purpose
Create professional software diagrams using Mermaid's text-based syntax. Diagrams render natively in GitHub, GitLab, VS Code, Notion, Obsidian, and Confluence.

## When to Use
- README documentation
- Architecture docs in Markdown
- Pull request descriptions
- Quick prototype diagrams
- Inline Markdown rendering

## Trigger Phrases
- "create a mermaid diagram"
- "draw a flowchart"
- "sequence diagram for API"
- "ER diagram for database"
- "C4 architecture diagram"
- "state machine diagram"
- "gantt chart for project"

## 9 Diagram Types

### 1. Flowchart
```mermaid
flowchart TD
    A[Start] --> B{Condition}
    B -->|Yes| C[Process A]
    B -->|No| D[Process B]
    C --> E[End]
    D --> E
```

### 2. Sequence Diagram
```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    participant D as Database
    C->>S: POST /api/auth/login
    S->>D: Query user
    D-->>S: User data
    S-->>C: JWT token
```

### 3. Class Diagram
```mermaid
classDiagram
    class User {
        +String id
        +String email
        +String[] roles
        +login()
        +logout()
    }
    class Role {
        +String id
        +String name
    }
    User --> Role : has
```

### 4. Entity Relationship Diagram
```mermaid
erDiagram
    USER ||--o{ USER_ROLE : has
    ROLE ||--o{ USER_ROLE : assigned
    USER {
        string id PK
        string email
        string password_hash
        string approval_status
    }
```

### 5. C4 Architecture (Context)
```mermaid
C4Context
    title System Context Diagram
    person(user, "Customer", "A user of the ecommerce platform")
    system(storefront, "Storefront", "Next.js web app")
    system(auth, "Auth Worker", "Cloudflare Worker auth service")
    system(api, "API Worker", "Cloudflare Worker REST API")
    user --> storefront : browses
    storefront --> auth : authenticates
    storefront --> api : fetches products
```

### 6. State Diagram
```mermaid
stateDiagram-v2
    [*] --> Pending
    Pending --> Approved : admin approves
    Pending --> Rejected : admin rejects
    Approved --> Active : user logs in
    Rejected --> [*]
    Active --> [*]
```

### 7. Git Graph
```mermaid
gitGraph
    commit id: "init"
    branch develop
    checkout develop
    commit id: "feat-1"
    branch feature/auth
    checkout feature/auth
    commit id: "rbac"
    checkout develop
    merge feature/auth
    checkout main
    merge develop
```

### 8. Gantt Chart
```mermaid
gantt
    title Sprint S14 â RBAC Auth System
    dateFormat YYYY-MM-DD
    section Auth Worker
    RBAC implementation :a1, 2026-07-28, 3d
    Seed data & migration :a2, after a1, 2d
    section Frontends
    Remove Logto SDK :b1, 2026-07-31, 2d
    Role checks & approval UI :b2, after b1, 2d
```

### 9. Pie Chart
```mermaid
pie title Users by Role
    "Customer" : 65
    "Merchant" : 20
    "Admin" : 10
    "Super Admin" : 5
```

## Best Practices
- Use `flowchart TD` for top-down, `LR` for left-to-right
- Keep diagrams under 20 nodes for readability
- Use subgraphs to group related components
- Add styling with `classDef` for color-coded nodes
- Export via Mermaid Live Editor or CLI (`mmdc`)

## File Convention
- Save as `<name>.mmd` in `docs/architecture/diagrams/`
- **CRITICAL**: `.mmd` files must contain RAW Mermaid syntax only â NO ` ```mermaid ` code fences
- VS Code Mermaid preview extensions parse `.mmd` files directly; code fences cause rendering errors
- For inline Markdown (`.md` files), USE ` ```mermaid ` code fences as normal
- Export via Mermaid Live Editor or CLI (`mmdc`)

