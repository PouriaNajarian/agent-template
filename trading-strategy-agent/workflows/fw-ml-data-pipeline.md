# Workflow: Fw Ml Data Pipeline

**Category:** `framework`  
**Slug:** `fw-ml-data-pipeline`

## Purpose

Framework-style ML data pipeline: ingestion, cleaning, feature engineering, DVC versioning, validation.

## Keywords

`data-pipeline`, `etl`, `dvc`, `feature-engineering`, `framework`

## Trigger

Run this workflow when:
- The task matches: data-pipeline, etl, dvc
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — ml-web-research

**Skill:** `ml-web-research`  
**Action:** Research latest data engineering tools and techniques.

```text
1. Invoke skill: ml-web-research
2. Research latest data engineering tools and techniques.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-writing-plans

**Skill:** `eng-writing-plans`  
**Action:** Define data architecture, quality standards, DVC stages, splitting strategy.

```text
1. Invoke skill: eng-writing-plans
2. Define data architecture, quality standards, DVC stages, splitting strategy.
3. Verify the output before proceeding to the next step
```

### Step 3 — ml-data-pipeline

**Skill:** `ml-data-pipeline`  
**Action:** Implement data ingestion, cleaning, preprocessing, and DVC pipeline.

```text
1. Invoke skill: ml-data-pipeline
2. Implement data ingestion, cleaning, preprocessing, and DVC pipeline.
3. Verify the output before proceeding to the next step
```

### Step 4 — ml-feature-engineering

**Skill:** `ml-feature-engineering`  
**Action:** Implement feature engineering, selection, and transformation pipeline.

```text
1. Invoke skill: ml-feature-engineering
2. Implement feature engineering, selection, and transformation pipeline.
3. Verify the output before proceeding to the next step
```

### Step 5 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Review for correctness, reproducibility, and data leakage prevention.

```text
1. Invoke skill: eng-code-review-and-quality
2. Review for correctness, reproducibility, and data leakage prevention.
3. Verify the output before proceeding to the next step
```

### Step 6 — web-documentation

**Skill:** `web-documentation`  
**Action:** Compile data dictionary, pipeline diagram, and quality report.

```text
1. Invoke skill: web-documentation
2. Compile data dictionary, pipeline diagram, and quality report.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (ml-web-research): output verified
- [ ] Step 2 (eng-writing-plans): output verified
- [ ] Step 3 (ml-data-pipeline): output verified
- [ ] Step 4 (ml-feature-engineering): output verified
- [ ] Step 5 (eng-code-review-and-quality): output verified
- [ ] Step 6 (web-documentation): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-6 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-ml-data-pipeline")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
