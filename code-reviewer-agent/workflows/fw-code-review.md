# Workflow: Fw Code Review

**Category:** `framework`  
**Slug:** `fw-code-review`

## Purpose

Framework-style systematic code review for quality, security, and best practices.

## Keywords

`code-review`, `quality`, `security`, `lint`, `framework`

## Trigger

Run this workflow when:
- The task matches: code-review, quality, security
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Search for latest code review best practices and linting rules.

```text
1. Invoke skill: web-web-research
2. Search for latest code review best practices and linting rules.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Define review scope, quality criteria, and severity levels.

```text
1. Invoke skill: eng-code-review-and-quality
2. Define review scope, quality criteria, and severity levels.
3. Verify the output before proceeding to the next step
```

### Step 3 — web-code-review

**Skill:** `web-code-review`  
**Action:** Review code for correctness, security, performance, and maintainability.

```text
1. Invoke skill: web-code-review
2. Review code for correctness, security, performance, and maintainability.
3. Verify the output before proceeding to the next step
```

### Step 4 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Assess test coverage and quality.

```text
1. Invoke skill: eng-test-driven-development
2. Assess test coverage and quality.
3. Verify the output before proceeding to the next step
```

### Step 5 — dev-requesting-code-review

**Skill:** `dev-requesting-code-review`  
**Action:** Final review and approval decision.

```text
1. Invoke skill: dev-requesting-code-review
2. Final review and approval decision.
3. Verify the output before proceeding to the next step
```

### Step 6 — web-documentation

**Skill:** `web-documentation`  
**Action:** Compile review report with findings, severity, and recommendations.

```text
1. Invoke skill: web-documentation
2. Compile review report with findings, severity, and recommendations.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-code-review-and-quality): output verified
- [ ] Step 3 (web-code-review): output verified
- [ ] Step 4 (eng-test-driven-development): output verified
- [ ] Step 5 (dev-requesting-code-review): output verified
- [ ] Step 6 (web-documentation): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-6 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-code-review")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
