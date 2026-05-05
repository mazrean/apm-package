---
applyTo: "**/*.go"
---

# Go conventions

- Manage build / lint / generate tools via the Go 1.24+ `tool` directive in `go.mod` (see `using-go-tool-directive` skill). Do not maintain a `tools.go` file.
- Run `golangci-lint` before committing.
- Prefer `go test ./...` for the full module; use `-race` in CI.
- For DI, prefer `wire`. Generate via `go generate ./...`.
- For LSP-backed code intelligence, use `gopls` (locally or via `serena` MCP if registered).
