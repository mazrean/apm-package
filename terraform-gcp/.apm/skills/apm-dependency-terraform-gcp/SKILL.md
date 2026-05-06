---
name: apm-dependency-terraform-gcp
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/terraform-gcp. Use when bootstrapping or auditing a Terraform-on-GCP repo's mise.toml.
---

# Terraform-GCP package — mise dependencies

Merge the terraform package's tools (`terraform`, `tflint`, `terraform-mcp-server`) plus:

```toml
[tools]
gcloud = "latest"
```

## Notes

- `gcloud` is required for Application Default Credentials (`gcloud auth application-default login`) and for ad-hoc inspection of provisioned resources during plan review.
- No GCP-specific MCP server is registered by this package. Documentation lookup goes through `deepwiki` (from `common`) and the `terraform` MCP server (from `apm-plackage/terraform`) for `google` / `google-beta` provider attributes.
- For Workload Identity Federation in CI: configure GitHub OIDC + a `roles/iam.workloadIdentityUser` binding in the target project; do NOT issue or store SA JSON keys.
