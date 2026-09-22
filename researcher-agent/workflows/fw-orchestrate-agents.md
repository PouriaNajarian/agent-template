# Workflow: Fw Orchestrate Agents

**Category:** `framework`  
**Slug:** `fw-orchestrate-agents`

## Purpose

Framework-style parallel agent orchestration via Devin/OpenCode/9Router CLI with LLM tiering.

## Keywords

`orchestrate`, `agents`, `parallel`, `devin`, `opencode`, `framework`

## Trigger

Run this workflow when:
- The task matches: orchestrate, agents, parallel
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest agent orchestration patterns and CLI tools.

```text
1. Invoke skill: web-web-research
2. Research latest agent orchestration patterns and CLI tools.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-planning-and-task-breakdown

**Skill:** `eng-planning-and-task-breakdown`  
**Action:** Break work into independent tasks suitable for parallel agent execution.

```text
1. Invoke skill: eng-planning-and-task-breakdown
2. Break work into independent tasks suitable for parallel agent execution.
3. Verify the output before proceeding to the next step
```

### Step 3 — dev-dispatching-parallel-agents

**Skill:** `dev-dispatching-parallel-agents`  
**Action:** Dispatch tasks to parallel agents with appropriate model tiering (senior/mid/junior).

```text
1. Invoke skill: dev-dispatching-parallel-agents
2. Dispatch tasks to parallel agents with appropriate model tiering (senior/mid/junior).
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Collect and verify all agent outputs, resolve conflicts.

```text
1. Invoke skill: dev-verification-before-completion
2. Collect and verify all agent outputs, resolve conflicts.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-planning-and-task-breakdown): output verified
- [ ] Step 3 (dev-dispatching-parallel-agents): output verified
- [ ] Step 4 (dev-verification-before-completion): output verified
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

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-orchestrate-agents")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
