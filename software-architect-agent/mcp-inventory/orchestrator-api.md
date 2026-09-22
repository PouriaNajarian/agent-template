# agent-mcp-orchestrator — Local API Reference

Base URL: `http://localhost:8790` (dashboard + REST API)
MCP endpoint: `http://localhost:8793/mcp` (talking-to-agents MCP server)

The orchestrator is the **source of truth for what MCP servers and functions exist on this machine**.
Always query it before assuming a server or tool is available.

## Read endpoints used to build this inventory

| Method | Path | Purpose |
|---|---|---|
| GET | `/api/health` | Live status of every server: http, stdio, remote, frontends + summary counts. |
| GET | `/api/servers` | `catalog` (all installable MCP servers) + `http`/`stdio`/`remote`/`frontends` groups with status, ports, install commands, docs links. |
| GET | `/api/functions` | Every function/tool exposed by every installed MCP server (`server`, `name`, `description`, `parameters`). May report `rebuilding: true` while it re-probes. |
| GET | `/api/agents` | Agent CLI configs detected on this machine (Claude Code, Codex, Cursor, Cline, Zed, VS Code Copilot, Devin/Cascade, OpenCode) with live paths + sync state. |
| GET | `/api/agent-config?agent=<id>` | Read a specific agent's MCP config file. |
| GET | `/api/logs` `/api/logs/stats` | Health-check logs and severity stats. |
| GET | `/api/incidents` `/api/incidents/stats` | Open/resolved server incidents. |
| GET | `/api/monitor` `/api/settings` | Monitor state + log/incident retention. |

## Write / action endpoints

| Method | Path | Purpose |
|---|---|---|
| POST | `/api/server/action` | Start / stop / restart / pause / resume a server by name. |
| POST | `/api/start` `/api/stop` | Start / stop all MCP servers. |
| POST | `/api/sync-configs` | Push the server set to every agent CLI config. |
| GET | `/api/discover-agents` | Scan PATH + known config locations for AI agents/CLIs. |
| POST | `/api/test-agent` | Static checks + CLI smoke test for an agent config. |
| POST | `/api/agent/chat` | Orchestrator's built-in AI chat (install/uninstall, status, functions). |
| POST | `/api/auto-debug` | DeepSeek AI incident auto-diagnosis. |
| POST | `/api/incidents` / PATCH `/api/incidents/<id>` | Create / update incidents. |
| POST | `/api/firewall` | Add firewall rules for HTTP/SSE server ports. |

## MCP tools exposed by the orchestrator (to agents)

| Tool | Purpose |
|---|---|
| `get_mcp_status` | **START HERE** — live health of all MCP servers (http/stdio/remote/frontends) + summary. |
| `list_mcp_servers` | List installed + the installable catalog; `filter` to search. |
| `get_server_info` | Full details for one server incl. a ready-to-paste MCP client config snippet. |
| `get_server_docs` | Fetch a catalog entry's README/docs; extract install commands + remote MCP URLs. |
| `get_server_functions` | List the tools a server exposes (probes it live if needed). |
| `get_server_logs` | Recent health logs for one server (debug flapping/down). |
| `get_open_incidents` | Open server incidents with priority + lifecycle status. |
| `install_mcp_server` | Install/register a server (local command or hosted URL) and push to all agent configs. |
| `uninstall_mcp_server` | Remove a custom server from the system and all agent configs. |

Source of truth on disk: `D:\projects\agent-mcp-orchestrator\`
