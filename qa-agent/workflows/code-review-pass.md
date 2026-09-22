# Workflow: Code Review Pass

**Category:** `quality`  
**Slug:** `code-review-pass`

## Purpose

Review a code change for correctness, security, and maintainability.

## Keywords

`review`, `pr`, `merge`, `quality`

## Trigger

Run this workflow when:
- The task matches: review, pr, merge
- A quality-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Review across correctness, security, readability, maintainability.

```text
1. Invoke skill: eng-code-review-and-quality
2. Review across correctness, security, readability, maintainability.
3. Verify the output before proceeding to the next step
```

### Step 2 — sec-authentication-review

**Skill:** `sec-authentication-review`  
**Action:** Check auth/session handling in the diff.

```text
1. Invoke skill: sec-authentication-review
2. Check auth/session handling in the diff.
3. Verify the output before proceeding to the next step
```

### Step 3 — web-code-review

**Skill:** `web-code-review`  
**Action:** Apply stack-specific review checklist.

```text
1. Invoke skill: web-code-review
2. Apply stack-specific review checklist.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-requesting-code-review

**Skill:** `dev-requesting-code-review`  
**Action:** Summarize findings for the author with priorities.

```text
1. Invoke skill: dev-requesting-code-review
2. Summarize findings for the author with priorities.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (eng-code-review-and-quality): output verified
- [ ] Step 2 (sec-authentication-review): output verified
- [ ] Step 3 (web-code-review): output verified
- [ ] Step 4 (dev-requesting-code-review): output verified
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

- This workflow belongs to the **quality** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("code-review-pass")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
