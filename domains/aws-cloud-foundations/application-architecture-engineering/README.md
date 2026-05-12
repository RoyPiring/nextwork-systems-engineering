# Application Architecture Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **9 validated build(s)**.

## Overview

This domain captures **9 validated build(s)** in application architecture engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

This project implements a serverless read path for user data stored in Amazon DynamoDB. This project implements a serverless REST API using AWS Lambda and Amazon API Gateway. This project implements a basic three-tier web application on AWS to demonstrate separation of concerns across presentation, logic, and data tiers using managed services.

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Fetch Data with AWS Lambda](./diagrams/01-serverless-foundation-lambda.md)**, AWS · Lambda · DynamoDB · JSON
- **[APIs with Lambda + API Gateway](./diagrams/02-api-layer-gateway-lambda.md)**, APIs · Lambda · API · REST
- **[Build a Three-Tier Web App](./diagrams/03-complete-three-tier-application.md)**, Three-Tier · AWS · S3 · CloudFront
- **[Deploy an App with Docker](./diagrams/04-container-deployment-elastic-beanstalk.md)**, Docker · AWS · CMD · ENTRYPOINT
- **[Deploy an App Across Accounts](./diagrams/05-container-registry-ecr.md)**, AWS · ECR · IAM · Docker
- **[Launch a Kubernetes Cluster](./diagrams/06-kubernetes-cluster-eks-part1.md)**, EKS · AWS · IAM
- **[Set Up Kubernetes Deployment](./diagrams/07-kubernetes-deployment-eks-part2.md)**, EKS · Docker · ECR
- **[Create Kubernetes Manifests](./diagrams/08-kubernetes-scaling-eks-part3.md)**, EKS · AWS · CLI · Docker
- **[Deploy Backend with Kubernetes](./diagrams/09-kubernetes-advanced-eks-part4.md)**, EKS · AWS-managed · ECR · EC2

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Fetch Data with AWS Lambda](./documents/01-serverless-foundation-lambda.md)**, AWS · Lambda · DynamoDB · JSON
2. **[APIs with Lambda + API Gateway](./documents/02-api-layer-gateway-lambda.md)**, APIs · Lambda · API · REST
3. **[Build a Three-Tier Web App](./documents/03-complete-three-tier-application.md)**, Three-Tier · AWS · S3 · CloudFront
4. **[Deploy an App with Docker](./documents/04-container-deployment-elastic-beanstalk.md)**, Docker · AWS · CMD · ENTRYPOINT
5. **[Deploy an App Across Accounts](./documents/05-container-registry-ecr.md)**, AWS · ECR · IAM · Docker
6. **[Launch a Kubernetes Cluster](./documents/06-kubernetes-cluster-eks-part1.md)**, EKS · AWS · IAM
7. **[Set Up Kubernetes Deployment](./documents/07-kubernetes-deployment-eks-part2.md)**, EKS · Docker · ECR
8. **[Create Kubernetes Manifests](./documents/08-kubernetes-scaling-eks-part3.md)**, EKS · AWS · CLI · Docker
9. **[Deploy Backend with Kubernetes](./documents/09-kubernetes-advanced-eks-part4.md)**, EKS · AWS-managed · ECR · EC2

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Fetch Data with AWS Lambda
- ✅ APIs with Lambda + API Gateway
- ✅ Build a Three-Tier Web App
- ✅ Deploy an App with Docker
- ✅ Deploy an App Across Accounts
- ✅ Launch a Kubernetes Cluster
- ✅ Set Up Kubernetes Deployment
- ✅ Create Kubernetes Manifests
- ✅ Deploy Backend with Kubernetes
