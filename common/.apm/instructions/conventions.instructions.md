---
applyTo: "**"
---

# Project conventions

## Agent instruction file

- `AGENTS.md` is the single source of truth.
- `CLAUDE.md` MUST contain only `@AGENTS.md` so Claude Code imports the same content.
- Other client-specific instruction files (`GEMINI.md`, `.cursor/rules`, etc.) should also point at `AGENTS.md` rather than duplicate content.

## Spec-driven development

- New specs live under `specs/`. The legacy `.kiro/specs/` layout is deprecated.
- Use the `writing-feature-spec`, `writing-technical-design`, `writing-implementation-tasks`, and `writing-project-constitution` skills from `mazrean/agent-skills`.
- `cc-sdd` and `github/spec-kit` are deprecated org-wide.

## Commits

- Use Conventional Commits via the `committing-code` skill.
- Keep commits atomic; never bypass hooks (`--no-verify`) without explicit authorization.

## Tool versions

- Pin CLI tool versions in `mise.toml` at the repo root.
- The coding-agent CLI (claude-code / codex / etc.) is NOT pinned in mise — install per developer.
- Each `apm-plackage` stack package ships an `apm-dependency-<package>` Agent Skill listing the tools it expects in `mise.toml`. The repo owner hand-merges these into the local `mise.toml`.

## Browser automation

- Use the Playwright CLI + the Playwright Agent Skill. Do NOT register a Playwright MCP server.

## Adding new shared skills

- Reusable skills (cross-repo) belong in `mazrean/agent-skills`, not in individual repos.
- Per-stack standards belong in the appropriate `mazrean/apm-plackage/<stack>` package.
