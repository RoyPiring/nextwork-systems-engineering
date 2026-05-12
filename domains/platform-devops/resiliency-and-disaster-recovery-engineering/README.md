# Resiliency and Disaster Recovery Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **3 validated build(s)**.

## Overview

This domain captures **3 validated build(s)** in resiliency and disaster recovery engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -s-h-o-w-s- -h-o-w- -t-o- -d-e-p-l-o-y- -t-h-e- -s-a-m-e- -a-p-p-l-i-c-a-t-i-o-n- -i-n- -m-u-l-t-i-p-l-e- -A-W-S- -r-e-g-i-o-n-s- -t-o- -i-m-p-r-o-v-e- -a-v-a-i-l-a-b-i-l-i-t-y- -a-n-d- -r-e-d-u-c-e- -t-h-e- -i-m-p-a-c-t- -o-f- -r-e-g-i-o-n-a-l- -o-u-t-a-g-e-s-.- -T-h-e- -a-p-p- -i-s- -d-e-p-l-o-y-e-d- -u-s-i-n-g- -A-W-S- -A-p-p- -R-u-n-n-e-r- -w-i-t-h- -G-i-t-H-u-b---b-a-s-e-d- -d-e-p-l-o-y-m-e-n-t-s- -s-o- -u-p-d-a-t-e-s- -a-r-e- -a-u-t-o-m-a-t-i-c- -a-n-d- -c-o-n-s-i-s-t-e-n-t-.--
--
-T-h-e- -m-a-i-n- -g-o-a-l- -i-s- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -p-r-a-c-t-i-c-a-l- -d-i-s-a-s-t-e-r- -r-e-c-o-v-e-r-y-.- -B-y- -r-u-n-n-i-n-g- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -i-n- -m-o-r-e- -t-h-a-n- -o-n-e- -r-e-g-i-o-n-,- -a- -s-i-n-g-l-e- -r-e-g-i-o-n-a-l- -f-a-i-l-u-r-e- -d-o-e-s- -n-o-t- -t-a-k-e- -t-h-e- -s-e-r-v-i-c-e- -o-f-f-l-i-n-e-.--
--
-
--
-A-W-S- -A-p-p- -R-u-n-n-e-r- -i-s- -u-s-e-d- -t-o- -r-u-n- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n-,- -G-i-t-H-u-b- -i-s- -u-s-e-d- -t-o- -m-a-n-a-g-e- -c-o-d-e- -a-n-d- -t-r-i-g-g-e-r- -d-e-p-l-o-y-m-e-n-t-s-,- -a-n-d- -E-x-p-r-e-s-s-.-j-s- -p-r-o-v-i-d-e-s- -a- -s-i-m-p-l-e- -w-e-b- -f-r-a-m-e-w-o-r-k-.- -T-h-e- -p-r-o-j-e-c-t- -f-o-c-u-s-e-s- -o-n- -A-W-S- -r-e-g-i-o-n-s-,- -a-u-t-o-m-a-t-e-d- -d-e-p-l-o-y-m-e-n-t-s-,- -a-n-d- -m-u-l-t-i---r-e-g-i-o-n- -d-e-s-i-g-n- -a-s- -a- -r-e-l-i-a-b-i-l-i-t-y- -s-t-r-a-t-e-g-y-.--
--
-T-h-e- -k-e-y- -i-d-e-a- -i-s- -t-h-a-t- -r-e-g-i-o-n-s- -a-r-e- -i-s-o-l-a-t-e-d- -b-y- -d-e-s-i-g-n-.- -E-a-c-h- -r-e-g-i-o-n- -m-u-s-t- -b-e- -d-e-p-l-o-y-e-d- -a-n-d- -m-a-n-a-g-e-d- -i-n-d-e-p-e-n-d-e-n-t-l-y- -f-o-r- -t-r-u-e- -r-e-s-i-l-i-e-n-c-e-.--
--
-
--
-T-h-e- -m-a-i-n- -c-h-a-l-l-e-n-g-e- -w-a-s- -u-n-d-e-r-s-t-a-n-d-i-n-g- -t-h-a-t- -A-p-p- -R-u-n-n-e-r- -a-n-d- -G-i-t-H-u-b- -i-n-t-e-g-r-a-t-i-o-n-s- -a-r-e- -r-e-g-i-o-n---s-p-e-c-i-f-i-c-.- -E-a-c-h- -r-e-g-i-o-n- -r-e-q-u-i-r-e-s- -i-t-s- -o-w-n- -s-e-t-u-p- -e-v-e-n- -w-h-e-n- -u-s-i-n-g- -t-h-e- -s-a-m-e- -c-o-d-e-.--
--
-T-h-e- -w-i-n- -w-a-s- -c-o-n-f-i-r-m-i-n-g- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -w-a-s- -r-u-n-n-i-n-g- -a-t- -t-h-e- -s-a-m-e- -t-i-m-e- -i-n- -t-w-o- -r-e-g-i-o-n-s-.- -T-h-i-s- -v-a-l-i-d-a-t-e-d- -t-h-e- -m-u-l-t-i---r-e-g-i-o-n- -d-e-s-i-g-n- -a-n-d- -s-h-o-w-e-d- -h-o-w- -r-e-d-u-n-d-a-n-c-y- -i-m-p-r-o-v-e-s- -r-e-l-i-a-b-i-l-i-t-y-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -h-o-w- -t-o- -b-u-i-l-d- -a-u-t-o-m-a-t-i-c-,- -n-e-a-r---i-n-s-t-a-n-t- -f-a-i-l-o-v-e-r- -b-e-t-w-e-e-n- -r-e-g-i-o-n-s- -u-s-i-n-g- -A-m-a-z-o-n- -C-l-o-u-d-F-r-o-n-t- -o-r-i-g-i-n- -g-r-o-u-p-s-.- -T-h-e- -g-o-a-l- -i-s- -t-o- -e-n-s-u-r-e- -u-s-e-r-s- -e-x-p-e-r-i-e-n-c-e- -m-i-n-i-m-a-l- -d-i-s-r-u-p-t-i-o-n- -d-u-r-i-n-g- -a- -r-e-g-i-o-n-a-l- -o-u-t-a-g-e- -w-h-i-l-e- -t-r-a-f-f-i-c- -i-s- -t-r-a-n-s-p-a-r-e-n-t-l-y- -r-o-u-t-e-d- -t-o- -a- -h-e-a-l-t-h-y- -b-a-c-k-u-p- -r-e-g-i-o-n-.--
--
-C-l-o-u-d-F-r-o-n-t- -i-s- -u-s-e-d- -b-e-c-a-u-s-e- -i-t- -o-p-e-r-a-t-e-s- -a-t- -t-h-e- -e-d-g-e- -a-n-d- -c-a-n- -d-e-t-e-c-t- -o-r-i-g-i-n- -f-a-i-l-u-r-e-s- -q-u-i-c-k-l-y-.- -W-h-e-n- -c-o-m-b-i-n-e-d- -w-i-t-h- -m-u-l-t-i---r-e-g-i-o-n- -A-p-p- -R-u-n-n-e-r- -s-e-r-v-i-c-e-s-,- -i-t- -p-r-o-v-i-d-e-s- -a- -s-i-m-p-l-e- -a-n-d- -e-f-f-e-c-t-i-v-e- -d-i-s-a-s-t-e-r- -r-e-c-o-v-e-r-y- -m-e-c-h-a-n-i-s-m- -w-i-t-h-o-u-t- -r-e-q-u-i-r-i-n-g- -c-u-s-t-o-m- -r-o-u-t-i-n-g- -l-o-g-i-c-.--
--
-
--
-T-h-i-s- -p-r-o-j-e-c-t- -u-s-e-s- -A-m-a-z-o-n- -C-l-o-u-d-F-r-o-n-t- -a-n-d- -A-W-S- -A-p-p- -R-u-n-n-e-r-.- -T-h-e- -k-e-y- -c-o-n-c-e-p-t-s- -i-n-c-l-u-d-e- -o-r-i-g-i-n- -g-r-o-u-p-s-,- -h-e-a-l-t-h- -c-h-e-c-k-s-,- -f-a-i-l-o-v-e-r- -c-r-i-t-e-r-i-a-,- -a-n-d- -e-d-g-e---b-a-s-e-d- -t-r-a-f-f-i-c- -r-o-u-t-i-n-g-.--
--
-T-o-g-e-t-h-e-r-,- -t-h-e-s-e- -s-e-r-v-i-c-e-s- -a-l-l-o-w- -t-r-a-f-f-i-c- -t-o- -b-e- -s-e-r-v-e-d- -f-r-o-m- -a- -p-r-i-m-a-r-y- -r-e-g-i-o-n- -u-n-d-e-r- -n-o-r-m-a-l- -c-o-n-d-i-t-i-o-n-s- -a-n-d- -a-u-t-o-m-a-t-i-c-a-l-l-y- -r-e-d-i-r-e-c-t-e-d- -t-o- -a- -s-e-c-o-n-d-a-r-y- -r-e-g-i-o-n- -w-h-e-n- -t-h-e- -p-r-i-m-a-r-y- -b-e-c-o-m-e-s- -u-n-a-v-a-i-l-a-b-l-e-.--
--
-
--
-T-h-e- -p-r-o-j-e-c-t- -t-o-o-k- -a-p-p-r-o-x-i-m-a-t-e-l-y- -n-i-n-e-t-y- -m-i-n-u-t-e-s- -t-o- -c-o-m-p-l-e-t-e-.- -T-h-e- -m-o-s-t- -c-h-a-l-l-e-n-g-i-n-g- -p-a-r-t- -w-a-s- -c-o-n-f-i-g-u-r-i-n-g- -C-l-o-u-d-W-a-t-c-h- -a-l-a-r-m-s- -c-o-r-r-e-c-t-l-y- -s-o- -t-h-a-t- -f-a-i-l-o-v-e-r- -e-v-e-n-t-s- -w-o-u-l-d- -g-e-n-e-r-a-t-e- -a-c-c-u-r-a-t-e- -a-n-d- -t-i-m-e-l-y- -a-l-e-r-t-s-.--
--
-T-h-e- -m-o-s-t- -r-e-w-a-r-d-i-n-g- -o-u-t-c-o-m-e- -w-a-s- -o-b-s-e-r-v-i-n-g- -C-l-o-u-d-F-r-o-n-t- -a-u-t-o-m-a-t-i-c-a-l-l-y- -s-w-i-t-c-h- -t-o- -t-h-e- -b-a-c-k-u-p- -o-r-i-g-i-n- -d-u-r-i-n-g- -a- -s-i-m-u-l-a-t-e-d- -o-u-t-a-g-e- -a-n-d- -t-h-e-n- -r-e-t-u-r-n- -t-r-a-f-f-i-c- -t-o- -t-h-e- -p-r-i-m-a-r-y- -o-r-i-g-i-n- -o-n-c-e- -i-t- -w-a-s- -r-e-s-t-o-r-e-d-.- -T-h-i-s- -c-o-n-f-i-r-m-e-d- -t-h-a-t- -b-o-t-h- -f-a-i-l-o-v-e-r- -a-n-d- -f-a-i-l-b-a-c-k- -w-e-r-e- -w-o-r-k-i-n-g- -a-s- -d-e-s-i-g-n-e-d-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -h-o-w- -t-o- -b-u-i-l-d- -a- -m-u-l-t-i---c-l-o-u-d- -d-i-s-a-s-t-e-r- -r-e-c-o-v-e-r-y- -s-e-t-u-p- -u-s-i-n-g- -P-u-l-u-m-i- -t-o- -m-a-n-a-g-e- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -a-c-r-o-s-s- -A-W-S- -a-n-d- -G-C-P-.- -T-h-e- -g-o-a-l- -i-s- -t-o- -c-r-e-a-t-e- -a- -t-h-r-e-e---w-a-y- -f-a-i-l-o-v-e-r- -d-e-s-i-g-n- -t-h-a-t- -i-m-p-r-o-v-e-s- -a-v-a-i-l-a-b-i-l-i-t-y- -a-n-d- -r-e-s-i-l-i-e-n-c-e- -b-y- -d-i-s-t-r-i-b-u-t-i-n-g- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -a-c-r-o-s-s- -m-u-l-t-i-p-l-e- -r-e-g-i-o-n-s- -a-n-d- -c-l-o-u-d- -p-r-o-v-i-d-e-r-s-.--
--
-M-u-l-t-i---c-l-o-u-d- -d-i-s-a-s-t-e-r- -r-e-c-o-v-e-r-y- -r-e-d-u-c-e-s- -d-e-p-e-n-d-e-n-c-y- -o-n- -a- -s-i-n-g-l-e- -p-r-o-v-i-d-e-r- -a-n-d- -l-i-m-i-t-s- -t-h-e- -b-l-a-s-t- -r-a-d-i-u-s- -o-f- -o-u-t-a-g-e-s-.- -U-s-i-n-g- -I-n-f-r-a-s-t-r-u-c-t-u-r-e- -a-s- -C-o-d-e- -m-a-k-e-s- -t-h-i-s- -p-o-s-s-i-b-l-e- -b-y- -a-l-l-o-w-i-n-g- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -t-o- -b-e- -d-e-p-l-o-y-e-d-,- -t-r-a-c-k-e-d-,- -a-n-d- -u-p-d-a-t-e-d- -c-o-n-s-i-s-t-e-n-t-l-y- -t-h-r-o-u-g-h- -v-e-r-s-i-o-n---c-o-n-t-r-o-l-l-e-d- -c-o-d-e- -r-a-t-h-e-r- -t-h-a-n- -m-a-n-u-a-l- -c-o-n-f-i-g-u-r-a-t-i-o-n-.--
--
-
--
-P-u-l-u-m-i- -i-s- -u-s-e-d- -a-s- -t-h-e- -I-n-f-r-a-s-t-r-u-c-t-u-r-e- -a-s- -C-o-d-e- -p-l-a-t-f-o-r-m-,- -w-i-t-h- -A-W-S- -A-p-p- -R-u-n-n-e-r- -p-r-o-v-i-d-i-n-g- -r-e-g-i-o-n-a-l- -s-e-r-v-i-c-e-s- -i-n- -A-W-S- -a-n-d- -G-C-P- -C-l-o-u-d- -R-u-n- -a-c-t-i-n-g- -a-s- -a-n- -i-n-d-e-p-e-n-d-e-n-t- -b-a-c-k-u-p- -p-l-a-t-f-o-r-m-.- -T-y-p-e-S-c-r-i-p-t- -i-s- -u-s-e-d- -t-o- -d-e-f-i-n-e- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -d-e-c-l-a-r-a-t-i-v-e-l-y- -a-c-r-o-s-s- -p-r-o-v-i-d-e-r-s-.--
--
-T-h-e- -k-e-y- -c-o-n-c-e-p-t-s- -i-n-c-l-u-d-e- -i-m-p-o-r-t-i-n-g- -e-x-i-s-t-i-n-g- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -i-n-t-o- -P-u-l-u-m-i-,- -m-a-n-a-g-i-n-g- -m-u-l-t-i---c-l-o-u-d- -r-e-s-o-u-r-c-e-s- -f-r-o-m- -a- -s-i-n-g-l-e- -c-o-d-e-b-a-s-e-,- -a-n-d- -u-s-i-n-g- -I-a-C- -t-o- -e-n-f-o-r-c-e- -c-o-n-s-i-s-t-e-n-c-y-,- -r-e-p-e-a-t-a-b-i-l-i-t-y-,- -a-n-d- -c-o-n-t-r-o-l-l-e-d- -c-h-a-n-g-e- -a-c-r-o-s-s- -e-n-v-i-r-o-n-m-e-n-t-s-.--
--
-
--
-A- -m-a-j-o-r- -c-h-a-l-l-e-n-g-e- -w-a-s- -e-x-t-e-n-d-i-n-g- -t-h-e- -e-x-i-s-t-i-n-g- -A-W-S- -s-e-t-u-p- -i-n-t-o- -G-C-P- -w-h-i-l-e- -k-e-e-p-i-n-g- -e-v-e-r-y-t-h-i-n-g- -m-a-n-a-g-e-d- -u-n-d-e-r- -o-n-e- -P-u-l-u-m-i- -p-r-o-j-e-c-t-.- -T-h-i-s- -r-e-q-u-i-r-e-d- -c-a-r-e-f-u-l- -c-o-n-f-i-g-u-r-a-t-i-o-n- -o-f- -c-r-e-d-e-n-t-i-a-l-s-,- -A-P-I-s-,- -a-n-d- -i-m-p-o-r-t-s- -t-o- -e-n-s-u-r-e- -P-u-l-u-m-i- -a-c-c-u-r-a-t-e-l-y- -r-e-f-l-e-c-t-e-d- -t-h-e- -l-i-v-e- -i-n-f-r-a-s-t-r-u-c-t-u-r-e-.--
--
-T-h-e- -b-i-g-g-e-s-t- -w-i-n- -w-a-s- -s-u-c-c-e-s-s-f-u-l-l-y- -m-a-n-a-g-i-n-g- -A-W-S- -a-n-d- -G-C-P- -s-e-r-v-i-c-e-s- -t-o-g-e-t-h-e-r- -t-h-r-o-u-g-h- -a- -s-i-n-g-l-e- -P-u-l-u-m-i- -s-t-a-c-k-.- -T-h-i-s- -v-a-l-i-d-a-t-e-d- -t-h-a-t- -m-u-l-t-i---c-l-o-u-d- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -c-a-n- -b-e- -c-o-n-t-r-o-l-l-e-d- -c-o-h-e-r-e-n-t-l-y- -w-i-t-h-o-u-t- -f-r-a-g-m-e-n-t-i-n-g- -t-o-o-l-i-n-g- -o-r- -w-o-r-k-f-l-o-w-s-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Build Multi-Region Apps on AWS](./diagrams/01-ai-disaster-recovery-multiregion.md)**, Multi-Region · AWS · GitHub-based · GitHub
- **[Build Instant Failover with CloudFront Origin Groups](./diagrams/02-ai-disaster-recovery-failover.md)**, CloudFront · AWS · CloudWatch
- **[Multi-Cloud Disaster Recovery with Pulumi](./diagrams/03-ai-disaster-recovery-pulumi.md)**, Multi-Cloud · Pulumi · AWS · GCP

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Build Multi-Region Apps on AWS](./documents/01-ai-disaster-recovery-multiregion.md)**, Multi-Region · AWS · GitHub-based · GitHub
2. **[Build Instant Failover with CloudFront Origin Groups](./documents/02-ai-disaster-recovery-failover.md)**, CloudFront · AWS · CloudWatch
3. **[Multi-Cloud Disaster Recovery with Pulumi](./documents/03-ai-disaster-recovery-pulumi.md)**, Multi-Cloud · Pulumi · AWS · GCP

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Build Multi-Region Apps on AWS
- ✅ Build Instant Failover with CloudFront Origin Groups
- ✅ Multi-Cloud Disaster Recovery with Pulumi
