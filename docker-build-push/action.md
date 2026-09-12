# Docker Build and Push

Builds a multi-platform Docker image and pushes it to a registry in a single step.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `registry` | Yes | — | Docker registry to push to |
| `username` | Yes | — | Registry username |
| `password` | Yes | — | Registry password or token |
| `image` | Yes | — | Docker image name |
| `context` | Yes | — | Docker build context |
| `target` | Yes | — | Docker build target |
| `secrets` | No | — | List of secrets environment variables |

## Usage

```yaml
- uses: okkema/actions/docker-build-push@v1
  with:
    registry: ghcr.io
    username: ${{ github.actor }}
    password: ${{ secrets.GITHUB_TOKEN }}
    image: my-image
    context: .
    target: production
```

## Notes

Builds for `amd64`, `linux/arm64`, and `linux/arm/v7` platforms. The `secrets` input accepts the Docker Buildx secret syntax, e.g. `GIT_AUTH_TOKEN=...,SOME_SECRET=...`.