# GitHub Action Reusable workflows

## Build Container and Push to AWS ECR (multi-platform)

```yaml
# example
jobs:
    uses: fdkevin0/workflows/.github/workflows/aws-build-container.yml@main
    with:
      container-name: YOUR_CONTAINER_NAME
      aws-oidc-role: arn:aws:iam::AWS_ACCOUNT_ID:role/AWS_OIDC_ROLE_NAME
      aws-region: AWS_REGION
      tags: |
        type=schedule
        type=ref,event=branch
        type=ref,event=pr
        type=semver,pattern={{version}}
        type=semver,pattern={{major}}.{{minor}}
        type=semver,pattern={{major}}
        type=sha
      platforms:
        - linux/amd64
        - linux/arm64
```