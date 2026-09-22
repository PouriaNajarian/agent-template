---
name: graphify-knowledge-graph
description: Read the global skills knowledge graph before starting any task. Maps 514 skills across 16 prefixes with cross-category relationships. Use to discover which skills to invoke for a given workflow, find related skills, and avoid duplicating work. The graph lives at ~/.claude/skills/knowledge-graph.json.
---

# Knowledge Graph Skill

## When to Use
- **BEFORE any task**: Read the knowledge graph to discover which skills are available and relevant
- When planning a workflow: Find skills by category and cross-category relationships
- When uncertain about which skill to invoke: Query the graph for related skills
- After adding new skills: Regenerate the graph with `gen-knowledge-graph.ps1`

## How to Read the Graph

The knowledge graph is at `~/.claude/skills/knowledge-graph.json`.

### Structure
```json
{
  "version": "1.0",
  "totalSkills": 514,
  "totalCategories": 15,
  "totalLinks": 1028,
  "nodes": [
    {
      "id": "skill-name",
      "type": "skill",
      "category": "Cloudflare",
      "path": "~/.claude/skills/skill-name/SKILL.md",
      "label": "skill name",
      "description": "...",
      "references": 3,
      "scripts": 2
    },
    {
      "id": "hub-cf-",
      "type": "category",
      "category": "Cloudflare",
      "label": "Cloudflare skills",
      "description": "84 skills in the Cloudflare category"
    }
  ],
  "links": [
    { "source": "hub-cf-", "target": "cf-cloudflare", "type": "contains" },
    { "source": "dev-test-driven-development", "target": "eng-test-driven-development", "type": "related" }
  ]
}
```

### Link Types
- **contains**: Category hub → skill (membership)
- **related**: Skills that share a common topic (TDD, code review, security, deployment)
- **companion**: Official + community versions of the same domain (e.g., Figma)

## Querying Workflow

1. **Read the graph** at the start of every task
2. **Find the category** that matches the task domain
3. **List skills** in that category via `contains` links
4. **Check for related skills** via `related` links across categories
5. **Invoke the most specific skill** that matches the task
6. **If no skill matches**, research the web for best practices

## Categories and Prefixes

| Prefix | Category | Count |
|--------|----------|-------|
| `web-` | Next.js/Hono/CF | ~15 |
| `ml-` | ML pipelines | ~25 |
| `sec-` | security | ~30 |
| `ecom-` | ecommerce | ~10 |
| `cf-` | Cloudflare | ~84 |
| `vercel-` | Vercel | ~6 |
| `stripe-` | Stripe | ~6 |
| `google-` | Google/GCP | ~96 |
| `claude-` | Anthropic | ~17 |
| `openai-` | OpenAI | ~43 |
| `ms-` | Microsoft/Azure | ~182 |
| `figma-` | Figma official | ~12 |
| `figma-community-` | Figma community | ~18 |
| `notebooklm-` | NotebookLM | ~1 |
| `dev-` | Superpowers/TDD | ~14 |
| `eng-` | engineering | ~24 |

## Regenerating the Graph

After adding or removing skills, regenerate:
```powershell
powershell -ExecutionPolicy Bypass -File D:\Projects\gen-knowledge-graph.ps1
```

The script scans `~/.claude/skills/`, reads each `SKILL.md` frontmatter, builds category hubs, creates cross-category links, and writes the JSON to both the skills folder and the git repo.
