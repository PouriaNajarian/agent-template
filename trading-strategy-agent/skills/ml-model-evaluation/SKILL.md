---
name: ml-model-evaluation
description: Comprehensive model evaluation including metrics, benchmarks, cross-validation, ablation studies, and statistical significance testing. Covers classification, regression, ranking, generation, and L...
---

# Skill: Model Evaluation

## Used By
- [[ml-lead]]
- [[model-evaluator]]
- [[code-reviewer]]
- [[mlops-lead]]

## Description
Comprehensive model evaluation including metrics, benchmarks, cross-validation, ablation studies, and statistical significance testing. Covers classification, regression, ranking, generation, and LLM-specific evaluation.

## Key Areas
- Classification metrics: accuracy, precision, recall, F1, ROC-AUC, PR-AUC, confusion matrix
- Regression metrics: MSE, MAE, RMSE, R2, MAPE
- Ranking metrics: NDCG, MRR, MAP, Hit Rate
- Generation metrics: BLEU, ROUGE, METEOR, BERTScore, perplexity
- LLM evaluation: MMLU, HumanEval, GSM8K, MT-Bench, AlpacaEval, arena Elo
- Cross-validation: k-fold, stratified, time-series, nested
- Ablation studies: component removal, feature importance, architecture variants
- Statistical significance: bootstrap CI, paired t-test, McNemar's test
- Bias and fairness: demographic parity, equalized odds, calibration
- Robustness: adversarial inputs, OOD detection, perturbation tests

## MCP Tools
- [[mlflow]] — Log evaluation metrics, compare model versions
- [[wandb]] — Visualize evaluation results, create comparison tables
- [[huggingface]] — Load evaluation datasets and benchmarks
- [[jupyter]] — Run evaluation notebooks with inline analysis
- [[filesystem]] — Read model checkpoints, write evaluation reports
- [[brave-search]] — Research latest evaluation metrics and benchmarks

## Methodology
1. Define evaluation protocol — metrics, splits, significance tests
2. Prepare evaluation datasets — held-out test, OOD, adversarial
3. Run model inference on all evaluation sets
4. Compute metrics with confidence intervals
5. Compare against baselines and prior model versions
6. Run ablation studies to understand component contributions
7. Check for bias, fairness, and robustness issues
8. Document findings in evaluation report with recommendations
