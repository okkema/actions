# Build Test and Publish .NET Packages

Builds, tests, packs, and publishes .NET NuGet packages in a single step.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `dotnet-version` | No | `8.x` | .NET SDK version to use |
| `configuration` | No | `Release` | Build configuration |
| `package-source` | No | `https://nuget.pkg.github.com/okkema/index.json` | NuGet source URL to push packages to |
| `nuget-token` | Yes | — | NuGet authentication token for the package source |

## Usage

```yaml
- uses: okkema/actions/dotnet-publish@v2
  with:
    nuget-token: ${{ secrets.GITHUB_TOKEN }}
```

## Secrets

The `nuget-token` authenticates against the package source. For GitHub Packages, pass `${{ secrets.GITHUB_TOKEN }}`.
