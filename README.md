# Reusable Workflows

## Usage

### Build and Push to ECR

Builds a Docker image and push it to AWS Elastic Container Registry.

```yaml
jobs:
  build_and_push_to_ecr:
    name: Build and Push to ECR
    uses: globaluy/workflows/.github/workflows/ecr.yml@v1.0.0
    with:
      aws-region: us-west-2
      ecr-repository: repository-name
    secrets: inherit
```

### Build and Push to S3

Builds an Angular application and push it to AWS Simple Storage Service.
AWS CloudFront invalidation is optional.

```yaml
jobs:
  build_and_push_to_s3:
    name: Build and Push to S3
    uses: globaluy/workflows/.github/workflows/s3.yml@v1.0.0
    with:
      aws-region: us-west-2
      s3-bucket-name: bucket-name
      cloud-front-distribution-id: distribution-id (optional)
    secrets: inherit
```

### Deploy ECR image to ECS

Deploy an AWS Elastic Container Registry image to AWS Elastic Container Service.

```yaml
jobs:
  deploy_image_to_ecs:
    name: Deploy ECR image to ECS
    uses: globaluy/workflows/.github/workflows/ecs.yml@v1.0.0
    with:
      aws-region: us-west-2
      task-definition: task-definition
      cluster: cluster
      service: service
      image-tag: image-tag
    secrets: inherit
```

### SonarQube Scan

Generates a code coverage report and push it to SonarQube.

```yaml
jobs:
  sonarqube_scan:
    name: SonarQube scan
    uses: globaluy/workflows/.github/workflows/sonar.yml@v1.0.0
    secrets: inherit
```
