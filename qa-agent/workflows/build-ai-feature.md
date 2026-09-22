# Workflow: Build Ai Feature

**Category:** `development`  
**Slug:** `build-ai-feature`

## Purpose

Build a new AI-powered feature end-to-end: plan, implement, test, ship.

## Keywords

`ai`, `feature`, `build`, `implement`

## Trigger

Run this workflow when:
- The task matches: ai, feature, build
- A development-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — writing-plans

**Skill:** `writing-plans`  
**Action:** Ask the LLM to write a step-by-step plan with acceptance criteria before coding.

```text
1. Invoke skill: writing-plans
2. Ask the LLM to write a step-by-step plan with acceptance criteria before coding.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-api-and-interface-design

**Skill:** `eng-api-and-interface-design`  
**Action:** Define the public interface/API contract first, then implement against it.

```text
1. Invoke skill: eng-api-and-interface-design
2. Define the public interface/API contract first, then implement against it.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Write failing tests for the core logic, then implement to green.

```text
1. Invoke skill: eng-test-driven-development
2. Write failing tests for the core logic, then implement to green.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Run the full test suite and manual checks before declaring done.

```text
1. Invoke skill: dev-verification-before-completion
2. Run the full test suite and manual checks before declaring done.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (writing-plans): output verified
- [ ] Step 2 (eng-api-and-interface-design): output verified
- [ ] Step 3 (eng-test-driven-development): output verified
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

- This workflow belongs to the **development** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("build-ai-feature")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
