# Workflow: Fw Verification Loop

**Category:** `framework`  
**Slug:** `fw-verification-loop`

## Purpose

Framework-style verification loop: treat tests as the executable definition of done.

## Keywords

`verification`, `tests`, `done`, `framework`

## Trigger

Run this workflow when:
- The task matches: verification, tests, done
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest verification loop patterns.

```text
1. Invoke skill: web-web-research
2. Research latest verification loop patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Run verification commands and confirm output before declaring success.

```text
1. Invoke skill: dev-verification-before-completion
2. Run verification commands and confirm output before declaring success.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Ensure tests are the executable definition of done, not an afterthought.

```text
1. Invoke skill: eng-test-driven-development
2. Ensure tests are the executable definition of done, not an afterthought.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (dev-verification-before-completion): output verified
- [ ] Step 3 (eng-test-driven-development): output verified
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

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-verification-loop")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
