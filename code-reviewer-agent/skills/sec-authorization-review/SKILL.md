---
name: sec-authorization-review
description: Assessment of access control mechanisms to ensure proper enforcement of permissions and privilege boundaries.
---

# Skill: Authorization Review

## Used By
- [[api-security]]
- [[web-security]]

## Description
Assessment of access control mechanisms to ensure proper enforcement of permissions and privilege boundaries.

## Key Areas
- Role-based access control (RBAC) enforcement
- Object-level authorization (IDOR/BOLA)
- Function-level authorization
- Privilege escalation (vertical and horizontal)
- Path traversal and forced browsing
- API endpoint authorization consistency
- Multi-tenant isolation
- Administrative interface protection
- Feature flag and toggle access control

## Methodology
1. Map all roles and permission levels
2. Test each endpoint with different role tokens
3. Test object access across user boundaries
4. Test privilege escalation vectors
5. Document bypass conditions with evidence
