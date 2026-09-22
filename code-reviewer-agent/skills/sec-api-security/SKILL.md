---
name: sec-api-security
description: Security assessment of REST and GraphQL APIs, including authentication, authorization, and data exposure.
---

# Skill: API Security

## Used By
- [[api-security]]

## Description
Security assessment of REST and GraphQL APIs, including authentication, authorization, and data exposure.

## Key Areas
- REST API endpoint enumeration and testing
- GraphQL query/mutation analysis, introspection, batching attacks
- JWT validation (algorithm confusion, expired tokens, key confusion)
- Rate limiting and quota bypass testing
- Object-level authorization (IDOR/BOLA)
- Mass assignment vulnerabilities
- Excessive data exposure in responses
- API parameter tampering
- HTTP method tampering

## Methodology
1. Enumerate all API endpoints via documentation and discovery
2. Test authentication and session management
3. Test authorization at object and function level
4. Test input validation and injection vectors
5. Test rate limiting and abuse scenarios
6. Document findings with reproducible evidence
