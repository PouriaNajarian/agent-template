# AGENTS.md — code-reviewer-agent

Operating guide + manifest for any AI agent working in this repository.
Generated from a full **mcp-skills `get_task_advice`** run (see
`advice/task-advice-report.md`). Recommended workflow: **`fw-code-review`**.

## What this repo is

A **self-contained code-reviewer agent package**: the agent definition
(`agent.md`), its helper subagents (`subagents/`), and verbatim copies of every
skill, workflow, MCP-server entry, tool, doc and feature the mcp-skills advisor
recommended for the task — plus a full live inventory of the MCP servers and
functions installed on this machine (`mcp-inventory/`).

This repo contains **no application code**. It is knowledge + agent
configuration. Do not add build tooling.

## How to use the agent

1. Read `agent.md` — the authoritative agent definition and operating loop.
2. Load the workflow `workflows/fw-code-review.md` (fast pass:
   `workflows/code-review-pass.md`).
3. Load the specific skills the review needs from `skills/` (see
   `skills-index.md`).
4. Use the MCP tools listed in `agent.md`; confirm they exist via
   `mcp-inventory/system-mcps.md` / `mcp-inventory/mcp-functions.md`.
5. For large diffs, fan out to `subagents/` and merge findings.
6. Emit the report format defined in `agent.md`.

## Layout

| Path | Contents |
|---|---|
| `agent.md` | The code-reviewer agent definition (main deliverable). |
| `subagents/` | Correctness / security / performance / test-coverage / PR-context reviewers. |
| `skills/` | 53 verbatim `SKILL.md` copies + a combined ranking JSON. See `skills-index.md`. |
| `workflows/` | 16 verbatim workflow `.md` files. See `workflows-index.md`. |
| `mcpservers/` | JSON entries for recommended + installed MCP servers. |
| `agents/` | JSON entries for recommended AI agent platforms (langflow, flowise, dify, crewai, autogen, comfyui). |
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

## The advice loop (mandated by `get_task_advice`)

1. **Persist** — every skill/workflow/MCP/agent/doc loaded for a task is saved
   under this repo (already done).
2. **Report back** — after each review step, update the notes/graph, query the
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
