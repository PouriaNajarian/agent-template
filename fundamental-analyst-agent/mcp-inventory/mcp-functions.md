# MCP Functions Inventory (agent-mcp-orchestrator :8790)

Generated: 2026-09-22 13:59  
Source: http://localhost:8790/api/functions  

## 9router

| Function | Description |
|---|---|
| $(@{server=9router; name=status; description=Proxy status: uptime, tiers, providers (GET /v1/status); parameters=}.name) | Proxy status: uptime, tiers, providers (GET /v1/status) |
| $(@{server=9router; name=models; description=List available models across tiers (GET /v1/models); parameters=}.name) | List available models across tiers (GET /v1/models) |
| $(@{server=9router; name=chat_completions; description=OpenAI-compatible completions with 3-tier fallback (POST /v1/chat/completions); parameters=model, messages}.name) | OpenAI-compatible completions with 3-tier fallback (POST /v1/chat/completions) |
| $(@{server=9router; name=providers; description=Provider list with quota/quota-tracker status (GET /v1/providers); parameters=}.name) | Provider list with quota/quota-tracker status (GET /v1/providers) |
| $(@{server=9router; name=usage; description=Token saver usage reports (GET /v1/usage); parameters=period}.name) | Token saver usage reports (GET /v1/usage) |

## 9router-dashboard

| Function | Description |
|---|---|
| $(@{server=9router-dashboard; name=manage_providers; description=Providers, combos, quota tracker (UI at :20228/dashboard); parameters=}.name) | Providers, combos, quota tracker (UI at :20228/dashboard) |
| $(@{server=9router-dashboard; name=token_saver; description=Token saver stats and settings (UI at :20228/dashboard); parameters=}.name) | Token saver stats and settings (UI at :20228/dashboard) |

## agent-mcp-orchestrator

| Function | Description |
|---|---|
| $(@{server=agent-mcp-orchestrator; name=get_mcp_status; description=Get the live health status of ALL MCP servers on this system (local HTTP/SSE servers, frontend dashboards, stdio servers, remote servers) plus a summary. START HERE for any question about what is running, what is down, or the overall health.; parameters=}.name) | Get the live health status of ALL MCP servers on this system (local HTTP/SSE servers, frontend dashboards, stdio servers, remote servers) pl... |
| $(@{server=agent-mcp-orchestrator; name=list_mcp_servers; description=List all known MCP servers — installed ones AND the ~15k-server installable catalog (awesome-mcp-servers + mcpservers.org). Use 'filter' to search (e.g. 'pdf', 'github', 'browser'). Entries show status (up/down/not_installed), transport, and the install command when known. To install one: note its name, then call get_server_docs for the exact command, then install_mcp_server.; parameters=filter}.name) | List all known MCP servers — installed ones AND the ~15k-server installable catalog (awesome-mcp-servers + mcpservers.org). Use 'filter' to ... |
| $(@{server=agent-mcp-orchestrator; name=get_server_info; description=Get full details for one MCP server: status, port, transport, endpoints, install command, docs link, AND a ready-to-paste 'How to use it' MCP client config snippet. Use after installing, or when the user asks how to connect/use a server.; parameters=name}.name) | Get full details for one MCP server: status, port, transport, endpoints, install command, docs link, AND a ready-to-paste 'How to use it' MC... |
| $(@{server=agent-mcp-orchestrator; name=get_server_docs; description=Fetch the documentation/README for a catalog server and extract install commands, remote MCP URLs, and API-key requirements. CALL THIS BEFORE install_mcp_server whenever the catalog entry has no install command — never guess commands.; parameters=name}.name) | Fetch the documentation/README for a catalog server and extract install commands, remote MCP URLs, and API-key requirements. CALL THIS BEFOR... |
| $(@{server=agent-mcp-orchestrator; name=get_server_functions; description=List the MCP functions/tools a server exposes (probes it live if needed). Use after installing a server to confirm it works and show the user what it can do. Also useful to decide whether a catalog server fits the user's needs.; parameters=name}.name) | List the MCP functions/tools a server exposes (probes it live if needed). Use after installing a server to confirm it works and show the use... |
| $(@{server=agent-mcp-orchestrator; name=install_mcp_server; description=Install/register an MCP server on this system and push it to ALL agent CLI configs automatically. Two ways: (1) LOCAL: install_command must be an exact runnable command whose runner exists (npx/uvx/node/pip/docker/...); (2) HOSTED/REMOTE: pass url (e.g. https://api.example.com/mcp) — no local process needed. The command is VALIDATED first; if rejected, read the error, use get_server_docs/web_search to find the correct command, and retry. Ask the user before installing anything they did not explicitly request.; parameters=description, install_command, name, port, transport, url}.name) | Install/register an MCP server on this system and push it to ALL agent CLI configs automatically. Two ways: (1) LOCAL: install_command must ... |
| $(@{server=agent-mcp-orchestrator; name=uninstall_mcp_server; description=Uninstall a CUSTOM MCP server (one installed via install_mcp_server) — removes it from this system AND from every agent CLI config. Built-in servers cannot be uninstalled. Always confirm with the user before calling.; parameters=name}.name) | Uninstall a CUSTOM MCP server (one installed via install_mcp_server) — removes it from this system AND from every agent CLI config. Built-in... |
| $(@{server=agent-mcp-orchestrator; name=get_server_logs; description=Get recent health logs for a specific MCP server (or all servers) — useful to debug why a server is down or flapping.; parameters=limit, server}.name) | Get recent health logs for a specific MCP server (or all servers) — useful to debug why a server is down or flapping. |
| $(@{server=agent-mcp-orchestrator; name=get_open_incidents; description=Get open incidents (server problems) recorded by the health dashboard, with priority and lifecycle status. Use to report outstanding problems.; parameters=}.name) | Get open incidents (server problems) recorded by the health dashboard, with priority and lifecycle status. Use to report outstanding problem... |

## Binance Cryptocurrency MCP

| Function | Description |
|---|---|
| $(@{server=Binance Cryptocurrency MCP; name=get_order_book; description=; parameters=limit, symbol}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_recent_trades; description=; parameters=limit, symbol}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_historical_trades; description=; parameters=fromId, limit, symbol}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_aggregate_trades; description=; parameters=endTime, fromId, limit, startTime, symbol}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_klines; description=; parameters=endTime, interval, limit, startTime, symbol, timeZone}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_ui_klines; description=; parameters=endTime, interval, limit, startTime, symbol, timeZone}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_avg_price; description=; parameters=symbol}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_24hr_ticker; description=; parameters=symbol, symbols}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_trading_day_ticker; description=; parameters=symbol, symbols, timeZone, type}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_price; description=; parameters=symbol, symbols}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_book_ticker; description=; parameters=symbol, symbols}.name) |  |
| $(@{server=Binance Cryptocurrency MCP; name=get_rolling_window_ticker; description=; parameters=symbol, symbols, type, windowSize}.name) |  |

## context7

| Function | Description |
|---|---|
| $(@{server=context7; name=resolve-library-id; description=Resolve a library name to its context7 id; parameters=libraryName}.name) | Resolve a library name to its context7 id |
| $(@{server=context7; name=get-library-docs; description=Fetch up-to-date documentation for a library; parameters=context7Id, topic, toc}.name) | Fetch up-to-date documentation for a library |

## devin/cloudflare-docs

| Function | Description |
|---|---|
| $(@{server=devin/cloudflare-docs; name=search_cloudflare_docs; description=Search Cloudflare documentation (auth required); parameters=query}.name) | Search Cloudflare documentation (auth required) |
| $(@{server=devin/cloudflare-docs; name=get_docs_page; description=Fetch a Cloudflare docs page (auth required); parameters=url}.name) | Fetch a Cloudflare docs page (auth required) |

## devin/deepwiki

| Function | Description |
|---|---|
| $(@{server=devin/deepwiki; name=read_wiki_structure; description=Repository wiki table of contents (auth required); parameters=repo}.name) | Repository wiki table of contents (auth required) |
| $(@{server=devin/deepwiki; name=ask_question; description=Ask a question about a repository (auth required); parameters=repo, question}.name) | Ask a question about a repository (auth required) |

## devin/github-mcp-server

| Function | Description |
|---|---|
| $(@{server=devin/github-mcp-server; name=get_me; description=Authenticated GitHub user profile (auth required); parameters=}.name) | Authenticated GitHub user profile (auth required) |
| $(@{server=devin/github-mcp-server; name=search_repositories; description=Search GitHub repositories (auth required); parameters=query}.name) | Search GitHub repositories (auth required) |
| $(@{server=devin/github-mcp-server; name=get_file_contents; description=Read a file from a repository (auth required); parameters=owner, repo, path}.name) | Read a file from a repository (auth required) |
| $(@{server=devin/github-mcp-server; name=list_issues; description=List issues in a repository (auth required); parameters=owner, repo}.name) | List issues in a repository (auth required) |

## filesystem

| Function | Description |
|---|---|
| $(@{server=filesystem; name=read_file; description=Read a file's contents; parameters=path}.name) | Read a file's contents |
| $(@{server=filesystem; name=write_file; description=Create or overwrite a file; parameters=path, content}.name) | Create or overwrite a file |
| $(@{server=filesystem; name=edit_file; description=Make line-based edits to a file; parameters=path, edits, dryRun}.name) | Make line-based edits to a file |
| $(@{server=filesystem; name=list_directory; description=List files and subdirectories; parameters=path}.name) | List files and subdirectories |
| $(@{server=filesystem; name=search_files; description=Recursively search for files matching a pattern; parameters=path, pattern, excludePatterns}.name) | Recursively search for files matching a pattern |
| $(@{server=filesystem; name=get_file_info; description=Get file metadata; parameters=path}.name) | Get file metadata |
| $(@{server=filesystem; name=create_directory; description=Create a new directory; parameters=path}.name) | Create a new directory |
| $(@{server=filesystem; name=move_file; description=Move or rename a file; parameters=source, destination}.name) | Move or rename a file |
| $(@{server=filesystem; name=directory_tree; description=Get a recursive tree of a directory; parameters=path}.name) | Get a recursive tree of a directory |

## git

| Function | Description |
|---|---|
| $(@{server=git; name=git_status; description=Show the working tree status; parameters=repo_path}.name) | Show the working tree status |
| $(@{server=git; name=git_diff_unstaged; description=Show unstaged changes; parameters=repo_path}.name) | Show unstaged changes |
| $(@{server=git; name=git_add; description=Stage files for commit; parameters=repo_path, files}.name) | Stage files for commit |
| $(@{server=git; name=git_commit; description=Commit staged changes; parameters=repo_path, message}.name) | Commit staged changes |
| $(@{server=git; name=git_log; description=Show commit history; parameters=repo_path, max_count}.name) | Show commit history |
| $(@{server=git; name=git_branch; description=List/create branches; parameters=repo_path}.name) | List/create branches |
| $(@{server=git; name=git_checkout; description=Switch branches; parameters=repo_path, branch_name}.name) | Switch branches |

## google-merchant-mcp

| Function | Description |
|---|---|
| $(@{server=google-merchant-mcp; name=placeholder; description=Placeholder stub - project not implemented yet (server.js stub for PELLE); parameters=}.name) | Placeholder stub - project not implemented yet (server.js stub for PELLE) |

## mcp-skills

| Function | Description |
|---|---|
| $(@{server=mcp-skills; name=get_workflows_vector; description=Vector-only ranking over the workflows catalog (fast, ~10ms). Prefer get_workflows_combined for best quality.; parameters=limit, task}.name) | Vector-only ranking over the workflows catalog (fast, ~10ms). Prefer get_workflows_combined for best quality. |
| $(@{server=mcp-skills; name=get_workflows_llm; description=DeepSeek semantic ranking over the workflows catalog (~10-30s, with reasons). Prefer get_workflows_combined unless you need pure-LLM picks.; parameters=limit, task}.name) | DeepSeek semantic ranking over the workflows catalog (~10-30s, with reasons). Prefer get_workflows_combined unless you need pure-LLM picks. |
| $(@{server=mcp-skills; name=get_workflows_combined; description=BEST DEFAULT ranking over the workflows catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first.; parameters=limit, task}.name) | BEST DEFAULT ranking over the workflows catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first... |
| $(@{server=mcp-skills; name=get_workflows_batch; description=Rank the workflows catalog for MANY tasks (up to 15) in one batched DeepSeek call.; parameters=limit, tasks}.name) | Rank the workflows catalog for MANY tasks (up to 15) in one batched DeepSeek call. |
| $(@{server=mcp-skills; name=get_mcpservers_vector; description=Vector-only ranking over the mcpservers catalog (fast, ~10ms). Prefer get_mcpservers_combined for best quality.; parameters=limit, task}.name) | Vector-only ranking over the mcpservers catalog (fast, ~10ms). Prefer get_mcpservers_combined for best quality. |
| $(@{server=mcp-skills; name=get_mcpservers_llm; description=DeepSeek semantic ranking over the mcpservers catalog (~10-30s, with reasons). Prefer get_mcpservers_combined unless you need pure-LLM picks.; parameters=limit, task}.name) | DeepSeek semantic ranking over the mcpservers catalog (~10-30s, with reasons). Prefer get_mcpservers_combined unless you need pure-LLM picks... |
| $(@{server=mcp-skills; name=get_mcpservers_combined; description=BEST DEFAULT ranking over the mcpservers catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first.; parameters=limit, task}.name) | BEST DEFAULT ranking over the mcpservers catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant firs... |
| $(@{server=mcp-skills; name=get_mcpservers_for_task; description=Rank the mcpservers catalog for a task (wrapper: use_llm=False -> vector, True -> llm).; parameters=limit, task, use_llm}.name) | Rank the mcpservers catalog for a task (wrapper: use_llm=False -> vector, True -> llm). |
| $(@{server=mcp-skills; name=get_mcpservers_batch; description=Rank the mcpservers catalog for MANY tasks (up to 15) in one batched DeepSeek call.; parameters=limit, tasks}.name) | Rank the mcpservers catalog for MANY tasks (up to 15) in one batched DeepSeek call. |
| $(@{server=mcp-skills; name=get_agents_vector; description=Vector-only ranking over the agents catalog (fast, ~10ms). Prefer get_agents_combined for best quality.; parameters=limit, task}.name) | Vector-only ranking over the agents catalog (fast, ~10ms). Prefer get_agents_combined for best quality. |
| $(@{server=mcp-skills; name=get_agents_llm; description=DeepSeek semantic ranking over the agents catalog (~10-30s, with reasons). Prefer get_agents_combined unless you need pure-LLM picks.; parameters=limit, task}.name) | DeepSeek semantic ranking over the agents catalog (~10-30s, with reasons). Prefer get_agents_combined unless you need pure-LLM picks. |
| $(@{server=mcp-skills; name=get_agents_combined; description=BEST DEFAULT ranking over the agents catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first.; parameters=limit, task}.name) | BEST DEFAULT ranking over the agents catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. |
| $(@{server=mcp-skills; name=get_agents_for_task; description=Rank the agents catalog for a task (wrapper: use_llm=False -> vector, True -> llm).; parameters=limit, task, use_llm}.name) | Rank the agents catalog for a task (wrapper: use_llm=False -> vector, True -> llm). |
| $(@{server=mcp-skills; name=get_agents_batch; description=Rank the agents catalog for MANY tasks (up to 15) in one batched DeepSeek call.; parameters=limit, tasks}.name) | Rank the agents catalog for MANY tasks (up to 15) in one batched DeepSeek call. |
| $(@{server=mcp-skills; name=get_docs_vector; description=Vector-only ranking over the docs catalog (fast, ~10ms). Prefer get_docs_combined for best quality.; parameters=limit, task}.name) | Vector-only ranking over the docs catalog (fast, ~10ms). Prefer get_docs_combined for best quality. |
| $(@{server=mcp-skills; name=get_docs_llm; description=DeepSeek semantic ranking over the docs catalog (~10-30s, with reasons). Prefer get_docs_combined unless you need pure-LLM picks.; parameters=limit, task}.name) | DeepSeek semantic ranking over the docs catalog (~10-30s, with reasons). Prefer get_docs_combined unless you need pure-LLM picks. |
| $(@{server=mcp-skills; name=get_docs_combined; description=BEST DEFAULT ranking over the docs catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first.; parameters=limit, task}.name) | BEST DEFAULT ranking over the docs catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. |
| $(@{server=mcp-skills; name=get_docs_for_task; description=Rank the docs catalog for a task (wrapper: use_llm=False -> vector, True -> llm).; parameters=limit, task, use_llm}.name) | Rank the docs catalog for a task (wrapper: use_llm=False -> vector, True -> llm). |
| $(@{server=mcp-skills; name=get_docs_batch; description=Rank the docs catalog for MANY tasks (up to 15) in one batched DeepSeek call.; parameters=limit, tasks}.name) | Rank the docs catalog for MANY tasks (up to 15) in one batched DeepSeek call. |
| $(@{server=mcp-skills; name=get_tools_vector; description=Vector-only ranking over the tools catalog (fast, ~10ms). Prefer get_tools_combined for best quality.; parameters=limit, task}.name) | Vector-only ranking over the tools catalog (fast, ~10ms). Prefer get_tools_combined for best quality. |
| $(@{server=mcp-skills; name=get_tools_llm; description=DeepSeek semantic ranking over the tools catalog (~10-30s, with reasons). Prefer get_tools_combined unless you need pure-LLM picks.; parameters=limit, task}.name) | DeepSeek semantic ranking over the tools catalog (~10-30s, with reasons). Prefer get_tools_combined unless you need pure-LLM picks. |
| $(@{server=mcp-skills; name=get_tools_combined; description=BEST DEFAULT ranking over the tools catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first.; parameters=limit, task}.name) | BEST DEFAULT ranking over the tools catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. |
| $(@{server=mcp-skills; name=get_tools_for_task; description=Rank the tools catalog for a task (wrapper: use_llm=False -> vector, True -> llm).; parameters=limit, task, use_llm}.name) | Rank the tools catalog for a task (wrapper: use_llm=False -> vector, True -> llm). |
| $(@{server=mcp-skills; name=get_tools_batch; description=Rank the tools catalog for MANY tasks (up to 15) in one batched DeepSeek call.; parameters=limit, tasks}.name) | Rank the tools catalog for MANY tasks (up to 15) in one batched DeepSeek call. |
| $(@{server=mcp-skills; name=get_features_vector; description=Vector-only ranking over the features catalog (fast, ~10ms). Prefer get_features_combined for best quality.; parameters=limit, task}.name) | Vector-only ranking over the features catalog (fast, ~10ms). Prefer get_features_combined for best quality. |
| $(@{server=mcp-skills; name=get_features_llm; description=DeepSeek semantic ranking over the features catalog (~10-30s, with reasons). Prefer get_features_combined unless you need pure-LLM picks.; parameters=limit, task}.name) | DeepSeek semantic ranking over the features catalog (~10-30s, with reasons). Prefer get_features_combined unless you need pure-LLM picks. |
| $(@{server=mcp-skills; name=get_features_combined; description=BEST DEFAULT ranking over the features catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first.; parameters=limit, task}.name) | BEST DEFAULT ranking over the features catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. |
| $(@{server=mcp-skills; name=get_features_for_task; description=Rank the features catalog for a task (wrapper: use_llm=False -> vector, True -> llm).; parameters=limit, task, use_llm}.name) | Rank the features catalog for a task (wrapper: use_llm=False -> vector, True -> llm). |
| $(@{server=mcp-skills; name=get_features_batch; description=Rank the features catalog for MANY tasks (up to 15) in one batched DeepSeek call.; parameters=limit, tasks}.name) | Rank the features catalog for MANY tasks (up to 15) in one batched DeepSeek call. |
| $(@{server=mcp-skills; name=get_skills_vector; description=Rank skills for a task using ONLY the local index (vector DB + BM25).

Fast (~10ms): chromadb cosine top-50 pool re-ranked with word-level BM25.
Good lexical recall; misses purely semantic matches that the LLM finds.
Prefer get_skills_combined for best quality.; parameters=limit, task}.name) | Rank skills for a task using ONLY the local index (vector DB + BM25).

Fast (~10ms): chromadb cosine top-50 pool re-ranked with word-level B... |
| $(@{server=mcp-skills; name=get_skills_llm; description=Rank skills for a task using ONLY the DeepSeek API semantic ranker.

Slower (~10-30s): the full catalog is sent to deepseek-v4-flash which
returns the most semantically relevant skills with reasons. Falls back
to the opencode skill-ranker subagent if no API key, then to the local
index on failure. Prefer get_skills_combined unless you need pure-LLM
picks.; parameters=limit, task}.name) | Rank skills for a task using ONLY the DeepSeek API semantic ranker.

Slower (~10-30s): the full catalog is sent to deepseek-v4-flash which
r... |
| $(@{server=mcp-skills; name=get_skills_combined; description=Return INTEGRATED skills: research + vector + DeepSeek corrective ranking.

BEST DEFAULT for skill ranking. Prefer this over get_skills_vector /
get_skills_llm:

1. ALWAYS runs live discovery for the task (new skills are found, written
   and indexed before ranking).
2. The local index (vector + BM25) produces candidate hits.
3. Those candidates are INJECTED into DeepSeek, which validates each one
   (corrective phase: related or noise), keeps the related ones and adds
   its own semantic picks from the full catalog.
4. The final list is returned, tagged with engines used, whether a vector
   hit was corrected away, and the LLM reason.; parameters=limit, task}.name) | Return INTEGRATED skills: research + vector + DeepSeek corrective ranking.

BEST DEFAULT for skill ranking. Prefer this over get_skills_vect... |
| $(@{server=mcp-skills; name=get_skills_batch; description=Rank skills for MANY tasks in one call (batched corrective ranking).

Same pipeline as get_skills_combined (vector candidates injected into
DeepSeek for corrective validation + its own picks) but all tasks share a
single LLM call, making large-scale evaluation fast.; parameters=limit, tasks}.name) | Rank skills for MANY tasks in one call (batched corrective ranking).

Same pipeline as get_skills_combined (vector candidates injected into
... |
| $(@{server=mcp-skills; name=get_workflows_for_task; description=Find the most relevant skill-usage WORKFLOWS for a task.

Workflows are reusable plans that combine skills with LLM instructions
step by step. Use when the agent wants a guided multi-skill procedure
rather than a flat list of skills. use_llm=True adds DeepSeek semantic
ranking (with reasons); combined = vector + LLM fused.; parameters=limit, task, use_llm}.name) | Find the most relevant skill-usage WORKFLOWS for a task.

Workflows are reusable plans that combine skills with LLM instructions
step by ste... |
| $(@{server=mcp-skills; name=get_workflow; description=Return a full workflow by name (steps, skills used, instructions, references).; parameters=name}.name) | Return a full workflow by name (steps, skills used, instructions, references). |
| $(@{server=mcp-skills; name=list_workflows; description=List workflows, optionally filtered by category.; parameters=category}.name) | List workflows, optionally filtered by category. |
| $(@{server=mcp-skills; name=list_workflow_categories; description=Distinct workflow categories.; parameters=}.name) | Distinct workflow categories. |
| $(@{server=mcp-skills; name=create_workflow; description=Create a tailored workflow for a specific requirement.

If `steps` is given they are stored as-is (each: "step text").
Otherwise the LLM composes a workflow by grounding on the best matching
skills (via the combined ranker) - name, description, category, and
ordered steps that reference skills + LLM instructions. The workflow is
saved to the workflows catalog + vector DB when save=True, so future
tasks can retrieve it.; parameters=name, save, steps, task}.name) | Create a tailored workflow for a specific requirement.

If `steps` is given they are stored as-is (each: "step text").
Otherwise the LLM com... |
| $(@{server=mcp-skills; name=search_mcp_servers; description=Search the MCP server catalog (install guides, platforms, IDEs).

Includes well-known MCP servers with their install command, source URL,
supported platforms (windows/linux/mac) and IDEs (opencode, claude,
cursor, devin, cline...). Filter by platform, IDE, or category.
use_llm=True adds DeepSeek semantic ranking (combined = vector + LLM).; parameters=category, ide, limit, platform, query, use_llm}.name) | Search the MCP server catalog (install guides, platforms, IDEs).

Includes well-known MCP servers with their install command, source URL,
su... |
| $(@{server=mcp-skills; name=get_mcp_server; description=Full detail of an MCP server (install, platforms, IDEs, source, references).; parameters=name}.name) | Full detail of an MCP server (install, platforms, IDEs, source, references). |
| $(@{server=mcp-skills; name=add_mcp_server; description=Add an MCP server to the catalog.

It is indexed for search AND its source URL is added to the tracked
sources list (purpose 'mcp') so discovery can check it regularly.; parameters=category, description, ides, install, keywords, name, platforms, source_url}.name) | Add an MCP server to the catalog.

It is indexed for search AND its source URL is added to the tracked
sources list (purpose 'mcp') so disco... |
| $(@{server=mcp-skills; name=search_agents; description=Search the AI agent / IDE catalog (coding, video, audio, design...).

Includes CLI agents, IDEs, extensions, platforms, and visual tools
(e.g. ComfyUI for video/image/audio) with install commands, tutorials,
and related skills. Filter by usage area (coding, video, audio, image,
design, automation, agents, chat, local-llm, rag...), platform, or
category. use_llm=True adds DeepSeek semantic ranking (combined).; parameters=category, limit, platform, query, usage_area, use_llm}.name) | Search the AI agent / IDE catalog (coding, video, audio, design...).

Includes CLI agents, IDEs, extensions, platforms, and visual tools
(e.... |
| $(@{server=mcp-skills; name=get_agent; description=Full detail of an AI agent / IDE (install, tutorials, usage areas, references).; parameters=name}.name) | Full detail of an AI agent / IDE (install, tutorials, usage areas, references). |
| $(@{server=mcp-skills; name=add_agent; description=Add an AI agent / IDE to the catalog (with install + tutorial links).

The source URL is added to the tracked sources list (purpose 'agents').; parameters=category, description, install, keywords, name, platforms, source_url, tutorial, usage_areas}.name) | Add an AI agent / IDE to the catalog (with install + tutorial links).

The source URL is added to the tracked sources list (purpose 'agents'... |
| $(@{server=mcp-skills; name=get_skills_for_task; description=Return the most relevant skills for a task (backwards-compatible).

use_llm=False: local index only (see get_skills_vector, ~10ms).
use_llm=True: DeepSeek semantic ranking (see get_skills_llm, ~10-30s).

For the best of both worlds call get_skills_combined instead.; parameters=limit, task, use_llm}.name) | Return the most relevant skills for a task (backwards-compatible).

use_llm=False: local index only (see get_skills_vector, ~10ms).
use_llm=... |
| $(@{server=mcp-skills; name=list_all_skills; description=List every skill in the catalog, optionally filtered by category.; parameters=category}.name) | List every skill in the catalog, optionally filtered by category. |
| $(@{server=mcp-skills; name=get_skill; description=Return the full detail of a single skill by exact name.

Includes the complete SKILL.md content in 'file_content' so agents can
read the skill's full instructions through the MCP without touching the
filesystem.; parameters=name}.name) | Return the full detail of a single skill by exact name.

Includes the complete SKILL.md content in 'file_content' so agents can
read the ski... |
| $(@{server=mcp-skills; name=list_categories; description=List the distinct categories present in the skill catalog.; parameters=}.name) | List the distinct categories present in the skill catalog. |
| $(@{server=mcp-skills; name=add_skill; description=Add a new skill.

Creates skills/<name>/SKILL.md in this project AND registers it in
~/.claude/skills so opencode loads it after restart. The vector DB is
synced immediately.; parameters=category, description, name}.name) | Add a new skill.

Creates skills/<name>/SKILL.md in this project AND registers it in
~/.claude/skills so opencode loads it after restart. Th... |
| $(@{server=mcp-skills; name=_advice_review; description=Final reviewer: polish + optimize the task-advice report with the
configured reviewer model (REVIEWER_MODEL, default DeepSeek; point it at
Claude Opus 5 etc. via REVIEWER_BASE_URL/API_KEY/MODEL). The schema is
preserved; on any failure the original report is returned unchanged.; parameters=advice, requirement}.name) | Final reviewer: polish + optimize the task-advice report with the
configured reviewer model (REVIEWER_MODEL, default DeepSeek; point it at
C... |
| $(@{server=mcp-skills; name=sync_skills; description=Re-index everything: skills + workflows + MCP servers + agents.

New items are embedded+added, changed items re-embedded, removed items
deleted (content-hash detection), for every catalog kind.; parameters=}.name) | Re-index everything: skills + workflows + MCP servers + agents.

New items are embedded+added, changed items re-embedded, removed items
dele... |
| $(@{server=mcp-skills; name=get_related_docs; description=Find documentation / reference pages relevant to a task.

Combined ranking over the docs catalog (vector + DeepSeek fused). Each hit
has name, description, category, keywords and the docs url - use the url
when you need the actual documentation page.; parameters=limit, task}.name) | Find documentation / reference pages relevant to a task.

Combined ranking over the docs catalog (vector + DeepSeek fused). Each hit
has nam... |
| $(@{server=mcp-skills; name=get_system_mcp_status; description=Live status of the MCP servers INSTALLED on this machine, read from the
local agent-mcp-orchestrator dashboard (default http://127.0.0.1:8790,
override with ORCHESTRATOR_DASHBOARD_URL).

Returns ONLY installed servers (HTTP/SSE services, frontends, stdio
servers agents spawn) - the installable catalog is deliberately NOT
included, so an agent never mistakes a catalog entry for a running
service. Call this to know which MCP servers are actually available
locally before using them in the advice plan.; parameters=}.name) | Live status of the MCP servers INSTALLED on this machine, read from the
local agent-mcp-orchestrator dashboard (default http://127.0.0.1:879... |
| $(@{server=mcp-skills; name=get_advice_cache; description=Retrieve FULL previous task-advice reports from the permanent cache.

Every get_task_advice run is stored (prompt vectorized + full report on
disk). Use this to reuse a past plan instead of recomputing:

- get_advice_cache(task="<similar task>") -> the most similar cached
  reports with cosine similarity and the COMPLETE stored result
  (advice, categories, how_to_read, combined_ranking, report,
  past_advice) plus the LLM that produced them.
- get_advice_cache(advice_id="<id>") -> one exact report (ids are shown
  in every advice's past_advice block and in list_advice_cache).; parameters=advice_id, limit, task}.name) | Retrieve FULL previous task-advice reports from the permanent cache.

Every get_task_advice run is stored (prompt vectorized + full report o... |
| $(@{server=mcp-skills; name=list_advice_cache; description=List recent cached task-advice reports (newest first, with ids you can
pass to get_advice_cache(advice_id=...)).; parameters=limit}.name) | List recent cached task-advice reports (newest first, with ids you can
pass to get_advice_cache(advice_id=...)). |
| $(@{server=mcp-skills; name=get_task_advice; description=Turn ANY user prompt into full-catalog advice (one-call advisor).

USE THIS FIRST for any new task. DeepSeek preprocesses the raw prompt into
a clean requirement (intent, constraints, focus areas), then runs COMBINED
ranking (vector + LLM) across ALL catalogs (skills, workflows, MCP servers,
agents, docs, tools, features) and post-processes the hits into concrete
advice: which skills to load, which workflow to follow, which MCP
server/agent to use, in what order, and what to watch out for. The reply
includes the parsed prompt, per-catalog hits, a plan (summary, recommended
items, ordered steps, cautions) and - for every recommendation -
references/links the agent can read for details (how_to_read).

To refine ONE catalog after the advice, use its get_*_combined variant
(e.g. get_skills_combined, get_workflows_combined) - the best default per
catalog.

The reply also carries advice.report: a generalized methodology report
(20 sections, professional project-plan style). Every section lists the
exact MCP functions to call (get_*_combined per catalog + item readers
for the top hits) and the actual combined-ranked hits for that section -
so the agent can act section by section without re-ranking. One section
('System MCP Discovery') points at the locally-running
agent-mcp-orchestrator MCP (get_mcp_status / list_mcp_servers /
get_server_info / get_server_logs / get_open_incidents) to discover
every MCP server on the system.; parameters=limit, progress_cb, prompt}.name) | Turn ANY user prompt into full-catalog advice (one-call advisor).

USE THIS FIRST for any new task. DeepSeek preprocesses the raw prompt int... |
| $(@{server=mcp-skills; name=discover_all; description=Discover EVERYTHING from the web for a requirement.

Runs the live research pipeline with category-aware GitHub/web queries so
one call can grow ALL catalogs: skills (written + indexed), MCP servers,
AI agents, documentation links and open-source tools (link-only entries,
no download). Returns what was found per category so the agent can use the
new items immediately.; parameters=budget_s, max_new, requirement}.name) | Discover EVERYTHING from the web for a requirement.

Runs the live research pipeline with category-aware GitHub/web queries so
one call can ... |
| $(@{server=mcp-skills; name=sync_workflows; description=Re-index ONLY the workflows catalog into the vector DB (add/update/remove by content hash).; parameters=}.name) | Re-index ONLY the workflows catalog into the vector DB (add/update/remove by content hash). |
| $(@{server=mcp-skills; name=sync_mcpservers; description=Re-index ONLY the MCP servers catalog into the vector DB (add/update/remove by content hash).; parameters=}.name) | Re-index ONLY the MCP servers catalog into the vector DB (add/update/remove by content hash). |
| $(@{server=mcp-skills; name=sync_agents; description=Re-index ONLY the agents catalog into the vector DB (add/update/remove by content hash).; parameters=}.name) | Re-index ONLY the agents catalog into the vector DB (add/update/remove by content hash). |
| $(@{server=mcp-skills; name=sync_docs; description=Re-index ONLY the docs catalog into the vector DB (add/update/remove by content hash).; parameters=}.name) | Re-index ONLY the docs catalog into the vector DB (add/update/remove by content hash). |
| $(@{server=mcp-skills; name=sync_tools; description=Re-index ONLY the tools catalog into the vector DB (add/update/remove by content hash).; parameters=}.name) | Re-index ONLY the tools catalog into the vector DB (add/update/remove by content hash). |
| $(@{server=mcp-skills; name=status; description=Report the active embedder and index health.; parameters=}.name) | Report the active embedder and index health. |
| $(@{server=mcp-skills; name=get_help; description=Get usage guidance for this MCP server.

Use when the agent is unsure how to use the mcp-skills server or wants to
know its tools, the recommended workflow, or when to use each ranking
engine.; parameters=topic}.name) | Get usage guidance for this MCP server.

Use when the agent is unsure how to use the mcp-skills server or wants to
know its tools, the recom... |
| $(@{server=mcp-skills; name=similar_skills; description=Find skills related to a given skill using vector similarity.

Use when an agent found a skill and wants to discover its neighbors
(e.g. to combine related skills, or to check for duplicates).; parameters=limit, name}.name) | Find skills related to a given skill using vector similarity.

Use when an agent found a skill and wants to discover its neighbors
(e.g. to ... |
| $(@{server=mcp-skills; name=skill_health; description=Report catalog health: broken entries, duplicates, category coverage.

Use when checking data quality or before/after running discovery.; parameters=}.name) | Report catalog health: broken entries, duplicates, category coverage.

Use when checking data quality or before/after running discovery. |

## mcp-skills-dashboard

| Function | Description |
|---|---|
| $(@{server=mcp-skills-dashboard; name=browse_skills; description=Browse/search 678 skills with rankings (UI at :8787); parameters=query}.name) | Browse/search 678 skills with rankings (UI at :8787) |
| $(@{server=mcp-skills-dashboard; name=activity_feed; description=Live skill usage activity feed (UI at :8787); parameters=}.name) | Live skill usage activity feed (UI at :8787) |

## memory

| Function | Description |
|---|---|
| $(@{server=memory; name=create_entities; description=Create entities in the knowledge graph; parameters=entities}.name) | Create entities in the knowledge graph |
| $(@{server=memory; name=create_relations; description=Create relations between entities; parameters=relations}.name) | Create relations between entities |
| $(@{server=memory; name=add_observations; description=Add observations to entities; parameters=observations}.name) | Add observations to entities |
| $(@{server=memory; name=delete_entities; description=Delete entities and their relations; parameters=entityNames}.name) | Delete entities and their relations |
| $(@{server=memory; name=delete_relations; description=Delete relations; parameters=relations}.name) | Delete relations |
| $(@{server=memory; name=delete_observations; description=Delete observations; parameters=deletions}.name) | Delete observations |
| $(@{server=memory; name=read_graph; description=Read the entire knowledge graph; parameters=}.name) | Read the entire knowledge graph |
| $(@{server=memory; name=search_nodes; description=Search graph nodes by query; parameters=query}.name) | Search graph nodes by query |
| $(@{server=memory; name=open_nodes; description=Open specific nodes by name; parameters=names}.name) | Open specific nodes by name |

## meta-ads-mcp-server

| Function | Description |
|---|---|
| $(@{server=meta-ads-mcp-server; name=meta_ads_list_ad_accounts; description=List all ad accounts accessible with the token; parameters=}.name) | List all ad accounts accessible with the token |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_account_details; description=Get detailed information for a specific ad account; parameters=account_id}.name) | Get detailed information for a specific ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_campaign_by_id; description=Fetch a specific campaign by ID; parameters=campaign_id}.name) | Fetch a specific campaign by ID |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_campaigns_by_adaccount; description=List campaigns within an ad account; parameters=account_id, filters}.name) | List campaigns within an ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adset_by_id; description=Fetch a single ad set by ID; parameters=adset_id}.name) | Fetch a single ad set by ID |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adsets_by_ids; description=Batch fetch multiple ad sets; parameters=adset_ids}.name) | Batch fetch multiple ad sets |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adsets_by_adaccount; description=List ad sets in an ad account; parameters=account_id, filters}.name) | List ad sets in an ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adsets_by_campaign; description=List ad sets within a campaign; parameters=campaign_id}.name) | List ad sets within a campaign |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_by_id; description=Fetch a single ad by ID; parameters=ad_id}.name) | Fetch a single ad by ID |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ads_by_adaccount; description=List ads in an ad account; parameters=account_id, filters}.name) | List ads in an ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ads_by_campaign; description=List ads within a campaign; parameters=campaign_id}.name) | List ads within a campaign |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ads_by_adset; description=List ads within an ad set; parameters=adset_id}.name) | List ads within an ad set |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_creative_by_id; description=Fetch one creative by ID; parameters=creative_id}.name) | Fetch one creative by ID |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_creatives_by_ad_id; description=List creatives attached to an ad; parameters=ad_id}.name) | List creatives attached to an ad |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adcreatives_by_adaccount; description=List creatives in an ad account; parameters=account_id}.name) | List creatives in an ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_compute_image_crops; description=Compute centered crop boxes for the 6 Meta aspect ratios; parameters=image_url, image_hash}.name) | Compute centered crop boxes for the 6 Meta aspect ratios |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_images; description=List image assets in an ad account; parameters=account_id}.name) | List image assets in an ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_image_by_hash; description=Single-image lookup by hash (URL + dimensions); parameters=account_id, image_hash}.name) | Single-image lookup by hash (URL + dimensions) |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_previews; description=Rendered previews of an ad across placements; parameters=ad_id, formats}.name) | Rendered previews of an ad across placements |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_video; description=Video details by ad_id or video_id; parameters=ad_id, video_id}.name) | Video details by ad_id or video_id |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adaccount_insights; description=Performance metrics at the account level; parameters=account_id, date_range, metrics}.name) | Performance metrics at the account level |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_campaign_insights; description=Performance metrics for a campaign; parameters=campaign_id, date_range, metrics}.name) | Performance metrics for a campaign |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_adset_insights; description=Performance metrics for an ad set; parameters=adset_id, date_range, metrics}.name) | Performance metrics for an ad set |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_ad_insights; description=Performance metrics for an ad; parameters=ad_id, date_range, metrics}.name) | Performance metrics for an ad |
| $(@{server=meta-ads-mcp-server; name=meta_ads_search_interests; description=Search Meta's interest catalog by keyword; parameters=query}.name) | Search Meta's interest catalog by keyword |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_interest_suggestions; description=Related interests from a seed list; parameters=interest_list}.name) | Related interests from a seed list |
| $(@{server=meta-ads-mcp-server; name=meta_ads_search_behaviors; description=List available behavior targeting options; parameters=}.name) | List available behavior targeting options |
| $(@{server=meta-ads-mcp-server; name=meta_ads_search_demographics; description=List demographic targeting options; parameters=type}.name) | List demographic targeting options |
| $(@{server=meta-ads-mcp-server; name=meta_ads_search_geo_locations; description=Search countries / regions / cities / zips / geo markets; parameters=query, type}.name) | Search countries / regions / cities / zips / geo markets |
| $(@{server=meta-ads-mcp-server; name=meta_ads_estimate_audience_size; description=Estimate reach for a targeting spec; parameters=targeting_spec}.name) | Estimate reach for a targeting spec |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_account_pages; description=List Facebook Pages reachable from the token; parameters=}.name) | List Facebook Pages reachable from the token |
| $(@{server=meta-ads-mcp-server; name=meta_ads_search_pages_by_name; description=Search the token's Facebook Pages by name; parameters=query}.name) | Search the token's Facebook Pages by name |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_activities_by_adaccount; description=Change history log for an ad account; parameters=account_id, filters}.name) | Change history log for an ad account |
| $(@{server=meta-ads-mcp-server; name=meta_ads_get_activities_by_adset; description=Change history log for an ad set; parameters=adset_id, filters}.name) | Change history log for an ad set |
| $(@{server=meta-ads-mcp-server; name=meta_ads_fetch_pagination_url; description=Fetch a subsequent page of a paginated result; parameters=url}.name) | Fetch a subsequent page of a paginated result |

## omniroute

| Function | Description |
|---|---|
| $(@{server=omniroute; name=status; description=Gateway status: uptime, providers, key pools (GET /v1/status); parameters=}.name) | Gateway status: uptime, providers, key pools (GET /v1/status) |
| $(@{server=omniroute; name=models; description=List 1200+ models across 352 providers (GET /v1/models); parameters=}.name) | List 1200+ models across 352 providers (GET /v1/models) |
| $(@{server=omniroute; name=chat_completions; description=OpenAI-compatible chat completions with fallback (POST /v1/chat/completions); parameters=model, messages}.name) | OpenAI-compatible chat completions with fallback (POST /v1/chat/completions) |
| $(@{server=omniroute; name=providers; description=Provider list with health and key status (GET /v1/providers); parameters=}.name) | Provider list with health and key status (GET /v1/providers) |
| $(@{server=omniroute; name=usage; description=Token/cost usage reports (GET /v1/usage); parameters=period}.name) | Token/cost usage reports (GET /v1/usage) |

## omniroute-dashboard

| Function | Description |
|---|---|
| $(@{server=omniroute-dashboard; name=manage_providers; description=Providers, API keys, combos management (UI at :20128/dashboard); parameters=}.name) | Providers, API keys, combos management (UI at :20128/dashboard) |
| $(@{server=omniroute-dashboard; name=usage_reports; description=Token/cost usage dashboards (UI at :20128/dashboard); parameters=}.name) | Token/cost usage dashboards (UI at :20128/dashboard) |

## playwright

| Function | Description |
|---|---|
| $(@{server=playwright; name=browser_navigate; description=Navigate to a URL; parameters=url}.name) | Navigate to a URL |
| $(@{server=playwright; name=browser_click; description=Click an element; parameters=element, ref}.name) | Click an element |
| $(@{server=playwright; name=browser_type; description=Type text into an element; parameters=element, ref, text}.name) | Type text into an element |
| $(@{server=playwright; name=browser_fill_form; description=Fill multiple form fields; parameters=fields}.name) | Fill multiple form fields |
| $(@{server=playwright; name=browser_snapshot; description=Capture accessibility snapshot of the page; parameters=}.name) | Capture accessibility snapshot of the page |
| $(@{server=playwright; name=browser_take_screenshot; description=Take a screenshot of the page; parameters=filename, element}.name) | Take a screenshot of the page |
| $(@{server=playwright; name=browser_press_key; description=Press a keyboard key; parameters=key}.name) | Press a keyboard key |
| $(@{server=playwright; name=browser_hover; description=Hover over an element; parameters=element, ref}.name) | Hover over an element |
| $(@{server=playwright; name=browser_wait_for; description=Wait for text to appear/disappear; parameters=text, textGone, time}.name) | Wait for text to appear/disappear |
| $(@{server=playwright; name=browser_tabs; description=List, create, close, or select tabs; parameters=action, index}.name) | List, create, close, or select tabs |
| $(@{server=playwright; name=browser_close; description=Close the browser page; parameters=}.name) | Close the browser page |
| $(@{server=playwright; name=browser_file_upload; description=Upload files to an input; parameters=paths}.name) | Upload files to an input |
| $(@{server=playwright; name=browser_console_messages; description=Read console messages; parameters=level}.name) | Read console messages |
| $(@{server=playwright; name=browser_network_requests; description=List network requests; parameters=}.name) | List network requests |
| $(@{server=playwright; name=browser_evaluate; description=Evaluate JavaScript in the page; parameters=function}.name) | Evaluate JavaScript in the page |

## postgres-mcp

| Function | Description |
|---|---|
| $(@{server=postgres-mcp; name=postgres_mcp_query; description=Run read-only SQL against a PostgreSQL database; parameters=sql, profile}.name) | Run read-only SQL against a PostgreSQL database |
| $(@{server=postgres-mcp; name=postgres_mcp_modify; description=Run DDL/DML SQL (CREATE/INSERT/UPDATE/DELETE); parameters=sql, profile}.name) | Run DDL/DML SQL (CREATE/INSERT/UPDATE/DELETE) |
| $(@{server=postgres-mcp; name=postgres_mcp_describe_csv; description=Describe a local CSV file (columns, types); parameters=path}.name) | Describe a local CSV file (columns, types) |
| $(@{server=postgres-mcp; name=postgres_mcp_bulk_load_csv; description=Bulk-load a CSV into a table via COPY; parameters=path, table, profile}.name) | Bulk-load a CSV into a table via COPY |
| $(@{server=postgres-mcp; name=postgres_mcp_schema; description=Fetch CREATE scripts for tables, indexes, functions, sequences; parameters=profile, object}.name) | Fetch CREATE scripts for tables, indexes, functions, sequences |

## tdai-memory

| Function | Description |
|---|---|
| $(@{server=tdai-memory; name=tdai_capture; description=Persist a conversation turn into memory (L0); parameters=user_content, assistant_content, session_key}.name) | Persist a conversation turn into memory (L0) |
| $(@{server=tdai-memory; name=tdai_memory_search; description=Search structured L1 atomic memories; parameters=query}.name) | Search structured L1 atomic memories |
| $(@{server=tdai-memory; name=tdai_recall; description=Recall conversational memories and persona context; parameters=query, session_key}.name) | Recall conversational memories and persona context |
| $(@{server=tdai-memory; name=tdai_conversation_search; description=Search raw L0 conversation history; parameters=query}.name) | Search raw L0 conversation history |
| $(@{server=tdai-memory; name=tdai_session_end; description=End a memory session and flush pending work; parameters=session_key}.name) | End a memory session and flush pending work |
| $(@{server=tdai-memory; name=unified_recall; description=Combined recall from memory + codebase knowledge graph; parameters=query, session_key}.name) | Combined recall from memory + codebase knowledge graph |

## time

| Function | Description |
|---|---|
| $(@{server=time; name=get_current_time; description=Get current time in a timezone; parameters=timezone}.name) | Get current time in a timezone |
| $(@{server=time; name=convert_time; description=Convert time between timezones; parameters=source_timezone, time, target_timezone}.name) | Convert time between timezones |

## winremote

| Function | Description |
|---|---|
| $(@{server=winremote; name=run_command; description=Run a shell command (Windows remote control); parameters=command}.name) | Run a shell command (Windows remote control) |
| $(@{server=winremote; name=process_list; description=List running processes; parameters=}.name) | List running processes |
| $(@{server=winremote; name=process_kill; description=Kill a process; parameters=pid/name}.name) | Kill a process |
| $(@{server=winremote; name=registry_query; description=Query a registry key/value; parameters=key, value}.name) | Query a registry key/value |
| $(@{server=winremote; name=registry_set; description=Set a registry value; parameters=key, value, data}.name) | Set a registry value |
| $(@{server=winremote; name=service_list; description=List Windows services; parameters=}.name) | List Windows services |
| $(@{server=winremote; name=service_start; description=Start a Windows service; parameters=name}.name) | Start a Windows service |
| $(@{server=winremote; name=service_stop; description=Stop a Windows service; parameters=name}.name) | Stop a Windows service |
| $(@{server=winremote; name=clipboard_get; description=Read clipboard contents; parameters=}.name) | Read clipboard contents |
| $(@{server=winremote; name=clipboard_set; description=Write clipboard contents; parameters=text}.name) | Write clipboard contents |
| $(@{server=winremote; name=screenshot; description=Capture a screenshot; parameters=save_path}.name) | Capture a screenshot |

## youtube-mcp

| Function | Description |
|---|---|
| $(@{server=youtube-mcp; name=get_transcript; description=Download captions/transcript of a YouTube video; parameters=video_url, lang}.name) | Download captions/transcript of a YouTube video |
| $(@{server=youtube-mcp; name=get_video_info; description=Fetch video metadata (title, author, duration); parameters=video_url}.name) | Fetch video metadata (title, author, duration) |
| $(@{server=youtube-mcp; name=get_comments; description=Fetch comments of a YouTube video; parameters=video_url, max_results}.name) | Fetch comments of a YouTube video |


