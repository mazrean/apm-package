---
applyTo: "**/*.{ts,tsx,js,jsx,astro,svelte,vue,templ}"
---

# Frontend conventions

## Browser automation

- Use the Playwright CLI for E2E and visual regression tests.
- Do NOT register a Playwright MCP server. The Agent Skill (`playwright-cli`) is the canonical interface.
- `chrome-devtools` MCP may be added per-repo for debugging if needed; Playwright remains the testing path.

## Build tooling

- Prefer `pnpm` as the package manager unless an existing repo uses `npm` or `bun`.
- Pin `node` at LTS in `mise.toml`.

## CSS

- For design-token + dark-mode work, rely on per-repo `tech-css-*` skills (e.g. `tech-css-design-tokens-dark-mode`, `tech-css-oklch`).
