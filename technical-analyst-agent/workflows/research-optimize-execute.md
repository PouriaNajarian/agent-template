# Workflow: Research → Optimize → Execute

## Purpose

Mandatory workflow wrapper for every agent task. Before executing any new kind of work, the agent researches the web for the latest suitable skills, tools, and techniques; compares findings against the framework; optimizes the plan by updating framework artifacts if needed; and only then performs the actual job.

## Trigger

- Any agent receives a task from `AGENT_PROTOCOL.md` §7
- Any Devin session launched by `scripts/orchestrate.ps1` Phase 0
- Any new target or technique not already covered by `.devin/skills/` and `.devin/mcp/`

## Relationship to Other Workflows

This workflow runs as Phase 0 before every other workflow (`penetration-test`, `black-box-red-team`, `reverse-engineering`, `bug-bounty`). It is a cross-cutting requirement, not a standalone engagement type.

## Phases

### Phase 0 — Web Research

**Agent:** Any (self-executed by the assigned agent)

1. Read `.devin/knowledge/obsidian-graph.json` and query Graphify for existing .devin/skills/MCPs
2. Use `[[browser]]` or `[[web-search]]` to find current techniques and tools
3. Record findings to `.devin/knowledge/research-notes/<date>_<agent>-web-research.md`

### Phase 1 — Compare & Optimize

**Agent:** Any

1. Compare web findings against `.devin/skills/` and `.devin/mcp/`
2. Decide if the framework needs:
   - A new or updated skill
   - A new or updated MCP
   - An agent definition update
   - A model change in `agent-models.md`
3. Apply the smallest viable framework update
4. Update `.devin/knowledge/obsidian-graph.json` and refresh Graphify

### Phase 2 — Execute

**Agent:** Any

1. Use the optimized plan, skills, and MCPs
2. Execute the original assigned task
3. Cite web sources in the report
4. Save the report to the correct `reports/<workflow>/` directory

## Quality Gates

- [ ] Web research completed with at least 2 sources
- [ ] Framework skills and MCPs compared against findings
- [ ] Framework updated if a better approach was found
- [ ] Knowledge graph updated if any framework artifact changed
- [ ] Final report cites sources and reflects optimized approach

## Outputs

- `.devin/knowledge/research-notes/<date>_<agent>-web-research.md`
- Updated `.devin/skills/` or `.devin/mcp/` file (if optimization found)
- Updated `.devin/knowledge/obsidian-graph.json` (if any artifact changed)
- Final task report in `reports/<workflow>/`
