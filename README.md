# Actions

Reusable GitHub Actions for internal use across repos.

## Actions

### [npm-publish](npm-publish/)

Sets up Node.js and publishes a package to npm.

```yaml
- uses: okkema/actions/npm-publish@v2
  with:
    npm-token: ${{ secrets.NPM_TOKEN }}
```

### [terraform](terraform/)

Initializes, validates, plans, and applies Terraform configuration. Set `upgrade: true` to upgrade providers and modules on init.

```yaml
- uses: okkema/actions/terraform@v2
  with:
    terraform-token: ${{ secrets.TF_API_TOKEN }}
```
