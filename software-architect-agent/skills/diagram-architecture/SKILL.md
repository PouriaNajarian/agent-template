---
name: diagram-architecture
description: Master architecture diagram skill â orchestrates D2, Structurizr, Mermaid, PlantUML, Graphviz, and Excalidraw. Use for HLD, LLD, UML, RUP, C4, Scrum, and project management diagrams. ALWAYS invoke before creating any architecture documentation.
---

# Architecture Diagrams â Master Skill

## Purpose
This is the **master orchestrator** for all diagram types. It defines WHEN to use each tool and provides the standard architecture documentation workflow.

## Diagram Tool Selection Matrix

| Need | Tool | Format | Use Case |
|------|------|--------|----------|
| System architecture (HLD) | **D2** | `.d2` â SVG | Cloud topology, system context |
| C4 enterprise architecture | **Structurizr** | `.dsl` â SVG | Context, container, component |
| README/inline docs | **Mermaid** | `.mmd` â MD | Flowcharts, sequence, ER, Gantt |
| Formal UML (RUP) | **PlantUML** | `.puml` â SVG | Use case, activity, component |
| Dependency/knowledge graphs | **Graphviz** | `.dot` â SVG | Call graphs, module deps |
| Presentations/whiteboard | **Excalidraw** | `.excalidraw` | Hand-drawn sketches |

## Standard Diagram Types by Project Phase

### HLD (High-Level Design)
- **System Context** â D2 or Structurizr Level 1
- **Architecture Overview** â D2 with cloud icons
- **Deployment Topology** â D2 or PlantUML deployment
- **Data Flow** â D2 dataflow diagram

### LLD (Low-Level Design)
- **Container Diagram** â Structurizr Level 2 or D2
- **Component Diagram** â Structurizr Level 3 or PlantUML
- **ER Diagram** â Mermaid or PlantUML
- **Sequence Diagram** â Mermaid or PlantUML

### UML / RUP
- **Use Case** â PlantUML
- **Class Diagram** â PlantUML or Mermaid
- **Activity Diagram** â PlantUML
- **State Diagram** â Mermaid or PlantUML
- **Deployment Diagram** â PlantUML

### Project Management / Scrum
- **Gantt Chart** â Mermaid
- **Burndown Chart** â Mermaid pie/bar
- **Sprint Timeline** â Mermaid gantt
- **Git Flow** â Mermaid gitGraph
- **User Journey** â Mermaid journey

## Standard Documentation Structure

```
docs/
 âââ architecture/
 â    âââ system.json          # Architecture source of truth (JSON model)
 â    âââ containers.dsl       # Structurizr C4 model
 â    âââ architecture.d2      # D2 system architecture
 â    âââ diagrams/
 â         âââ system-context.svg
 â         âââ container-diagram.svg
 â         âââ dataflow.svg
 â         âââ deployment.svg
 â         âââ er-diagram.svg
 â         âââ sequence-auth.svg
 âââ uml/
 â    âââ usecase.puml
 â    âââ class-diagram.puml
 â    âââ activity-auth.puml
 â    âââ diagrams/
 â         âââ usecase.svg
 â         âââ class-diagram.svg
 âââ scrum/
 â    âââ sprint-plan.mmd
 â    âââ gantt-s14.mmd
 â    âââ burndown.mmd
 âââ dependencies/
      âââ module-deps.dot
      âââ call-graph.dot
```

## Architecture Source of Truth (JSON Model)

```json
{
  "system": "ShopEdge Ecommerce Platform",
  "version": "1.0.0",
  "components": [
    {
      "name": "Storefront",
      "type": "frontend",
      "technology": "Next.js 15",
      "platform": "Cloudflare Pages",
      "url": "https://cf-ecom-app.pr-najjarian-jobs.workers.dev"
    },
    {
      "name": "Admin Dashboard",
      "type": "frontend",
      "technology": "Next.js 15",
      "platform": "Cloudflare Pages",
      "url": "https://cf-ecom-admin.pr-najjarian-jobs.workers.dev"
    },
    {
      "name": "Merchant Dashboard",
      "type": "frontend",
      "technology": "Next.js 15",
      "platform": "Cloudflare Pages",
      "url": "https://cf-ecom-merchant.pr-najjarian-jobs.workers.dev"
    },
    {
      "name": "Auth Worker",
      "type": "backend",
      "technology": "Hono + Cloudflare Workers",
      "platform": "Cloudflare Workers",
      "database": "D1 (auth) + KV (token blacklist)",
      "url": "https://logto-cf-auth-api.pr-najjarian-jobs.workers.dev"
    },
    {
      "name": "API Worker",
      "type": "backend",
      "technology": "Hono + Cloudflare Workers",
      "platform": "Cloudflare Workers",
      "database": "D1 (ecommerce)",
      "url": "https://cf-ecom-api.pr-najjarian-jobs.workers.dev"
    }
  ],
  "dataFlows": [
    { "from": "Storefront", "to": "Auth Worker", "protocol": "JWT", "description": "Authentication" },
    { "from": "Storefront", "to": "API Worker", "protocol": "REST", "description": "Product browsing" },
    { "from": "Admin Dashboard", "to": "Auth Worker", "protocol": "JWT", "description": "Admin auth + RBAC" },
    { "from": "Admin Dashboard", "to": "API Worker", "protocol": "REST", "description": "Platform management" },
    { "from": "Merchant Dashboard", "to": "Auth Worker", "protocol": "JWT", "description": "Merchant auth + approval" },
    { "from": "Merchant Dashboard", "to": "API Worker", "protocol": "REST", "description": "Product management" }
  ]
}
```

## Workflow: Architecture-First Development

1. **Before any code change**: Read `docs/architecture/system.json`
2. **Update the JSON model** with new/changed components
3. **Regenerate D2 diagram** from the model
4. **Update Structurizr DSL** if container/component changed
5. **Update Mermaid inline docs** in README
6. **Write code** following the architecture
7. **After code change**: Verify diagrams match implementation
8. **Commit diagrams alongside code** in the same PR

## Rules
- **D2** is the primary architecture visualization tool
- **Structurizr DSL** is the C4 enterprise architecture tool
- **Mermaid** is for README and inline documentation
- **PlantUML** is for formal UML/RUP documentation
- **Graphviz** is for dependency and knowledge graphs
- **Excalidraw** is for presentations and informal sketches
- All diagrams must be stored in `docs/architecture/diagrams/` as SVG
- The JSON model (`system.json`) is the single source of truth
- Diagrams must be updated BEFORE and AFTER any architecture change

