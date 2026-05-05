---
applyTo: "wrangler.{toml,jsonc,json}, src/**/*.{ts,tsx}"
---

# Cloudflare Workers conventions

- Configure bindings (`d1_databases`, `kv_namespaces`, `r2_buckets`, `caches`, etc.) in `wrangler.jsonc` (preferred) or `wrangler.toml`.
- Use the Workers runtime types from `worker-configuration.d.ts`. Re-generate via `wrangler types` after binding changes.
- For D1 migrations: keep SQL files under `migrations/` and apply via `wrangler d1 migrations apply <db>`.
- For local dev, run `pnpm dlx wrangler dev` (or `mise exec -- wrangler dev`) — never embed credentials in source.
- This package inherits from `apm-plackage/frontend` because Workers projects also need Node + pnpm + (optionally) Playwright.
