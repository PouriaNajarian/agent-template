# Skills Index

Verbatim copies from the mcp-skills catalog (`skills`),
selected for the code-reviewer agent. Each entry links to its `SKILL.md`.

| Skill | Description |
|---|---|
| [agent-creator](skills/agent-creator/SKILL.md) | Create custom AI subagents with proper plugin structure, persona generation, and companion routing skills. |
| [api-security](skills/api-security/SKILL.md) | Authorized security assessment of REST, GraphQL, WebSocket, and SOAP APIs: discovery, authentication and authorization flaws (BOLA/IDOR, JWT/OAuth), rate-lim... |
| [api-security-best-practices](skills/api-security-best-practices/SKILL.md) | Implement secure API design patterns including authentication, authorization, input validation, rate limiting, and protection against common API vulnerabilities |
| [api-security-testing](skills/api-security-testing/SKILL.md) | API security testing workflow for REST and GraphQL APIs covering authentication, authorization, rate limiting, input validation, and security best practices. |
| [brooks-review](skills/brooks-review/SKILL.md) | PR code review that surfaces decay risks, design smells, and maintainability issues with concrete Symptom â†’ Source â†’ Consequence â†’ Remedy findings, dra... |
| [build-scenario-tests](skills/build-scenario-tests/SKILL.md) | Inspect an unfamiliar repository, turn a focused Markdown behavior scenario into a deterministic test in the repository's native test stack, run it, and pres... |
| [cf-code-review](skills/cf-code-review/SKILL.md) | Reviews Workers and Cloudflare Developer Platform code for type correctness, API usage, and configuration validity. Load when reviewing TypeScript/JavaScript... |
| [code-review](skills/code-review/SKILL.md) | Review code for correctness, security, readability, and maintainability before merging. |
| [code-review-checklist](skills/code-review-checklist/SKILL.md) | Comprehensive checklist for conducting thorough code reviews covering functionality, security, performance, and maintainability |
| [code-reviewer](skills/code-reviewer/SKILL.md) | Elite code review expert specializing in modern AI-powered code |
| [code-review-excellence](skills/code-review-excellence/SKILL.md) | Transform code reviews from gatekeeping to knowledge sharing through constructive feedback, systematic analysis, and collaborative improvement. |
| [code-standards](skills/code-standards/SKILL.md) | Apply a disciplined engineering workflow to any code change. Use whenever implementing a feature, fixing a bug, or refactoring â€” before writing code, not a... |
| [codex-review](skills/codex-review/SKILL.md) | Professional code review with auto CHANGELOG generation, integrated with Codex AI. Use when you want professional code review before commits, you need automa... |
| [coding-standards](skills/coding-standards/SKILL.md) | Baseline cross-project coding conventions for naming, readability, immutability, and code-quality review. Use detailed frontend or backend skills for framewo... |
| [comprehensive-review-full-review](skills/comprehensive-review-full-review/SKILL.md) | Use when working with comprehensive review full review |
| [comprehensive-review-pr-enhance](skills/comprehensive-review-pr-enhance/SKILL.md) | > |
| [coverage-analysis](skills/coverage-analysis/SKILL.md) | Interprets .NET Cobertura line, branch, and condition evidence and, when explicitly requested, computes project-wide CRAP/refactoring-risk hotspots. MUST USE... |
| [crap-score](skills/crap-score/SKILL.md) | Calculates CRAP (Change Risk Anti-Patterns) for a named .NET method, class, or file. USE FOR: explicit CRAP calculation or coverage-and-complexity risk withi... |
| [dev-receiving-code-review](skills/dev-receiving-code-review/SKILL.md) | Use when receiving code review feedback, before implementing suggestions, especially if feedback seems unclear or technically questionable - requires technic... |
| [dev-requesting-code-review](skills/dev-requesting-code-review/SKILL.md) | Use when completing tasks, implementing major features, or before merging to verify work meets requirements |
| [dev-verification-before-completion](skills/dev-verification-before-completion/SKILL.md) | Use when about to claim work is complete, fixed, or passing, before committing or creating PRs - requires running verification commands and confirming output... |
| [differential-review](skills/differential-review/SKILL.md) | Security-focused code review for PRs, commits, and diffs. |
| [eng-code-review-and-quality](skills/eng-code-review-and-quality/SKILL.md) | Conducts multi-axis code review. Use before merging any change. Use when reviewing code written by yourself, another agent, or a human. Use when you need to ... |
| [fix-review](skills/fix-review/SKILL.md) | Verify fix commits address audit findings without new bugs |
| [gh-review-requests](skills/gh-review-requests/SKILL.md) | Fetch unread GitHub notifications for open PRs where review is requested from a specified team or opened by a team member. Use when asked to "find PRs I need... |
| [git-pr-review](skills/git-pr-review/SKILL.md) | Generate a concise and structured PR description from commit history with minimal token usage |
| [git-pr-workflows-git-workflow](skills/git-pr-workflows-git-workflow/SKILL.md) | Orchestrate review, tests, commits, branch pushes, and pull-request creation with parallel agents. Use when completed changes must move through validation in... |
| [karpathy-guidelines](skills/karpathy-guidelines/SKILL.md) | Behavioral guidelines to reduce common LLM coding mistakes. Use when writing, reviewing, or refactoring code to avoid overcomplication, make surgical changes... |
| [logic-review](skills/logic-review/SKILL.md) | Find logic bugs in a single file or function via semi-formal execution tracing (Premises â†’ Trace â†’ Divergence â†’ Trigger â†’ Remedy). Trigger when a use... |
| [openai-security-best-practices](skills/openai-security-best-practices/SKILL.md) | Perform language and framework specific security best-practice reviews and suggest improvements. Trigger only when the user explicitly requests security best... |
| [performance-testing-review-ai-review](skills/performance-testing-review-ai-review/SKILL.md) | You are an expert AI-powered code review specialist combining automated static analysis, intelligent pattern recognition, and modern DevOps practices. Levera... |
| [performance-testing-review-multi-agent-review](skills/performance-testing-review-multi-agent-review/SKILL.md) | Use when working with performance testing review multi agent review |
| [receiving-code-review](skills/receiving-code-review/SKILL.md) | Code review requires technical evaluation, not emotional performance. |
| [review-and-simplify-changes](skills/review-and-simplify-changes/SKILL.md) | Review a git diff or explicit file scope for reuse, code quality, efficiency, clarity, and standards issues, then optionally apply safe Codex-driven fixes. U... |
| [review-multi-agent-orchestration](skills/review-multi-agent-orchestration/SKILL.md) | Use when a supervisor, swarm, graph, planner-worker system, or parallel agent workflow needs review for task boundaries, shared state, branch joins, retries,... |
| [review-refiner](skills/review-refiner/SKILL.md) | Facilitate a structured conversation to customize how the review molecule works -- atom loading rules, severity classification, report format, scope rules, i... |
| [review-swarm](skills/review-swarm/SKILL.md) | Parallel read-only multi-agent review of a current git diff or explicit file scope to find behavioral regressions, security or privacy risks, performance or ... |
| [sec-api-review](skills/sec-api-review/SKILL.md) | Design-level review of API architecture and implementation to identify security design flaws and implementation issues. |
| [sec-api-security](skills/sec-api-security/SKILL.md) | Security assessment of REST and GraphQL APIs, including authentication, authorization, and data exposure. |
| [sec-authentication-review](skills/sec-authentication-review/SKILL.md) | Assessment of authentication mechanisms including session management, credential handling, and identity verification. |
| [sec-authorization-review](skills/sec-authorization-review/SKILL.md) | Assessment of access control mechanisms to ensure proper enforcement of permissions and privilege boundaries. |
| [security-audit](skills/security-audit/SKILL.md) | Comprehensive security auditing workflow covering web application testing, API security, penetration testing, vulnerability scanning, and security hardening. |
| [security-auditor](skills/security-auditor/SKILL.md) | Expert security auditor specializing in DevSecOps, comprehensive cybersecurity, and compliance frameworks. |
| [security-review](skills/security-review/SKILL.md) | Use this skill when adding authentication, handling user input, working with secrets, creating API endpoints, or implementing payment/sensitive features. Pro... |
| [security-scanning-security-dependencies](skills/security-scanning-security-dependencies/SKILL.md) | You are a security expert specializing in dependency vulnerability analysis, SBOM generation, and supply chain security. Scan project dependencies across mul... |
| [security-scanning-security-hardening](skills/security-scanning-security-hardening/SKILL.md) | Coordinate multi-layer security scanning and hardening across application, infrastructure, and compliance controls. |
| [security-scanning-security-sast](skills/security-scanning-security-sast/SKILL.md) | Static Application Security Testing (SAST) for code vulnerability |
| [sec-vulnerability-validation](skills/sec-vulnerability-validation/SKILL.md) | Confirmation of reported security findings through reproducible exploitation, impact assessment, and false positive elimination. |
| [test-anti-patterns](skills/test-anti-patterns/SKILL.md) | Audit a test file or suite; produce a severity-ranked diagnostic report. ALWAYS USE for tests that verify nothing, missing/tautological assertions, swallowed... |
| [test-smell-detection](skills/test-smell-detection/SKILL.md) | Audits existing tests in any language using formal, research-backed test smell names and the testsmells.org 19-smell academic taxonomy. Use when the caller a... |
| [verify-and-stop](skills/verify-and-stop/SKILL.md) | Prove existing work meets acceptance conditions without expanding scope. Use for validation-only tasks, completion checks, focused gate runs, and last-mile p... |
| [vibers-code-review](skills/vibers-code-review/SKILL.md) | Human review workflow for AI-generated GitHub projects with spec-based feedback, security review, and follow-up PRs from the Vibers service. |
| [web-code-review](skills/web-code-review/SKILL.md) | Systematic code review for Next.js + Hono + Cloudflare projects. Covers correctness, readability, maintainability, security, performance, TypeScript type saf... |

