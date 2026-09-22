# Workflow: Security Audit

**Category:** `security`  
**Slug:** `security-audit`

## Purpose

Audit an application against OWASP Top 10 and harden it.

## Keywords

`security`, `audit`, `owasp`, `harden`

## Trigger

Run this workflow when:
- The task matches: security, audit, owasp
- A security-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — sec-owasp-testing

**Skill:** `sec-owasp-testing`  
**Action:** Run through the OWASP Top 10 categories systematically.

```text
1. Invoke skill: sec-owasp-testing
2. Run through the OWASP Top 10 categories systematically.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-security-and-hardening

**Skill:** `eng-security-and-hardening`  
**Action:** Fix input validation, auth, and data-exposure issues found.

```text
1. Invoke skill: eng-security-and-hardening
2. Fix input validation, auth, and data-exposure issues found.
3. Verify the output before proceeding to the next step
```

### Step 3 — sec-secret-detection

**Skill:** `sec-secret-detection`  
**Action:** Scan the repo for leaked credentials.

```text
1. Invoke skill: sec-secret-detection
2. Scan the repo for leaked credentials.
3. Verify the output before proceeding to the next step
```

### Step 4 — sec-report-writing

**Skill:** `sec-report-writing`  
**Action:** Write findings with severity and remediation steps.

```text
1. Invoke skill: sec-report-writing
2. Write findings with severity and remediation steps.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (sec-owasp-testing): output verified
- [ ] Step 2 (eng-security-and-hardening): output verified
- [ ] Step 3 (sec-secret-detection): output verified
- [ ] Step 4 (sec-report-writing): output verified
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
- Use `get_workflow("security-audit")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
