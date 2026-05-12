# VPC Networking Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **11 validated build(s)**.

## Overview

This domain captures **11 validated build(s)** in vpc networking engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -s-e-r-i-e-s- -d-o-c-u-m-e-n-t-s- -t-h-e- -d-e-s-i-g-n- -a-n-d- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -o-f- -a- -f-o-u-n-d-a-t-i-o-n-a-l- -A-W-S- -V-i-r-t-u-a-l- -P-r-i-v-a-t-e- -C-l-o-u-d- -a-r-c-h-i-t-e-c-t-u-r-e-.- -T-h-e- -f-o-c-u-s- -i-s- -o-n- -h-o-w- -c-o-r-e- -n-e-t-w-o-r-k-i-n-g- -c-o-n-s-t-r-u-c-t-s- -a-r-e- -c-o-m-p-o-s-e-d- -t-o- -s-u-p-p-o-r-t- -i-s-o-l-a-t-i-o-n-,- -r-o-u-t-i-n-g-,- -a-n-d- -c-o-n-t-r-o-l-l-e-d- -a-c-c-e-s-s- -f-o-r- -c-l-o-u-d- -w-o-r-k-l-o-a-d-s-.--
--
-T-h-e- -w-o-r-k- -c-e-n-t-e-r-s- -o-n- -A-m-a-z-o-n- -V-P-C- -a-s- -t-h-e- -b-a-s-e-l-i-n-e- -p-r-i-m-i-t-i-v-e- -f-o-r- -s-e-c-u-r-e- -a-n-d- -s-c-a-l-a-b-l-e- -n-e-t-w-o-r-k- -d-e-s-i-g-n-.- -T-h-e- -a-r-c-h-i-t-e-c-t-u-r-e- -i-s- -b-u-i-l-t- -i-n-c-r-e-m-e-n-t-a-l-l-y- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -h-o-w- -a-d-d-r-e-s-s- -p-l-a-n-n-i-n-g-,- -s-u-b-n-e-t-s-,- -r-o-u-t-i-n-g-,- -a-n-d- -g-a-t-e-w-a-y-s- -i-n-t-e-r-a-c-t- -t-o- -s-u-p-p-o-r-t- -a-p-p-l-i-c-a-t-i-o-n- -d-e-p-l-o-y-m-e-n-t- -a-n-d- -o-p-e-r-a-t-i-o-n-a-l- -r-e-q-u-i-r-e-m-e-n-t-s-.--
--
-C-l-o-u-d- -n-e-t-w-o-r-k-i-n-g- -i-s- -t-r-e-a-t-e-d- -a-s- -a-n- -e-n-a-b-l-i-n-g- -l-a-y-e-r- -f-o-r- -c-o-m-p-u-t-e- -a-n-d- -p-l-a-t-f-o-r-m- -s-e-r-v-i-c-e-s-.- -T-h-e- -i-n-t-e-n-t- -i-s- -t-o- -s-h-o-w- -h-o-w- -n-e-t-w-o-r-k- -d-e-s-i-g-n- -d-e-c-i-s-i-o-n-s- -i-n-f-l-u-e-n-c-e- -s-e-c-u-r-i-t-y- -p-o-s-t-u-r-e-,- -s-c-a-l-a-b-i-l-i-t-y- -b-o-u-n-d-a-r-i-e-s-,- -a-n-d- -o-p-e-r-a-t-i-o-n-a-l- -c-o-m-p-l-e-x-i-t-y- -i-n- -A-W-S- -e-n-v-i-r-o-n-m-e-n-t-s-.--
--
-T-r-a-d-i-t-i-o-n-a-l- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -m-o-d-e-l-s- -i-m-p-o-s-e- -c-o-s-t-,- -m-a-i-n-t-e-n-a-n-c-e-,- -a-n-d- -s-c-a-l-i-n-g- -c-o-n-s-t-r-a-i-n-t-s-.- -C-l-o-u-d- -n-e-t-w-o-r-k-i-n-g- -a-d-d-r-e-s-s-e-s- -t-h-e-s-e- -c-o-n-s-t-r-a-i-n-t-s- -t-h-r-o-u-g-h- -s-o-f-t-w-a-r-e---d-e-f-i-n-e-d- -i-s-o-l-a-t-i-o-n-,- -e-l-a-s-t-i-c- -c-a-p-a-c-i-t-y-,- -a-n-d- -p-o-l-i-c-y---d-r-i-v-e-n- -c-o-n-t-r-o-l-,- -e-n-a-b-l-i-n-g- -f-a-s-t-e-r- -a-d-a-p-t-a-t-i-o-n- -t-o- -c-h-a-n-g-i-n-g- -w-o-r-k-l-o-a-d- -d-e-m-a-n-d-s-.--
--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -d-o-c-u-m-e-n-t-s- -t-h-e- -c-o-n-s-t-r-u-c-t-i-o-n- -o-f- -a- -f-o-u-n-d-a-t-i-o-n-a-l- -A-m-a-z-o-n- -V-P-C- -t-o- -e-s-t-a-b-l-i-s-h- -c-o-n-t-r-o-l-l-e-d- -n-e-t-w-o-r-k- -i-s-o-l-a-t-i-o-n- -w-i-t-h-i-n- -A-W-S-.- -T-h-e- -f-o-c-u-s- -i-s- -o-n- -d-e-f-i-n-i-n-g- -a-d-d-r-e-s-s- -s-p-a-c-e-,- -r-o-u-t-i-n-g- -b-o-u-n-d-a-r-i-e-s-,- -a-n-d- -c-o-n-n-e-c-t-i-v-i-t-y- -p-r-i-m-i-t-i-v-e-s- -r-e-q-u-i-r-e-d- -f-o-r- -p-r-e-d-i-c-t-a-b-l-e- -a-n-d- -s-e-c-u-r-e- -c-l-o-u-d- -n-e-t-w-o-r-k-i-n-g-.--
--
-
--
-A-m-a-z-o-n- -V-P-C- -i-s- -a- -l-o-g-i-c-a-l-l-y- -i-s-o-l-a-t-e-d- -n-e-t-w-o-r-k-i-n-g- -b-o-u-n-d-a-r-y- -w-i-t-h-i-n- -a-n- -A-W-S- -a-c-c-o-u-n-t-.- -I-t- -d-e-f-i-n-e-s- -I-P- -a-d-d-r-e-s-s- -s-p-a-c-e-,- -r-o-u-t-i-n-g- -d-o-m-a-i-n-s-,- -a-n-d- -t-r-a-f-f-i-c- -c-o-n-t-r-o-l- -p-o-i-n-t-s- -t-h-a-t- -g-o-v-e-r-n- -h-o-w- -r-e-s-o-u-r-c-e-s- -c-o-m-m-u-n-i-c-a-t-e- -i-n-t-e-r-n-a-l-l-y- -a-n-d- -e-x-t-e-r-n-a-l-l-y-.--
--
-T-h-e- -V-P-C- -e-x-i-s-t-s- -t-o- -e-n-f-o-r-c-e- -d-e-t-e-r-m-i-n-i-s-t-i-c- -n-e-t-w-o-r-k- -i-s-o-l-a-t-i-o-n-,- -e-s-t-a-b-l-i-s-h- -s-e-c-u-r-i-t-y- -b-o-u-n-d-a-r-i-e-s-,- -a-n-d- -e-n-a-b-l-e- -c-o-n-t-r-o-l-l-e-d- -c-o-n-n-e-c-t-i-v-i-t-y- -t-o- -d-e-p-e-n-d-e-n-t- -s-e-r-v-i-c-e-s- -w-h-i-l-e- -s-u-p-p-o-r-t-i-n-g- -f-u-t-u-r-e- -s-c-a-l-a-b-i-l-i-t-y-.--
--
-
--
-T-h-e- -p-r-o-j-e-c-t- -s-c-o-p-e- -w-a-s- -i-n-t-e-n-t-i-o-n-a-l-l-y- -l-i-m-i-t-e-d- -t-o- -c-o-r-e- -n-e-t-w-o-r-k-i-n-g- -p-r-i-m-i-t-i-v-e-s-.- -T-h-e- -e-m-p-h-a-s-i-s- -w-a-s- -o-n- -u-n-d-e-r-s-t-a-n-d-i-n-g- -c-o-n-f-i-g-u-r-a-t-i-o-n- -b-o-u-n-d-a-r-i-e-s- -a-n-d- -t-h-e-i-r- -d-o-w-n-s-t-r-e-a-m- -i-m-p-a-c-t- -r-a-t-h-e-r- -t-h-a-n- -d-e-p-l-o-y-i-n-g- -a-p-p-l-i-c-a-t-i-o-n- -w-o-r-k-l-o-a-d-s-.--
--
-T-h-e- -d-e-p-t-h- -o-f- -c-o-n-f-i-g-u-r-a-t-i-o-n- -o-p-t-i-o-n-s- -h-i-g-h-l-i-g-h-t-s- -h-o-w- -r-o-u-t-i-n-g- -t-a-b-l-e-s-,- -s-u-b-n-e-t- -p-l-a-c-e-m-e-n-t-,- -a-n-d- -s-e-c-u-r-i-t-y- -c-o-n-t-r-o-l-s- -d-i-r-e-c-t-l-y- -i-n-f-l-u-e-n-c-e- -r-e-a-c-h-a-b-i-l-i-t-y- -a-n-d- -i-s-o-l-a-t-i-o-n-.- -T-h-e-s-e- -e-l-e-m-e-n-t-s- -m-u-s-t- -b-e- -a-l-i-g-n-e-d- -t-o- -p-r-e-v-e-n-t- -u-n-i-n-t-e-n-d-e-d- -e-x-p-o-s-u-r-e- -o-r- -l-o-s-s- -o-f- -c-o-n-n-e-c-t-i-v-i-t-y-.--
--
------- -
--
-A-m-a-z-o-n- -V-P-C- -i-s- -a- -l-o-g-i-c-a-l-l-y- -i-s-o-l-a-t-e-d- -n-e-t-w-o-r-k- -b-o-u-n-d-a-r-y- -w-i-t-h-i-n- -a-n- -A-W-S- -a-c-c-o-u-n-t-.- -I-t- -d-e-f-i-n-e-s- -I-P- -a-d-d-r-e-s-s- -s-p-a-c-e-,- -s-u-b-n-e-t- -s-e-g-m-e-n-t-a-t-i-o-n-,- -r-o-u-t-i-n-g- -b-e-h-a-v-i-o-r-,- -a-n-d- -t-r-a-f-f-i-c- -c-o-n-t-r-o-l- -p-o-i-n-t-s-.- -T-h-e- -s-e-r-v-i-c-e- -e-x-i-s-t-s- -t-o- -p-r-o-v-i-d-e- -i-s-o-l-a-t-i-o-n-,- -d-e-t-e-r-m-i-n-i-s-t-i-c- -n-e-t-w-o-r-k- -c-o-n-t-r-o-l-,- -a-n-d- -a- -f-o-u-n-d-a-t-i-o-n- -f-o-r- -s-e-c-u-r-e- -c-o-m-m-u-n-i-c-a-t-i-o-n- -b-e-t-w-e-e-n- -c-l-o-u-d- -r-e-s-o-u-r-c-e-s- -a-n-d- -e-x-t-e-r-n-a-l- -n-e-t-w-o-r-k-s-.--
--
-
--
-T-h-e- -V-P-C- -w-a-s- -u-s-e-d- -a-s- -a- -c-o-n-t-r-o-l-l-e-d- -e-n-v-i-r-o-n-m-e-n-t- -t-o- -v-a-l-i-d-a-t-e- -b-a-s-i-c- -n-e-t-w-o-r-k- -r-e-a-c-h-a-b-i-l-i-t-y- -b-e-t-w-e-e-n- -c-o-m-p-u-t-e- -r-e-s-o-u-r-c-e-s- -a-n-d- -e-x-t-e-r-n-a-l- -e-n-d-p-o-i-n-t-s-.- -T-h-e- -f-o-c-u-s- -w-a-s- -o-n- -u-n-d-e-r-s-t-a-n-d-i-n-g- -t-r-a-f-f-i-c- -f-l-o-w-,- -r-o-u-t-i-n-g- -d-e-p-e-n-d-e-n-c-i-e-s-,- -a-n-d- -t-h-e- -i-m-p-a-c-t- -o-f- -s-e-c-u-r-i-t-y- -c-o-n-t-r-o-l-s- -o-n- -c-o-n-n-e-c-t-i-v-i-t-y- -r-a-t-h-e-r- -t-h-a-n- -o-n- -f-e-a-t-u-r-e- -b-r-e-a-d-t-h-.--
--
-
--
-P-r-a-c-t-i-c-a-l- -v-a-l-i-d-a-t-i-o-n- -e-x-p-o-s-e-d- -h-o-w- -s-m-a-l-l- -c-o-n-f-i-g-u-r-a-t-i-o-n- -c-h-o-i-c-e-s- -i-n- -r-o-u-t-i-n-g- -t-a-b-l-e-s- -a-n-d- -s-e-c-u-r-i-t-y- -c-o-n-t-r-o-l-s- -d-i-r-e-c-t-l-y- -a-f-f-e-c-t- -r-e-a-c-h-a-b-i-l-i-t-y-.- -T-h-e- -e-x-e-r-c-i-s-e- -d-e-m-o-n-s-t-r-a-t-e-d- -t-h-a-t- -t-h-e-o-r-e-t-i-c-a-l- -u-n-d-e-r-s-t-a-n-d-i-n-g- -o-f- -V-P-C- -c-o-m-p-o-n-e-n-t-s- -i-s- -i-n-s-u-f-f-i-c-i-e-n-t- -w-i-t-h-o-u-t- -o-b-s-e-r-v-i-n-g- -r-e-a-l- -t-r-a-f-f-i-c- -b-e-h-a-v-i-o-r- -a-n-d- -f-a-i-l-u-r-e- -m-o-d-e-s-.--
--
-
--
-T-h-e- -w-o-r-k- -w-a-s- -s-c-o-p-e-d- -t-o- -a- -s-h-o-r-t- -e-x-e-c-u-t-i-o-n- -w-i-n-d-o-w- -a-n-d- -f-o-c-u-s-e-d- -o-n- -a- -s-i-n-g-l-e- -o-b-j-e-c-t-i-v-e-:- -v-a-l-i-d-a-t-i-n-g- -V-P-C- -c-o-n-n-e-c-t-i-v-i-t-y- -u-s-i-n-g- -E-C-2- -i-n-s-t-a-n-c-e-s-.- -T-i-m-e- -w-a-s- -a-l-l-o-c-a-t-e-d- -t-o- -c-o-n-f-i-g-u-r-a-t-i-o-n- -r-e-v-i-e-w-,- -v-a-l-i-d-a-t-i-o-n-,- -a-n-d- -t-r-o-u-b-l-e-s-h-o-o-t-i-n-g- -r-a-t-h-e-r- -t-h-a-n- -a-u-t-o-m-a-t-i-o-n- -o-r- -o-p-t-i-m-i-z-a-t-i-o-n-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Get Hands on with Cloud Networking!](./diagrams/01-networking-introduction.md)**, AWS · VPC
- **[Build a Virtual Private Cloud](./diagrams/02-subnet-segmentation.md)**, VPC · AWS · IP
- **[Testing VPC Connectivity](./diagrams/03-routing-boundaries.md)**, VPC · AWS · IP · EC2
- **[VPC Traffic Flow and Security](./diagrams/04-network-security-groups.md)**, VPC · AWS · IP · ACLs
- **[VPC Endpoints](./diagrams/05-vpc-endpoints.md)**, VPC · AWS · IP · AWS-managed
- **[Access S3 from a VPC](./diagrams/06-s3-networking.md)**, S3 · VPC · AWS · IP
- **[Launching VPC Resources](./diagrams/07-ec2-networking.md)**, VPC · AWS · IP · ACLs
- **[VPC Peering](./diagrams/08-vpc-peering-advanced.md)**, VPC · AWS · IP · VPCs
- **[Website Delivery with CloudFront](./diagrams/09-cloudfront-integration.md)**, CloudFront · CDN · S3
- **[Creating a Private Subnet](./diagrams/10-isolated-network-test.md)**, VPC · AWS · IP · CIDR
- **[VPC Monitoring with Flow Logs](./diagrams/11-flow-logs-validation.md)**, VPC · AWS · IP · CloudWatch

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Get Hands on with Cloud Networking!](./documents/01-networking-introduction.md)**, AWS · VPC
2. **[Build a Virtual Private Cloud](./documents/02-subnet-segmentation.md)**, VPC · AWS · IP
3. **[Testing VPC Connectivity](./documents/03-routing-boundaries.md)**, VPC · AWS · IP · EC2
4. **[VPC Traffic Flow and Security](./documents/04-network-security-groups.md)**, VPC · AWS · IP · ACLs
5. **[VPC Endpoints](./documents/05-vpc-endpoints.md)**, VPC · AWS · IP · AWS-managed
6. **[Access S3 from a VPC](./documents/06-s3-networking.md)**, S3 · VPC · AWS · IP
7. **[Launching VPC Resources](./documents/07-ec2-networking.md)**, VPC · AWS · IP · ACLs
8. **[VPC Peering](./documents/08-vpc-peering-advanced.md)**, VPC · AWS · IP · VPCs
9. **[Website Delivery with CloudFront](./documents/09-cloudfront-integration.md)**, CloudFront · CDN · S3
10. **[Creating a Private Subnet](./documents/10-isolated-network-test.md)**, VPC · AWS · IP · CIDR
11. **[VPC Monitoring with Flow Logs](./documents/11-flow-logs-validation.md)**, VPC · AWS · IP · CloudWatch

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Get Hands on with Cloud Networking!
- ✅ Build a Virtual Private Cloud
- ✅ Testing VPC Connectivity
- ✅ VPC Traffic Flow and Security
- ✅ VPC Endpoints
- ✅ Access S3 from a VPC
- ✅ Launching VPC Resources
- ✅ VPC Peering
- ✅ Website Delivery with CloudFront
- ✅ Creating a Private Subnet
- ✅ _… and **1 more validated build(s)**, see [`INDEX.md`](./INDEX.md)._
