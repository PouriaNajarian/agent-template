# Workflow: Test Strategy Rollout

**Category:** `testing`  
**Slug:** `test-strategy-rollout`

## Purpose

Establish a test strategy: unit, integration, E2E, coverage gates.

## Keywords

`testing`, `strategy`, `coverage`, `e2e`

## Trigger

Run this workflow when:
- The task matches: testing, strategy, coverage
- A testing-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-testing-strategy

**Skill:** `web-testing-strategy`  
**Action:** Define pyramid + risk matrix.

```text
1. Invoke skill: web-testing-strategy
2. Define pyramid + risk matrix.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Unit/integration suites per module.

```text
1. Invoke skill: eng-test-driven-development
2. Unit/integration suites per module.
3. Verify the output before proceeding to the next step
```

### Step 3 — e2e-testing

**Skill:** `e2e-testing`  
**Action:** Critical user journeys with Playwright.

```text
1. Invoke skill: e2e-testing
2. Critical user journeys with Playwright.
3. Verify the output before proceeding to the next step
```

### Step 4 — web-ci-cd

**Skill:** `web-ci-cd`  
**Action:** Coverage + flake gates in CI.

```text
1. Invoke skill: web-ci-cd
2. Coverage + flake gates in CI.
3. Verify the output before proceeding to the next step
```

### Step 5 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Mutation spot-checks on hot paths.

```text
1. Invoke skill: eng-code-review-and-quality
2. Mutation spot-checks on hot paths.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-testing-strategy): output verified
- [ ] Step 2 (eng-test-driven-development): output verified
- [ ] Step 3 (e2e-testing): output verified
- [ ] Step 4 (web-ci-cd): output verified
- [ ] Step 5 (eng-code-review-and-quality): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-5 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **testing** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("test-strategy-rollout")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
