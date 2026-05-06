---
name: apm-dependency-terraform
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/terraform. Use when bootstrapping or auditing a Terraform repo's mise.toml.
---

# Terraform package — mise dependencies

```toml
[tools]
terraform = "latest"
tflint = "latest"
"aqua:hashicorp/terraform-mcp-server" = "latest"
```

## Notes

- `terraform-mcp-server` MUST be installed; it backs the `terraform` MCP server that this package registers (`terraform-mcp-server stdio`).
- `terragrunt` is intentionally NOT pinned by default — add it per-repo if the repo uses it.
- `terraform-docs` is intentionally NOT pinned by default — add it per-repo if the repo auto-generates module READMEs.
- For cloud-specific tooling (gcloud / aws / az), depend on the corresponding `apm-plackage/terraform-<cloud>` package which extends this one.
