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

### [dotnet-publish](dotnet-publish/)

Builds, tests, packs, and publishes .NET NuGet packages.

```yaml
- uses: okkema/actions/dotnet-publish@v2
  with:
    nuget-token: ${{ secrets.GITHUB_TOKEN }}
```

### [docker-build-push](docker-build-push/)

Builds a multi-platform Docker image and pushes it to a registry.

```yaml
- uses: okkema/actions/docker-build-push@v2
  with:
    registry: ghcr.io
    username: ${{ github.actor }}
    password: ${{ secrets.GITHUB_TOKEN }}
    image: my-image
    context: .
    target: production
```
