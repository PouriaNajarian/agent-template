<div align="center">

# 🤖 Agent Template Collection

**14 self-contained AI agent packages** — trading team, research, security, QA, project management & scrum — each built from **mcp-skills advice** + **live agent-mcp-orchestrator inventory**.

[![GitHub](https://img.shields.io/badge/GitHub-agent--template-181717?logo=github&logoColor=white)](https://github.com/PouriaNajarian/agent-template)
[![AI Agents](https://img.shields.io/badge/AI-Agents-4f8cff)](https://github.com/PouriaNajarian/agent-template)
[![MCP](https://img.shields.io/badge/MCP-Model_Context_Protocol-6ee7b7)](https://modelcontextprotocol.io)
[![Made with opencode](https://img.shields.io/badge/Made%20with-opencode-1f6feb)](https://opencode.ai)

</div>

---

## What is this?

A **battle-tested template repository** for building production AI agents. Every
agent folder follows the **exact same method**: a full `mcp-skills` advice run
(`get_task_advice` / vector + DeepSeek ranking) packaged together with a **live
inventory of the MCP servers and functions installed on the machine**
(`agent-mcp-orchestrator`). Open any `agent.md` — it's a complete, runnable
agent definition with operating loop, quality gates, subagents and tool
contracts.

**No application code. Pure knowledge + agent configuration.** Clone → read →
load the workflow → the agent runs.

## Agents (14)

### 🧪 Trading / investment team
| Agent | Folder | What it does |
|---|---|---|
| 📊 **Market Researcher** | `market-researcher-agent` | Markets, sectors, news & sentiment; citation-backed reports with evidence ledger |
| 🛠️ **Data Engineer** | `data-engineer-agent` | Market-data pipelines: ingestion, cleaning, validation, schemas, quality gates |
| 🏦 **Fundamental Analyst** | `fundamental-analyst-agent` | Statements, SEC filings, earnings quality, DCF + multiples valuation |
| 📈 **Technical Analyst** | `technical-analyst-agent` | Price action, indicators, S/R levels, bias with entry/exit/invalidation |
| 🎯 **Trading Strategy Agent** | `trading-strategy-agent` | Falsifiable strategy specs: signals, sizing, risk, test plans |
| 🔬 **Backtest Agent** | `backtest-agent` | Runs backtests with realistic costs, IS/OOS, overfitting checks, verdicts |

### 🧰 Platform & quality
| Agent | Folder | What it does |
|---|---|---|
| 🔌 **MCP/Tool Agent** | `mcp-tool-agent` | Discovers, installs, builds, verifies and documents MCP servers |
| 🔐 **Security Agent** | `security-agent` | SAST/SCA/secrets/agent-layer audits with exploitability validation |
| ✅ **QA Agent** | `qa-agent` | Test strategy, unit/integration/E2E, coverage gates, verification sign-off |

### 📋 Delivery
| Agent | Folder | What it does |
|---|---|---|
| 🗺️ **Project Management Agent** | `project-management-agent` | Plans & tracks the program: milestones, task graph, risks, status |
| 🏃 **Scrum Master Agent** | `scrum-master-agent` | Ceremonies, velocity/burndown, impediment removal, retros |
| 🧠 **Researcher Agent** | `researcher-agent` | Deep multi-source research with source grading |
| 👁️ **Code Reviewer Agent** | `code-reviewer-agent` | Severity-ranked PR/diff review with approve/block verdicts |
| 🏗️ **Software Architect Agent** | `software-architect-agent` | Architecture design, ADRs, tech-debt & design reviews |

## Why this structure works

```
agent-name/
├── agent.md              # the agent: frontmatter, mission, operating loop, output format
├── AGENTS.md             # operating guide + manifest for any AI agent in the folder
├── README.md             # quick start
├── skills/               # verbatim SKILL.md copies the advisor recommended
├── workflows/            # verbatim workflow .md files
├── subagents/            # 5 role subagents per agent (parallel fan-out)
├── mcpservers/           # recommended + installed MCP server entries (JSON)
├── agents/               # agent/platform entries (langflow, dify, crewai…)
├── tools/  docs/  features/   # combined-ranking JSON per catalog
├── advice/               # full get_task_advice report + JSON payload
├── mcp-inventory/        # LIVE system inventory: servers, functions, catalog, API
└── manifest.json         # machine-readable index of every file
```

Every agent ships with: **operating loop, quality gates, severity/verdict
taxonomies, anti-patterns** — so a fresh model can execute it immediately.

## Quick start

```bash
# 1. Open any agent
cd market-researcher-agent
# 2. Read the agent definition (start here)
# agent.md
# 3. Load the recommended workflow
# workflows/fw-research-optimize-execute.md
# 4. Load skills as needed (see skills-index.md)
# 5. Confirm MCP tools via mcp-inventory/system-mcps.md
```

## How it's generated (the method)

1. **`mcp-skills`** (`http://localhost:8787`): `get_task_advice(<task>)` →
   recommended skills, workflows, MCP servers, agents, tools, docs, features.
2. **`agent-mcp-orchestrator`** (`http://localhost:8790`): live inventory —
   `/api/health`, `/api/servers`, `/api/functions`, `/api/agents`.
3. Assemble each folder: verbatim skill/workflow copies + JSON catalog entries
   + advice payload + inventory + hand-authored `agent.md`/`AGENTS.md`.

## Regenerating the MCP inventory

```powershell
curl.exe -s http://localhost:8790/api/health    > mcp-inventory/orchestrator-health.json
curl.exe -s http://localhost:8790/api/servers   > mcp-inventory/orchestrator-servers.json
curl.exe -s http://localhost:8790/api/functions > mcp-inventory/mcp-functions.json
curl.exe -s http://localhost:8790/api/agents    > mcp-inventory/agent-configs.json
```

## Related

- [mcp-skills](http://localhost:8787) — skill discovery & ranking (2,800+ skills)
- [agent-mcp-orchestrator](https://github.com/PouriaNajarian/agent-mcp-orchestrator) — MCP health dashboard
- [Model Context Protocol](https://modelcontextprotocol.io) — the protocol behind the tools

## License

MIT — use the templates, fork the agents, build your own team.

---

<div align="center">
⭐ **Star this repo** if you build agents — it keeps the templates alive.
</div>