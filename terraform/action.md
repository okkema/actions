# Deploy Terraform

Initializes, validates, plans, and applies Terraform configuration in a single step. Set `upgrade: true` to upgrade providers and modules on init.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `working-directory` | No | `terraform` | Directory containing Terraform configuration files |
| `terraform-version` | No | latest | Terraform version to use |
| `terraform-token` | Yes | — | Terraform Cloud / Enterprise API token |
| `upgrade` | No | `false` | Upgrade Terraform providers and modules on init |

## Usage

```yaml
- uses: okkema/actions/terraform@v2
  with:
    terraform-token: ${{ secrets.TF_API_TOKEN }}
```

With a specific directory and version:

```yaml
- uses: okkema/actions/terraform@v2
  with:
    working-directory: 'infra'
    terraform-version: '1.5.0'
    upgrade: true
    terraform-token: ${{ secrets.TF_API_TOKEN }}
```

## Secrets

Create a `TF_API_TOKEN` secret in your repository settings with a Terraform Cloud / Enterprise API token.
