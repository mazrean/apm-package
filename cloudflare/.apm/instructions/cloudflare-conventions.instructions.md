---
applyTo: "wrangler.{toml,jsonc,json}, src/**/*.{ts,tsx}, migrations/**/*.sql"
---

# Cloudflare Workers conventions

## Authoring skills

The following skills from `cloudflare/skills` are auto-installed via this package's `apm.yml` and should be the first reference for routine Workers work:

- **`cloudflare`** — cross-product overview and platform conventions.
- **`workers-best-practices`** — Workers runtime idioms (`compatibility_date`, fetch handlers, ctx.waitUntil, request scoping, etc.).
- **`wrangler`** — Wrangler CLI reference: bindings, secrets, types generation, D1 migrations, deploy / dev / tail commands.

Deeper, per-feature reference skills (e.g. `tech-cloudflare-d1`, `tech-cloudflare-r2-lifecycle`) live in consumer repositories and stay there — do not duplicate them here.

## Bindings & wrangler

- Configure bindings (`d1_databases`, `kv_namespaces`, `r2_buckets`, `caches`, etc.) in `wrangler.jsonc` (preferred) or `wrangler.toml`.
- Use the Workers runtime types from `worker-configuration.d.ts`. Re-generate via `wrangler types` after binding changes.
- For D1 migrations: keep SQL files under `migrations/` and apply via `wrangler d1 migrations apply <db>`.
- For local dev, run `pnpm dlx wrangler dev` (or `mise exec -- wrangler dev`) — never embed credentials in source.

## Frontend inheritance

This package inherits from `apm-plackage/frontend` because Workers projects also need Node + pnpm + Playwright CLI + chrome-devtools-mcp.

## Cloudflare MCP servers

This package registers the following remote MCP servers via OAuth-based HTTP transport:

- `cloudflare-docs` — documentation lookup
- `cloudflare-bindings` — bindings management (D1 / R2 / KV / Queues / Durable Objects)
- `cloudflare-observability` — invocation logs / errors / metrics
- `cloudflare-builds` — Workers Builds status
- `cloudflare-browser` — Browser Rendering API

Sign-in is handled per-developer at first use. Repositories may register additional product-specific Cloudflare MCPs (Radar, Logpush, AI Gateway, Audit Logs, DNS Analytics, DEX, CASB, GraphQL, Container) in their own `apm.yml` if they need them.
