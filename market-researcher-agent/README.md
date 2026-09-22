# market-researcher-agent

A **market research AI agent** for trading/investment systems, built from a
full **mcp-skills** advice run and packaged with every skill, workflow,
MCP-server entry, tool, doc and feature the advisor recommended — plus a
complete live inventory of the MCP servers and functions installed on this
machine.

## Contents

```
market-researcher-agent/
├── agent.md              # the market researcher agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 22 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 7 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # sector-scout / news-hunter / data-gatherer / synthesis-writer / citation-editor
├── mcpservers/           # recommended research/finance MCP-server entries
├── agents/               # agent/platform entries (claude-code, dify, crewai, langflow...)
├── tools/                # recommended open-source tools (ranking JSON)
├── docs/                 # recommended documentation (ranking JSON)
├── features/             # recommended product features (ranking JSON)
├── advice/               # advice report + JSON
├── mcp-inventory/        # live system MCP inventory (servers, functions, catalog, API)
└── manifest.json         # machine-readable index of every file
```

## The advice behind it

The mcp-skills advisor returned:

- **Workflow**: `fw-research-optimize-execute` (primary)
- **Top skills**: `deep-research`, `news-sentiment-engine`,
  `longbridge-market-data`, `multi-source-search`, `competitive-landscape`,
  `market-sizing-analysis`, `compile-knowledge`, `xvary-stock-research`
- **MCP servers**: `yahoo-finance`, `mcp-yahoo-finance`, `alpha-vantage`,
  `financekit-mcp`, `findata-mcp`, `binance-cryptocurrency-mcp`,
  `aegisgovdao-aegisgov-sec-mcp` (SEC EDGAR), `alpaca`
- **Agents**: claude-code, dify, crewai, langflow
- **Tools**: Pandas, DuckDB, open-deep-research

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-research-optimize-execute.md`.
3. Research a market:
   ```
   "research the AI infrastructure sector for long-term opportunities"
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