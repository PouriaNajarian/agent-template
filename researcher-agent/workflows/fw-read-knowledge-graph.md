# Workflow: Fw Read Knowledge Graph

**Category:** `framework`  
**Slug:** `fw-read-knowledge-graph`

## Purpose

Framework-style knowledge graph reading before starting any task.

## Keywords

`knowledge-graph`, `skills`, `discovery`, `framework`, `graph`

## Trigger

Run this workflow when:
- The task matches: knowledge-graph, skills, discovery
- A framework-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Research latest knowledge graph techniques for agent context.

```text
1. Invoke skill: web-web-research
2. Research latest knowledge graph techniques for agent context.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-context-engineering

**Skill:** `eng-context-engineering`  
**Action:** Read the knowledge graph JSON and query Graphify for all skills, workflows, and relationships.

```text
1. Invoke skill: eng-context-engineering
2. Read the knowledge graph JSON and query Graphify for all skills, workflows, and relationships.
3. Verify the output before proceeding to the next step
```

### Step 3 — eng-using-agent-skills

**Skill:** `eng-using-agent-skills`  
**Action:** Select the most specific skill and workflow for the task based on graph data.

```text
1. Invoke skill: eng-using-agent-skills
2. Select the most specific skill and workflow for the task based on graph data.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-context-engineering): output verified
- [ ] Step 3 (eng-using-agent-skills): output verified
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
- Use `get_workflow("fw-read-knowledge-graph")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
