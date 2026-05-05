---
name: apm-dependency-frontend
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/frontend. Required for E2E testing via Playwright CLI and for browser debugging via chrome-devtools-mcp.
---

# Frontend package — mise dependencies

```toml
[tools]
node = "lts"
pnpm = "latest"
"npm:@playwright/cli" = "latest"
"npm:chrome-devtools-mcp" = "latest"
```

## Notes

- **Playwright** is the unified browser-automation tool. The npm package is `@playwright/cli` (not `playwright`).
  Pair it with the `playwright-cli` Agent Skill (auto-installed by this package via `microsoft/playwright-cli/skills/playwright-cli`).
  Do NOT add a Playwright MCP server.
- **chrome-devtools-mcp** ships the `chrome-devtools-mcp` binary, used either as an MCP server or invoked directly as a CLI.
  Pair it with the `chrome-devtools-cli` Agent Skill (auto-installed by this package via `ChromeDevTools/chrome-devtools-mcp/skills/chrome-devtools-cli`).
- After installing `@playwright/cli`, run `mise exec -- playwright install --with-deps` once per environment to fetch browser binaries.
- Repos that use `npm` instead of `pnpm` (e.g. `portfolio3`, `conoha-wallpaper-scraper`) should drop the `pnpm` line.
- Repos that use `bun` instead may swap `pnpm` for `bun`.
