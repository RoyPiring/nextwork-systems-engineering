# Application Architecture Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **9 validated build(s)**.

## Overview

This domain captures **9 validated build(s)** in application architecture engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -s-e-r-v-e-r-l-e-s-s- -r-e-a-d- -p-a-t-h- -f-o-r- -u-s-e-r- -d-a-t-a- -s-t-o-r-e-d- -i-n- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B-.- -A- -L-a-m-b-d-a- -f-u-n-c-t-i-o-n- -r-e-t-r-i-e-v-e-s- -a- -s-i-n-g-l-e- -i-t-e-m- -b-y- -p-a-r-t-i-t-i-o-n- -k-e-y- -a-n-d- -r-e-t-u-r-n-s- -a- -s-t-r-u-c-t-u-r-e-d- -J-S-O-N- -r-e-s-p-o-n-s-e-.- -T-h-e- -d-e-s-i-g-n- -v-a-l-i-d-a-t-e-s- -b-a-s-i-c- -d-a-t-a- -a-c-c-e-s-s- -p-a-t-t-e-r-n-s-,- -I-A-M- -s-c-o-p-i-n-g-,- -a-n-d- -f-u-n-c-t-i-o-n- -t-e-s-t-i-n-g- -w-i-t-h-o-u-t- -i-n-t-r-o-d-u-c-i-n-g- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -o-r-c-h-e-s-t-r-a-t-i-o-n- -o-r- -A-P-I- -g-a-t-e-w-a-y-s-.- --
--
-T-h-i-s- -p-r-o-j-e-c-t- -e-x-i-s-t-s- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -h-o-w- -a- -L-a-m-b-d-a- -e-x-e-c-u-t-i-o-n- -r-o-l-e-,- -D-y-n-a-m-o-D-B- -a-c-c-e-s-s- -p-a-t-t-e-r-n-s-,- -a-n-d- -S-D-K- -u-s-a-g-e- -i-n-t-e-r-a-c-t- -a-t- -r-u-n-t-i-m-e-.- -I-t- -f-o-c-u-s-e-s- -o-n- -c-o-r-r-e-c-t-n-e-s-s- -o-f- -p-e-r-m-i-s-s-i-o-n-s-,- -r-e-q-u-e-s-t- -h-a-n-d-l-i-n-g-,- -a-n-d- -r-e-s-p-o-n-s-e- -b-e-h-a-v-i-o-r- -r-a-t-h-e-r- -t-h-a-n- -s-c-a-l-e- -o-r- -p-r-o-d-u-c-t-i-o-n- -i-n-t-e-g-r-a-t-i-o-n-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -u-s-e-s- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -f-o-r- -d-a-t-a- -s-t-o-r-a-g-e- -a-n-d- -A-W-S- -L-a-m-b-d-a- -f-o-r- -c-o-m-p-u-t-e-.- -C-o-r-e- -c-o-n-c-e-p-t-s- -i-n-c-l-u-d-e- -p-a-r-t-i-t-i-o-n---k-e-y---b-a-s-e-d- -a-c-c-e-s-s-,- -L-a-m-b-d-a- -e-x-e-c-u-t-i-o-n- -r-o-l-e-s-,- -I-A-M- -p-o-l-i-c-y- -s-c-o-p-i-n-g-,- -a-n-d- -S-D-K---b-a-s-e-d- -s-e-r-v-i-c-e- -c-a-l-l-s-.- --
--
-
--
-T-h-e- -w-o-r-k- -s-u-r-f-a-c-e-d- -c-o-m-m-o-n- -f-a-i-l-u-r-e- -m-o-d-e-s- -w-h-e-n- -S-D-K- -c-a-l-l-s- -a-r-e- -u-n-d-e-r---s-p-e-c-i-f-i-e-d-,- -p-a-r-t-i-c-u-l-a-r-l-y- -a-r-o-u-n-d- -k-e-y- -c-o-n-d-i-t-i-o-n-s- -a-n-d- -r-e-q-u-e-s-t- -p-a-r-a-m-e-t-e-r-s-.- -T-h-e- -p-r-i-m-a-r-y- -t-e-c-h-n-i-c-a-l- -c-o-n-s-t-r-a-i-n-t- -w-a-s- -e-n-s-u-r-i-n-g- -t-h-e- -f-u-n-c-t-i-o-n- -r-e-t-u-r-n-e-d- -d-e-t-e-r-m-i-n-i-s-t-i-c- -r-e-s-u-l-t-s- -o-n-l-y- -w-h-e-n- -p-e-r-m-i-s-s-i-o-n-s- -a-n-d- -q-u-e-r-y- -p-a-r-a-m-e-t-e-r-s- -w-e-r-e- -c-o-r-r-e-c-t-l-y- -a-l-i-g-n-e-d-.--
--
-T-h-e- -p-r-o-j-e-c-t- -w-a-s- -s-e-l-e-c-t-e-d- -t-o- -r-e-i-n-f-o-r-c-e- -s-e-r-v-e-r-l-e-s-s- -r-e-a-d- -p-a-t-t-e-r-n-s- -a-n-d- -I-A-M- -b-o-u-n-d-a-r-i-e-s- -i-n- -i-s-o-l-a-t-i-o-n-.- -I-t- -i-n-t-e-n-t-i-o-n-a-l-l-y- -a-v-o-i-d-s- -b-r-o-a-d-e-r- -s-y-s-t-e-m- -c-o-n-c-e-r-n-s- -s-u-c-h- -a-s- -A-P-I-s-,- -a-u-t-h-e-n-t-i-c-a-t-i-o-n- -l-a-y-e-r-s-,- -o-r- -e-v-e-n-t---d-r-i-v-e-n- -f-a-n-o-u-t- -t-o- -k-e-e-p- -t-h-e- -s-c-o-p-e- -f-o-c-u-s-e-d- -o-n- -d-a-t-a- -a-c-c-e-s-s- -c-o-r-r-e-c-t-n-e-s-s-.- --
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -s-e-r-v-e-r-l-e-s-s- -R-E-S-T- -A-P-I- -u-s-i-n-g- -A-W-S- -L-a-m-b-d-a- -a-n-d- -A-m-a-z-o-n- -A-P-I- -G-a-t-e-w-a-y-.- -T-h-e- -s-y-s-t-e-m- -e-x-p-o-s-e-s- -a-n- -H-T-T-P- -i-n-t-e-r-f-a-c-e- -t-h-a-t- -i-n-v-o-k-e-s- -L-a-m-b-d-a- -f-u-n-c-t-i-o-n-s- -o-n- -d-e-m-a-n-d- -a-n-d- -i-n-t-e-g-r-a-t-e-s- -w-i-t-h- -D-y-n-a-m-o-D-B- -f-o-r- -d-a-t-a- -r-e-t-r-i-e-v-a-l-.- -T-h-e- -o-b-j-e-c-t-i-v-e- -i-s- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -a-n- -e-v-e-n-t---d-r-i-v-e-n- -A-P-I- -a-r-c-h-i-t-e-c-t-u-r-e- -t-h-a-t- -m-i-n-i-m-i-z-e-s- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -m-a-n-a-g-e-m-e-n-t- -w-h-i-l-e- -s-u-p-p-o-r-t-i-n-g- -h-o-r-i-z-o-n-t-a-l- -s-c-a-l-a-b-i-l-i-t-y- -a-n-d- -u-s-a-g-e---b-a-s-e-d- -c-o-s-t- -c-o-n-t-r-o-l-.--
--
-
--
-T-h-e- -s-y-s-t-e-m- -i-s- -c-o-m-p-o-s-e-d- -o-f- -A-W-S- -L-a-m-b-d-a- -f-o-r- -c-o-m-p-u-t-e- -e-x-e-c-u-t-i-o-n-,- -A-m-a-z-o-n- -A-P-I- -G-a-t-e-w-a-y- -f-o-r- -r-e-q-u-e-s-t- -r-o-u-t-i-n-g- -a-n-d- -A-P-I- -m-a-n-a-g-e-m-e-n-t-,- -a-n-d- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -f-o-r- -p-e-r-s-i-s-t-e-n-t- -s-t-o-r-a-g-e-.- -T-h-e- -a-r-c-h-i-t-e-c-t-u-r-e- -r-e-l-i-e-s- -o-n- -s-e-r-v-e-r-l-e-s-s- -e-x-e-c-u-t-i-o-n-,- -R-E-S-T---b-a-s-e-d- -r-e-s-o-u-r-c-e- -m-o-d-e-l-i-n-g-,- -a-n-d- -e-v-e-n-t---d-r-i-v-e-n- -i-n-v-o-c-a-t-i-o-n-.- -D-e-p-l-o-y-m-e-n-t- -s-t-a-g-e-s- -a-r-e- -u-s-e-d- -t-o- -i-s-o-l-a-t-e- -e-n-v-i-r-o-n-m-e-n-t-s- -a-n-d- -m-a-n-a-g-e- -A-P-I- -l-i-f-e-c-y-c-l-e- -a-n-d- -e-x-p-o-s-u-r-e-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -f-o-c-u-s-e-d- -o-n- -i-n-t-e-g-r-a-t-i-n-g- -A-P-I- -G-a-t-e-w-a-y- -w-i-t-h- -D-y-n-a-m-o-D-B- -t-h-r-o-u-g-h- -L-a-m-b-d-a- -w-h-i-l-e- -m-a-i-n-t-a-i-n-i-n-g- -c-o-r-r-e-c-t- -r-e-q-u-e-s-t- -h-a-n-d-l-i-n-g- -a-n-d- -a-c-c-e-s-s- -c-o-n-f-i-g-u-r-a-t-i-o-n-.- -T-h-e- -p-r-i-m-a-r-y- -e-n-g-i-n-e-e-r-i-n-g- -c-o-n-c-e-r-n- -w-a-s- -e-n-s-u-r-i-n-g- -t-h-e- -A-P-I- -G-a-t-e-w-a-y- -m-e-t-h-o-d- -i-n-t-e-g-r-a-t-i-o-n- -a-n-d- -L-a-m-b-d-a- -e-x-e-c-u-t-i-o-n- -r-o-l-e- -p-e-r-m-i-s-s-i-o-n-s- -a-l-i-g-n-e-d- -w-i-t-h- -D-y-n-a-m-o-D-B- -a-c-c-e-s-s- -r-e-q-u-i-r-e-m-e-n-t-s-.- --
--
-T-h-e- -c-o-m-p-l-e-t-e-d- -s-y-s-t-e-m- -v-a-l-i-d-a-t-e-s- -t-h-a-t- -t-h-e- -A-P-I- -f-u-n-c-t-i-o-n-s- -c-o-r-r-e-c-t-l-y- -w-i-t-h-o-u-t- -p-r-e---p-r-o-v-i-s-i-o-n-e-d- -s-e-r-v-e-r-s- -a-n-d- -s-c-a-l-e-s- -b-a-s-e-d- -o-n- -r-e-q-u-e-s-t- -v-o-l-u-m-e-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -b-a-s-i-c- -t-h-r-e-e---t-i-e-r- -w-e-b- -a-p-p-l-i-c-a-t-i-o-n- -o-n- -A-W-S- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -s-e-p-a-r-a-t-i-o-n- -o-f- -c-o-n-c-e-r-n-s- -a-c-r-o-s-s- -p-r-e-s-e-n-t-a-t-i-o-n-,- -l-o-g-i-c-,- -a-n-d- -d-a-t-a- -t-i-e-r-s- -u-s-i-n-g- -m-a-n-a-g-e-d- -s-e-r-v-i-c-e-s-.--
--
-T-h-e- -s-y-s-t-e-m- -u-s-e-s- -S-3- -a-n-d- -C-l-o-u-d-F-r-o-n-t- -f-o-r- -s-t-a-t-i-c- -c-o-n-t-e-n-t- -d-e-l-i-v-e-r-y-,- -A-P-I- -G-a-t-e-w-a-y- -a-n-d- -L-a-m-b-d-a- -f-o-r- -r-e-q-u-e-s-t- -h-a-n-d-l-i-n-g-,- -a-n-d- -D-y-n-a-m-o-D-B- -f-o-r- -d-a-t-a- -p-e-r-s-i-s-t-e-n-c-e-.- -T-h-e- -t-i-e-r-s- -a-r-e- -i-n-t-e-g-r-a-t-e-d- -t-h-r-o-u-g-h- -H-T-T-P---b-a-s-e-d- -A-P-I-s-.--
--
-
--
-A-m-a-z-o-n- -S-3- -p-r-o-v-i-d-e-s- -o-b-j-e-c-t- -s-t-o-r-a-g-e- -f-o-r- -s-t-a-t-i-c- -a-s-s-e-t-s-.- -A-m-a-z-o-n- -C-l-o-u-d-F-r-o-n-t- -d-i-s-t-r-i-b-u-t-e-s- -t-h-o-s-e- -a-s-s-e-t-s- -g-l-o-b-a-l-l-y- -w-i-t-h- -e-d-g-e- -c-a-c-h-i-n-g-.- -A-W-S- -L-a-m-b-d-a- -e-x-e-c-u-t-e-s- -r-e-q-u-e-s-t- -l-o-g-i-c- -w-i-t-h-o-u-t- -s-e-r-v-e-r- -m-a-n-a-g-e-m-e-n-t-.- -A-m-a-z-o-n- -A-P-I- -G-a-t-e-w-a-y- -e-x-p-o-s-e-s- -R-E-S-T- -e-n-d-p-o-i-n-t-s-.- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -s-t-o-r-e-s- -a-p-p-l-i-c-a-t-i-o-n- -d-a-t-a- -w-i-t-h- -l-o-w---l-a-t-e-n-c-y- -a-c-c-e-s-s-.--
--
-T-h-e- -c-o-r-e- -c-o-n-c-e-p-t-s- -e-x-e-r-c-i-s-e-d- -i-n-c-l-u-d-e- -s-e-r-v-e-r-l-e-s-s- -c-o-m-p-u-t-e-,- -m-a-n-a-g-e-d- -A-P-I- -r-o-u-t-i-n-g-,- -N-o-S-Q-L- -d-a-t-a- -m-o-d-e-l-i-n-g-,- -s-t-a-t-i-c- -c-o-n-t-e-n-t- -d-e-l-i-v-e-r-y-,- -a-n-d- -s-e-r-v-i-c-e---t-o---s-e-r-v-i-c-e- -i-n-t-e-g-r-a-t-i-o-n-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -f-o-c-u-s-e-d- -o-n- -v-a-l-i-d-a-t-i-n-g- -s-e-r-v-i-c-e- -i-n-t-e-g-r-a-t-i-o-n- -r-a-t-h-e-r- -t-h-a-n- -p-r-o-d-u-c-t-i-o-n- -h-a-r-d-e-n-i-n-g-.- -T-h-e- -p-r-i-m-a-r-y- -c-o-m-p-l-e-x-i-t-y- -i-n-v-o-l-v-e-d- -c-r-o-s-s---o-r-i-g-i-n- -r-e-q-u-e-s-t- -h-a-n-d-l-i-n-g- -b-e-t-w-e-e-n- -C-l-o-u-d-F-r-o-n-t---h-o-s-t-e-d- -a-s-s-e-t-s- -a-n-d- -A-P-I- -G-a-t-e-w-a-y- -e-n-d-p-o-i-n-t-s-.--
--
-T-h-e- -o-u-t-c-o-m-e- -c-o-n-f-i-r-m-s- -t-h-a-t- -t-h-e- -t-h-r-e-e- -t-i-e-r-s- -c-o-m-m-u-n-i-c-a-t-e- -c-o-r-r-e-c-t-l-y- -a-n-d- -r-e-t-u-r-n- -d-a-t-a- -e-n-d- -t-o- -e-n-d- -u-n-d-e-r- -e-x-p-e-c-t-e-d- -r-e-q-u-e-s-t- -p-a-t-h-s-.--
--
-------

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
