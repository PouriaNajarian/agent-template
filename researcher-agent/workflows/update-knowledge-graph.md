---
description: Update Obsidian knowledge graph and Graphify index after any project change
---
# Update Knowledge Graph (MANDATORY After Changes)

> **This workflow is MANDATORY after any change that creates, modifies, or retires project artifacts.**
> See `AGENT_PROTOCOL.md` §6 for the full protocol.

## When to Run
- After creating a new agent, skill, MCP tool, workflow, or template
- After modifying an existing agent's responsibilities, skills, MCP tools, or reporting hierarchy
- After adding or removing MCP tool assignments
- After changing LLM tier assignments
- After retiring or renaming any artifact
- After updating workflow phases or quality gates

## Steps

### 1. Update obsidian-graph.json — Add/Modify Nodes
```powershell
$graph = Get-Content ".devin/knowledge/obsidian-graph.json" -Raw | ConvertFrom-Json
# Add new nodes or update existing ones
$graph | ConvertTo-Json -Depth 10 | Set-Content ".devin/knowledge/obsidian-graph.json"
```

### 2. Update obsidian-graph.json — Add/Modify Links
```powershell
$graph = Get-Content ".devin/knowledge/obsidian-graph.json" -Raw | ConvertFrom-Json
# Add new links (reports-to, uses-skill, uses-mcp, workflow, receives-input-from, manages)
$graph | ConvertTo-Json -Depth 10 | Set-Content ".devin/knowledge/obsidian-graph.json"
```

### 3. Update Metadata Counts
```powershell
$graph = Get-Content ".devin/knowledge/obsidian-graph.json" -Raw | ConvertFrom-Json
$graph.metadata.total_nodes = $graph.nodes.Count
$graph.metadata.total_links = $graph.links.Count
$graph.metadata.tiers.senior.count = @($graph.nodes | Where-Object { $_.type -eq "agent-senior" }).Count
$graph.metadata.tiers.mid.count = @($graph.nodes | Where-Object { $_.type -eq "agent-mid" }).Count
$graph.metadata.tiers.junior.count = @($graph.nodes | Where-Object { $_.type -eq "agent-junior" }).Count
$linkTypes = $graph.links | Group-Object type
$linkTypes | ForEach-Object { $graph.metadata.link_types.($_.Name) = $_.Count }
$graph | ConvertTo-Json -Depth 10 | Set-Content ".devin/knowledge/obsidian-graph.json"
```

### 4. Validate JSON Integrity
```powershell
$graph = Get-Content ".devin/knowledge/obsidian-graph.json" -Raw | ConvertFrom-Json
Write-Host "Nodes: $($graph.nodes.Count) (metadata: $($graph.metadata.total_nodes))"
Write-Host "Links: $($graph.links.Count) (metadata: $($graph.metadata.total_links))"
if ($graph.nodes.Count -ne $graph.metadata.total_nodes) { Write-Host "MISMATCH: node count" -ForegroundColor Red; exit 1 }
if ($graph.links.Count -ne $graph.metadata.total_links) { Write-Host "MISMATCH: link count" -ForegroundColor Red; exit 1 }
Write-Host "Validation: PASS" -ForegroundColor Green
```

### 5. Refresh Graphify Index
```
graphify.build()
```
Then verify the change is indexed:
```
graphify.query("<changed artifact name>")
```

### 6. Record Change in Research Notes
Create or update a file in `.devin/knowledge/research-notes/` with:
- What changed (create/update/retire)
- Which artifacts were affected
- Which agents are impacted
- Workflow phase context
- Date and agent name

## Verification
- [ ] `obsidian-graph.json` parses without errors
- [ ] Node count matches metadata
- [ ] Link count matches metadata
- [ ] New/modified artifact appears as a node
- [ ] All relationships have corresponding links
- [ ] Graphify query returns the new/modified artifact
- [ ] Research notes updated with change record

## Result

The knowledge graph and Graphify index now reflect the current state of the project. The next agent that reads the graph will see accurate nodes, links, and metadata — preventing duplicated work and wrong tool selection.
