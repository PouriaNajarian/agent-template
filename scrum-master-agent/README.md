# scrum-master-agent

A **scrum master AI agent** for trading/investment systems, built from a full
**mcp-skills** advice run and packaged with every skill, workflow, MCP-server
entry, tool, doc and feature the advisor recommended — plus a complete live
inventory of the MCP servers and functions installed on this machine.

## Contents

```
scrum-master-agent/
├── agent.md              # the scrum master agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 15 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 6 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # backlog-groomer / sprint-planner / standup-runner / retro-facilitator / metrics-reporter
├── mcpservers/           # recommended agile MCP-server entries
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

- **Workflow**: `fw-role-separated-agents` (scrum cadence)
- **Top skills**: `ecom-project-management`, `team-collaboration-standup-notes`,
  `plan-writing`, `eng-planning-and-task-breakdown`, `retro`
- **MCP servers**: `jira-mcp`, `jira-sprint-dashboard`, `pm33-mcp-server`,
  `spranab-saga-mcp`, `qretro`, `agile-team-mcp-server`
- **Tools**: Jira, Linear, QRetro, EasyRetro

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-role-separated-agents.md`.
3. Run a ceremony:
   ```
   "sprint planning for the trading system sprint 5"
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