---
name: ecom-project-management
description: Scrum-based project management for AI coding agents managing multi-service ecommerce projects. Covers sprint planning, backlog management, task tracking, retrospectives, cross-project coordination, and portfolio management. Use when planning sprints, managing multiple microservices, tracking tasks across projects, or running scrum ceremonies with AI agents.
---

# Project Management Skill (Scrum for AI Coding Agents)

## When to Use
- Planning sprints across one or more projects
- Managing a portfolio of microservices
- Creating project management folders and files
- Running scrum ceremonies with AI agents (planning, review, retrospective)
- Tracking tasks across cross-project dependencies
- Creating product backlogs and sprint backlogs

## Scrum Roles for AI-Agent Teams

| Role | Who | Responsibility |
|------|-----|----------------|
| Product Owner | Human | Defines vision, prioritizes backlog, approves specs |
| Scrum Master | AI (opus) | Facilitates ceremonies, removes blockers, tracks progress |
| Planner | Human + AI | Decomposes stories, sets constraints, defines acceptance criteria |
| Executor | AI (sonnet) | Generates drafts, scaffolds tests, proposes refactors |
| Verifier | Human | Validates design intent, risk assumptions, production impact |
| Auditor | Automation (CI) | Enforces policy and quality gates |

**Rule:** Agents should NOT play Planner and Verifier roles in the same workflow for medium/high-risk changes.

## Folder Structure (Per Project)

```
<project>/
├── Project Management/
│   ├── project-management.md       # Full PM doc: milestones, sprints, risks, decisions
│   ├── task-tracker.md             # Active/completed tasks with IDs
│   ├── sprint-backlog.md           # Current sprint user stories
│   ├── product-backlog.md          # Full product backlog (all stories)
│   └── retrospective.md            # Sprint retrospectives (Keep/Stop/Avoid/Challenge)
├── architecture/
│   ├── architecture.md             # System architecture for this service
│   ├── data-model.md               # Database schema
│   └── security.md                 # Security model
└── .devin/
    └── knowledge/
        └── obsidian-graph.json     # Project knowledge graph
```

## Portfolio Structure (Cross-Project)

```
ecom-project-management/
├── README.md
├── portfolio-overview.md           # All projects summary
├── sprint-plan.md                  # Cross-project sprint timeline
├── cross-project-dependencies.md   # Service dependencies
├── shared-architecture.md          # System diagram
├── shared-data-model.md            # Shared databases
├── shared-security.md              # Auth flow across services
├── deployment-order.md             # Deployment sequence
├── risk-register.md                # Cross-project risks
├── decision-log.md                 # Architecture decisions
├── team-roster.md                  # AI agent roles
└── .devin/
    └── knowledge/
        └── obsidian-graph.json     # Portfolio knowledge graph
```

## Sprint Process

### 1. Sprint Planning (15-30 min)
1. Read knowledge graph for all relevant projects
2. Review product backlog, prioritize by business value
3. Label each item with `agent-suitability`: high / medium / low
4. Select items for sprint based on team capacity
5. Write detailed spec for each item (spec-driven development)
6. Define acceptance criteria as executable commands
7. Output: `sprint-backlog.md` with committed items

### 2. Sprint Execution (1-3 hours)
1. For each backlog item:
   a. Executor agent writes failing test (TDD: Red)
   b. Executor writes minimum code to pass (TDD: Green)
   c. Executor refactors with tests as safety net
   d. Executor records decisions in `implementation-notes.md`
2. Auditor (CI) runs quality gates: lint, typecheck, build, test
3. Verifier reviews diff against spec (not against vibes)
4. Limit agent throughput to human review capacity

### 3. Sprint Review (10-15 min)
1. Demo working software (not slides)
2. Show throughput plus quality trend
3. Compare AI-assisted vs human-only defect rates
4. Highlight one learning outcome

### 4. Sprint Retrospective (10 min)
1. Categorize feedback: Keep / Stop / Avoid / Challenge
2. Turn review feedback into improvement issues
3. Update skills, rules, memory with learnings
4. Audit where agents saved effort vs created hidden debt
5. Output: `retrospective.md` with action items

## Definition of Done (AI-Augmented)

Traditional:
- [ ] Code written and committed
- [ ] Tests pass (unit + integration)
- [ ] Code reviewed by human
- [ ] Documentation updated

AI-Specific additions:
- [ ] Spec reviewed and approved before implementation
- [ ] Provenance of generated artifacts recorded
- [ ] No prohibited autonomous edits (auth, billing, compliance)
- [ ] Post-merge monitoring for AI-heavy changes
- [ ] `implementation-notes.md` records all unwritten decisions
- [ ] Knowledge graph updated with new nodes/links

## Metrics (Good vs Bad)

**Good metrics:**
- Cycle time by change risk tier
- Rework percentage after first AI-generated PR
- Escaped defects per 100 merged changes
- Review depth time for AI-heavy diffs
- Onboarding productivity without quality drop

**Bad metrics (don't use in isolation):**
- Number of AI-generated commits
- Token usage volume
- Raw story points completed

## Task Tracker Format

```markdown
## Active Tasks — Sprint N

| ID | Task | Assignee | Priority | Status | Notes |
|----|------|----------|----------|--------|-------|
| T-001 | Description | agent-role | High | In Progress | Context |

## Completed Tasks

| ID | Task | Completed | Notes |
|----|------|-----------|-------|
| C-001 | Description | 2026-01-01 | What was done |
```

## Anti-Rationalization Table

| Excuse | Counter |
|--------|---------|
| "This sprint is too small to plan" | If it has >1 task, it needs a sprint backlog |
| "I'll write the spec during implementation" | Spec before code — always |
| "Retrospective can wait" | Retro after every sprint — no exceptions |
| "Task tracker is overhead" | If you can't track it, you can't manage it |
| "Quality gates slow us down" | Rework is slower than review |

## Skills to Invoke Together
- `eng-planning-and-task-breakdown` — Break work into tasks
- `eng-spec-driven-development` — Write specs before code
- `eng-incremental-implementation` — Implement incrementally
- `eng-verification-before-completion` — Verify before claiming done
- `eng-git-workflow-and-versioning` — Git conventions
- `graphify-knowledge-graph` — Read knowledge graph before planning
