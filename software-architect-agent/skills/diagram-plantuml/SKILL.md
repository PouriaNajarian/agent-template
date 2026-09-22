---
name: diagram-plantuml
description: Create PlantUML diagrams â UML class, sequence, use case, activity, component, deployment. Use for RUP and formal UML documentation.
---

# PlantUML Diagrams Skill

## Purpose
Create formal UML diagrams using PlantUML. Use for RUP (Rational Unified Process) documentation, formal UML specifications, and detailed component diagrams.

## When to Use
- Formal UML documentation (class, component, deployment)
- RUP-compliant architecture documents
- Use case diagrams
- Activity diagrams (business process)
- Detailed sequence diagrams with alt/loop/opt blocks
- When PlantUML server rendering is available

## Trigger Phrases
- "UML diagram"
- "PlantUML"
- "use case diagram"
- "activity diagram"
- "component diagram"
- "deployment diagram"
- "RUP diagram"

## Diagram Types

### Use Case Diagram
```plantuml
@startuml
left to right direction
actor "Customer" as customer
actor "Merchant" as merchant
actor "Admin" as admin

rectangle "Ecommerce System" {
  usecase "Browse Products" as UC1
  usecase "Add to Cart" as UC2
  usecase "Checkout" as UC3
  usecase "Manage Products" as UC4
  usecase "Approve Merchants" as UC5
  usecase "Login" as UC6
}

customer --> UC1
customer --> UC2
customer --> UC3
merchant --> UC4
admin --> UC5
customer --> UC6
merchant --> UC6
admin --> UC6
@enduml
```

### Activity Diagram
```plantuml
@startuml
start
:User submits registration;
if (Role = merchant?) then (yes)
  :Set approvalStatus = pending;
  :Notify admin;
  :Wait for approval;
  if (Approved?) then (yes)
    :Account active;
  else (no)
    :Account rejected;
  endif
else (no)
  :Set role = customer;
  :Account active;
endif
:Send welcome email;
stop
@enduml
```

### Component Diagram
```plantuml
@startuml
package "Cloudflare Workers" {
  component [Storefront] as storefront
  component [Admin Dashboard] as admin
  component [Merchant Dashboard] as merchant
  component [Auth Worker] as auth
  component [API Worker] as api
}

package "Data Layer" {
  database "D1 Auth DB" as d1auth
  database "D1 Ecom DB" as d1ecom
  database "KV Namespace" as kv
}

storefront --> auth : JWT
storefront --> api : REST
admin --> auth : JWT
admin --> api : REST
merchant --> auth : JWT
merchant --> api : REST
auth --> d1auth
auth --> kv
api --> d1ecom
@enduml
```

### Deployment Diagram
```plantuml
@startuml
node "Cloudflare Edge" as edge {
  node "Storefront Worker" as sw
  node "Admin Worker" as aw
  node "Merchant Worker" as mw
  node "Auth Worker" as authw
  node "API Worker" as apiw
}

database "D1 Auth" as d1a
database "D1 Ecom" as d1e
database "KV" as kv

authw --> d1a
authw --> kv
apiw --> d1e
@enduml
```

### Class Diagram (Formal UML)
```plantuml
@startuml
class User {
  +id: string
  +email: string
  +passwordHash: string
  +approvalStatus: ApprovalStatus
  +roles: Role[]
  +login(password): JWT
  +logout(): void
}

class Role {
  +id: string
  +name: string
  +permissions: Permission[]
}

class Permission {
  +id: string
  +name: string
  +resource: string
  +action: string
}

enum ApprovalStatus {
  PENDING
  APPROVED
  REJECTED
}

User "1" --> "*" Role : has
Role "1" --> "*" Permission : grants
User --> ApprovalStatus
@enduml
```

## CLI Usage
```bash
# Install
npm install -g plantuml

# Generate
plantuml diagram.puml -tsvg

# Or use online server
# https://www.plantuml.com/plantuml/svg/
```

## Best Practices
- Use `left to right direction` for use case diagrams
- Use packages to group components
- Use proper UML notation (arrows, visibility modifiers)
- Keep diagrams focused â one concept per diagram
- Use `skinparam` for styling

## File Convention
- Save as `<name>.puml` in `docs/architecture/diagrams/`
- Export SVG to `docs/architecture/diagrams/<name>.svg`

