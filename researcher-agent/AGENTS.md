# AGENTS.md — researcher-agent

Operating guide + manifest for any AI agent working in this repository.
Generated from a full **mcp-skills `get_task_advice`** run (see
`advice/task-advice-report.md`). Recommended workflow: **`fw-research-optimize-execute`**.

## What this repo is

A **self-contained researcher agent package**: the agent definition
(`agent.md`), its helper subagents (`subagents/`), and verbatim copies of every
skill, workflow, MCP-server entry, agent, tool, doc and feature the mcp-skills
advisor recommended for the research task — plus the research-core catalog
curation (the advisor flagged catalog coverage as weak for this task; the
irrelevant #1 workflow hit `fix-slow-checkout-page` was noted and superseded)
— plus a full live inventory of the MCP servers and functions installed on
this machine (`mcp-inventory/`).

This repo contains **no application code**. It is knowledge + agent
configuration. Do not add build tooling.

## How to use the agent

1. Read `agent.md` — the authoritative agent definition and operating loop.
2. Load the workflow `workflows/fw-research-optimize-execute.md`
   (plain variant: `workflows/research-optimize-execute.md`).
3. Load the specific skills the research needs from `skills/`
   (see `skills-index.md`).
4. Use the MCP tools listed in `agent.md`; confirm they exist via
   `mcp-inventory/system-mcps.md` / `mcp-inventory/mcp-functions.md`.
5. For multi-part questions, fan out to `subagents/` (scout → hunters →
   fact-checker → writer → citation-editor) and merge.
6. Emit the report format defined in `agent.md`.

## Layout

| Path | Contents |
|---|---|
| `agent.md` | The researcher agent definition (main deliverable). |
| `subagents/` | Topic-scout / source-hunter / fact-checker / synthesis-writer / citation-editor. |
| `skills/` | 36 verbatim `SKILL.md` copies (advice hits + research-core curation). See `skills-index.md`. |
| `workflows/` | 15 verbatim workflow `.md` files. See `workflows-index.md`. |
| `mcpservers/` | JSON entries: 15 advice-recommended research MCPs + 11 installed on this machine + combined ranking. |
| `agents/` | JSON entries: 12 recommended agent/platform entries (crewai top) + combined ranking. |
| `tools/` | Combined ranking JSON of recommended open-source tools. |
| `docs/` | Combined ranking JSON of recommended documentation. |
| `features/` | Combined ranking JSON of recommended product features. |
| `advice/` | The full `get_task_advice` payload (`task-advice.json`) + readable report (`task-advice-report.md`). |
| `mcp-inventory/` | Live system MCP inventory: servers, functions, catalog, orchestrator API. |
| `knowledge/` | Reserved for an Obsidian vault + Graphify graph (optional, not populated). |
| `manifest.json` | Machine-readable index of every file in this package. |

## MCP inventory (source of truth)

Regenerate any time with the local **agent-mcp-orchestrator** (`http://localhost:8790`):

| Endpoint | Writes |
|---|---|
| `GET /api/health` | `mcp-inventory/orchestrator-health.json` |
| `GET /api/servers` | `mcp-inventory/orchestrator-servers.json` (installed + 14k catalog) |
| `GET /api/functions` | `mcp-inventory/mcp-functions.json` |
| `GET /api/agents` | `mcp-inventory/agent-configs.json` |

Human-readable views are `system-mcps.md`, `mcp-functions.md`, `mcp-catalog.md`.
API reference: `mcp-inventory/orchestrator-api.md`.

## The advice loop (mandated by get_task_advice)

1. **Persist** — every skill/workflow/MCP/agent/doc loaded for a task is saved
   under this repo (already done).
2. **Report back** — after each research step, update the notes/graph, query the
   graph, and pass only the graph summary + this advice as context to the LLM
   (saves tokens).
3. **Re-advise** — call `get_task_advice(<updated status>)` again and refresh
   `advice/` when the task changes.

## Conventions

- **Do not edit** the copied `skills/` and `workflows/` files — they are
  verbatim source artifacts. Add new material in a new folder.
- Keep `manifest.json` in sync when adding files.
- Never commit secrets. `advice/` and `mcp-inventory/` contain machine-local
  paths and server names only (no keys).
