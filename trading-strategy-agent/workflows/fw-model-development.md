# Workflow: Fw Model Development

**Category:** `framework`  
**Slug:** `fw-model-development`

## Purpose

Framework-style end-to-end ML model development: architecture, parallel implementation, evaluation, documentation.

## Keywords

`ml`, `model`, `development`, `training`, `framework`

## Trigger

Run this workflow when:
- The task matches: ml, model, development
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — ml-web-research

**Skill:** `ml-web-research`  
**Action:** Research latest ML techniques, tools, and frameworks.

```text
1. Invoke skill: ml-web-research
2. Research latest ML techniques, tools, and frameworks.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-writing-plans

**Skill:** `eng-writing-plans`  
**Action:** Define model architecture, training strategy, loss function, evaluation metrics, and implementation plan.

```text
1. Invoke skill: eng-writing-plans
2. Define model architecture, training strategy, loss function, evaluation metrics, and implementation plan.
3. Verify the output before proceeding to the next step
```

### Step 3 — ml-model-development

**Skill:** `ml-model-development`  
**Action:** Implement model architecture, training loop, and experiment tracking.

```text
1. Invoke skill: ml-model-development
2. Implement model architecture, training loop, and experiment tracking.
3. Verify the output before proceeding to the next step
```

### Step 4 — ml-data-pipeline

**Skill:** `ml-data-pipeline`  
**Action:** Implement data loading, preprocessing, and validation pipeline.

```text
1. Invoke skill: ml-data-pipeline
2. Implement data loading, preprocessing, and validation pipeline.
3. Verify the output before proceeding to the next step
```

### Step 5 — ml-feature-engineering

**Skill:** `ml-feature-engineering`  
**Action:** Design and implement feature engineering pipeline.

```text
1. Invoke skill: ml-feature-engineering
2. Design and implement feature engineering pipeline.
3. Verify the output before proceeding to the next step
```

### Step 6 — ml-model-evaluation

**Skill:** `ml-model-evaluation`  
**Action:** Design evaluation protocol, metrics, and test harness.

```text
1. Invoke skill: ml-model-evaluation
2. Design evaluation protocol, metrics, and test harness.
3. Verify the output before proceeding to the next step
```

### Step 7 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Review for correctness, reproducibility, data leakage, and model reproducibility.

```text
1. Invoke skill: eng-code-review-and-quality
2. Review for correctness, reproducibility, data leakage, and model reproducibility.
3. Verify the output before proceeding to the next step
```

### Step 8 — web-documentation

**Skill:** `web-documentation`  
**Action:** Compile model card, training guide, architecture doc, and evaluation results.

```text
1. Invoke skill: web-documentation
2. Compile model card, training guide, architecture doc, and evaluation results.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (ml-web-research): output verified
- [ ] Step 2 (eng-writing-plans): output verified
- [ ] Step 3 (ml-model-development): output verified
- [ ] Step 4 (ml-data-pipeline): output verified
- [ ] Step 5 (ml-feature-engineering): output verified
- [ ] Step 6 (ml-model-evaluation): output verified
- [ ] Step 7 (eng-code-review-and-quality): output verified
- [ ] Step 8 (web-documentation): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-8 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-model-development")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
