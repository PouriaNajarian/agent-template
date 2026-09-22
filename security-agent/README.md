# security-agent

A **security AI agent** for trading/investment systems, built from a full
**mcp-skills** advice run and packaged with every skill, workflow, MCP-server
entry, tool, doc and feature the advisor recommended — plus a complete live
inventory of the MCP servers and functions installed on this machine.

## Contents

```
security-agent/
├── agent.md              # the security agent (start here)
├── AGENTS.md             # operating guide + manifest
├── skills/               # 24 verbatim SKILL.md copies (+ skills-index.md)
├── workflows/            # 6 verbatim workflow .md files (+ workflows-index.md)
├── subagents/            # scanner / api-reviewer / agent-layer-reviewer / validator / report-writer
├── mcpservers/           # recommended security MCP-server entries
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

- **Workflow**: `fw-penetration-test` (primary), `security-audit`, `api-security-review`
- **Top skills**: `security-audit`, `security-scanning-security-sast`,
  `security-scanning-security-dependencies`, `api-security-testing`,
  `llm-security`, `threat-modeling-expert`, `exploitability-validation`
- **MCP servers**: `skyrxin-sast-mcp-server`, `mcp-zap-server`, `mcpshield`,
  `owasp-agentic-security-mcp`, `mcp-prompt-injection-scanner`, `semgrep`
- **Tools**: ZAP, Semgrep, Gitleaks, Trivy, Burp Suite, Bandit

Full plan, steps, cautions, `how_to_read`, combined-ranking functions and the
methodology report are in **`advice/task-advice-report.md`**.

## Quick start

1. Open `agent.md`.
2. Load `workflows/fw-penetration-test.md`.
3. Run an assessment:
   ```
   "security audit of the trading system repo and MCP stack"
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