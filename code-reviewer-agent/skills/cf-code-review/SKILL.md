---
name: cf-code-review
description: Reviews Workers and Cloudflare Developer Platform code for type correctness, API usage, and configuration validity. Load when reviewing TypeScript/JavaScript Workers code.
---

# Code Review (Cloudflare)

> Source: [mcpservers.org/agent-skills/cloudflare/code-review](https://mcpservers.org/agent-skills/cloudflare/code-review)
> Author: Cloudflare (official)

## Description
Reviews Workers and Cloudflare Developer Platform code for type correctness, API usage, and configuration validity. Load when reviewing TypeScript/JavaScript Workers code.

## Key Checks
- Type correctness — no `any`, proper return types
- API usage — correct Workers API patterns, proper binding access
- Configuration validity — `wrangler.jsonc` matches code bindings
- Error handling — proper try/catch, no swallowed errors
- Security — no secrets in code, proper input validation

## When to Use
- Reviewing Workers code
- Reviewing Cloudflare Platform code
- Checking TypeScript correctness in Workers context
