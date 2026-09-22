# Workflow: Fw Research Optimize Execute

**Category:** `framework`  
**Slug:** `fw-research-optimize-execute`

## Purpose

Framework-style mandatory pre-task research: web research, compare, optimize, then execute.

## Keywords

`research`, `optimize`, `execute`, `pre-task`, `framework`

## Trigger

Run this workflow when:
- The task matches: research, optimize, execute
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Search web for latest suitable skills, tools, and techniques for the task.

```text
1. Invoke skill: web-web-research
2. Search web for latest suitable skills, tools, and techniques for the task.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-source-driven-development

**Skill:** `eng-source-driven-development`  
**Action:** Compare findings against existing skills and MCP definitions.

```text
1. Invoke skill: eng-source-driven-development
2. Compare findings against existing skills and MCP definitions.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-documentation-and-adrs

**Skill:** `eng-documentation-and-adrs`  
**Action:** Apply smallest viable framework update if a better approach is found.

```text
1. Invoke skill: eng-documentation-and-adrs
2. Apply smallest viable framework update if a better approach is found.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Execute the original task using optimized plan, cite web sources in report.

```text
1. Invoke skill: dev-verification-before-completion
2. Execute the original task using optimized plan, cite web sources in report.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-source-driven-development): output verified
- [ ] Step 3 (eng-documentation-and-adrs): output verified
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
- Use `get_workflow("fw-research-optimize-execute")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
