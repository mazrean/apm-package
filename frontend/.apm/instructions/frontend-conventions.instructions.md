---
applyTo: "**/*.{ts,tsx,js,jsx,astro,svelte,vue,templ}"
---

# Frontend conventions

## Browser automation & debugging

- **Playwright (E2E / VRT)**: use the Playwright CLI — the `@playwright/cli` npm package, installed via mise.
  The `playwright-cli` Agent Skill (from `microsoft/playwright-cli`) is auto-installed by this package and is the canonical interface for agents.
  Do NOT register a Playwright MCP server.
- **chrome-devtools-mcp (debugging)**: the `chrome-devtools-mcp` npm package is installed via mise so the binary is available both as an MCP server and as a CLI.
  The `chrome-devtools-cli` Agent Skill (from `ChromeDevTools/chrome-devtools-mcp`) is auto-installed by this package; prefer it for skill-based agent flows.
  Per-repo `apm.yml` may still register `chrome-devtools-mcp` as an MCP server when runtime tool-calling is preferred.

## Build tooling

- Prefer `pnpm` as the package manager unless an existing repo uses `npm` or `bun`.
- Pin `node` at LTS in `mise.toml`.

## CSS

- For design-token + dark-mode work, rely on per-repo `tech-css-*` skills (e.g. `tech-css-design-tokens-dark-mode`, `tech-css-oklch`).
