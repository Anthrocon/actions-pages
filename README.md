# actions-pages

[![Unit test](https://github.com/Anthrocon/actions-pages/actions/workflows/test.yaml/badge.svg)](https://github.com/Anthrocon/actions-pages/actions/workflows/test.yaml)

Action generates Hugo production and preview pages, then deploys to Cloudflare Workers.

## Scope

Intended for Anthrocon internal use, however may be useful elsewhere.

## Usage

Create a workflow in `.github/workflows` with:

```yaml
on:
  push:

jobs:
  call:
    uses: Anthrocon/actions-pages/.github/workflows/deploy.yaml@v1
    with:
      cloudflare-project: NAME

    secrets:
      CLOUDFLARE_ACCOUNT_ID: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
      CLOUDFLARE_API_TOKEN: ${{ secrets.CLOUDFLARE_API_TOKEN }}
```

If no existing Cloudflare Workers project is specified, action will build without deploy.

Authentication is stored in repository secrets. Further information can be [found in Cloudflare Docs](https://developers.cloudflare.com/workers/ci-cd/external-cicd/github-actions/#api-token).

### Specify Hugo version

Recommended. Overrides action default, and prevents unexpected changes.

```yaml
uses: Anthrocon/actions-pages/.github/workflows/deploy.yaml@v1
with:
  hugo-version: 0.164.0
```

### Disable cache

By default, action caches Hugo package, build cache, and resources. Cache can be disabled for testing.

```yaml
uses: Anthrocon/actions-pages/.github/workflows/deploy.yaml@v1
with:
  cache: false
```

## License

No license implied. All rights reserved copyright Anthrocon, Inc., 2026.
