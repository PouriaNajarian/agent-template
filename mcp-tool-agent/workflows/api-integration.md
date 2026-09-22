# Workflow: Api Integration

**Category:** `integration`  
**Slug:** `api-integration`

## Purpose

Integrate a third-party API with retries and tests.

## Keywords

`api`, `integration`, `client`

## Trigger

Run this workflow when:
- The task matches: api, integration, client
- A integration-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — api-design

**Skill:** `api-design`  
**Action:** Design the client contract.

```text
1. Invoke skill: api-design
2. Design the client contract.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Mock-based unit tests first.

```text
1. Invoke skill: eng-test-driven-development
2. Mock-based unit tests first.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-observability-and-instrumentation

**Skill:** `eng-observability-and-instrumentation`  
**Action:** Add retries, timeouts and logs.

```text
1. Invoke skill: eng-observability-and-instrumentation
2. Add retries, timeouts and logs.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (api-design): output verified
- [ ] Step 2 (eng-test-driven-development): output verified
- [ ] Step 3 (eng-observability-and-instrumentation): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-3 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **integration** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("api-integration")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
