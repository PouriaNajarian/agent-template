---
name: ml-data-pipeline
description: Data ingestion, cleaning, preprocessing, validation, and versioning for ML pipelines. Covers batch and streaming data flows, schema enforcement, data quality checks, and reproducible data versionin...
---

# Skill: Data Pipeline Development

## Used By
- [[data-lead]]
- [[data-engineer]]
- [[feature-engineer]]
- [[ml-engineer]]

## Description
Data ingestion, cleaning, preprocessing, validation, and versioning for ML pipelines. Covers batch and streaming data flows, schema enforcement, data quality checks, and reproducible data versioning with DVC.

## Key Areas
- Data ingestion from files, databases, APIs, and streaming sources
- Data cleaning: missing values, outliers, duplicates, type coercion
- Data preprocessing: normalization, tokenization, encoding, augmentation
- Data validation: schema enforcement, distribution checks, anomaly detection
- Data versioning with DVC: reproducible pipelines, dataset lineage
- Feature stores: online/offline feature serving

## MCP Tools
- [[dvc]] — Data version control, pipeline reproducibility
- [[filesystem]] — Read/write data files and pipeline configs
- [[jupyter]] — Exploratory data analysis in notebooks
- [[brave-search]] — Research latest data engineering tools and techniques

## Methodology
1. Profile the data source — schema, volume, velocity, quality
2. Design the pipeline DAG — ingestion → validation → cleaning → feature engineering → output
3. Implement with DVC pipeline stages for reproducibility
4. Add data quality checks at each stage (schema, distribution, completeness)
5. Version datasets with DVC, track lineage and provenance
6. Document data dictionary, schema, and quality metrics
