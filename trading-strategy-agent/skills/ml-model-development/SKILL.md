---
name: ml-model-development
description: Model architecture design, training loop implementation, and optimization for deep learning and classical ML. Covers PyTorch, TensorFlow, JAX, Hugging Face Transformers, scikit-learn, and distribut...
---

# Skill: Model Development

## Used By
- [[ml-lead]]
- [[ml-engineer]]
- [[code-reviewer]]

## Description
Model architecture design, training loop implementation, and optimization for deep learning and classical ML. Covers PyTorch, TensorFlow, JAX, Hugging Face Transformers, scikit-learn, and distributed training.

## Key Areas
- Model architecture design: layers, attention, normalization, residual connections
- Training loops: forward pass, loss computation, backprop, gradient clipping
- Optimizers: AdamW, SGD with momentum, LAMB, Lion
- Learning rate schedules: cosine, warmup, step, cyclic
- Regularization: dropout, weight decay, label smoothing, mixup
- Distributed training: DDP, FSDP, DeepSpeed, model parallelism
- Mixed precision: AMP, bf16, fp8
- Gradient accumulation and gradient checkpointing
- Reproducibility: seeding, deterministic ops, experiment tracking

## MCP Tools
- [[mlflow]] — Experiment tracking, model registry, hyperparameter logging
- [[wandb]] — Experiment visualization, model comparison, sweep configs
- [[huggingface]] — Pre-trained models, tokenizers, model hub
- [[context7]] — Up-to-date PyTorch/TensorFlow/JAX documentation
- [[jupyter]] — Prototype model architectures in notebooks
- [[filesystem]] — Read/write model code and configs
- [[brave-search]] — Research latest model architectures and training techniques

## Methodology
1. Define the problem — input/output, loss function, evaluation metric
2. Select or design model architecture based on problem type and data
3. Implement training loop with proper logging, checkpointing, and early stopping
4. Track all experiments in MLflow/W&B — hyperparameters, metrics, artifacts
5. Validate on held-out data, check for overfitting/underfitting
6. Document architecture decisions, training config, and results
