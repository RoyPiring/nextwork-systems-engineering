# Security and Compliance Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **5 validated build(s)**.

## Overview

This domain captures **5 validated build(s)** in security and compliance engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-
--
-T-h-i-s- -p-r-o-j-e-c-t- -c-o-n-f-i-g-u-r-e-s- -A-W-S- -I-d-e-n-t-i-t-y- -a-n-d- -A-c-c-e-s-s- -M-a-n-a-g-e-m-e-n-t- -t-o- -c-o-n-t-r-o-l- -a-c-c-e-s-s- -t-o- -A-W-S- -r-e-s-o-u-r-c-e-s-.- -T-h-e- -s-c-o-p-e- -i-n-c-l-u-d-e-s- -I-A-M- -u-s-e-r-s-,- -g-r-o-u-p-s-,- -p-o-l-i-c-i-e-s-,- -a-c-c-o-u-n-t- -a-l-i-a-s-e-s-,- -a-n-d- -p-e-r-m-i-s-s-i-o-n- -e-v-a-l-u-a-t-i-o-n- -a-g-a-i-n-s-t- -E-C-2- -r-e-s-o-u-r-c-e-s-.--
--
-
--
-T-h-e- -s-y-s-t-e-m- -u-s-e-s- -I-A-M- -t-o- -d-e-f-i-n-e- -w-h-o- -c-a-n- -p-e-r-f-o-r-m- -a-c-t-i-o-n-s- -a-g-a-i-n-s-t- -s-p-e-c-i-f-i-c- -A-W-S- -r-e-s-o-u-r-c-e-s-.- -P-o-l-i-c-i-e-s- -e-x-p-r-e-s-s- -a-l-l-o-w-e-d- -a-n-d- -d-e-n-i-e-d- -a-c-t-i-o-n-s-,- -w-h-i-l-e- -u-s-e-r-s- -a-n-d- -g-r-o-u-p-s- -p-r-o-v-i-d-e- -a- -s-t-r-u-c-t-u-r-e- -f-o-r- -a-s-s-i-g-n-i-n-g- -t-h-o-s-e- -p-e-r-m-i-s-s-i-o-n-s-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -v-a-l-i-d-a-t-e-s- -h-o-w- -I-A-M- -e-n-f-o-r-c-e-s- -l-e-a-s-t---p-r-i-v-i-l-e-g-e- -a-c-c-e-s-s- -a-n-d- -h-o-w- -m-i-s-a-l-i-g-n-e-d- -p-e-r-m-i-s-s-i-o-n-s- -s-u-r-f-a-c-e- -a-s- -e-x-p-l-i-c-i-t- -a-c-c-e-s-s- -f-a-i-l-u-r-e-s-.--
--
------- -
--
-T-h-i-s- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -t-h-e- -s-e-c-u-r-i-t-y- -i-m-p-l-i-c-a-t-i-o-n-s- -o-f- -e-m-b-e-d-d-i-n-g- -c-l-o-u-d- -c-r-e-d-e-n-t-i-a-l-s- -i-n- -a-p-p-l-i-c-a-t-i-o-n- -c-o-d-e- -a-n-d- -t-h-e- -c-o-r-r-e-c-t-i-v-e- -u-s-e- -o-f- -A-W-S- -S-e-c-r-e-t-s- -M-a-n-a-g-e-r- -t-o- -e-x-t-e-r-n-a-l-i-z-e- -a-n-d- -c-o-n-t-r-o-l- -s-e-n-s-i-t-i-v-e- -c-o-n-f-i-g-u-r-a-t-i-o-n-.- -T-h-e- -s-y-s-t-e-m- -t-r-a-n-s-i-t-i-o-n-s- -a- -w-e-b- -a-p-p-l-i-c-a-t-i-o-n- -f-r-o-m- -s-t-a-t-i-c- -c-r-e-d-e-n-t-i-a-l- -s-t-o-r-a-g-e- -t-o- -m-a-n-a-g-e-d- -s-e-c-r-e-t- -r-e-t-r-i-e-v-a-l- -t-o- -r-e-d-u-c-e- -e-x-p-o-s-u-r-e- -r-i-s-k- -a-n-d- -a-l-i-g-n- -w-i-t-h- -s-t-a-n-d-a-r-d- -c-l-o-u-d- -s-e-c-u-r-i-t-y- -p-r-a-c-t-i-c-e-s-.- -T-h-e- -w-o-r-k-f-l-o-w- -v-a-l-i-d-a-t-e-s- -h-o-w- -s-e-c-r-e-t-s- -a-r-e- -r-e-m-o-v-e-d- -f-r-o-m- -s-o-u-r-c-e- -c-o-n-t-r-o-l-,- -s-t-o-r-e-d- -c-e-n-t-r-a-l-l-y-,- -a-n-d- -a-c-c-e-s-s-e-d- -p-r-o-g-r-a-m-m-a-t-i-c-a-l-l-y- -a-t- -r-u-n-t-i-m-e- -w-i-t-h-o-u-t- -e-m-b-e-d-d-i-n-g- -s-e-n-s-i-t-i-v-e- -v-a-l-u-e-s- -i-n- -c-o-d-e-.--
--
-
--
-T-h-e- -s-y-s-t-e-m- -u-s-e-s- -A-W-S- -S-e-c-r-e-t-s- -M-a-n-a-g-e-r- -a-s- -t-h-e- -a-u-t-h-o-r-i-t-a-t-i-v-e- -s-t-o-r-e- -f-o-r- -s-e-n-s-i-t-i-v-e- -c-r-e-d-e-n-t-i-a-l-s-,- -w-i-t-h- -A-W-S- -I-A-M- -e-n-f-o-r-c-i-n-g- -a-c-c-e-s-s- -b-o-u-n-d-a-r-i-e-s-.- -G-i-t-H-u-b- -f-u-n-c-t-i-o-n-s- -a-s- -t-h-e- -v-e-r-s-i-o-n- -c-o-n-t-r-o-l- -s-y-s-t-e-m- -w-h-e-r-e- -e-x-p-o-s-u-r-e- -r-i-s-k- -i-s- -e-v-a-l-u-a-t-e-d-.- -T-h-e- -p-r-o-j-e-c-t- -c-e-n-t-e-r-s- -o-n- -h-a-r-d-c-o-d-e-d- -c-r-e-d-e-n-t-i-a-l- -r-i-s-k-s-,- -s-e-c-r-e-t- -l-i-f-e-c-y-c-l-e- -m-a-n-a-g-e-m-e-n-t-,- -a-n-d- -c-o-n-t-r-o-l-l-e-d- -r-e-t-r-i-e-v-a-l- -p-a-t-t-e-r-n-s- -r-a-t-h-e-r- -t-h-a-n- -t-o-o-l- -u-s-a-g-e- -a-l-o-n-e-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -h-i-g-h-l-i-g-h-t-s- -t-h-e- -o-p-e-r-a-t-i-o-n-a-l- -f-r-i-c-t-i-o-n- -i-n-t-r-o-d-u-c-e-d- -w-h-e-n- -r-e-t-r-o-f-i-t-t-i-n-g- -s-e-c-r-e-t- -m-a-n-a-g-e-m-e-n-t- -i-n-t-o- -e-x-i-s-t-i-n-g- -c-o-d-e-.- -T-h-e- -p-r-i-m-a-r-y- -c-o-n-s-t-r-a-i-n-t- -a-d-d-r-e-s-s-e-d- -i-s- -m-a-i-n-t-a-i-n-i-n-g- -a-p-p-l-i-c-a-t-i-o-n- -f-u-n-c-t-i-o-n-a-l-i-t-y- -w-h-i-l-e- -r-e-m-o-v-i-n-g- -e-m-b-e-d-d-e-d- -c-r-e-d-e-n-t-i-a-l-s-.- --
--
-T-h-e- -o-u-t-c-o-m-e- -d-e-m-o-n-s-t-r-a-t-e-s- -r-e-d-u-c-e-d- -c-r-e-d-e-n-t-i-a-l- -e-x-p-o-s-u-r-e- -a-n-d- -c-l-e-a-r-e-r- -s-e-p-a-r-a-t-i-o-n- -b-e-t-w-e-e-n- -c-o-d-e- -a-n-d- -c-o-n-f-i-g-u-r-a-t-i-o-n-.--
--
------- -
--
-T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -e-n-c-r-y-p-t-i-o-n- -a-t- -r-e-s-t- -f-o-r- -d-a-t-a- -s-t-o-r-e-d- -i-n- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -u-s-i-n-g- -A-W-S- -K-e-y- -M-a-n-a-g-e-m-e-n-t- -S-e-r-v-i-c-e-.- -T-h-e- -s-y-s-t-e-m- -i-n-t-e-g-r-a-t-e-s- -a- -c-u-s-t-o-m-e-r---m-a-n-a-g-e-d- -K-M-S- -k-e-y- -w-i-t-h- -D-y-n-a-m-o-D-B- -t-o- -e-n-f-o-r-c-e- -e-n-c-r-y-p-t-i-o-n-,- -k-e-y- -o-w-n-e-r-s-h-i-p-,- -a-n-d- -a-c-c-e-s-s- -b-o-u-n-d-a-r-i-e-s- -t-h-r-o-u-g-h- -I-A-M- -a-n-d- -k-e-y- -p-o-l-i-c-i-e-s-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -u-s-e-s- -A-W-S- -K-M-S- -f-o-r- -k-e-y- -l-i-f-e-c-y-c-l-e- -a-n-d- -a-c-c-e-s-s- -c-o-n-t-r-o-l- -a-n-d- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -a-s- -t-h-e- -e-n-c-r-y-p-t-e-d- -d-a-t-a- -s-t-o-r-e-.- -C-o-r-e- -c-o-n-c-e-p-t-s- -i-n-c-l-u-d-e- -e-n-v-e-l-o-p-e- -e-n-c-r-y-p-t-i-o-n-,- -s-y-m-m-e-t-r-i-c- -c-u-s-t-o-m-e-r---m-a-n-a-g-e-d- -k-e-y-s-,- -I-A-M- -a-u-t-h-o-r-i-z-a-t-i-o-n-,- -a-n-d- -s-e-r-v-i-c-e---i-n-t-e-g-r-a-t-e-d- -e-n-c-r-y-p-t-i-o-n- -b-e-h-a-v-i-o-r-.--
--
-
--
-T-h-e- -w-o-r-k- -f-o-c-u-s-e-d- -o-n- -e-v-a-l-u-a-t-i-n-g- -D-y-n-a-m-o-D-B- -e-n-c-r-y-p-t-i-o-n- -o-p-t-i-o-n-s- -a-n-d- -s-e-l-e-c-t-i-n-g- -a- -c-u-s-t-o-m-e-r---m-a-n-a-g-e-d- -K-M-S- -k-e-y- -t-o- -m-e-e-t- -a-u-d-i-t-a-b-i-l-i-t-y- -a-n-d- -a-c-c-e-s-s- -c-o-n-t-r-o-l- -r-e-q-u-i-r-e-m-e-n-t-s-.- -T-h-e- -p-r-i-m-a-r-y- -c-o-m-p-l-e-x-i-t-y- -w-a-s- -u-n-d-e-r-s-t-a-n-d-i-n-g- -h-o-w- -D-y-n-a-m-o-D-B- -e-n-c-r-y-p-t-i-o-n- -i-n-t-e-r-a-c-t-s- -w-i-t-h- -I-A-M- -a-n-d- -K-M-S- -k-e-y- -p-o-l-i-c-i-e-s-.--
--
-T-h-e- -p-r-o-j-e-c-t- -e-x-i-s-t-s- -t-o- -e-s-t-a-b-l-i-s-h- -a- -b-a-s-e-l-i-n-e- -p-a-t-t-e-r-n- -f-o-r- -p-r-o-t-e-c-t-i-n-g- -s-e-n-s-i-t-i-v-e- -d-a-t-a- -i-n- -m-a-n-a-g-e-d- -A-W-S- -s-e-r-v-i-c-e-s- -w-h-e-r-e- -e-n-c-r-y-p-t-i-o-n- -m-u-s-t- -b-e- -e-n-f-o-r-c-e-d- -i-n-d-e-p-e-n-d-e-n-t-l-y- -o-f- -a-p-p-l-i-c-a-t-i-o-n- -l-o-g-i-c-.--
--
-------

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
