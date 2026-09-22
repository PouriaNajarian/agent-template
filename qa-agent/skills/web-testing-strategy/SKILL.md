---
name: web-testing-strategy
description: Comprehensive testing strategy for Next.js + Hono + Cloudflare projects. Covers unit testing (Vitest), integration testing, E2E testing (Playwright), test design patterns, coverage analysis, and qu...
---

# Skill: Testing Strategy

## Used By
- [[qa-lead]]
- [[test-engineer]]
- [[tech-lead]]
- [[frontend-dev]]
- [[backend-dev]]
- [[api-dev]]
- [[code-reviewer]]
- [[unit-tester]]
- [[e2e-tester]]

## Description
Comprehensive testing strategy for Next.js + Hono + Cloudflare projects. Covers unit testing (Vitest), integration testing, E2E testing (Playwright), test design patterns, coverage analysis, and quality gates.

## Key Areas
- Unit testing with Vitest (components, handlers, utilities)
- Integration testing for API endpoints and Cloudflare bindings
- E2E testing with Playwright (user flows, visual regression)
- Test data management and fixtures
- Mocking strategies (modules, fetch, Cloudflare bindings)
- Coverage analysis and thresholds
- Boundary value analysis and equivalence partitioning
- Accessibility testing
- Performance testing (Core Web Vitals)
- Test-driven development (TDD) patterns

## MCP Tools
- [[mcp-vitest-testgen]] — Vitest test code generation from specifications
- [[mcp-playwright]] — Browser automation for E2E testing
- [[mcp-chrome-devtools]] — Performance profiling and debugging
- [[mcp-filesystem]] — Read and write test files

## Methodology
1. Define test strategy: unit (70%), integration (20%), E2E (10%)
2. Generate unit tests from specifications using `vitest-testgen`
3. Implement integration tests with Wrangler's `unstable_dev` for Workers
4. Design E2E tests with Playwright for critical user flows
5. Set coverage thresholds (80% statements, 70% branches)
6. Run tests in CI/CD pipeline with parallel execution
7. Analyze failures with Chrome DevTools for debugging
8. Report coverage gaps and quality gate status
