# Workflow: Fw Update Knowledge Graph

**Category:** `framework`  
**Slug:** `fw-update-knowledge-graph`

## Purpose

Framework-style knowledge graph update after any project change.

## Keywords

`knowledge-graph`, `update`, `graphify`, `obsidian`, `framework`

## Trigger

Run this workflow when:
- The task matches: knowledge-graph, update, graphify
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest knowledge graph update patterns.

```text
1. Invoke skill: web-web-research
2. Research latest knowledge graph update patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-documentation-and-adrs

**Skill:** `eng-documentation-and-adrs`  
**Action:** Update the Obsidian knowledge graph JSON with new skills, workflows, files, and relationships.

```text
1. Invoke skill: eng-documentation-and-adrs
2. Update the Obsidian knowledge graph JSON with new skills, workflows, files, and relationships.
3. Verify the output before proceeding to the next step
```

### Step 3 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Refresh Graphify index and verify the graph is consistent.

```text
1. Invoke skill: dev-verification-before-completion
2. Refresh Graphify index and verify the graph is consistent.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-documentation-and-adrs): output verified
- [ ] Step 3 (dev-verification-before-completion): output verified
- [ ] All steps completed successfully
- [ ] Final deliverable meets acceptance criteria

## Agent Usage

```text
1. Agent receives a task matching this workflow.
2. Follow steps 1-3 in order, loading each skill.
3. Execute each skill's instructions before moving to the next step.
4. Check quality gates before declaring done.
```

## Relationship to Other Workflows

- This workflow belongs to the **framework** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("fw-update-knowledge-graph")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
