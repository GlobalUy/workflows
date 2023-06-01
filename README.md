# Reusable Workflows

Global reusable workflows.

## Usage

### Build and Push to ECR

```yaml
jobs:
  build_and_push_to_ecr:
    uses: globaluy/workflows/.github/workflows/ecr.yml@1.0.0
    with:
      aws-region: us-west-2
      ecr-repository: repository-name
    secrets: inherit
```
