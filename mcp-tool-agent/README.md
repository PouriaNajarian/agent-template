# mcp-tool-agent

An **MCP/Tool engineering AI agent** for trading/investment systems, built
from a full **mcp-skills** advice run and packaged with every skill, workflow,
MCP-server entry, tool, doc and feature the advisor recommended — plus a
complete live inventory of the MCP servers and functions installed on this
machine.

## Contents

```
mcp-tool-agent/
├── agent.md              # the mcp/tool agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 16 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 4 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # tool-scout / mcp-builder / verifier / contract-writer / gateway-planner
├── mcpservers/           # recommended tool/gateway MCP-server entries
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

- **Workflow**: `api-integration` (primary)
- **Top skills**: `mcp-tool-developer`, `claude-mcp-builder`, `mcp-builder-ms`,
  `mcp-apps-builder`, `global-chat-agent-discovery`, `api-contract-testing`
- **MCP servers**: `mikkoparkkola-mcp-gateway`, `mcp360-universal-gateway`,
  `markgatcha-universal-mcp-toolkit`, `ai-security-gateway-mcp-gateway`
- **Tools**: FastMCP, MCP SDK, mcp-gateway, pytest, OmniRoute

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/api-integration.md`.
3. Install/verify a tool:
   ```
   "install the financekit-mcp server and verify it works"
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