# Workflow: Fw Penetration Test

**Category:** `framework`  
**Slug:** `fw-penetration-test`

## Purpose

Framework-style authorized penetration testing: scope, parallel assessment, validation, reporting.

## Keywords

`pentest`, `penetration`, `security`, `authorized`, `framework`

## Trigger

Run this workflow when:
- The task matches: pentest, penetration, security
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest penetration testing techniques and tools.

```text
1. Invoke skill: web-web-research
2. Research latest penetration testing techniques and tools.
3. Verify the output before proceeding to the next step
```

### Step 2 — sec-threat-modeling

**Skill:** `sec-threat-modeling`  
**Action:** Define engagement scope, identify targets, confirm authorization, define testing rules.

```text
1. Invoke skill: sec-threat-modeling
2. Define engagement scope, identify targets, confirm authorization, define testing rules.
3. Verify the output before proceeding to the next step
```

### Step 3 — sec-web-assessment

**Skill:** `sec-web-assessment`  
**Action:** Assess web application surface: auth, sessions, input validation, business logic.

```text
1. Invoke skill: sec-web-assessment
2. Assess web application surface: auth, sessions, input validation, business logic.
3. Verify the output before proceeding to the next step
```

### Step 4 — sec-api-security

**Skill:** `sec-api-security`  
**Action:** Assess API surface: REST/GraphQL, JWT, rate limiting, object authz.

```text
1. Invoke skill: sec-api-security
2. Assess API surface: REST/GraphQL, JWT, rate limiting, object authz.
3. Verify the output before proceeding to the next step
```

### Step 5 — sec-infrastructure-review

**Skill:** `sec-infrastructure-review`  
**Action:** Assess infrastructure: exposed services, config, container security, TLS.

```text
1. Invoke skill: sec-infrastructure-review
2. Assess infrastructure: exposed services, config, container security, TLS.
3. Verify the output before proceeding to the next step
```

### Step 6 — sec-cloud-security

**Skill:** `sec-cloud-security`  
**Action:** Assess cloud: IAM, secrets, storage config, network policy.

```text
1. Invoke skill: sec-cloud-security
2. Assess cloud: IAM, secrets, storage config, network policy.
3. Verify the output before proceeding to the next step
```

### Step 7 — sec-dependency-analysis

**Skill:** `sec-dependency-analysis`  
**Action:** Assess dependencies: third-party libraries, known vulnerabilities, license compliance.

```text
1. Invoke skill: sec-dependency-analysis
2. Assess dependencies: third-party libraries, known vulnerabilities, license compliance.
3. Verify the output before proceeding to the next step
```

### Step 8 — sec-vulnerability-validation

**Skill:** `sec-vulnerability-validation`  
**Action:** Validate findings, assess impact, eliminate false positives, document evidence.

```text
1. Invoke skill: sec-vulnerability-validation
2. Validate findings, assess impact, eliminate false positives, document evidence.
3. Verify the output before proceeding to the next step
```

### Step 9 — sec-report-writing

**Skill:** `sec-report-writing`  
**Action:** Create executive summary, document findings, recommend mitigations, assign severity.

```text
1. Invoke skill: sec-report-writing
2. Create executive summary, document findings, recommend mitigations, assign severity.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (sec-threat-modeling): output verified
- [ ] Step 3 (sec-web-assessment): output verified
- [ ] Step 4 (sec-api-security): output verified
- [ ] Step 5 (sec-infrastructure-review): output verified
- [ ] Step 6 (sec-cloud-security): output verified
- [ ] Step 7 (sec-dependency-analysis): output verified
- [ ] Step 8 (sec-vulnerability-validation): output verified
- [ ] Step 9 (sec-report-writing): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-9 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-penetration-test")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
