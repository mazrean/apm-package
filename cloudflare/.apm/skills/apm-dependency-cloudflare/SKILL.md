---
name: apm-dependency-cloudflare
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/cloudflare. Use when bootstrapping or auditing a Cloudflare Workers repo's mise.toml.
---

# Cloudflare package — mise dependencies

Merge the frontend package's tools (Node + pnpm + Playwright) plus:

```toml
[tools]
"npm:wrangler" = "latest"
```

## Notes

- Wrangler is preferred via `npm:` backend so the version stays in lockstep with the worker types it generates.
- For D1 migrations and R2 lifecycle rules, no extra tool is needed — wrangler covers both.
- See `apm-plackage/frontend` for Node / pnpm / Playwright entries.
