# code-reviewer-agent

A **code-reviewer AI agent** built from a full
[**mcp-skills**](http://localhost:8787) `get_task_advice` run, packaged with every
skill, workflow, MCP-server entry, tool, doc and feature the advisor recommended —
plus a complete live inventory of the MCP servers and functions installed on this
machine.

## Contents

```
code-reviewer-agent/
├── agent.md              # the code-reviewer agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 53 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 16 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # correctness / security / performance / tests / PR-context reviewers
├── mcpservers/           # 17 MCP-server entries (recommended + installed)
├── agents/               # 6 AI agent/platform entries
├── tools/                # recommended open-source tools (ranking JSON)
├── docs/                 # recommended documentation (ranking JSON)
├── features/             # recommended product features (ranking JSON)
├── advice/               # full get_task_advice payload + readable report
├── mcp-inventory/        # live system MCP inventory (servers, functions, catalog, API)
└── manifest.json         # machine-readable index of every file
```

## The advice behind it

`get_task_advice("Build a code reviewer AI agent ...")` returned:

- **Workflow**: `fw-code-review` (primary), `code-review-pass` (fast pass)
- **Top skills**: `code-review`, `vibers-code-review`, `code-review-checklist`,
  `review-swarm`, `differential-review`, `eng-code-review-and-quality`,
  `web-code-review`, `cf-code-review`, `openai-security-best-practices`,
  `performance-testing-review-multi-agent-review`
- **MCP servers**: `notasandy-mcp-code-sanitizer`, `mcp-code-review-server`,
  `selvage-lab-selvage`, `corbym-backlog-mcp`
- **Tools**: SonarQube, ripgrep, Prettier

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
21-section methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-code-review.md`.
3. Review a diff:
   ```
   git diff <base>...HEAD
   ```
4. Produce the report using the format in `agent.md`.

## MCP inventory

Built from the local **agent-mcp-orchestrator** (`http://localhost:8790`):

- `mcp-inventory/system-mcps.md` — installed servers (http / stdio / remote / frontends)
- `mcp-inventory/mcp-functions.md` — every tool every installed server exposes
- `mcp-inventory/mcp-catalog.md` — 14,111-server installable catalog (index + category summary)
- `mcp-inventory/orchestrator-api.md` — orchestrator REST/MCP reference

## Regenerating

```powershell
# system MCP inventory
curl.exe -s http://localhost:8790/api/health   > mcp-inventory/orchestrator-health.json
curl.exe -s http://localhost:8790/api/servers  > mcp-inventory/orchestrator-servers.json
curl.exe -s http://localhost:8790/api/functions> mcp-inventory/mcp-functions.json
curl.exe -s http://localhost:8790/api/agents   > mcp-inventory/agent-configs.json
```

## Notes

- `skills/` and `workflows/` are **verbatim** copies — do not edit them.
- `code-review` is a catalog-only seed skill (no source file on disk); its
  catalog entry is preserved under `skills/code-review/`.
- No secrets are stored; only local paths and server names.
