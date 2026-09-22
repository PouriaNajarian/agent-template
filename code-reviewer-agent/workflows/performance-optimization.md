# Workflow: Performance Optimization

**Category:** `performance`  
**Slug:** `performance-optimization`

## Purpose

Profile and optimize an application's performance end-to-end.

## Keywords

`performance`, `optimize`, `profile`, `latency`, `vitals`, `speed`, `slow`, `load`, `fast`

## Trigger

Run this workflow when:
- The task matches: performance, optimize, profile
- A performance-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-performance-optimization

**Skill:** `web-performance-optimization`  
**Action:** Measure Core Web Vitals / load time before changing anything.

```text
1. Invoke skill: web-performance-optimization
2. Measure Core Web Vitals / load time before changing anything.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-performance-optimization

**Skill:** `eng-performance-optimization`  
**Action:** Profile to find the real bottleneck, then optimize it.

```text
1. Invoke skill: eng-performance-optimization
2. Profile to find the real bottleneck, then optimize it.
3. Verify the output before proceeding to the next step
```

### Step 3 — redis-caching

**Skill:** `redis-caching`  
**Action:** Add caching where queries are hot and safe to cache.

```text
1. Invoke skill: redis-caching
2. Add caching where queries are hot and safe to cache.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Re-measure and confirm improvement with before/after numbers.

```text
1. Invoke skill: dev-verification-before-completion
2. Re-measure and confirm improvement with before/after numbers.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-performance-optimization): output verified
- [ ] Step 2 (eng-performance-optimization): output verified
- [ ] Step 3 (redis-caching): output verified
- [ ] Step 4 (dev-verification-before-completion): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-4 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **performance** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("performance-optimization")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
