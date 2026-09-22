# Workflow: Learning New Stack

**Category:** `learning`  
**Slug:** `learning-new-stack`

## Purpose

Learn and adopt a new framework or tool with LLM assistance.

## Keywords

`learn`, `new stack`, `framework`, `onboard`

## Trigger

Run this workflow when:
- The task matches: learn, new stack, framework
- A learning-related deliverable is needed
- Multiple skills must be coordinated in sequence

## Steps

### Step 1 — web-web-research

**Skill:** `web-web-research`  
**Action:** Fetch official docs first - no stale patterns.

```text
1. Invoke skill: web-web-research
2. Fetch official docs first - no stale patterns.
3. Verify the output before proceeding to the next step
```

### Step 2 — eng-source-driven-development

**Skill:** `eng-source-driven-development`  
**Action:** Ground every implementation decision in official docs.

```text
1. Invoke skill: eng-source-driven-development
2. Ground every implementation decision in official docs.
3. Verify the output before proceeding to the next step
```

### Step 3 — web-nextjs-development

**Skill:** `web-nextjs-development`  
**Action:** Follow the framework's canonical patterns.

```text
1. Invoke skill: web-nextjs-development
2. Follow the framework's canonical patterns.
3. Verify the output before proceeding to the next step
```

### Step 4 — dev-verification-before-completion

**Skill:** `dev-verification-before-completion`  
**Action:** Validate with a small working example.

```text
1. Invoke skill: dev-verification-before-completion
2. Validate with a small working example.
3. Verify the output before proceeding to the next step
```

## Quality Gates

- [ ] Step 1 (web-web-research): output verified
- [ ] Step 2 (eng-source-driven-development): output verified
- [ ] Step 3 (web-nextjs-development): output verified
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

- This workflow belongs to the **learning** category.
- Combine with `get_task_advice(task)` for cross-catalog recommendations.
- Use `get_workflow("learning-new-stack")` to retrieve this workflow programmatically.

---
*Generated from `workflows.json` by `generate_workflow_mds.py`*
