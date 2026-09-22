---
description: Deploy Next.js and Hono applications to Cloudflare Pages and Workers with CI/CD and rollback
---
# Deployment

Deploy Next.js and Hono applications to Cloudflare Pages and Workers with proper CI/CD, environment management, and rollback strategy.

## Steps

1. **Research current best practices** — Search for latest Wrangler and Cloudflare deployment best practices. Compare findings against existing skills and MCP definitions. Update framework artifacts if a better approach is found.

2. **Define deployment strategy** — Choose deployment strategy (blue-green, canary, rolling). Define environment configurations (development, preview, production). Define rollback procedure. Define health checks and monitoring.

3. **Configure Wrangler and Cloudflare** — Set up `wrangler.toml` or `wrangler.jsonc` with correct bindings and environments. Configure KV, D1, R2, Durable Objects, Queues, AI, Analytics Engine bindings as needed. Set up custom domains and routing rules.

4. **Manage secrets** — Set up secrets via `wrangler secret put` — never commit to version control. Configure environment variables per environment. Verify secrets are not exposed in code or config files.

5. **Audit dependencies** — Check all dependencies for Cloudflare Workers compatibility. Verify no Node.js-specific APIs that don't work at the edge. Pin dependency versions for reproducibility.

6. **Deploy to preview** — Deploy to preview environment first (`--env preview` or `--branch preview`). Verify deployment health and Worker URL. Run observability checks for errors and logs.

7. **Review and validate** — Review deployment config for correctness and security. Verify secrets management. Check environment isolation. Confirm preview deployment is healthy.

8. **Deploy to production** — Deploy to production after preview validation. Monitor deployment for errors. Verify production health checks pass.

9. **Document** — Compile deployment guide and runbook. Document rollback procedure. Update README with deployment instructions.

## Quality Gates

- [ ] Deployment plan approved
- [ ] Wrangler configuration valid
- [ ] Secrets configured via `wrangler secret put`
- [ ] Dependencies compatible with Cloudflare Workers
- [ ] Preview deployment verified
- [ ] Production deployment healthy
- [ ] Deployment guide documented
- [ ] Rollback procedure documented
