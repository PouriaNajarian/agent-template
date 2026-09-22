# Workflow: Fw Ai Agent Setup

**Category:** `framework`  
**Slug:** `fw-ai-agent-setup`

## Purpose

Framework-style AI agent setup: recommendations, chatbot, smart search, inventory forecasting.

## Keywords

`ai-agent`, `chatbot`, `recommendations`, `forecasting`, `framework`

## Trigger

Run this workflow when:
- The task matches: ai-agent, chatbot, recommendations
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest AI agent patterns and tools.

```text
1. Invoke skill: web-web-research
2. Research latest AI agent patterns and tools.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-spec-driven-development

**Skill:** `eng-spec-driven-development`  
**Action:** Spec the AI agent: recommendations, chatbot, search, forecasting.

```text
1. Invoke skill: eng-spec-driven-development
2. Spec the AI agent: recommendations, chatbot, search, forecasting.
3. Verify the output before proceeding to the next step
```

### Step 3 — ecom-ai-agent-integration

**Skill:** `ecom-ai-agent-integration`  
**Action:** Integrate AI agents using Cloudflare Workers AI.

```text
1. Invoke skill: ecom-ai-agent-integration
2. Integrate AI agents using Cloudflare Workers AI.
3. Verify the output before proceeding to the next step
```

### Step 4 — llm-app-integration

**Skill:** `llm-app-integration`  
**Action:** Wire the LLM integration with error handling.

```text
1. Invoke skill: llm-app-integration
2. Wire the LLM integration with error handling.
3. Verify the output before proceeding to the next step
```

### Step 5 — eng-test-driven-development

**Skill:** `eng-test-driven-development`  
**Action:** TDD the agent logic and response handling.

```text
1. Invoke skill: eng-test-driven-development
2. TDD the agent logic and response handling.
3. Verify the output before proceeding to the next step
```

### Step 6 — eng-observability-and-instrumentation

**Skill:** `eng-observability-and-instrumentation`  
**Action:** Monitor agent quality and latency.

```text
1. Invoke skill: eng-observability-and-instrumentation
2. Monitor agent quality and latency.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-spec-driven-development): output verified
- [ ] Step 3 (ecom-ai-agent-integration): output verified
- [ ] Step 4 (llm-app-integration): output verified
- [ ] Step 5 (eng-test-driven-development): output verified
- [ ] Step 6 (eng-observability-and-instrumentation): output verified
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
- Use `get_workflow("fw-ai-agent-setup")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
