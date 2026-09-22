# Workflow: Fw Compliance Audit

**Category:** `framework`  
**Slug:** `fw-compliance-audit`

## Purpose

Framework-style compliance audit: GDPR, CCPA, Google Merchant Center, Facebook/Meta.

## Keywords

`compliance`, `gdpr`, `ccpa`, `audit`, `framework`

## Trigger

Run this workflow when:
- The task matches: compliance, gdpr, ccpa
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest compliance regulations and requirements.

```text
1. Invoke skill: web-web-research
2. Research latest compliance regulations and requirements.
3. Verify the output before proceeding to the next step
```

### Step 2 — ecom-compliance-audit

**Skill:** `ecom-compliance-audit`  
**Action:** Audit for GDPR, CCPA, Google Merchant Center, Facebook/Meta compliance.

```text
1. Invoke skill: ecom-compliance-audit
2. Audit for GDPR, CCPA, Google Merchant Center, Facebook/Meta compliance.
3. Verify the output before proceeding to the next step
```

### Step 3 — web-frontend-regulations

**Skill:** `web-frontend-regulations`  
**Action:** Check frontend compliance: WCAG, EAA, ADA, GDPR cookie consent.

```text
1. Invoke skill: web-frontend-regulations
2. Check frontend compliance: WCAG, EAA, ADA, GDPR cookie consent.
3. Verify the output before proceeding to the next step
```

### Step 4 — web-backend-regulations

**Skill:** `web-backend-regulations`  
**Action:** Check backend compliance: GDPR data processing, SOC 2, HIPAA, audit logging.

```text
1. Invoke skill: web-backend-regulations
2. Check backend compliance: GDPR data processing, SOC 2, HIPAA, audit logging.
3. Verify the output before proceeding to the next step
```

### Step 5 — sec-report-writing

**Skill:** `sec-report-writing`  
**Action:** Write compliance audit report with findings and remediation steps.

```text
1. Invoke skill: sec-report-writing
2. Write compliance audit report with findings and remediation steps.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (ecom-compliance-audit): output verified
- [ ] Step 3 (web-frontend-regulations): output verified
- [ ] Step 4 (web-backend-regulations): output verified
- [ ] Step 5 (sec-report-writing): output verified
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

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-compliance-audit")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
