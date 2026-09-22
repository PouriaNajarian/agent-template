# Workflow: Api Security Hardening

**Category:** `security`  
**Slug:** `api-security-hardening`

## Purpose

Harden an API: auth, input validation, rate limits, audit.

## Keywords

`security`, `api`, `hardening`, `owasp`

## Trigger

Run this workflow when:
- The task matches: security, api, hardening
- A security-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — sec-api-review

**Skill:** `sec-api-review`  
**Action:** Review auth, authz, data exposure.

```text
1. Invoke skill: sec-api-review
2. Review auth, authz, data exposure.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-security-and-hardening

**Skill:** `eng-security-and-hardening`  
**Action:** Fix authn/authz + input validation.

```text
1. Invoke skill: eng-security-and-hardening
2. Fix authn/authz + input validation.
3. Verify the output before proceeding to the next step
```

### Step 3 — api-design

**Skill:** `api-design`  
**Action:** Rate limiting + abuse protection.

```text
1. Invoke skill: api-design
2. Rate limiting + abuse protection.
3. Verify the output before proceeding to the next step
```

### Step 4 — sec-owasp-testing

**Skill:** `sec-owasp-testing`  
**Action:** OWASP top-10 regression checks.

```text
1. Invoke skill: sec-owasp-testing
2. OWASP top-10 regression checks.
3. Verify the output before proceeding to the next step
```

### Step 5 — eng-observability-and-instrumentation

**Skill:** `eng-observability-and-instrumentation`  
**Action:** Audit log + anomaly alerts.

```text
1. Invoke skill: eng-observability-and-instrumentation
2. Audit log + anomaly alerts.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (sec-api-review): output verified
- [ ] Step 2 (eng-security-and-hardening): output verified
- [ ] Step 3 (api-design): output verified
- [ ] Step 4 (sec-owasp-testing): output verified
- [ ] Step 5 (eng-observability-and-instrumentation): output verified
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

- This workflow belongs to the **security** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("api-security-hardening")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
