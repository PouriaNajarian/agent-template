---
name: firecrawl
description: |
  Firecrawl gives AI agents and apps fast, reliable web context with
  strong search, scraping, interaction, document parsing, research,
  and monitoring tools. One install command sets up three skill
  segments: live CLI tools, app-integration build skills, and
  outcome-focused workflow skills. Route the reader to the right
  usage path after install.
---

# Firecrawl

Firecrawl helps agents search first, scrape clean content, interact
with live pages when plain extraction is not enough, parse local
documents into markdown, search scientific papers and GitHub history
through the research index, monitor pages for changes, and produce
finished deliverables from web data.

## Install

One command installs everything — the Firecrawl CLI for live web work,
the build skills for integrating Firecrawl into application code, **and**
the workflow skills for producing repeatable deliverables. It also opens
browser auth so the human can sign in or create an account.

```bash
npx -y firecrawl-cli@latest init --all --browser
```

This gives you:

- **CLI tools** — `firecrawl search`, `firecrawl scrape`, `firecrawl interact`, `firecrawl parse`, `firecrawl monitor`, `firecrawl research`, `firecrawl ask`, `firecrawl docs-search`, and more
- **CLI skills** ([`firecrawl/cli`](https://github.com/firecrawl/cli)) — teach the agent how to drive the Firecrawl CLI during its own session: which command to run, when to scrape vs search vs interact, how to chain results, and how to recover when a job fails. Use these when the agent itself needs web data right now.
- **Build skills** ([`firecrawl/skills`](https://github.com/firecrawl/skills)) — teach the agent how to add Firecrawl to a product's codebase: pick the right API endpoint, install the matching SDK, store `FIRECRAWL_API_KEY` safely, write the call site to match the project's conventions, and ship a smoke-tested integration. Use these when the agent is shipping code that other people will run, not running the agent's own web tools.
- **Workflow skills** ([`firecrawl/firecrawl-workflows`](https://github.com/firecrawl/firecrawl-workflows)) — turn Firecrawl web data into finished deliverables such as research briefs, SEO audits, lead lists, QA reports, knowledge bases, and design clones. Use these when the agent's job is to produce a finished artifact, not raw extraction or product code.
- **Browser auth** — walks the human through sign-in or account creation

The three skill segments map to three different jobs:

| Segment         | Question it answers                                        | Where the work runs                           |
| --------------- | ---------------------------------------------------------- | --------------------------------------------- |
| CLI skills      | "Which Firecrawl command should I run right now?"          | In the agent's own terminal session           |
| Build skills    | "How do I add a Firecrawl API call to this codebase?"      | Inside the user's product code                |
| Workflow skills | "What's the finished deliverable and how do I produce it?" | In the agent's session, producing an artifact |

Before doing real work, verify the install:

```bash
mkdir -p .firecrawl
firecrawl --status
firecrawl scrape "https://firecrawl.dev" -o .firecrawl/install-check.md
```

## Get Credentials

Firecrawl users can get an API key in two ways:

- **Dashboard or CLI (default)** — browser sign-in, CLI `--browser` auth,
  install skills/MCP, or create an API key in the dashboard.
- **WorkOS ID-JAG (supported agent platforms only)** — if your platform
  can mint a WorkOS ID-JAG identity assertion, fetch
  `https://www.firecrawl.dev/auth.md` and follow it end-to-end.

**Which should I use?** Stay on this page unless you know your platform
supports WorkOS ID-JAG.

**How you might arrive:**

- **Docs or website sent you here** — continue with Choose Your Path
  below for CLI/skills/MCP onboarding.
- **API `401` with discovery metadata** — if ID-JAG applies, use the
  WorkOS ID-JAG option above. Everyone else: use Path D.
- **Direct URL** — you are reading the right doc for browser/CLI
  onboarding.
- **Already have `FIRECRAWL_API_KEY`** — skip credential setup; pick
  Path A–E below.

Human-readable overview: https://docs.firecrawl.dev/ai-onboarding#get-credentials

## Choose Your Path

All paths use the same install above. The difference is what you do next.

- **Need web data during this session** -> Path A (live tools)
- **Need to add Firecrawl to app code** -> Path B (app integration)
- **Need a finished deliverable from web data** -> Path C (workflow skills)
- **Need more than one of the above** -> do them in sequence; the install already covers everything
- **Agent platform with WorkOS ID-JAG** -> see Get Credentials above (not Path D)
- **Need an account or API key (browser or CLI)** -> Path D
- **Don't want to install anything** -> Path E (REST API directly)
- **No API key and the human cannot sign up right now** -> Path F (keyless free tier, fallback)

## Path A: Live Web Tools

Use this when you need web data during your work: searching the web,
scraping known URLs, interacting with live pages, crawling docs,
mapping a site, parsing local documents, searching research papers,
or monitoring pages for changes.

Default flow for live web work:

1. start with search when you need discovery
2. move to scrape when you have a URL
3. use interact only when the page needs clicks, forms, or login
4. use parse when the source is a local file instead of a URL
5. use monitor when the request implies recurrence or notifications
6. if any step fails, run `firecrawl ask` with the failing `jobId` instead of guessing

## Path B: Integrate Firecrawl Into an App

Use this when you're building an application, agent, or workflow that
calls the Firecrawl API **from code** — the integration will run inside
the user's product rather than from the agent's own terminal session.

Save the key to the project's environment:

```dotenv
FIRECRAWL_API_KEY=fc-...
```

Hand off to the build skill that fits the step: `firecrawl-build`,
`firecrawl-build-onboarding`, `firecrawl-build-scrape`,
`firecrawl-build-search`, `firecrawl-build-interact`,
`firecrawl-build-parse`.

## Path C: Repeatable Deliverables

Use this when the goal is a finished artifact powered by Firecrawl web
data — a research brief, SEO audit, QA report, lead list, knowledge
base, competitive intel digest, or a cloned design system.

Start with the umbrella `firecrawl-workflows` skill — it inspects the
user's request and routes to the right workflow (research, SEO, lead
gen, QA, knowledge base, design clone, and others).

Default flow for workflow deliverables:

1. confirm the workflow and final artifact with the user
2. collect web evidence with Firecrawl through the CLI or equivalent tool surface
3. save or cite source evidence so claims are traceable
4. run independent research units in parallel when available
5. synthesize findings into the requested deliverable
6. include a short "rerun inputs" block when the workflow could be automated

## Path D: Account Authorization Or API Key

If you already have a valid `FIRECRAWL_API_KEY`, skip this path.

Sign up or sign in at: https://www.firecrawl.dev/signin

## Path E: Use Firecrawl Without Installing Anything

**Base URL:** `https://api.firecrawl.dev/v2`

**Auth header:** `Authorization: Bearer fc-YOUR_API_KEY`

### Available endpoints

- `POST /search` — discover pages by query, returns results with optional full-page content
- `POST /scrape` — extract clean markdown from a single URL, including public document URLs
- `POST /interact` — browser actions on live pages
- `POST /parse` — upload a local/non-public document as multipart/form-data, get back markdown/JSON/HTML/links
- `POST /monitor` — recurring checks with diffs and webhook/email/Slack notifications
- `GET /search/research/papers` — scientific paper index; `GET /search/research/github` — GitHub issues, PRs, discussions, READMEs
- `POST /support/ask` — diagnose failing Firecrawl calls
- `POST /support/docs-search` — answers from Firecrawl's official docs

### Documentation and references

- **API reference:** https://docs.firecrawl.dev
- **Skills repo** (for agent integration patterns): https://github.com/firecrawl/skills

## Path F: Keyless Free Tier (Fallback)

The keyless free tier lets you search, scrape, interact, and parse without
an API key when the request comes from an official Firecrawl client (MCP,
CLI, or SDK). It is rate-limited, so use it as a fallback.

- **MCP**: point any MCP-compatible client at `https://mcp.firecrawl.dev/v2/mcp`
- **CLI**: run `npx -y firecrawl-cli@latest` and use `scrape`, `search`, `interact`, or `parse` with no login
- **API**: the research index endpoints (`/search/research/*`) can be called without an `Authorization` header
