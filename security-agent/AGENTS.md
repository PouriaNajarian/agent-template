# AGENTS.md — security-agent

Operating guide + manifest for any AI agent working in this repository.
Generated from a full **mcp-skills** advice run (vector index; DeepSeek
combined ranker unavailable at build time — see `advice/task-advice-report.md`).
Recommended workflow: **`fw-penetration-test`**.

## What this repo is

A **self-contained security agent package**: the agent definition (`agent.md`),
its helper subagents (`subagents/`), and verbatim copies of every skill,
workflow, MCP-server entry, tool, doc and feature the mcp-skills advisor
recommended for security — plus a full live inventory of the MCP servers and
functions installed on this machine (`mcp-inventory/`).

This repo contains **no application code**. It is knowledge + agent
configuration. Do not add build tooling.

## How to use the agent

1. Read `agent.md` — the authoritative agent definition and operating loop.
2. Load the workflow `workflows/fw-penetration-test.md`
   (+ `workflows/security-audit.md`, `workflows/api-security-review.md`).
3. Load the specific skills the assessment needs from `skills/`
   (see `skills-index.md`).
4. Use the MCP tools listed in `agent.md`; confirm they exist via
   `mcp-inventory/system-mcps.md` / `mcp-inventory/mcp-functions.md`.
5. Fan out to `subagents/` (scanner → api-reviewer → agent-layer-reviewer →
   validator → report-writer) and merge.
6. Emit the report format defined in `agent.md`.

## Layout

| Path | Contents |
|---|---|
| `agent.md` | The security agent definition (main deliverable). |
| `subagents/` | Scanner / api-reviewer / agent-layer-reviewer / validator / report-writer. |
| `skills/` | 24 verbatim `SKILL.md` copies. See `skills-index.md`. |
| `workflows/` | 6 verbatim workflow `.md` files. See `workflows-index.md`. |
| `mcpservers/` | JSON entries: recommended security MCPs + installed on this machine. |
| `agents/` | JSON entries for recommended agent platforms. |
| `tools/` | Combined ranking JSON of recommended open-source tools. |
| `docs/` | Combined ranking JSON of recommended documentation. |
| `features/` | Combined ranking JSON of recommended product features. |
| `advice/` | The advice report (`task-advice-report.md`) + JSON (`task-advice.json`). |
| `mcp-inventory/` | Live system MCP inventory: servers, functions, catalog, orchestrator API. |
| `knowledge/` | Reserved for an Obsidian vault + Graphify graph (optional, not populated). |
| `manifest.json` | Machine-readable index of every file in this package. |

## MCP inventory (source of truth)

Regenerate any time with the local **agent-mcp-orchestrator** (`http://localhost:8790`):

| Endpoint | Writes |
|---|---|
| `GET /api/health` | `mcp-inventory/orchestrator-health.json` |
| `GET /api/servers` | `mcp-inventory/orchestrator-servers.json` (installed + catalog) |
| `GET /api/functions` | `mcp-inventory/mcp-functions.json` |
| `GET /api/agents` | `mcp-inventory/agent-configs.json` |

Human-readable views are `system-mcps.md`, `mcp-functions.md`, `mcp-catalog.md`.
API reference: `mcp-inventory/orchestrator-api.md`.

## The advice loop (mandated by get_task_advice)

1. **Persist** — every skill/workflow/MCP/agent/doc loaded for a task is saved
   under this repo (already done).
2. **Report back** — after each step, update the notes/graph, query the graph,
   and pass only the graph summary + this advice as context to the LLM.
3. **Re-advise** — call `get_task_advice(<updated status>)` again and refresh
   `advice/` when the task changes.

## Conventions

- **Do not edit** the copied `skills/` and `workflows/` files — they are
  verbatim source artifacts. Add new material in a new folder.
- Keep `manifest.json` in sync when adding files.
- Never commit secrets. `advice/` and `mcp-inventory/` contain machine-local
  paths and server names only (no keys).