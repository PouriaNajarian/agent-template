# System MCP Inventory (agent-mcp-orchestrator :8790)

Generated: 2026-09-20 20:58  
Source: `http://localhost:8790/api/health`  
Summary: total=24 up=24 down=0 degraded=0

## HTTP

| Name | Transport | Port | Status | Description | URL / Command |
|---|---|---|---|---|---|
| mcp-skills | http | 8788 | up | Skill discovery and ranking (678 skills) | http://localhost:8788/mcp |
| playwright | sse | 8791 | up | Browser automation (chromium) | http://localhost:8791/sse |
| winremote | http | 8792 | up | Windows remote control (process, registry, services) | http://localhost:8792/mcp |
| agent-mcp-orchestrator | http | 8793 | up | MCP server: AI agents query server status + usage info | http://localhost:8793/mcp |
| omniroute | http | 20128 | up | OmniRoute AI gateway MCP - 352 providers, 1200+ models (dashboard :20128/dashboard) | http://localhost:20128/api/mcp/stream |
| 9router | http | 20228 | up | 9Router AI proxy MCP - 60+ providers, 3-tier fallback (dashboard :20228/dashboard) | http://localhost:20228/api/mcp |

## STDIO

| Name | Transport | Port | Status | Description | URL / Command |
|---|---|---|---|---|---|
| context7 | stdio | - | available | Library docs lookup | npx -y @upstash/context7-mcp@latest |
| filesystem | stdio | - | available | File system access | npx -y @modelcontextprotocol/server-filesystem |
| git | stdio | - | available | Git operations | uvx mcp-server-git |
| memory | stdio | - | available | Knowledge graph memory | npx -y @modelcontextprotocol/server-memory |
| time | stdio | - | available | Time/timezone | uvx --system-certs mcp-server-time |
| tdai-memory | stdio | - | available | TencentDB memory | node mcp-server.mjs |
| agent-mcp-orchestrator | stdio | - | available | Query MCP server status and usage info | python agent_mcp_orchestrator.py |
| google-merchant-mcp | stdio | - | available | Google Merchant Center MCP — product feed diagnostics for PELLE | node D:\Projects\google-merchant-mcp\server.js |
| meta-ads-mcp-server | stdio | - | available | Meta Ads Catalog MCP - Facebook/Instagram Ads API: accounts, campaigns, ad sets, ads, creatives, media, insights, targeting, pages (PELLE) | node D:\Projects\meta-ads-mcp\dist\index.js |
| postgres-mcp | stdio | - | available | Official Microsoft Postgres MCP server - query, analyze, and manage PostgreSQL databases (stdio) | npx -y @microsoft/postgres-mcp run |
| Binance Cryptocurrency MCP | stdio | - | available | Access real-time Binance cryptocurrency market data: prices, candlestick charts, order books and trading history. | npx -y @snjyor/binance-mcp@latest |
| @hanoak/unsplash-mcp-server | stdio | - | available | Production-ready MCP server for the Unsplash API — search photos, fetch details, Unsplash attribution & download-tracking compliance. Unofficial. | npx -y @hanoak/unsplash-mcp-server |

## REMOTE

| Name | Transport | Port | Status | Description | URL / Command |
|---|---|---|---|---|---|
| devin/cloudflare-docs | remote | - | up | Cloudflare documentation | https://docs.mcp.cloudflare.com/mcp |
| devin/deepwiki | remote | - | up | DeepWiki repository docs | https://mcp.deepwiki.com/mcp |
| devin/github-mcp-server | remote | - | up | GitHub MCP server | https://api.githubcopilot.com/mcp |

## FRONTENDS

| Name | Transport | Port | Status | Description | URL / Command |
|---|---|---|---|---|---|
| mcp-skills-dashboard | frontends | 8787 | up | MCP Skills web dashboard (browse/search skills, activity feed) | http://localhost:8787 |
| omniroute-dashboard | frontends | 20128 | up | OmniRoute web dashboard (352 providers, API keys, combos, usage) | http://localhost:20128/dashboard |
| 9router-dashboard | frontends | 20228 | up | 9Router web dashboard (providers, combos, quota tracker, token saver) | http://localhost:20228/dashboard |


