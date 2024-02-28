# Reusable workflows :sunglasses:

## Usage

### Build and push image to ECR

Build a Docker image and push it to AWS Elastic Container Registry.

```yaml
jobs:
  build_and_push_to_ecr:
    name: Build and push image to ECR
    uses: globaluy/workflows/.github/workflows/ecr.yml@v3.0.0
    with:
      aws-region: us-west-2
      ecr-repository: repository-name
      node-version: 18.x (optional)
    secrets: inherit
```

### Deploy ECR image to AWS

Push revision files to AWS Simple Storage Service and create a deployment into AWS CodeDeploy.
Application must work with Docker.

```yaml
jobs:
  deploy_to_aws:
    name: Deploy ECR image to AWS
    uses: globaluy/workflows/.github/workflows/docker.yml@v3.0.0
    with:
      aws-region: us-west-2
      compose-file-name: production.yml
      s3-bucket-name: bucket-name
      application-name: ec2-on-premises (optional)
      deployment-group-name: deployment-group-name
      appspec-file-name: appspec.yml (optional)
    secrets: inherit
```

### Deploy ECR image to EKS

Deploy an AWS Elastic Container Registry image to AWS Elastic Kubernetes Service.

```yaml
jobs:
  deploy_image_to_eks:
    name: Deploy ECR image to EKS
    uses: globaluy/workflows/.github/workflows/eks.yml@v3.0.0
    with:
      aws-region: us-west-2
      eks-cluster: cluster-name
      deployment-file: deployment.yml (optional)
      service-file: service.yml (optional)
    secrets: inherit
```

### Build and push to S3 + CloudFront invalidation

Build an Angular application and push it to AWS Simple Storage Service.
AWS CloudFront invalidation is optional.

```yaml
jobs:
  build_and_push_to_s3:
    name: Build and push to S3 + CloudFront invalidation
    uses: globaluy/workflows/.github/workflows/s3.yml@v3.0.0
    with:
      aws-region: us-west-2
      s3-bucket-name: bucket-name
      cloud-front-distribution-id: distribution-id (optional)
      environment: production (optional)
      node-version: 18.x (optional)
    secrets: inherit
```

### SonarQube scan

Generate and upload a code coverage report to SonarQube.

```yaml
jobs:
  sonarqube_scan:
    name: SonarQube scan
    uses: globaluy/workflows/.github/workflows/sonar.yml@v3.0.0
    with:
      node-version: 18.x (optional)
    secrets: inherit
```

## Extra

### Deploy ECR image to ECS

Deploy an AWS Elastic Container Registry image to AWS Elastic Container Service.

```yaml
jobs:
  deploy_image_to_ecs:
    name: Deploy ECR image to ECS
    uses: globaluy/workflows/.github/workflows/ecs.yml@v3.0.0
    with:
      aws-region: us-west-2
      task-definition: task-definition
      cluster: cluster
      service: service
      image-tag: image-tag
    secrets: inherit
```

### Build and deploy to AWS

Build a Typescript application, push files to AWS Simple Storage Service and create a deployment into AWS CodeDeploy.

```yaml
jobs:
  build_and_deploy_to_aws:
    name: Build and deploy to AWS
    uses: globaluy/workflows/.github/workflows/deploy.yml@v3.0.0
    with:
      aws-region: us-west-2
      s3-bucket-name: bucket-name
      application-name: ec2-on-premises (optional)
      deployment-group-name: deployment-group-name
      appspec-file-name: appspec.yml (optional)
      node-version: 18.x (optional)
    secrets: inherit
```
