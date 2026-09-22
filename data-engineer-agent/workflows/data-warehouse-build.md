# Workflow: Data Warehouse Build

**Category:** `data`  
**Slug:** `data-warehouse-build`

## Purpose

Build a data warehouse: ELT, modeling, reporting, quality.

## Keywords

`warehouse`, `elt`, `modeling`, `reporting`

## Trigger

Run this workflow when:
- The task matches: warehouse, elt, modeling
- A data-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — ml-data-pipeline

**Skill:** `ml-data-pipeline`  
**Action:** ELT ingestion + schema evolution.

```text
1. Invoke skill: ml-data-pipeline
2. ELT ingestion + schema evolution.
3. Verify the output before proceeding to the next step
```

### Step 2 — sql-schema-design

**Skill:** `sql-schema-design`  
**Action:** Star schema + dbt-style models.

```text
1. Invoke skill: sql-schema-design
2. Star schema + dbt-style models.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-performance-optimization

**Skill:** `eng-performance-optimization`  
**Action:** Query optimization + partitioning.

```text
1. Invoke skill: eng-performance-optimization
2. Query optimization + partitioning.
3. Verify the output before proceeding to the next step
```

### Step 4 — eng-observability-and-instrumentation

**Skill:** `eng-observability-and-instrumentation`  
**Action:** Data quality + freshness checks.

```text
1. Invoke skill: eng-observability-and-instrumentation
2. Data quality + freshness checks.
3. Verify the output before proceeding to the next step
```

### Step 5 — cron-scheduler

**Skill:** `cron-scheduler`  
**Action:** Scheduled refreshes + alerting.

```text
1. Invoke skill: cron-scheduler
2. Scheduled refreshes + alerting.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (ml-data-pipeline): output verified
- [ ] Step 2 (sql-schema-design): output verified
- [ ] Step 3 (eng-performance-optimization): output verified
- [ ] Step 4 (eng-observability-and-instrumentation): output verified
- [ ] Step 5 (cron-scheduler): output verified
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

- This workflow belongs to the **data** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("data-warehouse-build")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
