# Workflow: Llm App Integration

**Category:** `ai`  
**Slug:** `llm-app-integration`

## Purpose

Integrate an LLM into an application (chat, RAG, agents).

## Keywords

`llm`, `rag`, `embeddings`, `chat`, `agent`

## Trigger

Run this workflow when:
- The task matches: llm, rag, embeddings
- A ai-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — claude-claude-api

**Skill:** `claude-claude-api`  
**Action:** Pick the model/API and design prompts with correct parameters.

```text
1. Invoke skill: claude-claude-api
2. Pick the model/API and design prompts with correct parameters.
3. Verify the output before proceeding to the next step
```

### Step 2 — google-gemini-api

**Skill:** `google-gemini-api`  
**Action:** Compare/choose provider where relevant.

```text
1. Invoke skill: google-gemini-api
2. Compare/choose provider where relevant.
3. Verify the output before proceeding to the next step
```

### Step 3 — ecom-ai-agent-integration

**Skill:** `ecom-ai-agent-integration`  
**Action:** Wire the integration into the app with error handling.

```text
1. Invoke skill: ecom-ai-agent-integration
2. Wire the integration into the app with error handling.
3. Verify the output before proceeding to the next step
```

### Step 4 — ms-azure-ai

**Skill:** `ms-azure-ai`  
**Action:** Consider managed AI services for scale.

```text
1. Invoke skill: ms-azure-ai
2. Consider managed AI services for scale.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (claude-claude-api): output verified
- [ ] Step 2 (google-gemini-api): output verified
- [ ] Step 3 (ecom-ai-agent-integration): output verified
- [ ] Step 4 (ms-azure-ai): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-4 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **ai** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("llm-app-integration")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
