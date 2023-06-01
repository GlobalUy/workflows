# Reusable Workflows

## Usage

### Build and Push to ECR

Builds a Docker image and push it to AWS Elastic Container Registry.

```yaml
jobs:
  build_and_push_to_ecr:
    uses: globaluy/workflows/.github/workflows/ecr.yml@v1.0.0
    with:
      aws-region: us-west-2
      ecr-repository: repository-name
    secrets: inherit
```

### SonarQube Scan

Generates a code coverage report and push it to SonarQube.

```yaml
jobs:
  sonarqube_scan:
    uses: globaluy/workflows/.github/workflows/sonar.yml@v1.0.0
    secrets: inherit
```
