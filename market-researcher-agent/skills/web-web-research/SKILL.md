---
name: web-web-research
description: Web research methodology for finding the latest suitable skills, tools, and techniques before executing any task. This skill is mandatory for every agent before starting work, as defined in AGENT_P...
---

# Skill: Web Research

## Used By
- All agents (mandatory pre-execution per AGENT_PROTOCOL.md §7)

## Description
Web research methodology for finding the latest suitable skills, tools, and techniques before executing any task. This skill is mandatory for every agent before starting work, as defined in AGENT_PROTOCOL.md §7.

## Key Areas
- Search engine queries for current best practices
- Framework and library version-specific documentation
- GitHub repository and issue research
- Blog posts and conference talks
- Stack Overflow and community discussions
- Security advisories and vulnerability research
- Performance benchmarks and comparisons
- Migration guides and breaking changes
- Cloud provider documentation and updates
- Testing framework updates and patterns

## MCP Tools
- [[mcp-context7]] — Up-to-date library documentation
- [[mcp-deepwiki]] — AI-powered codebase context
- [[mcp-github]] — Repository search and issue tracking
- [[mcp-filesystem]] — Save research notes

## Methodology
1. **Search the web** — Query for current techniques, tools, and best practices
2. **Compare against framework** — Search `.devin/skills/` and `.devin/mcp/` for existing definitions
3. **Optimize the task plan** — Update framework artifacts if a better approach is found
4. **Execute only after optimization** — Perform the task with the optimized approach
5. **Document sources** — Record web sources used and how they influenced the approach
6. **Update knowledge base** — Save reusable findings to `.devin/knowledge/research-notes/`

## Research Note Format

```markdown
# Research: <topic>
**Date:** YYYY-MM-DD
**Agent:** <agent-name>
**Workflow Phase:** <phase>

## Findings
- Finding 1 (source: [link])
- Finding 2 (source: [link])

## Framework Updates
- Updated: `.devin/skills/<skill>.md` — reason
- Updated: `.devin/mcp/<mcp>.md` — reason

## Impact on Task
- How findings changed the approach
- What was done differently as a result
```
