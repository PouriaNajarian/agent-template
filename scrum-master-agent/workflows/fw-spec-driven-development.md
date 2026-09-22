# Workflow: Fw Spec Driven Development

**Category:** `framework`  
**Slug:** `fw-spec-driven-development`

## Purpose

Framework-style spec-driven development: write structured spec before code, then implement with TDD.

## Keywords

`spec`, `tdd`, `spec-driven`, `framework`

## Trigger

Run this workflow when:
- The task matches: spec, tdd, spec-driven
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest spec-driven development patterns.

```text
1. Invoke skill: web-web-research
2. Research latest spec-driven development patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-spec-driven-development

**Skill:** `eng-spec-driven-development`  
**Action:** Write a structured spec with requirements, acceptance criteria, and constraints.

```text
1. Invoke skill: eng-spec-driven-development
2. Write a structured spec with requirements, acceptance criteria, and constraints.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Implement against the spec with TDD verification.

```text
1. Invoke skill: eng-test-driven-development
2. Implement against the spec with TDD verification.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Verify all spec acceptance criteria are met.

```text
1. Invoke skill: dev-verification-before-completion
2. Verify all spec acceptance criteria are met.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-spec-driven-development): output verified
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

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-spec-driven-development")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
