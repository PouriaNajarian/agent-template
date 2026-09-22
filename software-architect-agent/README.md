# software-architect-agent

A **software-architect AI agent** built from a full
[**mcp-skills**](http://localhost:8788/mcp) `get_task_advice` run, packaged with
every skill, workflow, MCP-server entry, tool, doc and feature the advisor
recommended — plus a complete live inventory of the MCP servers and functions
installed on this machine.

## Contents

```
software-architect-agent/
├── agent.md              # the software-architect agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 97 SKILL.md copies fetched via get_skill (+ skills-index.md)
├── workflows/            # 36 workflow .md files fetched via get_workflow (+ workflows-index.md)
├── subagents/            # system-design / domain / integration / NFR / tech-debt / ADR
├── mcpservers/           # MCP-server combined ranking (get_mcpservers_combined)
├── agents/               # AI agent/platform combined ranking (get_agents_combined)
├── tools/                # open-source tools combined ranking (get_tools_combined)
├── docs/                 # documentation combined ranking (get_docs_combined)
├── features/             # product features combined ranking (get_features_combined)
├── advice/               # full get_task_advice payload(s) + readable report
├── mcp-inventory/        # live system MCP inventory (servers, functions, catalog, API)
└── manifest.json         # machine-readable index of every file
```

## The advice behind it

`get_task_advice("Build a software architect AI agent ...")` returned:

- **Workflow**: `fw-feature-delivery` (primary); supporting `fw-spec-driven-development`,
  `fw-role-separated-agents`, `fw-model-development`, `fw-code-review`, `fw-compliance-audit`
- **Top skills**: `software-architecture`, `architect-review`, `architecture-patterns`,
  `ontoly-software-graph`, `event-sourcing-architect`, `ms-cloud-solution-architect`,
  `design-orchestration`, `brave-man`
- **MCP servers**: `narasimhaponnada-mermaid-mcp`, `tosin2013-mcp-adr-analysis-server`,
  `rdanieli-tentra-mcp`, `bv-venky-excalidraw-architect-mcp`, `diagram-guru`
- **Tools**: Terraform, Mermaid Live, Excalidraw
- **Docs**: `deepseek-api-docs`, `flask-docs`, `model-context-protocol-spec`

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`** (run 2) and
`advice/task-advice-run1.json` (run 1).

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-feature-delivery.md`.
3. Follow the operating loop: frame → domain → structure → contracts → NFRs →
   decisions → diagrams → review.
4. Produce the Architecture Design Doc + ADRs + C4 diagram using the format in
   `agent.md`.

## MCP inventory

Copied from the local **agent-mcp-orchestrator** (`http://localhost:8790`):

- `mcp-inventory/system-mcps.md` — installed servers (http / stdio / remote / frontends)
- `mcp-inventory/mcp-functions.md` — every tool every installed server exposes
- `mcp-inventory/mcp-catalog.md` — installable catalog (index + category summary)
- `mcp-inventory/orchestrator-api.md` — orchestrator REST/MCP reference

## Notes

- `skills/` and `workflows/` are **fetched verbatim from the mcp-skills MCP
  server** (not read from the catalog folder) — do not edit them.
- No secrets are stored; only local paths and server names.
