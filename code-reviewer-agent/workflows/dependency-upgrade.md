# Workflow: Dependency Upgrade

**Category:** `maintenance`  
**Slug:** `dependency-upgrade`

## Purpose

Upgrade dependencies safely with changelog review.

## Keywords

`dependencies`, `upgrade`, `changelog`

## Trigger

Run this workflow when:
- The task matches: dependencies, upgrade, changelog
- A maintenance-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — dependency-doctor

**Skill:** `dependency-doctor`  
**Action:** Audit the manifest for footguns.

```text
1. Invoke skill: dependency-doctor
2. Audit the manifest for footguns.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Run the full test suite.

```text
1. Invoke skill: eng-test-driven-development
2. Run the full test suite.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-deprecation-and-migration

**Skill:** `eng-deprecation-and-migration`  
**Action:** Apply breaking changes incrementally.

```text
1. Invoke skill: eng-deprecation-and-migration
2. Apply breaking changes incrementally.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (dependency-doctor): output verified
- [ ] Step 2 (eng-test-driven-development): output verified
- [ ] Step 3 (eng-deprecation-and-migration): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-3 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **maintenance** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("dependency-upgrade")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
