---
applyTo: "**/*.tf, **/*.tfvars, **/.terraform.lock.hcl, **/versions.tf"
---

# Terraform conventions

## Tooling

- Pin `terraform` and `tflint` in `mise.toml`.
- Pin `terraform-mcp-server` in `mise.toml` (it backs the `terraform` MCP server registered by this package).
- Coding-agent CLIs are NOT pinned via mise (org-wide convention).

## Module layout

- Per module use the conventional file split: `main.tf`, `variables.tf`, `outputs.tf`, `versions.tf`, `providers.tf`.
- Reusable modules live under `modules/<name>/`. Environment-specific roots that compose modules live under `environments/<env>/` (or `live/<env>/`).
- Pin Terraform core and every provider version in `versions.tf` with a `~>` constraint.
- Commit `.terraform.lock.hcl`. Treat hash diffs in review as load-bearing.

## Formatting & lint

- Run `terraform fmt -recursive` and `terraform validate` before commit.
- Run `tflint --recursive` from the repo root and treat findings as blockers.
- Use the `terraform` MCP server to look up provider attributes and registry modules instead of guessing — do not invent resource arguments.

## State

- Never commit `terraform.tfstate` or `*.tfstate.backup`. Use a remote backend with state locking.
- Never run `terraform apply` against shared environments from a developer machine; route applies through CI with a reviewed plan artefact.

## Secrets

- Do not embed credentials in `.tf` or `.tfvars`. Use environment variables, workload identity, or a secret manager data source.
- `*.auto.tfvars` containing secrets is a bug — gitignore the file or move the value out of repo.
