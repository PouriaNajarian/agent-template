---
name: web-code-review
description: Systematic code review for Next.js + Hono + Cloudflare projects. Covers correctness, readability, maintainability, security, performance, TypeScript type safety, and adherence to coding standards.
---

# Skill: Code Review

## Used By
- [[tech-lead]]
- [[code-reviewer]]
- [[qa-lead]]
- [[linter]]

## Description
Systematic code review for Next.js + Hono + Cloudflare projects. Covers correctness, readability, maintainability, security, performance, TypeScript type safety, and adherence to coding standards.

## Key Areas
- Correctness: logic errors, edge cases, race conditions
- TypeScript: type safety, `any` avoidance, proper generics
- Security: input validation, XSS, CSRF, injection, auth bypass
- Performance: unnecessary re-renders, N+1 queries, bundle size
- Readability: naming, complexity, function length, comments
- Maintainability: coupling, cohesion, DRY, SOLID
- Error handling: proper try/catch, error propagation, user messages
- Test coverage: adequate tests, meaningful assertions, edge cases
- Next.js patterns: Server vs Client Components, Server Actions
- Hono patterns: middleware order, validation, error responses

## MCP Tools
- [[mcp-github]] — PR review, code search, and repository analysis
- [[mcp-filesystem]] — Read source files for review
- [[mcp-graphify]] — Query codebase structure and dependencies
- [[mcp-deepwiki]] — AI-powered codebase context for review
- [[mcp-context7]] — Verify current best practices

## Methodology
1. Read the PR diff and understand the change scope
2. Query Graphify for affected files and dependencies
3. Check TypeScript types and ESLint/Prettier compliance
4. Review logic for correctness and edge cases
5. Check security: input validation, auth, data exposure
6. Review performance: re-renders, queries, bundle size
7. Verify test coverage and test quality
8. Check adherence to Next.js and Hono best practices
9. Write structured review with severity levels (blocker, warning, suggestion)
10. Approve, request changes, or reject with clear rationale
