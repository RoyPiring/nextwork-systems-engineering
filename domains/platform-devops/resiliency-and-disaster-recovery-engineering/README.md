# Resiliency and Disaster Recovery Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **3 validated build(s)**.

## Overview

This domain captures **3 validated build(s)** in resiliency and disaster recovery engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

This project shows how to deploy the same application in multiple AWS regions to improve availability and reduce the impact of regional outages. This project demonstrates how to build automatic, near-instant failover between regions using Amazon CloudFront origin groups. This project demonstrates how to build a multi-cloud disaster recovery setup using Pulumi to manage infrastructure across AWS and GCP.

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Build Multi-Region Apps on AWS](./diagrams/01-ai-disaster-recovery-multiregion.md)** — Multi-Region · AWS · GitHub-based · GitHub
- **[Build Instant Failover with CloudFront Origin Groups](./diagrams/02-ai-disaster-recovery-failover.md)** — CloudFront · AWS · CloudWatch
- **[Multi-Cloud Disaster Recovery with Pulumi](./diagrams/03-ai-disaster-recovery-pulumi.md)** — Multi-Cloud · Pulumi · AWS · GCP

## Implementation

**Build sequence.** Ordered builds — each step is a complete system the next builds on:

1. **[Build Multi-Region Apps on AWS](./documents/01-ai-disaster-recovery-multiregion.md)** — Multi-Region · AWS · GitHub-based · GitHub
2. **[Build Instant Failover with CloudFront Origin Groups](./documents/02-ai-disaster-recovery-failover.md)** — CloudFront · AWS · CloudWatch
3. **[Multi-Cloud Disaster Recovery with Pulumi](./documents/03-ai-disaster-recovery-pulumi.md)** — Multi-Cloud · Pulumi · AWS · GCP

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Build Multi-Region Apps on AWS
- ✅ Build Instant Failover with CloudFront Origin Groups
- ✅ Multi-Cloud Disaster Recovery with Pulumi
