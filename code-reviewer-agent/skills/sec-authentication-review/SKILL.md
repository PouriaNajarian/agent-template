---
name: sec-authentication-review
description: Assessment of authentication mechanisms including session management, credential handling, and identity verification.
---

# Skill: Authentication Review

## Used By
- [[api-security]]
- [[web-security]]

## Description
Assessment of authentication mechanisms including session management, credential handling, and identity verification.

## Key Areas
- Login mechanisms and credential validation
- Multi-factor authentication (MFA) bypass
- Session token generation, rotation, and invalidation
- Password policies and reset flows
- JWT structure, signing algorithm, expiration, claims
- OAuth/OIDC flow validation
- Credential stuffing and brute force protection
- Session fixation and hijacking vectors
- Remember-me token security

## Methodology
1. Map all authentication endpoints and flows
2. Test credential handling and storage
3. Test session lifecycle (creation, rotation, destruction)
4. Test MFA implementation and bypass vectors
5. Test password reset/account recovery flows
6. Document findings with CVSS ratings
