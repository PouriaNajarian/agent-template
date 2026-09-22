---
name: sec-secret-detection
description: Automated secret and credential detection in source code, configuration files, and JavaScript bundles. Scans for 32+ provider patterns including AWS, GCP, GitHub, Stripe, OpenAI, and private keys.
---

# Skill: Secret Detection

## Used By
- [[dependency-security]]
- [[web-security]]
- [[api-security]]
- [[cve-checker]]
- [[validation]]

## Description
Automated secret and credential detection in source code, configuration files, and JavaScript bundles. Scans for 32+ provider patterns including AWS, GCP, GitHub, Stripe, OpenAI, and private keys.

## Key Areas
- Cloud credential detection (AWS, GCP, Azure, Cloudflare)
- Source/CI token detection (GitHub PAT, npm, Docker Hub)
- Payment credential detection (Stripe)
- Communication token detection (Slack, Discord, Telegram, Twilio)
- AI/ML key detection (OpenAI, Anthropic, HuggingFace)
- Private key detection (RSA, EC, OpenSSH, PGP)
- JWT and generic secret detection

## MCP Tools
- [[secret-scanner]] — Primary secrets-audit MCP (32 rules, zero deps)
- [[mcpwner-security]] — MCPwner secrets scanning (Gitleaks, TruffleHog, detect-secrets, Whispers, Hawk-Eye)
- [[kali-security]] — Kali MCP gitleaks, trufflehog
- [[github]] — GitHub MCP secret scanning API

## Methodology
1. Scan target directory/repository recursively
2. Identify all secret types with risk scores (0-100)
3. Triage by severity (CRITICAL → HIGH → MEDIUM)
4. Verify findings (check if key is active/valid)
5. Document with redacted matches (never expose full secret)
6. Report for remediation
