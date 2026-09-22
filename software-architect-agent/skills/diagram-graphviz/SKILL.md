---
name: diagram-graphviz
description: Create Graphviz DOT diagrams â dependency graphs, knowledge graphs, call graphs, tree structures. Use for dependency analysis and knowledge graph visualization.
---

# Graphviz Diagrams Skill

## Purpose
Create dependency graphs, knowledge graphs, call graphs, and tree structures using Graphviz DOT language. Use for analyzing code dependencies, module relationships, and knowledge graph visualization.

## When to Use
- Dependency graphs (module/package dependencies)
- Call graphs (function/method call relationships)
- Knowledge graphs (concept relationships)
- Tree structures (organization, file system)
- Decision trees
- Any directed/undirected graph structure

## Trigger Phrases
- "dependency graph"
- "knowledge graph"
- "call graph"
- "graphviz"
- "DOT diagram"
- "module dependencies"

## Basic Syntax

### Dependency Graph
```dot
digraph dependencies {
    rankdir=LR
    node [shape=box, style=filled, fillcolor=lightblue]

    storefront [label="Storefront\n(Next.js)"]
    admin [label="Admin Dashboard\n(Next.js)"]
    merchant [label="Merchant Dashboard\n(Next.js)"]
    authWorker [label="Auth Worker\n(Hono)"]
    apiWorker [label="API Worker\n(Hono)"]
    d1Auth [label="D1 Auth DB", shape=cylinder, fillcolor=lightgreen]
    d1Ecom [label="D1 Ecom DB", shape=cylinder, fillcolor=lightgreen]
    kv [label="KV Namespace", shape=cylinder, fillcolor=lightyellow]

    storefront -> authWorker [label="JWT"]
    storefront -> apiWorker [label="REST"]
    admin -> authWorker [label="JWT"]
    admin -> apiWorker [label="REST"]
    merchant -> authWorker [label="JWT"]
    merchant -> apiWorker [label="REST"]
    authWorker -> d1Auth
    authWorker -> kv
    apiWorker -> d1Ecom
}
```

### Knowledge Graph
```dot
digraph knowledge {
    rankdir=TB
    node [shape=ellipse, style=filled]

    auth [label="Auth System", fillcolor="#dbeafe"]
    rbac [label="RBAC", fillcolor="#fef3c7"]
    roles [label="Roles", fillcolor="#dcfce7"]
    users [label="Users", fillcolor="#dcfce7"]
    middleware [label="Middleware", fillcolor="#fce7f3"]
    jwt [label="JWT", fillcolor="#e0e7ff"]
    bcrypt [label="bcrypt", fillcolor="#e0e7ff"]
    d1 [label="D1 Database", fillcolor="#ccfbf1"]

    auth -> rbac
    auth -> jwt
    auth -> bcrypt
    auth -> d1
    rbac -> roles
    rbac -> users
    rbac -> middleware
    roles -> d1
    users -> d1
    middleware -> jwt
}
```

### Call Graph
```dot
digraph callgraph {
    rankdir=TB
    node [shape=box, style=rounded]

    login [label="auth.login()"]
    verify [label="password.verify()"]
    genToken [label="jwt.generate()"]
    getUser [label="userModel.getByEmail()"]
    assignRole [label="roleModel.getUserRoles()"]

    login -> getUser
    login -> verify
    login -> genToken
    login -> assignRole

    register [label="auth.register()"]
    hash [label="password.hash()"]
    create [label="userModel.create()"]
    setRole [label="roleModel.assignRole()"]

    register -> hash
    register -> create
    register -> setRole
}
```

## CLI Usage
```bash
# Install
# Windows: winget install graphviz
# Mac: brew install graphviz

# Render
dot -Tsvg diagram.dot -o diagram.svg
dot -Tpng diagram.dot -o diagram.png

# With layout engine
neato -Tsvg diagram.dot -o diagram.svg  # spring model
fdp -Tsvg diagram.dot -o diagram.svg    # force-directed
```

## Best Practices
- Use `rankdir=LR` for dependency flows, `TB` for hierarchies
- Use `shape=cylinder` for databases, `shape=box` for services
- Color-code by layer (frontend, backend, data)
- Use `style=filled` with `fillcolor` for visual grouping
- Keep under 30 nodes per diagram
- Use `constraint=false` for cross-hierarchy edges

## File Convention
- Save as `<name>.dot` in `docs/architecture/diagrams/`
- Export SVG to `docs/architecture/diagrams/<name>.svg`

