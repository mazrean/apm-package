---
name: apm-dependency-frontend
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/frontend. Use when bootstrapping or auditing a frontend repo's mise.toml. Required for E2E testing via Playwright CLI.
---

# Frontend package — mise dependencies

```toml
[tools]
node = "lts"
pnpm = "latest"
"npm:playwright" = "latest"
```

## Notes

- `playwright` is the unified browser-automation tool. Pair it with the `playwright-cli` Agent Skill. Do not add a Playwright MCP server.
- After install, run `mise exec -- playwright install --with-deps` once per environment to fetch browser binaries.
- Repos that use `npm` instead of `pnpm` (e.g. `portfolio3`, `conoha-wallpaper-scraper`) should drop the `pnpm` line.
- Repos that use `bun` instead may swap `pnpm` for `bun`.
