# Workflow: Fw Role Separated Agents

**Category:** `framework`  
**Slug:** `fw-role-separated-agents`

## Purpose

Framework-style role-separated agent workflow: Planner decomposes, Executor implements, Reviewer verifies.

## Keywords

`role-separated`, `planner`, `executor`, `reviewer`, `framework`

## Trigger

Run this workflow when:
- The task matches: role-separated, planner, executor
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest role-separated agent patterns.

```text
1. Invoke skill: web-web-research
2. Research latest role-separated agent patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-planning-and-task-breakdown

**Skill:** `eng-planning-and-task-breakdown`  
**Action:** Planner decomposes the task into ordered implementation steps.

```text
1. Invoke skill: eng-planning-and-task-breakdown
2. Planner decomposes the task into ordered implementation steps.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-incremental-implementation

**Skill:** `eng-incremental-implementation`  
**Action:** Executor implements each step with fresh context.

```text
1. Invoke skill: eng-incremental-implementation
2. Executor implements each step with fresh context.
3. Verify the output before proceeding to the next step
```

### Step 4 — eng-code-review-and-quality

**Skill:** `eng-code-review-and-quality`  
**Action:** Reviewer verifies each implementation with fresh context.

```text
1. Invoke skill: eng-code-review-and-quality
2. Reviewer verifies each implementation with fresh context.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-planning-and-task-breakdown): output verified
- [ ] Step 3 (eng-incremental-implementation): output verified
- [ ] Step 4 (eng-code-review-and-quality): output verified
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
- Use `get_workflow("fw-role-separated-agents")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
