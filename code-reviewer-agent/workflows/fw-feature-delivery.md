# Workflow: Fw Feature Delivery

**Category:** `framework`  
**Slug:** `fw-feature-delivery`

## Purpose

Framework-style end-to-end feature delivery: architecture, parallel development, testing, deployment, documentation.

## Keywords

`feature`, `delivery`, `framework`, `parallel`, `architecture`, `deploy`

## Trigger

Run this workflow when:
- The task matches: feature, delivery, framework
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest skills, tools, and techniques before starting.

```text
1. Invoke skill: web-web-research
2. Research latest skills, tools, and techniques before starting.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-writing-plans

**Skill:** `eng-writing-plans`  
**Action:** Define technical architecture, API contracts, data models, and implementation plan.

```text
1. Invoke skill: eng-writing-plans
2. Define technical architecture, API contracts, data models, and implementation plan.
3. Verify the output before proceeding to the next step
```

### Step 3 — web-nextjs-development

**Skill:** `web-nextjs-development`  
**Action:** Implement Next.js frontend components, pages, and Server Actions in parallel.

```text
1. Invoke skill: web-nextjs-development
2. Implement Next.js frontend components, pages, and Server Actions in parallel.
3. Verify the output before proceeding to the next step
```

### Step 4 — web-hono-api-development

**Skill:** `web-hono-api-development`  
**Action:** Implement Hono backend handlers and Cloudflare Workers logic in parallel.

```text
1. Invoke skill: web-hono-api-development
2. Implement Hono backend handlers and Cloudflare Workers logic in parallel.
3. Verify the output before proceeding to the next step
```

### Step 5 — web-testing-strategy

**Skill:** `web-testing-strategy`  
**Action:** Design and implement unit, integration, and E2E tests in parallel.

```text
1. Invoke skill: web-testing-strategy
2. Design and implement unit, integration, and E2E tests in parallel.
3. Verify the output before proceeding to the next step
```

### Step 6 — web-cloudflare-deployment

**Skill:** `web-cloudflare-deployment`  
**Action:** Configure Cloudflare bindings and deployment configuration in parallel.

```text
1. Invoke skill: web-cloudflare-deployment
2. Configure Cloudflare bindings and deployment configuration in parallel.
3. Verify the output before proceeding to the next step
```

### Step 7 — web-code-review

**Skill:** `web-code-review`  
**Action:** Review all implementations for correctness, security, and quality.

```text
1. Invoke skill: web-code-review
2. Review all implementations for correctness, security, and quality.
3. Verify the output before proceeding to the next step
```

### Step 8 — web-documentation

**Skill:** `web-documentation`  
**Action:** Compile feature documentation, update README, create deployment guide.

```text
1. Invoke skill: web-documentation
2. Compile feature documentation, update README, create deployment guide.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-writing-plans): output verified
- [ ] Step 3 (web-nextjs-development): output verified
- [ ] Step 4 (web-hono-api-development): output verified
- [ ] Step 5 (web-testing-strategy): output verified
- [ ] Step 6 (web-cloudflare-deployment): output verified
- [ ] Step 7 (web-code-review): output verified
- [ ] Step 8 (web-documentation): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-8 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-feature-delivery")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
