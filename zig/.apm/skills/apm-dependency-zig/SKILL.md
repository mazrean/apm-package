---
name: apm-dependency-zig
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/zig. Use when bootstrapping or auditing a Zig repo's mise.toml.
---

# Zig package — mise dependencies

```toml
[tools]
zig = "0.13"
```

## Notes

- Pin a concrete Zig version (e.g. `0.13` or `0.14`) — Zig is pre-1.0 and breaks at every minor.
- If the repo releases binaries via goreleaser, also depend on `apm-plackage/goreleaser`.
