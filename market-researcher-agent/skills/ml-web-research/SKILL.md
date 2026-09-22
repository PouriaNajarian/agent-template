---
name: ml-web-research
description: Mandatory web research protocol for all agents before executing any task. Ensures agents use the latest tools, techniques, and best practices instead of relying on potentially stale training data.
---

# Skill: Web Research

## Used By
- All agents — Mandatory pre-task protocol per `AGENT_PROTOCOL.md` §7

## Description
Mandatory web research protocol for all agents before executing any task. Ensures agents use the latest tools, techniques, and best practices instead of relying on potentially stale training data.

## Key Areas
- Latest ML framework versions and features (PyTorch, TensorFlow, JAX)
- Latest Hugging Face Transformers, PEFT, and TRL releases
- Latest fine-tuning techniques and papers (LoRA variants, RLHF methods)
- Latest MLOps tools and deployment patterns
- Latest evaluation benchmarks and metrics
- Latest data engineering tools and pipeline patterns
- Security vulnerabilities in ML dependencies
- Reproducibility and reproducibility best practices

## MCP Tools
- [[brave-search]] — Web search for latest techniques and tools
- [[context7]] — Up-to-date library documentation
- [[deepwiki]] — AI-powered codebase context for GitHub repos
- [[huggingface]] — Model hub for latest pre-trained checkpoints
- [[filesystem]] — Save research notes to .devin/knowledge/research-notes/

## Methodology
1. Formulate search query based on the task
2. Search the web with Brave Search for current techniques and tools
3. Cross-reference with Context7 for up-to-date library documentation
4. Compare findings against existing framework skills and MCP definitions
5. If a better approach exists, update the smallest relevant framework artifact
6. Document sources and findings in .devin/knowledge/research-notes/
7. Only then proceed to task execution with the optimized approach
