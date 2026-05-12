# Database Services Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **5 validated build(s)**.

## Overview

This domain captures **5 validated build(s)** in database services engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -s-e-t- -f-o-c-u-s-e-s- -o-n- -b-u-i-l-d-i-n-g- -a-n-d- -e-v-a-l-u-a-t-i-n-g- -m-a-n-a-g-e-d- -d-a-t-a-b-a-s-e- -s-e-r-v-i-c-e-s- -o-n- -A-W-S-.- -T-h-e- -s-c-o-p-e- -c-o-v-e-r-s- -r-e-l-a-t-i-o-n-a-l- -a-n-d- -N-o-S-Q-L- -d-a-t-a-b-a-s-e- -m-o-d-e-l-s- -a-n-d- -h-o-w- -t-h-e-y- -a-r-e- -a-p-p-l-i-e-d- -w-i-t-h-i-n- -c-l-o-u-d---n-a-t-i-v-e- -a-r-c-h-i-t-e-c-t-u-r-e-s-.- -T-h-e- -i-n-t-e-n-t- -i-s- -t-o- -u-n-d-e-r-s-t-a-n-d- -s-e-r-v-i-c-e- -s-e-l-e-c-t-i-o-n-,- -o-p-e-r-a-t-i-o-n-a-l- -b-o-u-n-d-a-r-i-e-s-,- -a-n-d- -m-a-n-a-g-e-d- -s-c-a-l-i-n-g- -c-h-a-r-a-c-t-e-r-i-s-t-i-c-s- -r-a-t-h-e-r- -t-h-a-n- -d-a-t-a-b-a-s-e- -i-n-t-e-r-n-a-l-s-.- -T-h-e- -w-o-r-k- -r-e-s-u-l-t-s- -i-n- -a- -s-e-t- -o-f- -d-i-s-c-r-e-t-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n-s- -s-u-i-t-a-b-l-e- -f-o-r- -p-o-r-t-f-o-l-i-o- -r-e-v-i-e-w-.--
--
--
--
------- -
--
-T-h-i-s- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -t-h-e- -c-r-e-a-t-i-o-n- -o-f- -a-n- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -t-a-b-l-e- -a-n-d- -t-h-e- -l-o-a-d-i-n-g- -o-f- -s-a-m-p-l-e- -d-a-t-a- -u-s-i-n-g- -A-W-S---m-a-n-a-g-e-d- -t-o-o-l-i-n-g-.- -T-h-e- -s-c-o-p-e- -i-s- -l-i-m-i-t-e-d- -t-o- -b-a-s-i-c- -t-a-b-l-e- -d-e-f-i-n-i-t-i-o-n-,- -c-a-p-a-c-i-t-y- -c-o-n-f-i-g-u-r-a-t-i-o-n-,- -a-n-d- -d-a-t-a- -i-n-s-e-r-t-i-o-n- -t-o- -i-l-l-u-s-t-r-a-t-e- -h-o-w- -D-y-n-a-m-o-D-B- -o-p-e-r-a-t-e-s- -a-s- -a- -m-a-n-a-g-e-d- -N-o-S-Q-L- -s-e-r-v-i-c-e- -w-i-t-h-o-u-t- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -m-a-n-a-g-e-m-e-n-t-.--
--
-A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -i-s- -a- -f-u-l-l-y- -m-a-n-a-g-e-d-,- -s-e-r-v-e-r-l-e-s-s- -N-o-S-Q-L- -k-e-y---v-a-l-u-e- -a-n-d- -d-o-c-u-m-e-n-t- -d-a-t-a-b-a-s-e- -d-e-s-i-g-n-e-d- -f-o-r- -p-r-e-d-i-c-t-a-b-l-e- -p-e-r-f-o-r-m-a-n-c-e- -a-t- -s-c-a-l-e-.- -I-t- -a-b-s-t-r-a-c-t-s- -c-a-p-a-c-i-t-y- -p-r-o-v-i-s-i-o-n-i-n-g-,- -r-e-p-l-i-c-a-t-i-o-n-,- -a-n-d- -a-v-a-i-l-a-b-i-l-i-t-y- -m-a-n-a-g-e-m-e-n-t- -w-h-i-l-e- -p-r-o-v-i-d-i-n-g- -s-i-n-g-l-e---d-i-g-i-t- -m-i-l-l-i-s-e-c-o-n-d- -l-a-t-e-n-c-y- -f-o-r- -r-e-a-d- -a-n-d- -w-r-i-t-e- -o-p-e-r-a-t-i-o-n-s-.--
--
-
--
-A- -D-y-n-a-m-o-D-B- -t-a-b-l-e- -w-a-s- -c-r-e-a-t-e-d- -w-i-t-h- -e-x-p-l-i-c-i-t-l-y- -d-e-f-i-n-e-d- -a-t-t-r-i-b-u-t-e-s- -a-n-d- -a- -p-r-i-m-a-r-y- -k-e-y- -t-o- -s-u-p-p-o-r-t- -d-e-t-e-r-m-i-n-i-s-t-i-c- -i-t-e-m- -a-c-c-e-s-s-.- -R-e-a-d- -a-n-d- -w-r-i-t-e- -c-a-p-a-c-i-t-y- -s-e-t-t-i-n-g-s- -w-e-r-e- -c-o-n-f-i-g-u-r-e-d-,- -a-n-d- -d-a-t-a- -w-a-s- -i-n-s-e-r-t-e-d- -u-s-i-n-g- -A-W-S- -C-L-I- -c-o-m-m-a-n-d-s- -e-x-e-c-u-t-e-d- -f-r-o-m- -C-l-o-u-d-S-h-e-l-l- -t-o- -v-a-l-i-d-a-t-e- -t-a-b-l-e- -f-u-n-c-t-i-o-n-a-l-i-t-y- -a-n-d- -a-c-c-e-s-s- -p-a-t-t-e-r-n-s-.--
--
-
--
-I-n-i-t-i-a-l- -i-n-t-e-r-a-c-t-i-o-n- -w-i-t-h- -A-W-S- -C-L-I- -a-n-d- -C-l-o-u-d-S-h-e-l-l- -r-e-q-u-i-r-e-d- -u-n-d-e-r-s-t-a-n-d-i-n-g- -c-r-e-d-e-n-t-i-a-l- -c-o-n-t-e-x-t- -a-n-d- -c-o-m-m-a-n-d- -s-t-r-u-c-t-u-r-e-.- -O-n-c-e- -e-s-t-a-b-l-i-s-h-e-d-,- -t-h-e-s-e- -t-o-o-l-s- -p-r-o-v-i-d-e-d- -a- -c-o-n-s-i-s-t-e-n-t- -a-n-d- -r-e-p-e-a-t-a-b-l-e- -i-n-t-e-r-f-a-c-e- -f-o-r- -m-a-n-a-g-i-n-g- -D-y-n-a-m-o-D-B- -r-e-s-o-u-r-c-e-s- -w-i-t-h-o-u-t- -l-o-c-a-l- -e-n-v-i-r-o-n-m-e-n-t- -d-e-p-e-n-d-e-n-c-i-e-s-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -w-a-s- -c-o-m-p-l-e-t-e-d- -w-i-t-h-i-n- -a- -s-h-o-r-t- -t-i-m-e- -w-i-n-d-o-w-,- -c-o-v-e-r-i-n-g- -D-y-n-a-m-o-D-B- -f-u-n-d-a-m-e-n-t-a-l-s-,- -e-n-v-i-r-o-n-m-e-n-t- -s-e-t-u-p-,- -t-a-b-l-e- -c-r-e-a-t-i-o-n-,- -a-n-d- -d-a-t-a- -l-o-a-d-i-n-g-.- -T-h-e- -e-f-f-o-r-t- -r-e-f-l-e-c-t-s- -a- -c-o-n-s-t-r-a-i-n-e-d-,- -n-o-n---p-r-o-d-u-c-t-i-o-n- -e-x-e-r-c-i-s-e- -f-o-c-u-s-e-d- -o-n- -v-a-l-i-d-a-t-i-n-g- -s-e-r-v-i-c-e- -m-e-c-h-a-n-i-c-s- -r-a-t-h-e-r- -t-h-a-n- -l-o-n-g---t-e-r-m- -o-p-e-r-a-t-i-o-n-a-l- -t-u-n-i-n-g-.--
--
------- -
--
-A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -i-s- -a- -f-u-l-l-y- -m-a-n-a-g-e-d- -N-o-S-Q-L- -k-e-y- -v-a-l-u-e- -a-n-d- -d-o-c-u-m-e-n-t- -d-a-t-a-b-a-s-e- -d-e-s-i-g-n-e-d- -f-o-r- -p-r-e-d-i-c-t-a-b-l-e- -p-e-r-f-o-r-m-a-n-c-e- -a-t- -s-c-a-l-e-.- -I-t- -a-b-s-t-r-a-c-t-s- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -m-a-n-a-g-e-m-e-n-t- -w-h-i-l-e- -p-r-o-v-i-d-i-n-g- -s-i-n-g-l-e- -d-i-g-i-t- -m-i-l-l-i-s-e-c-o-n-d- -l-a-t-e-n-c-y-,- -a-u-t-o-m-a-t-i-c- -s-c-a-l-i-n-g-,- -a-n-d- -n-a-t-i-v-e- -h-i-g-h- -a-v-a-i-l-a-b-i-l-i-t-y-.- -T-h-e- -s-e-r-v-i-c-e- -e-n-f-o-r-c-e-s- -a-c-c-e-s-s- -p-a-t-t-e-r-n-s- -t-h-r-o-u-g-h- -p-r-i-m-a-r-y- -k-e-y-s- -a-n-d- -o-p-t-i-o-n-a-l- -s-e-c-o-n-d-a-r-y- -i-n-d-e-x-e-s-,- -w-h-i-c-h- -d-r-i-v-e-s- -d-a-t-a- -m-o-d-e-l-i-n-g- -d-e-c-i-s-i-o-n-s- -a-n-d- -q-u-e-r-y- -e-f-f-i-c-i-e-n-c-y-.--
--
-
--
-T-h-i-s- -p-r-o-j-e-c-t- -u-s-e-s- -A-m-a-z-o-n- -D-y-n-a-m-o-D-B- -a-s- -a- -b-a-c-k-i-n-g- -d-a-t-a- -s-t-o-r-e- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -b-a-s-i-c- -r-e-a-d- -a-c-c-e-s-s- -p-a-t-t-e-r-n-s- -t-h-r-o-u-g-h- -t-h-e- -A-W-S- -C-L-I- -i-n- -C-l-o-u-d-S-h-e-l-l-.- -T-h-e- -f-o-c-u-s- -i-s- -o-n- -h-o-w- -p-a-r-t-i-t-i-o-n- -k-e-y-s- -a-n-d- -s-o-r-t- -k-e-y-s- -c-o-n-t-r-o-l- -q-u-e-r-y- -b-e-h-a-v-i-o-r-,- -h-o-w- -Q-u-e-r-y- -a-n-d- -G-e-t-I-t-e-m- -o-p-e-r-a-t-i-o-n-s- -d-i-f-f-e-r- -f-r-o-m- -S-c-a-n-,- -a-n-d- -h-o-w- -t-h-e-s-e- -c-h-o-i-c-e-s- -a-f-f-e-c-t- -p-e-r-f-o-r-m-a-n-c-e- -a-n-d- -c-o-s-t- -c-h-a-r-a-c-t-e-r-i-s-t-i-c-s-.--
--
-
--
-I-n-s-u-f-f-i-c-i-e-n-t- -p-l-a-n-n-i-n-g- -o-f- -p-a-r-t-i-t-i-o-n- -a-n-d- -s-o-r-t- -k-e-y-s- -l-e-d- -t-o- -i-n-e-f-f-i-c-i-e-n-t- -a-c-c-e-s-s- -p-a-t-t-e-r-n-s-,- -r-e-i-n-f-o-r-c-i-n-g- -t-h-a-t- -D-y-n-a-m-o-D-B- -s-c-h-e-m-a- -d-e-s-i-g-n- -i-s- -a-n- -u-p-f-r-o-n-t- -a-r-c-h-i-t-e-c-t-u-r-a-l- -c-o-n-c-e-r-n- -r-a-t-h-e-r- -t-h-a-n- -a-n- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -d-e-t-a-i-l-.--
--
-
--
-T-h-e- -w-o-r-k- -w-a-s- -c-o-m-p-l-e-t-e-d- -w-i-t-h-i-n- -a- -s-h-o-r-t-,- -b-o-u-n-d-e-d- -s-e-s-s-i-o-n- -f-o-c-u-s-e-d- -o-n- -t-a-b-l-e- -i-n-t-e-r-a-c-t-i-o-n- -r-a-t-h-e-r- -t-h-a-n- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -p-r-o-v-i-s-i-o-n-i-n-g-.- -T-h-e- -t-i-m-e- -w-a-s- -p-r-i-m-a-r-i-l-y- -s-p-e-n-t- -v-a-l-i-d-a-t-i-n-g- -q-u-e-r-y- -b-e-h-a-v-i-o-r- -t-h-r-o-u-g-h- -t-h-e- -C-L-I- -a-n-d- -o-b-s-e-r-v-i-n-g- -h-o-w- -d-i-f-f-e-r-e-n-t- -k-e-y- -s-e-l-e-c-t-i-o-n-s- -a-f-f-e-c-t- -r-e-s-p-o-n-s-e- -e-f-f-i-c-i-e-n-c-y-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Get Hands On with AWS Databases!](./diagrams/01-databases-introduction.md)**, AWS · NoSQL
- **[Load Data into DynamoDB](./diagrams/02-nosql-dynamodb.md)**, DynamoDB · AWS-managed · NoSQL · AWS
- **[Query Data with DynamoDB](./diagrams/03-query-optimization.md)**, DynamoDB · NoSQL · AWS · CLI
- **[Aurora Database with EC2](./diagrams/04-relational-aurora.md)**, EC2 · MySQL · PostgreSQL · AWS
- **[Connect a Web App with Aurora](./diagrams/05-database-webapp-integration.md)**, EC2 · AWS · MySQL · PostgreSQL

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Get Hands On with AWS Databases!](./documents/01-databases-introduction.md)**, AWS · NoSQL
2. **[Load Data into DynamoDB](./documents/02-nosql-dynamodb.md)**, DynamoDB · AWS-managed · NoSQL · AWS
3. **[Query Data with DynamoDB](./documents/03-query-optimization.md)**, DynamoDB · NoSQL · AWS · CLI
4. **[Aurora Database with EC2](./documents/04-relational-aurora.md)**, EC2 · MySQL · PostgreSQL · AWS
5. **[Connect a Web App with Aurora](./documents/05-database-webapp-integration.md)**, EC2 · AWS · MySQL · PostgreSQL

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Get Hands On with AWS Databases!
- ✅ Load Data into DynamoDB
- ✅ Query Data with DynamoDB
- ✅ Aurora Database with EC2
- ✅ Connect a Web App with Aurora
