---
applyTo: "**/*.tf, **/*.tfvars, **/versions.tf, **/providers.tf, **/backend.tf"
---

# Terraform GCP conventions

## Authentication

- Local development: use Application Default Credentials (`gcloud auth application-default login`).
- CI: use GitHub OIDC + Workload Identity Federation. Never commit service-account JSON keys, and never store them in GitHub Actions secrets when WIF is available.

## Backend

- Store state in a GCS bucket with object versioning and uniform bucket-level access enabled.
- One state file per environment / per logical stack. Do not share state across environments or across projects.
- Configure the backend in `backend.tf` with `bucket`, `prefix` (per-stack), and rely on GCS's built-in locking.

## Provider

- Pin both `google` and `google-beta` providers in `versions.tf` with a `~>` constraint.
- Set `project`, `region`, and `zone` at the provider level via variables — never hard-code them.
- Prefer `google-beta` only for resources that have no GA equivalent; document the reason inline.

## Resources & naming

- Resource names follow `<env>-<service>-<purpose>` (lowercase, hyphenated).
- Apply a `terraform = "true"` label (or tag) on every resource that supports labels, plus `env` and `owner`.
- Prefer first-party `terraform-google-modules/*` modules for VPC, Cloud SQL, GKE, IAM, and Cloud Storage rather than hand-rolling.
- Use `google_project_iam_member` (not `_binding` or `_policy`) when granting per-principal roles to avoid silently revoking other bindings.

## Tooling

- Pin `gcloud` in `mise.toml` (see `apm-dependency-terraform-gcp` skill).
- Use the `terraform` MCP server (registered by `apm-plackage/terraform`) for `google` / `google-beta` resource lookups.
