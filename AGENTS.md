# AGENTS.md

## Versioning

This repo uses [semantic versioning](https://semver.org/). Consumers should pin to a major version tag (`@v1`, `@v2`) to receive compatible updates.

### Releasing

1. Merge all changes to `main`
2. Create a version tag:
   ```bash
   git tag -a v1.2.3 -m "v1.2.3"
   git push origin v1.2.3
   ```
3. Create a GitHub release:
   ```bash
   gh release create v1.2.3 --title "v1.2.3" --notes "Description of changes."
   ```
4. Update the major version tag to point to the latest commit:
   ```bash
   git tag -fa v1 -m "Update v1 tag"
   git push origin v1 --force
   ```

### Tag reference

| Tag | Purpose |
|-----|---------|
| `v1.2.3` | Exact version (immutable) |
| `v1` | Latest release in major version (mutable) |
| `main` | Latest development (unstable) |
