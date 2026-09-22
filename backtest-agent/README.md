# backtest-agent

A **backtest AI agent** for trading/investment systems, built from a full
**mcp-skills** advice run and packaged with every skill, workflow, MCP-server
entry, tool, doc and feature the advisor recommended — plus a complete live
inventory of the MCP servers and functions installed on this machine.

## Contents

```
backtest-agent/
├── agent.md              # the backtest agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 10 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 4 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # spec-interpreter / backtest-runner / metrics-computer / overfit-checker / report-writer
├── mcpservers/           # recommended backtest MCP-server entries
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

- **Workflow**: `fw-model-evaluation` (primary)
- **Top skills**: `backtesting-frameworks`, `quant-analyst`,
  `ml-model-evaluation`, `risk-manager`, `eng-test-driven-development`
- **MCP servers**: `alphaassay`, `alforge-labs-alpha-forge-mcp`,
  `tradingview-backtest-assistant`, `dolphinquant-echolon`,
  `crashtestyourstrategy`, `keel-trade-keel-trade`
- **Tools**: Backtrader, VectorBT, QuantStats, SciPy

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-model-evaluation.md`.
3. Backtest a strategy:
   ```
   "backtest the BTCUSDT mean-reversion strategy spec from the strategy agent"
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