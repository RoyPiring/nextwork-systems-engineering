# AWS Storage Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **2 validated build(s)**.

## Overview

This domain captures **2 validated build(s)** in aws storage engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -p-r-o-v-i-s-i-o-n-s- -a- -s-t-a-t-i-c- -w-e-b-s-i-t-e- -h-o-s-t-e-d- -o-n- -A-m-a-z-o-n- -S-3-.- -T-h-e- -s-y-s-t-e-m- -u-s-e-s- -S-3- -o-b-j-e-c-t- -s-t-o-r-a-g-e- -t-o- -s-e-r-v-e- -H-T-M-L- -a-n-d- -s-t-a-t-i-c- -a-s-s-e-t-s- -d-i-r-e-c-t-l-y- -o-v-e-r- -H-T-T-P- -w-i-t-h-o-u-t- -a-p-p-l-i-c-a-t-i-o-n- -s-e-r-v-e-r-s- -o-r- -c-o-m-p-u-t-e- -r-e-s-o-u-r-c-e-s-.- -T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -c-o-n-t-r-o-l-l-e-d- -d-a-t-a- -t-r-a-n-s-f-e-r- -p-a-t-h- -b-e-t-w-e-e-n- -A-m-a-z-o-n- -S-3- -a-n-d- -G-o-o-g-l-e- -C-l-o-u-d- -S-t-o-r-a-g-e- -u-s-i-n-g- -G-o-o-g-l-e- -C-l-o-u-d- -S-t-o-r-a-g-e- -T-r-a-n-s-f-e-r- -S-e-r-v-i-c-e-.- -T-h-e- -s-y-s-t-e-m- -d-e-m-o-n-s-t-r-a-t-e-s- -c-r-o-s-s---c-l-o-u-d- -o-b-j-e-c-t- -m-o-v-e-m-e-n-t- -w-i-t-h-o-u-t- -d-u-p-l-i-c-a-t-i-n-g- -c-r-e-d-e-n-t-i-a-l-s- -o-r- -b-u-i-l-d-i-n-g- -c-u-s-t-o-m- -t-r-a-n-s-f-e-r- -l-o-g-i-c-.- -T-h-e- -p-r-i-m-a-r-y- -o-b-j-e-c-t-i-v-e- -i-s- -t-o- -v-a-l-i-d-a-t-e- -i-n-t-e-r-o-p-e-r-a-b-i-l-i-t-y- -b-e-t-w-e-e-n- -A-W-S- -a-n-d- -G-C-P- -s-t-o-r-a-g-e- -s-e-r-v-i-c-e-s- -u-s-i-n-g- -n-a-t-i-v-e-,- -m-a-n-a-g-e-d- -t-r-a-n-s-f-e-r- -c-a-p-a-b-i-l-i-t-i-e-s-.--
--
-
--
-T-h-e- -s-y-s-t-e-m- -u-s-e-s- -G-o-o-g-l-e- -C-l-o-u-d- -S-t-o-r-a-g-e- -T-r-a-n-s-f-e-r- -S-e-r-v-i-c-e- -t-o- -o-r-c-h-e-s-t-r-a-t-e- -d-a-t-a- -m-o-v-e-m-e-n-t-,- -A-m-a-z-o-n- -S-3- -a-s- -t-h-e- -s-o-u-r-c-e- -o-b-j-e-c-t- -s-t-o-r-e-,- -a-n-d- -G-o-o-g-l-e- -C-l-o-u-d- -S-t-o-r-a-g-e- -a-s- -t-h-e- -d-e-s-t-i-n-a-t-i-o-n-.- -I-d-e-n-t-i-t-y- -a-n-d- -a-c-c-e-s-s- -c-o-n-t-r-o-l- -i-s- -e-n-f-o-r-c-e-d- -t-h-r-o-u-g-h- -A-W-S- -I-A-M- -r-o-l-e-s- -a-n-d- -G-C-P- -s-e-r-v-i-c-e- -i-d-e-n-t-i-t-i-e-s-.- -A-m-a-z-o-n- -S-Q-S- -i-s- -u-s-e-d- -b-y- -t-h-e- -t-r-a-n-s-f-e-r- -s-e-r-v-i-c-e- -t-o- -t-r-a-c-k- -a-n-d- -c-o-o-r-d-i-n-a-t-e- -o-b-j-e-c-t- -t-r-a-n-s-f-e-r- -s-t-a-t-e-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -f-o-c-u-s-e-s- -o-n- -c-o-r-r-e-c-t-n-e-s-s- -o-f- -i-d-e-n-t-i-t-y- -f-e-d-e-r-a-t-i-o-n- -a-n-d- -t-r-a-n-s-f-e-r- -e-x-e-c-u-t-i-o-n- -r-a-t-h-e-r- -t-h-a-n- -t-h-r-o-u-g-h-p-u-t- -o-p-t-i-m-i-z-a-t-i-o-n- -o-r- -p-r-o-d-u-c-t-i-o-n- -s-c-a-l-e-.- -T-h-e- -c-r-i-t-i-c-a-l- -e-n-g-i-n-e-e-r-i-n-g- -c-o-n-s-t-r-a-i-n-t- -i-s- -t-h-e- -t-r-u-s-t- -r-e-l-a-t-i-o-n-s-h-i-p- -c-o-n-f-i-g-u-r-a-t-i-o-n- -t-h-a-t- -a-l-l-o-w-s- -G-C-P- -t-o- -a-s-s-u-m-e- -a- -l-i-m-i-t-e-d- -A-W-S- -I-A-M- -r-o-l-e- -f-o-r- -r-e-a-d- -a-c-c-e-s-s- -t-o- -S-3- -o-b-j-e-c-t-s-.- -S-u-c-c-e-s-s-f-u-l- -t-r-a-n-s-f-e-r- -c-o-n-f-i-r-m-s- -t-h-a-t- -t-h-e- -t-r-u-s-t- -b-o-u-n-d-a-r-y- -a-n-d- -p-e-r-m-i-s-s-i-o-n-s- -m-o-d-e-l- -f-u-n-c-t-i-o-n- -a-s- -d-e-s-i-g-n-e-d-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Host a Website on Amazon S3](./diagrams/01-aws-host-a-website-on-s3.md)**, S3 · HTML · HTTP
- **[Multi-Cloud Data Transfer with AWS and GCP](./diagrams/02-aws-multicloud-storage.md)**, Multi-Cloud · AWS · GCP · S3

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Host a Website on Amazon S3](./documents/01-aws-host-a-website-on-s3.md)**, S3 · HTML · HTTP
2. **[Multi-Cloud Data Transfer with AWS and GCP](./documents/02-aws-multicloud-storage.md)**, Multi-Cloud · AWS · GCP · S3

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Host a Website on Amazon S3
- ✅ Multi-Cloud Data Transfer with AWS and GCP
