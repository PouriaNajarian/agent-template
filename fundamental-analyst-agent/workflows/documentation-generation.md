# Workflow: Documentation Generation

**Category:** `docs`  
**Slug:** `documentation-generation`

## Purpose

Generate project documentation (README, API docs, changelog).

## Keywords

`documentation`, `readme`, `docs`, `changelog`

## Trigger

Run this workflow when:
- The task matches: documentation, readme, docs
- A docs-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-documentation

**Skill:** `web-documentation`  
**Action:** Structure: README, API reference, deployment guide, ADRs.

```text
1. Invoke skill: web-documentation
2. Structure: README, API reference, deployment guide, ADRs.
3. Verify the output before proceeding to the next step
```

### Step 2 — claude-docx

**Skill:** `claude-docx`  
**Action:** Produce Word deliverables if requested.

```text
1. Invoke skill: claude-docx
2. Produce Word deliverables if requested.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-documentation-and-adrs

**Skill:** `eng-documentation-and-adrs`  
**Action:** Record architecture decisions as ADRs.

```text
1. Invoke skill: eng-documentation-and-adrs
2. Record architecture decisions as ADRs.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Verify commands in docs actually run.

```text
1. Invoke skill: dev-verification-before-completion
2. Verify commands in docs actually run.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-documentation): output verified
- [ ] Step 2 (claude-docx): output verified
- [ ] Step 3 (eng-documentation-and-adrs): output verified
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

- This workflow belongs to the **docs** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("documentation-generation")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
