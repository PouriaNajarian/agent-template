# MCP Functions / Tools Inventory

Generated: 2026-09-20 20:58  
Source: `http://localhost:8790/api/functions`  
Total tools: **216** across **23** servers. rebuilding=

## Index

- 9router: 5 tools
- 9router-dashboard: 2 tools
- agent-mcp-orchestrator: 9 tools
- Binance Cryptocurrency MCP: 12 tools
- context7: 2 tools
- devin/cloudflare-docs: 2 tools
- devin/deepwiki: 2 tools
- devin/github-mcp-server: 4 tools
- filesystem: 9 tools
- git: 7 tools
- google-merchant-mcp: 1 tools
- mcp-skills: 66 tools
- mcp-skills-dashboard: 2 tools
- memory: 9 tools
- meta-ads-mcp-server: 35 tools
- omniroute: 5 tools
- omniroute-dashboard: 2 tools
- playwright: 15 tools
- postgres-mcp: 5 tools
- tdai-memory: 6 tools
- time: 2 tools
- winremote: 11 tools
- youtube-mcp: 3 tools

## 9router  (5 tools)

| Tool | Description | Parameters |
|---|---|---|
| chat_completions | OpenAI-compatible completions with 3-tier fallback (POST /v1/chat/completions) | model, messages |
| models | List available models across tiers (GET /v1/models) |  |
| providers | Provider list with quota/quota-tracker status (GET /v1/providers) |  |
| status | Proxy status: uptime, tiers, providers (GET /v1/status) |  |
| usage | Token saver usage reports (GET /v1/usage) | period |

## 9router-dashboard  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| manage_providers | Providers, combos, quota tracker (UI at :20228/dashboard) |  |
| token_saver | Token saver stats and settings (UI at :20228/dashboard) |  |

## agent-mcp-orchestrator  (9 tools)

| Tool | Description | Parameters |
|---|---|---|
| get_mcp_status | Get the live health status of ALL MCP servers on this system (local HTTP/SSE servers, frontend dashboards, stdio servers, remote servers) plus a summary. START HERE for any question about what is running, what is down, or the overall health. |  |
| get_open_incidents | Get open incidents (server problems) recorded by the health dashboard, with priority and lifecycle status. Use to report outstanding problems. |  |
| get_server_docs | Fetch the documentation/README for a catalog server and extract install commands, remote MCP URLs, and API-key requirements. CALL THIS BEFORE install_mcp_server whenever the catalog entry has no install command — never guess commands. | name |
| get_server_functions | List the MCP functions/tools a server exposes (probes it live if needed). Use after installing a server to confirm it works and show the user what it can do. Also useful to decide whether a catalog server fits the user's needs. | name |
| get_server_info | Get full details for one MCP server: status, port, transport, endpoints, install command, docs link, AND a ready-to-paste 'How to use it' MCP client config snippet. Use after installing, or when the user asks how to connect/use a server. | name |
| get_server_logs | Get recent health logs for a specific MCP server (or all servers) — useful to debug why a server is down or flapping. | limit, server |
| install_mcp_server | Install/register an MCP server on this system and push it to ALL agent CLI configs automatically. Two ways: (1) LOCAL: install_command must be an exact runnable command whose runner exists (npx/uvx/node/pip/docker/...); (2) HOSTED/REMOTE: pass url (e.g. https://api.example.com/mcp) — no local process needed. The command is VALIDATED first; if rejected, read the error, use get_server_docs/web_search to find the correct command, and retry. Ask the user before installing anything they did not explicitly request. | description, install_command, name, port, transport, url |
| list_mcp_servers | List all known MCP servers — installed ones AND the ~15k-server installable catalog (awesome-mcp-servers + mcpservers.org). Use 'filter' to search (e.g. 'pdf', 'github', 'browser'). Entries show status (up/down/not_installed), transport, and the install command when known. To install one: note its name, then call get_server_docs for the exact command, then install_mcp_server. | filter |
| uninstall_mcp_server | Uninstall a CUSTOM MCP server (one installed via install_mcp_server) — removes it from this system AND from every agent CLI config. Built-in servers cannot be uninstalled. Always confirm with the user before calling. | name |

## Binance Cryptocurrency MCP  (12 tools)

| Tool | Description | Parameters |
|---|---|---|
| get_24hr_ticker |  | symbol, symbols |
| get_aggregate_trades |  | endTime, fromId, limit, startTime, symbol |
| get_avg_price |  | symbol |
| get_book_ticker |  | symbol, symbols |
| get_historical_trades |  | fromId, limit, symbol |
| get_klines |  | endTime, interval, limit, startTime, symbol, timeZone |
| get_order_book |  | limit, symbol |
| get_price |  | symbol, symbols |
| get_recent_trades |  | limit, symbol |
| get_rolling_window_ticker |  | symbol, symbols, type, windowSize |
| get_trading_day_ticker |  | symbol, symbols, timeZone, type |
| get_ui_klines |  | endTime, interval, limit, startTime, symbol, timeZone |

## context7  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| get-library-docs | Fetch up-to-date documentation for a library | context7Id, topic, toc |
| resolve-library-id | Resolve a library name to its context7 id | libraryName |

## devin/cloudflare-docs  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| get_docs_page | Fetch a Cloudflare docs page (auth required) | url |
| search_cloudflare_docs | Search Cloudflare documentation (auth required) | query |

## devin/deepwiki  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| ask_question | Ask a question about a repository (auth required) | repo, question |
| read_wiki_structure | Repository wiki table of contents (auth required) | repo |

## devin/github-mcp-server  (4 tools)

| Tool | Description | Parameters |
|---|---|---|
| get_file_contents | Read a file from a repository (auth required) | owner, repo, path |
| get_me | Authenticated GitHub user profile (auth required) |  |
| list_issues | List issues in a repository (auth required) | owner, repo |
| search_repositories | Search GitHub repositories (auth required) | query |

## filesystem  (9 tools)

| Tool | Description | Parameters |
|---|---|---|
| create_directory | Create a new directory | path |
| directory_tree | Get a recursive tree of a directory | path |
| edit_file | Make line-based edits to a file | path, edits, dryRun |
| get_file_info | Get file metadata | path |
| list_directory | List files and subdirectories | path |
| move_file | Move or rename a file | source, destination |
| read_file | Read a file's contents | path |
| search_files | Recursively search for files matching a pattern | path, pattern, excludePatterns |
| write_file | Create or overwrite a file | path, content |

## git  (7 tools)

| Tool | Description | Parameters |
|---|---|---|
| git_add | Stage files for commit | repo_path, files |
| git_branch | List/create branches | repo_path |
| git_checkout | Switch branches | repo_path, branch_name |
| git_commit | Commit staged changes | repo_path, message |
| git_diff_unstaged | Show unstaged changes | repo_path |
| git_log | Show commit history | repo_path, max_count |
| git_status | Show the working tree status | repo_path |

## google-merchant-mcp  (1 tools)

| Tool | Description | Parameters |
|---|---|---|
| placeholder | Placeholder stub - project not implemented yet (server.js stub for PELLE) |  |

## mcp-skills  (66 tools)

| Tool | Description | Parameters |
|---|---|---|
| _advice_review | Final reviewer: polish + optimize the task-advice report with the configured reviewer model (REVIEWER_MODEL, default DeepSeek; point it at Claude Opus 5 etc. via REVIEWER_BASE_URL/API_KEY/MODEL). The schema is preserved; on any failure the original report is returned unchanged. | advice, requirement |
| add_agent | Add an AI agent / IDE to the catalog (with install + tutorial links).  The source URL is added to the tracked sources list (purpose 'agents'). | category, description, install, keywords, name, platforms, source_url, tutorial, usage_areas |
| add_mcp_server | Add an MCP server to the catalog.  It is indexed for search AND its source URL is added to the tracked sources list (purpose 'mcp') so discovery can check it regularly. | category, description, ides, install, keywords, name, platforms, source_url |
| add_skill | Add a new skill.  Creates skills/<name>/SKILL.md in this project AND registers it in ~/.claude/skills so opencode loads it after restart. The vector DB is synced immediately. | category, description, name |
| create_workflow | Create a tailored workflow for a specific requirement.  If `steps` is given they are stored as-is (each: "step text"). Otherwise the LLM composes a workflow by grounding on the best matching skills (via the combined ranker) - name, description, category, and ordered steps that reference skills + LLM instructions. The workflow is saved to the workflows catalog + vector DB when save=True, so future tasks can retrieve it. | name, save, steps, task |
| discover_all | Discover EVERYTHING from the web for a requirement.  Runs the live research pipeline with category-aware GitHub/web queries so one call can grow ALL catalogs: skills (written + indexed), MCP servers, AI agents, documentation links and open-source tools (link-only entries, no download). Returns what was found per category so the agent can use the new items immediately. | budget_s, max_new, requirement |
| get_advice_cache | Retrieve FULL previous task-advice reports from the permanent cache.  Every get_task_advice run is stored (prompt vectorized + full report on disk). Use this to reuse a past plan instead of recomputing:  - get_advice_cache(task="<similar task>") -> the most similar cached   reports with cosine similarity and the COMPLETE stored result   (advice, categories, how_to_read, combined_ranking, report,   past_advice) plus the LLM that produced them. - get_advice_cache(advice_id="<id>") -> one exact report (ids are shown   in every advice's past_advice block and in list_advice_cache). | advice_id, limit, task |
| get_agent | Full detail of an AI agent / IDE (install, tutorials, usage areas, references). | name |
| get_agents_batch | Rank the agents catalog for MANY tasks (up to 15) in one batched DeepSeek call. | limit, tasks |
| get_agents_combined | BEST DEFAULT ranking over the agents catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. | limit, task |
| get_agents_for_task | Rank the agents catalog for a task (wrapper: use_llm=False -> vector, True -> llm). | limit, task, use_llm |
| get_agents_llm | DeepSeek semantic ranking over the agents catalog (~10-30s, with reasons). Prefer get_agents_combined unless you need pure-LLM picks. | limit, task |
| get_agents_vector | Vector-only ranking over the agents catalog (fast, ~10ms). Prefer get_agents_combined for best quality. | limit, task |
| get_docs_batch | Rank the docs catalog for MANY tasks (up to 15) in one batched DeepSeek call. | limit, tasks |
| get_docs_combined | BEST DEFAULT ranking over the docs catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. | limit, task |
| get_docs_for_task | Rank the docs catalog for a task (wrapper: use_llm=False -> vector, True -> llm). | limit, task, use_llm |
| get_docs_llm | DeepSeek semantic ranking over the docs catalog (~10-30s, with reasons). Prefer get_docs_combined unless you need pure-LLM picks. | limit, task |
| get_docs_vector | Vector-only ranking over the docs catalog (fast, ~10ms). Prefer get_docs_combined for best quality. | limit, task |
| get_features_batch | Rank the features catalog for MANY tasks (up to 15) in one batched DeepSeek call. | limit, tasks |
| get_features_combined | BEST DEFAULT ranking over the features catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. | limit, task |
| get_features_for_task | Rank the features catalog for a task (wrapper: use_llm=False -> vector, True -> llm). | limit, task, use_llm |
| get_features_llm | DeepSeek semantic ranking over the features catalog (~10-30s, with reasons). Prefer get_features_combined unless you need pure-LLM picks. | limit, task |
| get_features_vector | Vector-only ranking over the features catalog (fast, ~10ms). Prefer get_features_combined for best quality. | limit, task |
| get_help | Get usage guidance for this MCP server.  Use when the agent is unsure how to use the mcp-skills server or wants to know its tools, the recommended workflow, or when to use each ranking engine. | topic |
| get_mcp_server | Full detail of an MCP server (install, platforms, IDEs, source, references). | name |
| get_mcpservers_batch | Rank the mcpservers catalog for MANY tasks (up to 15) in one batched DeepSeek call. | limit, tasks |
| get_mcpservers_combined | BEST DEFAULT ranking over the mcpservers catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. | limit, task |
| get_mcpservers_for_task | Rank the mcpservers catalog for a task (wrapper: use_llm=False -> vector, True -> llm). | limit, task, use_llm |
| get_mcpservers_llm | DeepSeek semantic ranking over the mcpservers catalog (~10-30s, with reasons). Prefer get_mcpservers_combined unless you need pure-LLM picks. | limit, task |
| get_mcpservers_vector | Vector-only ranking over the mcpservers catalog (fast, ~10ms). Prefer get_mcpservers_combined for best quality. | limit, task |
| get_related_docs | Find documentation / reference pages relevant to a task.  Combined ranking over the docs catalog (vector + DeepSeek fused). Each hit has name, description, category, keywords and the docs url - use the url when you need the actual documentation page. | limit, task |
| get_skill | Return the full detail of a single skill by exact name.  Includes the complete SKILL.md content in 'file_content' so agents can read the skill's full instructions through the MCP without touching the filesystem. | name |
| get_skills_batch | Rank skills for MANY tasks in one call (batched corrective ranking).  Same pipeline as get_skills_combined (vector candidates injected into DeepSeek for corrective validation + its own picks) but all tasks share a single LLM call, making large-scale evaluation fast. | limit, tasks |
| get_skills_combined | Return INTEGRATED skills: research + vector + DeepSeek corrective ranking.  BEST DEFAULT for skill ranking. Prefer this over get_skills_vector / get_skills_llm:  1. ALWAYS runs live discovery for the task (new skills are found, written    and indexed before ranking). 2. The local index (vector + BM25) produces candidate hits. 3. Those candidates are INJECTED into DeepSeek, which validates each one    (corrective phase: related or noise), keeps the related ones and adds    its own semantic picks from the full catalog. 4. The final list is returned, tagged with engines used, whether a vector    hit was corrected away, and the LLM reason. | limit, task |
| get_skills_for_task | Return the most relevant skills for a task (backwards-compatible).  use_llm=False: local index only (see get_skills_vector, ~10ms). use_llm=True: DeepSeek semantic ranking (see get_skills_llm, ~10-30s).  For the best of both worlds call get_skills_combined instead. | limit, task, use_llm |
| get_skills_llm | Rank skills for a task using ONLY the DeepSeek API semantic ranker.  Slower (~10-30s): the full catalog is sent to deepseek-v4-flash which returns the most semantically relevant skills with reasons. Falls back to the opencode skill-ranker subagent if no API key, then to the local index on failure. Prefer get_skills_combined unless you need pure-LLM picks. | limit, task |
| get_skills_vector | Rank skills for a task using ONLY the local index (vector DB + BM25).  Fast (~10ms): chromadb cosine top-50 pool re-ranked with word-level BM25. Good lexical recall; misses purely semantic matches that the LLM finds. Prefer get_skills_combined for best quality. | limit, task |
| get_system_mcp_status | Live status of the MCP servers INSTALLED on this machine, read from the local agent-mcp-orchestrator dashboard (default http://127.0.0.1:8790, override with ORCHESTRATOR_DASHBOARD_URL).  Returns ONLY installed servers (HTTP/SSE services, frontends, stdio servers agents spawn) - the installable catalog is deliberately NOT included, so an agent never mistakes a catalog entry for a running service. Call this to know which MCP servers are actually available locally before using them in the advice plan. |  |
| get_task_advice | Turn ANY user prompt into full-catalog advice (one-call advisor).  USE THIS FIRST for any new task. DeepSeek preprocesses the raw prompt into a clean requirement (intent, constraints, focus areas), then runs COMBINED ranking (vector + LLM) across ALL catalogs (skills, workflows, MCP servers, agents, docs, tools, features) and post-processes the hits into concrete advice: which skills to load, which workflow to follow, which MCP server/agent to use, in what order, and what to watch out for. The reply includes the parsed prompt, per-catalog hits, a plan (summary, recommended items, ordered steps, cautions) and - for every recommendation - references/links the agent can read for details (how_to_read).  To refine ONE catalog after the advice, use its get_*_combined variant (e.g. get_skills_combined, get_workflows_combined) - the best default per catalog.  The reply also carries advice.report: a generalized methodology report (20 sections, professional project-plan style). Every section lists the exact MCP functions to call (get_*_combined per catalog + item readers for the top hits) and the actual combined-ranked hits for that section - so the agent can act section by section without re-ranking. One section ('System MCP Discovery') points at the locally-running agent-mcp-orchestrator MCP (get_mcp_status / list_mcp_servers / get_server_info / get_server_logs / get_open_incidents) to discover every MCP server on the system. | limit, progress_cb, prompt |
| get_tools_batch | Rank the tools catalog for MANY tasks (up to 15) in one batched DeepSeek call. | limit, tasks |
| get_tools_combined | BEST DEFAULT ranking over the tools catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. | limit, task |
| get_tools_for_task | Rank the tools catalog for a task (wrapper: use_llm=False -> vector, True -> llm). | limit, task, use_llm |
| get_tools_llm | DeepSeek semantic ranking over the tools catalog (~10-30s, with reasons). Prefer get_tools_combined unless you need pure-LLM picks. | limit, task |
| get_tools_vector | Vector-only ranking over the tools catalog (fast, ~10ms). Prefer get_tools_combined for best quality. | limit, task |
| get_workflow | Return a full workflow by name (steps, skills used, instructions, references). | name |
| get_workflows_batch | Rank the workflows catalog for MANY tasks (up to 15) in one batched DeepSeek call. | limit, tasks |
| get_workflows_combined | BEST DEFAULT ranking over the workflows catalog: vector candidates + DeepSeek picks fused (reciprocal-rank, ~10-30s). Use this variant first. | limit, task |
| get_workflows_for_task | Find the most relevant skill-usage WORKFLOWS for a task.  Workflows are reusable plans that combine skills with LLM instructions step by step. Use when the agent wants a guided multi-skill procedure rather than a flat list of skills. use_llm=True adds DeepSeek semantic ranking (with reasons); combined = vector + LLM fused. | limit, task, use_llm |
| get_workflows_llm | DeepSeek semantic ranking over the workflows catalog (~10-30s, with reasons). Prefer get_workflows_combined unless you need pure-LLM picks. | limit, task |
| get_workflows_vector | Vector-only ranking over the workflows catalog (fast, ~10ms). Prefer get_workflows_combined for best quality. | limit, task |
| list_advice_cache | List recent cached task-advice reports (newest first, with ids you can pass to get_advice_cache(advice_id=...)). | limit |
| list_all_skills | List every skill in the catalog, optionally filtered by category. | category |
| list_categories | List the distinct categories present in the skill catalog. |  |
| list_workflow_categories | Distinct workflow categories. |  |
| list_workflows | List workflows, optionally filtered by category. | category |
| search_agents | Search the AI agent / IDE catalog (coding, video, audio, design...).  Includes CLI agents, IDEs, extensions, platforms, and visual tools (e.g. ComfyUI for video/image/audio) with install commands, tutorials, and related skills. Filter by usage area (coding, video, audio, image, design, automation, agents, chat, local-llm, rag...), platform, or category. use_llm=True adds DeepSeek semantic ranking (combined). | category, limit, platform, query, usage_area, use_llm |
| search_mcp_servers | Search the MCP server catalog (install guides, platforms, IDEs).  Includes well-known MCP servers with their install command, source URL, supported platforms (windows/linux/mac) and IDEs (opencode, claude, cursor, devin, cline...). Filter by platform, IDE, or category. use_llm=True adds DeepSeek semantic ranking (combined = vector + LLM). | category, ide, limit, platform, query, use_llm |
| similar_skills | Find skills related to a given skill using vector similarity.  Use when an agent found a skill and wants to discover its neighbors (e.g. to combine related skills, or to check for duplicates). | limit, name |
| skill_health | Report catalog health: broken entries, duplicates, category coverage.  Use when checking data quality or before/after running discovery. |  |
| status | Report the active embedder and index health. |  |
| sync_agents | Re-index ONLY the agents catalog into the vector DB (add/update/remove by content hash). |  |
| sync_docs | Re-index ONLY the docs catalog into the vector DB (add/update/remove by content hash). |  |
| sync_mcpservers | Re-index ONLY the MCP servers catalog into the vector DB (add/update/remove by content hash). |  |
| sync_skills | Re-index everything: skills + workflows + MCP servers + agents.  New items are embedded+added, changed items re-embedded, removed items deleted (content-hash detection), for every catalog kind. |  |
| sync_tools | Re-index ONLY the tools catalog into the vector DB (add/update/remove by content hash). |  |
| sync_workflows | Re-index ONLY the workflows catalog into the vector DB (add/update/remove by content hash). |  |

## mcp-skills-dashboard  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| activity_feed | Live skill usage activity feed (UI at :8787) |  |
| browse_skills | Browse/search 678 skills with rankings (UI at :8787) | query |

## memory  (9 tools)

| Tool | Description | Parameters |
|---|---|---|
| add_observations | Add observations to entities | observations |
| create_entities | Create entities in the knowledge graph | entities |
| create_relations | Create relations between entities | relations |
| delete_entities | Delete entities and their relations | entityNames |
| delete_observations | Delete observations | deletions |
| delete_relations | Delete relations | relations |
| open_nodes | Open specific nodes by name | names |
| read_graph | Read the entire knowledge graph |  |
| search_nodes | Search graph nodes by query | query |

## meta-ads-mcp-server  (35 tools)

| Tool | Description | Parameters |
|---|---|---|
| meta_ads_compute_image_crops | Compute centered crop boxes for the 6 Meta aspect ratios | image_url, image_hash |
| meta_ads_estimate_audience_size | Estimate reach for a targeting spec | targeting_spec |
| meta_ads_fetch_pagination_url | Fetch a subsequent page of a paginated result | url |
| meta_ads_get_account_pages | List Facebook Pages reachable from the token |  |
| meta_ads_get_activities_by_adaccount | Change history log for an ad account | account_id, filters |
| meta_ads_get_activities_by_adset | Change history log for an ad set | adset_id, filters |
| meta_ads_get_ad_account_details | Get detailed information for a specific ad account | account_id |
| meta_ads_get_ad_by_id | Fetch a single ad by ID | ad_id |
| meta_ads_get_ad_creative_by_id | Fetch one creative by ID | creative_id |
| meta_ads_get_ad_creatives_by_ad_id | List creatives attached to an ad | ad_id |
| meta_ads_get_ad_images | List image assets in an ad account | account_id |
| meta_ads_get_ad_insights | Performance metrics for an ad | ad_id, date_range, metrics |
| meta_ads_get_ad_previews | Rendered previews of an ad across placements | ad_id, formats |
| meta_ads_get_ad_video | Video details by ad_id or video_id | ad_id, video_id |
| meta_ads_get_adaccount_insights | Performance metrics at the account level | account_id, date_range, metrics |
| meta_ads_get_adcreatives_by_adaccount | List creatives in an ad account | account_id |
| meta_ads_get_ads_by_adaccount | List ads in an ad account | account_id, filters |
| meta_ads_get_ads_by_adset | List ads within an ad set | adset_id |
| meta_ads_get_ads_by_campaign | List ads within a campaign | campaign_id |
| meta_ads_get_adset_by_id | Fetch a single ad set by ID | adset_id |
| meta_ads_get_adset_insights | Performance metrics for an ad set | adset_id, date_range, metrics |
| meta_ads_get_adsets_by_adaccount | List ad sets in an ad account | account_id, filters |
| meta_ads_get_adsets_by_campaign | List ad sets within a campaign | campaign_id |
| meta_ads_get_adsets_by_ids | Batch fetch multiple ad sets | adset_ids |
| meta_ads_get_campaign_by_id | Fetch a specific campaign by ID | campaign_id |
| meta_ads_get_campaign_insights | Performance metrics for a campaign | campaign_id, date_range, metrics |
| meta_ads_get_campaigns_by_adaccount | List campaigns within an ad account | account_id, filters |
| meta_ads_get_image_by_hash | Single-image lookup by hash (URL + dimensions) | account_id, image_hash |
| meta_ads_get_interest_suggestions | Related interests from a seed list | interest_list |
| meta_ads_list_ad_accounts | List all ad accounts accessible with the token |  |
| meta_ads_search_behaviors | List available behavior targeting options |  |
| meta_ads_search_demographics | List demographic targeting options | type |
| meta_ads_search_geo_locations | Search countries / regions / cities / zips / geo markets | query, type |
| meta_ads_search_interests | Search Meta's interest catalog by keyword | query |
| meta_ads_search_pages_by_name | Search the token's Facebook Pages by name | query |

## omniroute  (5 tools)

| Tool | Description | Parameters |
|---|---|---|
| chat_completions | OpenAI-compatible chat completions with fallback (POST /v1/chat/completions) | model, messages |
| models | List 1200+ models across 352 providers (GET /v1/models) |  |
| providers | Provider list with health and key status (GET /v1/providers) |  |
| status | Gateway status: uptime, providers, key pools (GET /v1/status) |  |
| usage | Token/cost usage reports (GET /v1/usage) | period |

## omniroute-dashboard  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| manage_providers | Providers, API keys, combos management (UI at :20128/dashboard) |  |
| usage_reports | Token/cost usage dashboards (UI at :20128/dashboard) |  |

## playwright  (15 tools)

| Tool | Description | Parameters |
|---|---|---|
| browser_click | Click an element | element, ref |
| browser_close | Close the browser page |  |
| browser_console_messages | Read console messages | level |
| browser_evaluate | Evaluate JavaScript in the page | function |
| browser_file_upload | Upload files to an input | paths |
| browser_fill_form | Fill multiple form fields | fields |
| browser_hover | Hover over an element | element, ref |
| browser_navigate | Navigate to a URL | url |
| browser_network_requests | List network requests |  |
| browser_press_key | Press a keyboard key | key |
| browser_snapshot | Capture accessibility snapshot of the page |  |
| browser_tabs | List, create, close, or select tabs | action, index |
| browser_take_screenshot | Take a screenshot of the page | filename, element |
| browser_type | Type text into an element | element, ref, text |
| browser_wait_for | Wait for text to appear/disappear | text, textGone, time |

## postgres-mcp  (5 tools)

| Tool | Description | Parameters |
|---|---|---|
| postgres_mcp_bulk_load_csv | Bulk-load a CSV into a table via COPY | path, table, profile |
| postgres_mcp_describe_csv | Describe a local CSV file (columns, types) | path |
| postgres_mcp_modify | Run DDL/DML SQL (CREATE/INSERT/UPDATE/DELETE) | sql, profile |
| postgres_mcp_query | Run read-only SQL against a PostgreSQL database | sql, profile |
| postgres_mcp_schema | Fetch CREATE scripts for tables, indexes, functions, sequences | profile, object |

## tdai-memory  (6 tools)

| Tool | Description | Parameters |
|---|---|---|
| tdai_capture | Persist a conversation turn into memory (L0) | user_content, assistant_content, session_key |
| tdai_conversation_search | Search raw L0 conversation history | query |
| tdai_memory_search | Search structured L1 atomic memories | query |
| tdai_recall | Recall conversational memories and persona context | query, session_key |
| tdai_session_end | End a memory session and flush pending work | session_key |
| unified_recall | Combined recall from memory + codebase knowledge graph | query, session_key |

## time  (2 tools)

| Tool | Description | Parameters |
|---|---|---|
| convert_time | Convert time between timezones | source_timezone, time, target_timezone |
| get_current_time | Get current time in a timezone | timezone |

## winremote  (11 tools)

| Tool | Description | Parameters |
|---|---|---|
| clipboard_get | Read clipboard contents |  |
| clipboard_set | Write clipboard contents | text |
| process_kill | Kill a process | pid/name |
| process_list | List running processes |  |
| registry_query | Query a registry key/value | key, value |
| registry_set | Set a registry value | key, value, data |
| run_command | Run a shell command (Windows remote control) | command |
| screenshot | Capture a screenshot | save_path |
| service_list | List Windows services |  |
| service_start | Start a Windows service | name |
| service_stop | Stop a Windows service | name |

## youtube-mcp  (3 tools)

| Tool | Description | Parameters |
|---|---|---|
| get_comments | Fetch comments of a YouTube video | video_url, max_results |
| get_transcript | Download captions/transcript of a YouTube video | video_url, lang |
| get_video_info | Fetch video metadata (title, author, duration) | video_url |


