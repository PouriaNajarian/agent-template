---
description: Systematic code review for Next.js + Hono + Cloudflare projects — correctness, security, performance, and standards
---
# Code Review

Systematic code review for Next.js + Hono + Cloudflare projects. Covers correctness, security, performance, maintainability, test coverage, and adherence to coding standards.

## Steps

1. **Research current best practices** — Search for latest code review best practices and linting rules. Compare findings against existing skills and MCP definitions. Update framework artifacts if a better approach is found.

2. **Define review scope** — Identify the PR diff and changed files. Define review scope and quality criteria. Define severity levels (blocker, warning, suggestion). Define acceptance thresholds.

3. **Run automated checks** — Run ESLint and confirm 0 errors. Run TypeScript type checker and confirm 0 type errors. Run Prettier and confirm all files formatted. Check test coverage meets threshold (>= 80%).

4. **Review correctness** — Check for logic errors, edge cases, and race conditions. Verify proper error handling (try/catch, error propagation, user messages). Check for proper TypeScript types — no `any`, proper generics.

5. **Review security** — Check input validation and sanitization. Look for XSS, CSRF, injection, and auth bypass vulnerabilities. Verify no secrets in code. Check proper use of auth middleware.

6. **Review performance** — Check for unnecessary re-renders, N+1 queries, and bundle size issues. Verify proper use of Server Components vs Client Components. Check Next.js Image component and font optimization. Review Cloudflare Workers for floating promises and global state.

7. **Review test quality** — Verify adequate test coverage for changed code. Check meaningful assertions and edge case coverage. Verify E2E tests cover critical user flows.

8. **Check framework patterns** — Verify Next.js App Router patterns (Server vs Client Components, Server Actions). Check Hono patterns (middleware order, validation, error responses). Verify Cloudflare bindings usage is correct.

9. **Make approval decision** — Compile findings with severity levels. Approve, request changes, or reject with clear rationale. Document any architectural concerns.

## Quality Gates

- [ ] ESLint: 0 errors
- [ ] TypeScript: 0 type errors
- [ ] Prettier: all files formatted
- [ ] Test coverage >= 80%
- [ ] No blocker-level findings
- [ ] Review report compiled
