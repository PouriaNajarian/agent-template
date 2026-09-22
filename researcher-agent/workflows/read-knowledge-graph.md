---
description: Read the knowledge graph before starting any development task
---
# Read Knowledge Graph (MANDATORY Pre-Task)

> **This workflow is MANDATORY before starting any development or agent task.**
> Run `/read-knowledge-graph` before any work.

## Steps

1. Read the knowledge graph JSON file
```powershell
Get-Content ".devin/knowledge/obsidian-graph.json" | ConvertFrom-Json | Select-Object -ExpandProperty nodes | Format-Table id, type, label -AutoSize
```

2. Read the agent protocol
```powershell
Get-Content "AGENT_PROTOCOL.md"
```

3. View link relationships (who reports to whom, which MCP tools each agent uses)
```powershell
$graph = Get-Content ".devin/knowledge/obsidian-graph.json" | ConvertFrom-Json
$graph.links | Where-Object { $_.type -eq "reports-to" } | Format-Table source, target -AutoSize
$graph.links | Where-Object { $_.type -eq "uses-mcp" } | Format-Table source, target -AutoSize
$graph.links | Where-Object { $_.type -eq "uses-skill" } | Format-Table source, target -AutoSize
```

4. View graph metadata (tier counts, LLM assignments, MCP server count)
```powershell
$graph = Get-Content ".devin/knowledge/obsidian-graph.json" | ConvertFrom-Json
$graph.metadata | Format-List
```

5. Query Graphify for task-specific context
```
graphify.query("<your specific task description>")
```

## What You Now Know

After running this workflow, you have:
- **All agents** — senior (tech-lead, devops-lead, qa-lead), mid (frontend, backend, api, cloud, test, reviewer, writer), junior (testers, linter, deploy, deps, docs)
- **All links** — reporting hierarchy, skill assignments, MCP tool assignments, workflow associations
- **LLM tier assignments** — which model each agent uses (opus/sonnet/swe-1-7)
- **MCP tool inventory** — 11 MCP servers for development and DevOps
- **Skill inventory** — reusable skill definitions
- **Agent protocol** — mandatory rules for hierarchy, reporting, token reduction

## Result

You are now ready to start your task with full project context. Do NOT skip this step — working without the knowledge graph leads to duplicated effort, wrong tool selection, and inconsistent code.

**After completing your task:** Run `/update-knowledge-graph` to update the Obsidian graph and refresh Graphify. This is mandatory per `AGENT_PROTOCOL.md` §6.
