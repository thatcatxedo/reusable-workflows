# Reusable GitHub Actions Workflows

Public repository containing reusable GitHub Actions workflows for GitOps deployments.

## Available Workflows

### `app-deploy.yml`

A reusable workflow for building Docker images and updating GitOps manifests.

**Usage:**

```yaml
jobs:
  deploy:
    uses: thatcatxedo/reusable-workflows/.github/workflows/app-deploy.yml@main
    with:
      app_name: my-app
      image_registry: ghcr.io/thatcatxedo/my-app
      version_source: config.yaml
      trigger_on: push
    secrets:
      deploy_key: ${{ secrets.DEPLOY_KEY }}
      github_token: ${{ secrets.GITHUB_TOKEN }}
```

**Inputs:**

- `app_name` (required): Application name
- `image_registry` (required): Docker image registry (e.g., `ghcr.io/thatcatxedo/my-app`)
- `version_source` (optional): File to extract version from (default: `config.yaml`)
- `kustomize_path` (optional): Custom Kustomize path (default: `apps/{app_name}/overlays/prod`)
- `trigger_on` (optional): Trigger type: `push`, `merge`, or `both` (default: `push`)

**Secrets:**

- `deploy_key`: SSH deploy key for homelab-deployments repository
- `github_token`: GitHub token with `packages: write` permission

