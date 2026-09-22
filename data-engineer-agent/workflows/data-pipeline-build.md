# Workflow: Data Pipeline Build

**Category:** `data`  
**Slug:** `data-pipeline-build`

## Purpose

Build a data pipeline from ingestion to storage with validation.

## Keywords

`pipeline`, `etl`, `data`, `ingestion`, `validation`

## Trigger

Run this workflow when:
- The task matches: pipeline, etl, data
- A data-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — ml-data-pipeline

**Skill:** `ml-data-pipeline`  
**Action:** Design ingestion, cleaning, validation, and versioning steps.

```text
1. Invoke skill: ml-data-pipeline
2. Design ingestion, cleaning, validation, and versioning steps.
3. Verify the output before proceeding to the next step
```

### Step 2 — sql-schema-design

**Skill:** `sql-schema-design`  
**Action:** Model the storage schema (keys, indexes, constraints).

```text
1. Invoke skill: sql-schema-design
2. Model the storage schema (keys, indexes, constraints).
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** Test transforms with fixtures before wiring the pipeline.

```text
1. Invoke skill: eng-test-driven-development
2. Test transforms with fixtures before wiring the pipeline.
3. Verify the output before proceeding to the next step
```

### Step 4 — cron-scheduler

**Skill:** `cron-scheduler`  
**Action:** Schedule the pipeline with idempotent runs and failure alerts.

```text
1. Invoke skill: cron-scheduler
2. Schedule the pipeline with idempotent runs and failure alerts.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (ml-data-pipeline): output verified
- [ ] Step 2 (sql-schema-design): output verified
- [ ] Step 3 (eng-test-driven-development): output verified
- [ ] Step 4 (cron-scheduler): output verified
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

- This workflow belongs to the **data** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("data-pipeline-build")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
