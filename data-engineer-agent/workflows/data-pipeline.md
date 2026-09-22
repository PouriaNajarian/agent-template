# Workflow: Data Pipeline

**Category:** `data`  
**Slug:** `data-pipeline`

## Purpose

Build a robust ETL data pipeline.

## Keywords

`etl`, `pipeline`, `data`

## Trigger

Run this workflow when:
- The task matches: etl, pipeline, data
- A data-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — ml-data-pipeline

**Skill:** `ml-data-pipeline`  
**Action:** Ingest and validate raw data.

```text
1. Invoke skill: ml-data-pipeline
2. Ingest and validate raw data.
3. Verify the output before proceeding to the next step
```

### Step 2 — ml-feature-engineering

**Skill:** `ml-feature-engineering`  
**Action:** Transform and enrich.

```text
1. Invoke skill: ml-feature-engineering
2. Transform and enrich.
3. Verify the output before proceeding to the next step
```

### Step 3 — cron-scheduler

**Skill:** `cron-scheduler`  
**Action:** Schedule with idempotency.

```text
1. Invoke skill: cron-scheduler
2. Schedule with idempotency.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (ml-data-pipeline): output verified
- [ ] Step 2 (ml-feature-engineering): output verified
- [ ] Step 3 (cron-scheduler): output verified
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

- This workflow belongs to the **data** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("data-pipeline")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
