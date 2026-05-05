---
applyTo: "**/*.zig"
---

# Zig conventions

- Track a single Zig version per repo, pinned in `mise.toml`.
- Build via `zig build`; tests via `zig build test`.
- For CLI tools, follow the `writing-zig-cli-tools` skill.
- For multi-process socket sharing patterns, see `sharing-sockets-with-so-reuseport-in-zig`.
- For cross-platform release, depend additionally on `apm-plackage/goreleaser` and follow `releasing-zig-with-goreleaser`.
