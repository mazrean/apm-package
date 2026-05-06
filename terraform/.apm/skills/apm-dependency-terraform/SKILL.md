---
name: apm-dependency-terraform
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/terraform. Use when bootstrapping or auditing a Terraform repo's mise.toml.
---

# Terraform package — mise dependencies

```toml
[tools]
terraform = "latest"
tflint = "latest"
"go:github.com/hashicorp/terraform-mcp-server/cmd/terraform-mcp-server" = "latest"
```

## Notes

- `terraform-mcp-server` MUST be installed; it backs the `terraform` MCP server that this package registers (`terraform-mcp-server stdio`).
- The `aqua:` backend cannot install `terraform-mcp-server` (HashiCorp ships it via `go_install`, which the aqua backend rejects). Use the `go:` backend as shown above.
- `terragrunt` is intentionally NOT pinned by default — add it per-repo if the repo uses it.
- `terraform-docs` is intentionally NOT pinned by default — add it per-repo if the repo auto-generates module READMEs.
- For cloud-specific tooling (gcloud / aws / az), depend on the corresponding `apm-plackage/terraform-<cloud>` package which extends this one.
