# Workflow: Api Security Review

**Category:** `security`  
**Slug:** `api-security-review`

## Purpose

Review an API surface for security flaws end-to-end.

## Keywords

`security`, `api`, `review`

## Trigger

Run this workflow when:
- The task matches: security, api, review
- A security-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — eng-security-and-hardening

**Skill:** `eng-security-and-hardening`  
**Action:** Inventory endpoints and trust boundaries.

```text
1. Invoke skill: eng-security-and-hardening
2. Inventory endpoints and trust boundaries.
3. Verify the output before proceeding to the next step
```

### Step 2 — sec-api-review

**Skill:** `sec-api-review`  
**Action:** Review auth, authorization and data exposure.

```text
1. Invoke skill: sec-api-review
2. Review auth, authorization and data exposure.
3. Verify the output before proceeding to the next step
```

### Step 3 — sec-owasp-testing

**Skill:** `sec-owasp-testing`  
**Action:** Run OWASP top-10 checks.

```text
1. Invoke skill: sec-owasp-testing
2. Run OWASP top-10 checks.
3. Verify the output before proceeding to the next step
```

### Step 4 — cf-code-review

**Skill:** `cf-code-review`  
**Action:** Fix findings and verify.

```text
1. Invoke skill: cf-code-review
2. Fix findings and verify.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (eng-security-and-hardening): output verified
- [ ] Step 2 (sec-api-review): output verified
- [ ] Step 3 (sec-owasp-testing): output verified
- [ ] Step 4 (cf-code-review): output verified
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

- This workflow belongs to the **security** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("api-security-review")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
