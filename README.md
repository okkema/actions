# Actions

Reusable GitHub Actions for internal use across repos.

## Actions

### [npm-publish](actions/npm-publish/)

Sets up Node.js and publishes a package to npm.

```yaml
- uses: okkema/actions/npm-publish@main
  with:
    npm-token: ${{ secrets.NPM_TOKEN }}
```
