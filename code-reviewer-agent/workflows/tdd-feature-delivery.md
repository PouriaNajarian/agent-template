# Workflow: Tdd Feature Delivery

**Category:** `testing`  
**Slug:** `tdd-feature-delivery`

## Purpose

Deliver a feature strictly test-first with coverage and refactor cycles.

## Keywords

`tdd`, `test`, `coverage`, `refactor`

## Trigger

Run this workflow when:
- The task matches: tdd, test, coverage
- A testing-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — dev-test-driven-development

**Skill:** `dev-test-driven-development`  
**Action:** Red-green-refactor loop for each unit of behavior.

```text
1. Invoke skill: dev-test-driven-development
2. Red-green-refactor loop for each unit of behavior.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Cover edge cases: errors, empty input, boundaries.

```text
1. Invoke skill: eng-test-driven-development
2. Cover edge cases: errors, empty input, boundaries.
3. Verify the output before proceeding to the next step
```

### Step 3 — web-testing-strategy

**Skill:** `web-testing-strategy`  
**Action:** Add integration/E2E for the critical path.

```text
1. Invoke skill: web-testing-strategy
2. Add integration/E2E for the critical path.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Run coverage report and full suite; fix regressions.

```text
1. Invoke skill: dev-verification-before-completion
2. Run coverage report and full suite; fix regressions.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (dev-test-driven-development): output verified
- [ ] Step 2 (eng-test-driven-development): output verified
- [ ] Step 3 (web-testing-strategy): output verified
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

- This workflow belongs to the **testing** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("tdd-feature-delivery")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
