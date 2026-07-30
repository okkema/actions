# Setup Node and Publish to npm

Sets up Node.js and publishes a package to npm in a single step.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `node-version` | No | `20` | Node.js version |
| `node-version-file` | No | — | Path to node version file (e.g. `.nvmrc`) |
| `registry-url` | No | `https://registry.npmjs.org` | npm registry URL |
| `npm-token` | No | — | npm authentication token (omit to use OIDC trusted publishing) |
| `scope` | No | — | npm scope (e.g. `@myorg`) |
| `version` | No | — | Package version to set before publishing (e.g. `v1.2.3` or `1.2.3`) |
| `commit` | No | `false` | Commit version change back to the repo after publishing |
| `access` | No | — | npm access level (e.g. `public` for scoped packages) |

## Usage

```yaml
- uses: okkema/actions/npm-publish@v2
  with:
    npm-token: ${{ secrets.NPM_TOKEN }}
```

With a specific Node version:

```yaml
- uses: okkema/actions/npm-publish@v2
  with:
    node-version: '18'
    npm-token: ${{ secrets.NPM_TOKEN }}
```

With a scope:

```yaml
- uses: okkema/actions/npm-publish@v2
  with:
    scope: '@myorg'
    npm-token: ${{ secrets.NPM_TOKEN }}
```

With version bump and auto-commit:

```yaml
- uses: okkema/actions/npm-publish@v2
  with:
    version: '1.2.3'
    commit: 'true'
    npm-token: ${{ secrets.NPM_TOKEN }}
```

With `.nvmrc` and public access for scoped packages:

```yaml
- uses: okkema/actions/npm-publish@v2
  with:
    node-version-file: '.nvmrc'
    access: 'public'
    npm-token: ${{ secrets.NPM_TOKEN }}
```

## Trusted Publishing (OIDC)

This action supports npm's [trusted publishing](https://docs.npmjs.com/trusted-publishers) via OIDC. No token needed — omit `npm-token` and add `id-token: write` to your workflow permissions:

```yaml
name: Publish

on:
  release:
    types: [published]

permissions:
  id-token: write
  contents: write

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: okkema/actions/npm-publish@v2
        with:
          version: ${{ github.event.release.tag_name }}
          commit: 'true'
          access: 'public'
          node-version-file: '.nvmrc'
```

## Secrets

Create an `NPM_TOKEN` secret in your repository settings with a npm access token that has publish permissions.
