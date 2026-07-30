# Deploy Terraform

Initializes, validates, and applies Terraform configuration in a single step.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `working-directory` | No | `terraform` | Directory containing Terraform configuration files |
| `terraform-version` | No | latest | Terraform version to use |
| `terraform-token` | Yes | — | Terraform Cloud / Enterprise API token |

## Usage

```yaml
- uses: okkema/actions/terraform@main
  with:
    terraform-token: ${{ secrets.TF_API_TOKEN }}
```

With a specific directory and version:

```yaml
- uses: okkema/actions/terraform@main
  with:
    working-directory: 'infra'
    terraform-version: '1.5.0'
    terraform-token: ${{ secrets.TF_API_TOKEN }}
```

## Secrets

Create a `TF_API_TOKEN` secret in your repository settings with a Terraform Cloud / Enterprise API token.
