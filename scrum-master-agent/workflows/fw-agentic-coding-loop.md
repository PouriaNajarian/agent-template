# Workflow: Fw Agentic Coding Loop

**Category:** `framework`  
**Slug:** `fw-agentic-coding-loop`

## Purpose

Framework-style agentic coding loop: explore, plan, implement, commit with human approval gates.

## Keywords

`agentic`, `coding-loop`, `explore`, `plan`, `implement`, `framework`

## Trigger

Run this workflow when:
- The task matches: agentic, coding-loop, explore
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest agentic coding patterns.

```text
1. Invoke skill: web-web-research
2. Research latest agentic coding patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-planning-and-task-breakdown

**Skill:** `eng-planning-and-task-breakdown`  
**Action:** Explore the codebase and plan the implementation.

```text
1. Invoke skill: eng-planning-and-task-breakdown
2. Explore the codebase and plan the implementation.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-incremental-implementation

**Skill:** `eng-incremental-implementation`  
**Action:** Implement the plan incrementally with human approval at each phase.

```text
1. Invoke skill: eng-incremental-implementation
2. Implement the plan incrementally with human approval at each phase.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Verify all changes pass tests before committing.

```text
1. Invoke skill: dev-verification-before-completion
2. Verify all changes pass tests before committing.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-planning-and-task-breakdown): output verified
- [ ] Step 3 (eng-incremental-implementation): output verified
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
- Use `get_workflow("fw-agentic-coding-loop")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
