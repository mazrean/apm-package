---
name: apm-dependency-go
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/go. Use when bootstrapping or auditing a Go repo's mise.toml.
---

# Go package — mise dependencies

Repos depending on `mazrean/apm-plackage/go` SHOULD include the following tools in `mise.toml`:

```toml
[tools]
go = "1.24"
"go:github.com/golangci/golangci-lint/v2/cmd/golangci-lint" = "latest"
```

## Optional add-ons

Add these only when used:

```toml
# Wire-based DI
"go:github.com/google/wire/cmd/wire" = "latest"

# gopls (e.g. for serena MCP)
"go:golang.org/x/tools/gopls" = "latest"
```

If the repo also releases binaries via goreleaser, also depend on `apm-plackage/goreleaser`.
