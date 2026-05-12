# Security and Compliance Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **5 validated build(s)**.

## Overview

This domain captures **5 validated build(s)** in security and compliance engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

This project configures AWS Identity and Access Management to control access to AWS resources. This project demonstrates the security implications of embedding cloud credentials in application code and the corrective use of AWS Secrets Manager to externalize and control sensitive configuration. This project implements encryption at rest for data stored in Amazon DynamoDB using AWS Key Management Service.

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Cloud Security with AWS IAM](./diagrams/01-iam-least-privilege.md)**, AWS · IAM · EC2
- **[Secure Secrets with Secrets Manager](./diagrams/02-secrets-management.md)**, AWS · IAM · GitHub
- **[Encrypt Data with AWS KMS](./diagrams/03-boundary-enforcement.md)**, AWS · KMS · DynamoDB · IAM
- **[Build a Security Monitoring System](./diagrams/04-compliance-checklist.md)**, AWS · API · CloudTrail · CloudWatch
- **[Threat Detection with GuardDuty](./diagrams/05-evidence-collection.md)**, GuardDuty · SQL · API · AWS

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Cloud Security with AWS IAM](./documents/01-iam-least-privilege.md)**, AWS · IAM · EC2
2. **[Secure Secrets with Secrets Manager](./documents/02-secrets-management.md)**, AWS · IAM · GitHub
3. **[Encrypt Data with AWS KMS](./documents/03-boundary-enforcement.md)**, AWS · KMS · DynamoDB · IAM
4. **[Build a Security Monitoring System](./documents/04-compliance-checklist.md)**, AWS · API · CloudTrail · CloudWatch
5. **[Threat Detection with GuardDuty](./documents/05-evidence-collection.md)**, GuardDuty · SQL · API · AWS

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Cloud Security with AWS IAM
- ✅ Secure Secrets with Secrets Manager
- ✅ Encrypt Data with AWS KMS
- ✅ Build a Security Monitoring System
- ✅ Threat Detection with GuardDuty
