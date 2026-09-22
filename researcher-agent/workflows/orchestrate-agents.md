---
description: Run parallel dev/ops agents via Devin/OpenCode/9Router CLI with proper LLM tiering
---
# Orchestrate Dev/Ops Agents (Multi-CLI)

Runs multiple development and DevOps agents simultaneously via Devin, OpenCode, or 9Router CLI, each with its assigned LLM model. Workflows are defined in JSON files under `.devin/workflows/`.

## Prerequisites
- At least one CLI app installed and authenticated:
  - Devin CLI: `$env:LOCALAPPDATA\devin\cli\bin\devin.exe` + `devin auth login`
  - OpenCode CLI: `npm i -g opencode-ai@latest` + `opencode auth list`
  - 9Router: `npm install -g 9router` + dashboard at `http://localhost:20128/dashboard`
- Headroom proxy running (optional, for token reduction)
- Knowledge graph read: run `/read-knowledge-graph` first

## Usage

### Dry Run (preview without executing)
```powershell
.\scripts\orchestrate.ps1 -Workflow feature-delivery -Target "my-app" -DryRun
```

### Devin (default)
```powershell
.\scripts\orchestrate.ps1 -Workflow feature-delivery -Target "my-app"
```

### OpenCode
```powershell
.\scripts\orchestrate.ps1 -Workflow api-development -Target "my-api" -CliApp opencode
```

### 9Router (auto-fallback)
```powershell
.\scripts\orchestrate.ps1 -Workflow deployment -Target "my-app" -CliApp 9router
```

### Custom model overrides
```powershell
.\scripts\orchestrate.ps1 -Workflow code-review -Target "my-app" -JuniorModel "haiku"
```

### Adding a new workflow
Create `.devin/workflows/<name>.json` (see `.devin/mcp/orchestrator.md` for format). No script edit needed.

## How It Works

1. Script loads `.devin/workflows/<name>.json` — any workflow with a JSON file is accepted
2. **Phase 1 (Sequential):** Senior lead defines architecture and plan
3. **Phase 2 (Parallel):** Mid specialists + Junior assistants run simultaneously (throttled)
4. **Phase 3 (Sequential):** Validation/review agent processes all Phase 2 outputs
5. **Phase 4 (Sequential):** Documentation agent compiles final docs

## LLM Tier per CLI App

| Tier | Devin | OpenCode | 9Router |
|------|-------|----------|---------|
| Senior | `opus` | `anthropic/claude-opus-4.5` | `kr/claude-opus-4.5` |
| Mid | `sonnet` | `anthropic/claude-sonnet-4.5` | `kr/claude-sonnet-4.5` |
| Junior | `swe-1-7` (free) | `glm/glm-5.2` (free) | `kr/glm-5-free` (free) |

Override any tier with `-SeniorModel`, `-MidModel`, `-JuniorModel`. See `agent-models.md` for full model lists.

## After Orchestration

1. Review reports in `reports/<workflow>/`
2. Run `/update-knowledge-graph` to sync the knowledge graph
3. Archive key findings to `.devin/knowledge/research-notes/`

## Troubleshooting

- **"Workflow definition not found"**: Create `.devin/workflows/<name>.json` or check available workflows in the error message
- **"Devin CLI not found"**: Install Devin CLI or use `-CliApp opencode` / `-CliApp 9router`
- **"Model not available"**: Check `agent-models.md` for valid model IDs per CLI app
- **Slow execution**: Reduce `-ThrottleLimit` to 3 if hitting rate limits
