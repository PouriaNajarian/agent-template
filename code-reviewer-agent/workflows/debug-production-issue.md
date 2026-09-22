# Workflow: Debug Production Issue

**Category:** `operations`  
**Slug:** `debug-production-issue`

## Purpose

Systematically debug a production incident using skills and LLM analysis.

## Keywords

`debug`, `production`, `incident`, `error`, `bug`

## Trigger

Run this workflow when:
- The task matches: debug, production, incident
- A operations-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — dev-systematic-debugging

**Skill:** `dev-systematic-debugging`  
**Action:** Reproduce, isolate, form hypotheses, verify root cause - no random fixes.

```text
1. Invoke skill: dev-systematic-debugging
2. Reproduce, isolate, form hypotheses, verify root cause - no random fixes.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-observability-and-instrumentation

**Skill:** `eng-observability-and-instrumentation`  
**Action:** Add logs/metrics/traces where the signal is missing.

```text
1. Invoke skill: eng-observability-and-instrumentation
2. Add logs/metrics/traces where the signal is missing.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-debugging-and-error-recovery

**Skill:** `eng-debugging-and-error-recovery`  
**Action:** Apply recovery steps, then a permanent fix with a regression test.

```text
1. Invoke skill: eng-debugging-and-error-recovery
2. Apply recovery steps, then a permanent fix with a regression test.
3. Verify the output before proceeding to the next step
```

### Step 4 — web-error-monitoring

**Skill:** `web-error-monitoring`  
**Action:** Check the error tracker for similar past issues and frequency.

```text
1. Invoke skill: web-error-monitoring
2. Check the error tracker for similar past issues and frequency.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (dev-systematic-debugging): output verified
- [ ] Step 2 (eng-observability-and-instrumentation): output verified
- [ ] Step 3 (eng-debugging-and-error-recovery): output verified
- [ ] Step 4 (web-error-monitoring): output verified
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

- This workflow belongs to the **operations** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("debug-production-issue")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
