# Workflow: Fw Parallel Agent Execution

**Category:** `framework`  
**Slug:** `fw-parallel-agent-execution`

## Purpose

Framework-style parallel agent execution with worktree isolation for simultaneous independent tasks.

## Keywords

`parallel`, `agents`, `worktree`, `isolation`, `framework`

## Trigger

Run this workflow when:
- The task matches: parallel, agents, worktree
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest parallel agent execution patterns.

```text
1. Invoke skill: web-web-research
2. Research latest parallel agent execution patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — dev-using-git-worktrees

**Skill:** `dev-using-git-worktrees`  
**Action:** Set up git worktrees for each parallel agent.

```text
1. Invoke skill: dev-using-git-worktrees
2. Set up git worktrees for each parallel agent.
3. Verify the output before proceeding to the next step
```

### Step 3 — dev-dispatching-parallel-agents

**Skill:** `dev-dispatching-parallel-agents`  
**Action:** Dispatch tasks to parallel agents in isolated worktrees.

```text
1. Invoke skill: dev-dispatching-parallel-agents
2. Dispatch tasks to parallel agents in isolated worktrees.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Collect and merge all agent outputs.

```text
1. Invoke skill: dev-verification-before-completion
2. Collect and merge all agent outputs.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (dev-using-git-worktrees): output verified
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
- Use `get_workflow("fw-parallel-agent-execution")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
