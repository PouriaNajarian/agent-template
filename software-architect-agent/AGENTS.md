# AGENTS.md — software-architect-agent

Operating guide + manifest for any AI agent working in this repository.
Generated from a full **mcp-skills `get_task_advice`** run (see
`advice/task-advice-report.md`). Recommended workflow: **`fw-feature-delivery`**.
Primary skills: **`software-architecture`**, **`architect-review`**.

## What this repo is

A **self-contained software-architect agent package**: the agent definition
(`agent.md`), its helper subagents (`subagents/`), and verbatim copies of every
skill and workflow the mcp-skills advisor recommended — fetched directly from the
**mcp-skills MCP server** (`get_skill`, `get_workflow`, `get_*_combined`) — plus a
live inventory of the MCP servers and functions installed on this machine
(`mcp-inventory/`).

This repo contains **no application code**. It is knowledge + agent
configuration. Do not add build tooling.

## How to use the agent

1. Read `agent.md` — the authoritative agent definition and operating loop.
2. Load the workflow `workflows/fw-feature-delivery.md` (supporting:
   `workflows/fw-spec-driven-development.md`, `workflows/fw-role-separated-agents.md`).
3. Load the specific skills the task needs from `skills/` (see `skills-index.md`).
4. Use the MCP tools listed in `agent.md`; confirm they exist via
   `mcp-inventory/system-mcps.md` / `mcp-inventory/mcp-functions.md`.
5. For large designs, fan out to `subagents/` and merge findings.
6. Emit the architecture output format defined in `agent.md`.

## Layout

| Path | Contents |
|---|---|
| `agent.md` | The software-architect agent definition (main deliverable). |
| `subagents/` | System-design / domain / integration / NFR / tech-debt / ADR subagents. |
| `skills/` | 97 `SKILL.md` copies fetched via `get_skill` + combined ranking JSON. See `skills-index.md`. |
| `workflows/` | 36 workflow `.md` files fetched via `get_workflow` + combined ranking JSON. See `workflows-index.md`. |
| `mcpservers/` | Combined ranking JSON of recommended MCP servers (the MCP catalog). |
| `agents/` | Combined ranking JSON of recommended AI agent platforms. |
| `tools/` | Combined ranking JSON of recommended open-source tools. |
| `docs/` | Combined ranking JSON of recommended documentation. |
| `features/` | Combined ranking JSON of recommended product features. |
| `advice/` | The full `get_task_advice` payload(s) + readable report. |
| `mcp-inventory/` | Live system MCP inventory: servers, functions, catalog, orchestrator API. |
| `knowledge/` | Reserved for an Obsidian vault + Graphify graph (optional). |
| `manifest.json` | Machine-readable index of every file in this package. |

## MCP inventory (source of truth)

Live system MCP inventory: `mcp-inventory/` (servers, functions, catalog,
orchestrator API). Human-readable views: `system-mcps.md`, `mcp-functions.md`,
`mcp-catalog.md`; API reference: `mcp-inventory/orchestrator-api.md`.

Regenerate any time with the local **agent-mcp-orchestrator** (`http://localhost:8790`):

| Endpoint | Writes |
|---|---|
| `GET /api/health` | `mcp-inventory/orchestrator-health.json` |
| `GET /api/servers` | `mcp-inventory/orchestrator-servers.json` |
| `GET /api/functions` | `mcp-inventory/mcp-functions.json` |
| `GET /api/agents` | `mcp-inventory/agent-configs.json` |

## The advice loop (mandated by `get_task_advice`)

1. **Persist** — every skill/workflow/MCP/agent/doc loaded for a task is saved
   under this repo (done).
2. **Report back** — after each design step, update notes/graph, query the graph,
   and pass only the graph summary + this advice as context to the LLM.
3. **Re-advise** — call `get_task_advice(<updated status>)` again and refresh
   `advice/` when the task changes.

## Refresh procedure

Skills and workflows were fetched from the mcp-skills MCP server
(`http://localhost:8788/mcp`), **not** read from disk. To refresh:

```powershell
# list of names in a file, then:
#   tools/call get_skill  -> skills/<name>/SKILL.md
#   tools/call get_workflow -> workflows/<name>.md
# combined rankings:
#   get_skills_combined / get_workflows_combined / get_mcpservers_combined /
#   get_agents_combined / get_docs_combined / get_tools_combined / get_features_combined
```

Keep `skills-index.md`, `workflows-index.md` and `manifest.json` in sync.

## Conventions

- **Do not edit** the fetched `skills/` and `workflows/` files — they are verbatim
  source artifacts. Add new material in a new folder.
- Keep `manifest.json` in sync when adding files.
- Never commit secrets. `advice/` and `mcp-inventory/` contain machine-local
  paths and server names only (no keys).
