---
name: apm-dependency-cloudflare
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/cloudflare. Use when bootstrapping or auditing a Cloudflare Workers repo's mise.toml.
---

# Cloudflare package — mise dependencies

Merge the frontend package's tools (Node + pnpm + `@playwright/cli` + `chrome-devtools-mcp`) plus:

```toml
[tools]
"npm:wrangler" = "latest"
```

## Notes

- Wrangler is preferred via the `npm:` backend so the version stays in lockstep with the worker types it generates.
- For D1 migrations and R2 lifecycle rules, no extra tool is needed — wrangler covers both.
- See `apm-plackage/frontend` for Node / pnpm / Playwright CLI / chrome-devtools-mcp entries.
- The Cloudflare authoring skills (`cloudflare`, `workers-best-practices`, `wrangler`) and remote MCP servers (`cloudflare-docs`, `cloudflare-bindings`, `cloudflare-observability`, `cloudflare-builds`, `cloudflare-browser`) are pulled transitively via this package's `apm.yml`. Sign-in for the MCP servers happens per-developer at first OAuth prompt; nothing is mise-managed for that path.
