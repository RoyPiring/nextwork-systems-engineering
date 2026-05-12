# AWS Prerequisites Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **2 validated build(s)**.

## Overview

This domain captures **2 validated build(s)** in aws prerequisites engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-
-S-e-t-t-i-n-g- -u-p- -a-n- -A-W-S- -a-c-c-o-u-n-t- -e-s-t-a-b-l-i-s-h-e-s- -a- -b-i-l-l-i-n-g- -b-o-u-n-d-a-r-y- -a-n-d- -i-d-e-n-t-i-t-y- -r-e-q-u-i-r-e-d- -t-o- -a-c-c-e-s-s- -A-W-S- -s-e-r-v-i-c-e-s-.- -C-r-e-d-i-t- -c-a-r-d- -i-n-f-o-r-m-a-t-i-o-n- -i-s- -c-o-l-l-e-c-t-e-d- -t-o- -e-n-a-b-l-e- -b-i-l-l-i-n-g- -a-l-e-r-t-s-,- -f-r-a-u-d- -p-r-e-v-e-n-t-i-o-n-,- -a-n-d- -a-c-c-o-u-n-t- -v-e-r-i-f-i-c-a-t-i-o-n-.- -N-o- -c-h-a-r-g-e-s- -o-c-c-u-r- -u-n-l-e-s-s- -u-s-a-g-e- -e-x-c-e-e-d-s- -f-r-e-e- -t-i-e-r- -l-i-m-i-t-s- -o-r- -p-a-i-d- -s-e-r-v-i-c-e-s- -a-r-e- -e-x-p-l-i-c-i-t-l-y- -c-o-n-s-u-m-e-d-.--
--
-
--- -I-n-i-t-i-a-l- -A-W-S- -a-c-c-o-u-n-t- -c-r-e-a-t-i-o-n- -f-o-r- -l-e-a-r-n-i-n-g- -a-n-d- -e-x-p-e-r-i-m-e-n-t-a-t-i-o-n--
--- -E-s-t-a-b-l-i-s-h-i-n-g- -b-i-l-l-i-n-g- -b-o-u-n-d-a-r-i-e-s- -a-n-d- -c-o-s-t- -c-o-n-t-r-o-l-s--
--- -A-c-c-e-s-s-i-n-g- -A-W-S- -F-r-e-e- -T-i-e-r- -s-e-r-v-i-c-e-s--
--- -S-e-t-t-i-n-g- -u-p- -i-d-e-n-t-i-t-y- -a-n-d- -a-c-c-e-s-s- -m-a-n-a-g-e-m-e-n-t- -f-o-u-n-d-a-t-i-o-n--
--
-
--- -V-a-l-i-d- -e-m-a-i-l- -a-d-d-r-e-s-s--
--- -C-r-e-d-i-t- -c-a-r-d- -f-o-r- -a-c-c-o-u-n-t- -v-e-r-i-f-i-c-a-t-i-o-n- -(-n-o- -c-h-a-r-g-e-s- -u-n-l-e-s-s- -u-s-a-g-e- -e-x-c-e-e-d-s- -f-r-e-e- -t-i-e-r-)--
--- -B-a-s-i-c- -u-n-d-e-r-s-t-a-n-d-i-n-g- -o-f- -c-l-o-u-d- -c-o-m-p-u-t-i-n-g- -c-o-n-c-e-p-t-s--
--
-
--- -A-W-S- -a-c-c-o-u-n-t- -c-r-e-a-t-i-o-n- -a-n-d- -v-e-r-i-f-i-c-a-t-i-o-n--
--- -F-r-e-e- -T-i-e-r- -a-c-c-e-s-s- -c-o-n-f-i-g-u-r-a-t-i-o-n--
--- -B-i-l-l-i-n-g- -a-l-e-r-t- -s-e-t-u-p--
--- -B-a-s-i-c- -s-e-c-u-r-i-t-y- -c-o-n-f-i-g-u-r-a-t-i-o-n--
--
-
--- -A-d-v-a-n-c-e-d- -I-A-M- -c-o-n-f-i-g-u-r-a-t-i-o-n- -(-c-o-v-e-r-e-d- -i-n- -S-e-c-u-r-i-t-y- -&- -C-o-m-p-l-i-a-n-c-e- -E-n-g-i-n-e-e-r-i-n-g-)--
--- -M-u-l-t-i---a-c-c-o-u-n-t- -s-e-t-u-p- -(-b-e-y-o-n-d- -s-i-n-g-l-e- -a-c-c-o-u-n-t- -s-c-o-p-e-)--
--- -E-n-t-e-r-p-r-i-s-e- -o-r-g-a-n-i-z-a-t-i-o-n- -m-a-n-a-g-e-m-e-n-t- -C-l-o-u-d- -c-o-m-p-u-t-i-n-g- -r-e-p-l-a-c-e-s- -o-n---p-r-e-m-i-s-e-s- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -d-e-p-e-n-d-e-n-c-y- -w-i-t-h- -o-n---d-e-m-a-n-d- -a-c-c-e-s-s- -t-o- -c-o-m-p-u-t-e-,- -s-t-o-r-a-g-e-,- -a-n-d- -n-e-t-w-o-r-k-i-n-g- -s-e-r-v-i-c-e-s-.- -T-h-i-s- -m-o-d-e-l- -s-h-i-f-t-s- -r-e-s-p-o-n-s-i-b-i-l-i-t-y- -b-o-u-n-d-a-r-i-e-s-,- -r-e-d-u-c-e-s- -c-a-p-i-t-a-l- -e-x-p-e-n-d-i-t-u-r-e-,- -a-n-d- -e-n-a-b-l-e-s- -e-l-a-s-t-i-c- -r-e-s-o-u-r-c-e- -c-o-n-s-u-m-p-t-i-o-n- -a-l-i-g-n-e-d- -t-o- -w-o-r-k-l-o-a-d- -d-e-m-a-n-d-.--
--
-
--
-A-m-a-z-o-n- -W-e-b- -S-e-r-v-i-c-e-s- -p-r-o-v-i-d-e-s- -m-a-n-a-g-e-d- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -p-r-i-m-i-t-i-v-e-s- -d-e-l-i-v-e-r-e-d- -o-v-e-r- -t-h-e- -i-n-t-e-r-n-e-t-,- -i-n-c-l-u-d-i-n-g- -c-o-m-p-u-t-e-,- -s-t-o-r-a-g-e-,- -d-a-t-a-b-a-s-e-s-,- -a-n-d- -n-e-t-w-o-r-k-i-n-g-.- -T-h-e-s-e- -s-e-r-v-i-c-e-s- -a-r-e- -c-o-m-m-o-n-l-y- -u-s-e-d- -t-o- -b-u-i-l-d-,- -o-p-e-r-a-t-e-,- -a-n-d- -m-a-i-n-t-a-i-n- -a-p-p-l-i-c-a-t-i-o-n- -p-l-a-t-f-o-r-m-s- -a-c-r-o-s-s- -m-u-l-t-i-p-l-e- -i-n-d-u-s-t-r-i-e-s- -a-n-d- -r-e-g-u-l-a-t-o-r-y- -e-n-v-i-r-o-n-m-e-n-t-s-.--
--
-C-l-o-u-d- -p-l-a-t-f-o-r-m-s- -s-u-p-p-o-r-t- -m-u-l-t-i-p-l-e- -t-e-c-h-n-i-c-a-l- -r-o-l-e-s-,- -i-n-c-l-u-d-i-n-g- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -e-n-g-i-n-e-e-r-i-n-g-,- -D-e-v-O-p-s-,- -s-e-c-u-r-i-t-y-,- -a-n-d- -d-a-t-a---f-o-c-u-s-e-d- -d-i-s-c-i-p-l-i-n-e-s-.- -E-a-c-h- -r-o-l-e- -i-n-t-e-r-a-c-t-s- -w-i-t-h- -s-h-a-r-e-d- -c-l-o-u-d- -p-r-i-m-i-t-i-v-e-s- -b-u-t- -a-p-p-l-i-e-s- -d-i-f-f-e-r-e-n-t- -c-o-n-s-t-r-a-i-n-t-s-,- -c-o-n-t-r-o-l-s-,- -a-n-d- -o-p-e-r-a-t-i-o-n-a-l- -p-r-i-o-r-i-t-i-e-s-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Set Up An AWS Account](./diagrams/01-aws-account-setup.md)**, AWS · IAM
- **[Join the Cloud Beginner Challenge!](./diagrams/02-aws-beginners-challenge.md)**, AWS · DevOps

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Set Up An AWS Account](./documents/01-aws-account-setup.md)**, AWS · IAM
2. **[Join the Cloud Beginner Challenge!](./documents/02-aws-beginners-challenge.md)**, AWS · DevOps

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Set Up An AWS Account
- ✅ Join the Cloud Beginner Challenge!
