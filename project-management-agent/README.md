# project-management-agent

A **project management AI agent** for trading/investment systems, built from a
full **mcp-skills** advice run and packaged with every skill, workflow,
MCP-server entry, tool, doc and feature the advisor recommended — plus a
complete live inventory of the MCP servers and functions installed on this
machine.

## Contents

```
project-management-agent/
├── agent.md              # the project management agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 20 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 8 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # planner / ticket-writer / scheduler / risk-tracker / status-reporter
├── mcpservers/           # recommended PM MCP-server entries
├── agents/               # agent/platform entries
├── tools/                # recommended open-source tools (ranking JSON)
├── docs/                 # recommended documentation (ranking JSON)
├── features/             # recommended product features (ranking JSON)
├── advice/               # advice report + JSON
├── mcp-inventory/        # live system MCP inventory (servers, functions, catalog, API)
└── manifest.json         # machine-readable index of every file
```

## The advice behind it

The mcp-skills advisor returned:

- **Workflows**: `fw-role-separated-agents`, `fw-agentic-coding-loop`,
  `fw-spec-driven-development`
- **Top skills**: `ecom-project-management`, `plan-writing`,
  `eng-planning-and-task-breakdown`, `planning-with-files`, `to-tickets`,
  `wayfinder`, `triage`, `changeset`
- **MCP servers**: `pm33-mcp-server`, `spranab-saga-mcp`, `jira-mcp`,
  `linear-mcp`, `corbym-backlog-mcp`, `notion-api-mcp`
- **Tools**: Jira, Linear, Notion, Asana, Todoist

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-role-separated-agents.md`.
3. Plan the program:
   ```
   "plan the trading system rollout - milestones, tasks, owners, risks"
   ```
4. Produce the report using the format in `agent.md`.

## MCP inventory

Built from the local **agent-mcp-orchestrator** (`http://localhost:8790`):

- `mcp-inventory/system-mcps.md` — installed servers (http / stdio / remote / frontends)
- `mcp-inventory/mcp-functions.md` — every tool every installed server exposes
- `mcp-inventory/mcp-catalog.md` — installable server catalog (index + category summary)
- `mcp-inventory/orchestrator-api.md` — orchestrator REST/MCP reference

## Regenerating

```powershell
curl.exe -s http://localhost:8790/api/health   > mcp-inventory/orchestrator-health.json
curl.exe -s http://localhost:8790/api/servers  > mcp-inventory/orchestrator-servers.json
curl.exe -s http://localhost:8790/api/functions> mcp-inventory/mcp-functions.json
curl.exe -s http://localhost:8790/api/agents   > mcp-inventory/agent-configs.json
```

## Notes

- `skills/` and `workflows/` are **verbatim** copies — do not edit them.
- No secrets are stored; only local paths and server names.