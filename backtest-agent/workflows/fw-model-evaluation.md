# Workflow: Fw Model Evaluation

**Category:** `framework`  
**Slug:** `fw-model-evaluation`

## Purpose

Framework-style model evaluation: metrics, benchmarks, cross-validation, ablation, statistical tests, bias.

## Keywords

`model-evaluation`, `metrics`, `ablation`, `cross-validation`, `framework`

## Trigger

Run this workflow when:
- The task matches: model-evaluation, metrics, ablation
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — ml-web-research

**Skill:** `ml-web-research`  
**Action:** Research latest evaluation metrics and benchmarks.

```text
1. Invoke skill: ml-web-research
2. Research latest evaluation metrics and benchmarks.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-writing-plans

**Skill:** `eng-writing-plans`  
**Action:** Define evaluation protocol, metrics, datasets, cross-validation, ablation, statistical tests, bias criteria.

```text
1. Invoke skill: eng-writing-plans
2. Define evaluation protocol, metrics, datasets, cross-validation, ablation, statistical tests, bias criteria.
3. Verify the output before proceeding to the next step
```

### Step 3 — ml-model-evaluation

**Skill:** `ml-model-evaluation`  
**Action:** Implement and run full evaluation suite: metrics, cross-validation, ablation, statistical tests.

```text
1. Invoke skill: ml-model-evaluation
2. Implement and run full evaluation suite: metrics, cross-validation, ablation, statistical tests.
3. Verify the output before proceeding to the next step
```

### Step 4 — ml-data-pipeline

**Skill:** `ml-data-pipeline`  
**Action:** Prepare evaluation datasets: held-out, OOD, adversarial samples.

```text
1. Invoke skill: ml-data-pipeline
2. Prepare evaluation datasets: held-out, OOD, adversarial samples.
3. Verify the output before proceeding to the next step
```

### Step 5 — ml-model-development

**Skill:** `ml-model-development`  
**Action:** Implement inference scripts and batch evaluation runner.

```text
1. Invoke skill: ml-model-development
2. Implement inference scripts and batch evaluation runner.
3. Verify the output before proceeding to the next step
```

### Step 6 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Review for correctness, statistical validity, and reproducibility.

```text
1. Invoke skill: eng-code-review-and-quality
2. Review for correctness, statistical validity, and reproducibility.
3. Verify the output before proceeding to the next step
```

### Step 7 — web-documentation

**Skill:** `web-documentation`  
**Action:** Compile evaluation report with metrics, ablation results, bias analysis, and recommendations.

```text
1. Invoke skill: web-documentation
2. Compile evaluation report with metrics, ablation results, bias analysis, and recommendations.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (ml-web-research): output verified
- [ ] Step 2 (eng-writing-plans): output verified
- [ ] Step 3 (ml-model-evaluation): output verified
- [ ] Step 4 (ml-data-pipeline): output verified
- [ ] Step 5 (ml-model-development): output verified
- [ ] Step 6 (eng-code-review-and-quality): output verified
- [ ] Step 7 (web-documentation): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-7 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-model-evaluation")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
