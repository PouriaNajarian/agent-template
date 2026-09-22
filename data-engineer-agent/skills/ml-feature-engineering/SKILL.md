---
name: ml-feature-engineering
description: Feature selection, transformation, encoding, and scaling for ML pipelines. Covers numerical, categorical, text, image, and time-series features, plus automated feature engineering and feature stores.
---

# Skill: Feature Engineering

## Used By
- [[data-lead]]
- [[feature-engineer]]
- [[data-engineer]]
- [[ml-engineer]]

## Description
Feature selection, transformation, encoding, and scaling for ML pipelines. Covers numerical, categorical, text, image, and time-series features, plus automated feature engineering and feature stores.

## Key Areas
- Numerical features: scaling (Standard, MinMax, Robust), transformation (log, Box-Cox), binning
- Categorical features: one-hot, label, target, frequency, hash encoding, embeddings
- Text features: TF-IDF, Count, hashing, word/sentence embeddings, BERT embeddings
- Image features: pixel, HOG, SIFT, CNN features, ViT features
- Time-series features: lag, rolling, expanding, seasonal decomposition, Fourier
- Feature selection: filter (correlation, mutual info), wrapper (RFE), embedded (L1, SHAP)
- Feature interactions: polynomial, manual, automated (featuretools)
- Feature stores: online/offline serving, feature freshness, point-in-time correctness
- Dimensionality reduction: PCA, UMAP, t-SNE, autoencoders

## MCP Tools
- [[dvc]] — Version feature pipelines and track feature lineage
- [[jupyter]] — Exploratory feature analysis and visualization
- [[filesystem]] — Read/write feature configs and transformed data
- [[brave-search]] — Research latest feature engineering techniques

## Methodology
1. Analyze raw features — distributions, correlations, missing rates, cardinality
2. Design feature transformations based on model requirements
3. Implement feature pipeline with DVC stages for reproducibility
4. Evaluate feature importance with model-specific methods (SHAP, permutation)
5. Select top features, remove redundant or low-importance ones
6. Validate feature pipeline on held-out data for leakage prevention
7. Document feature dictionary with types, sources, and transformations
