# RAG Applications Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **4 validated build(s)**.

## Overview

This domain captures **4 validated build(s)** in rag applications engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -r-e-t-r-i-e-v-a-l---a-u-g-m-e-n-t-e-d- -g-e-n-e-r-a-t-i-o-n- -(-R-A-G-)- -c-h-a-t-b-o-t- -u-s-i-n-g- -A-m-a-z-o-n- -B-e-d-r-o-c-k-.- -T-h-e- -s-y-s-t-e-m- -e-x-i-s-t-s- -t-o- -g-r-o-u-n-d- -m-o-d-e-l- -r-e-s-p-o-n-s-e-s- -i-n- -e-x-t-e-r-n-a-l- -d-a-t-a- -b-y- -c-o-m-b-i-n-i-n-g- -m-a-n-a-g-e-d- -f-o-u-n-d-a-t-i-o-n- -m-o-d-e-l-s- -w-i-t-h- -a- -s-e-a-r-c-h-a-b-l-e- -k-n-o-w-l-e-d-g-e- -b-a-s-e-.--
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -d-e-m-o-n-s-t-r-a-t-e-s- -k-n-o-w-l-e-d-g-e- -b-a-s-e- -c-r-e-a-t-i-o-n-,- -d-o-c-u-m-e-n-t- -i-n-g-e-s-t-i-o-n-,- -a-n-d- -r-e-s-p-o-n-s-e- -g-e-n-e-r-a-t-i-o-n- -u-s-i-n-g- -B-e-d-r-o-c-k---m-a-n-a-g-e-d- -s-e-r-v-i-c-e-s-.- -T-h-e- -r-e-s-u-l-t- -i-s- -a- -b-o-u-n-d-e-d- -c-h-a-t-b-o-t- -w-h-o-s-e- -a-n-s-w-e-r-s- -a-r-e- -c-o-n-s-t-r-a-i-n-e-d- -b-y- -i-n-d-e-x-e-d- -s-o-u-r-c-e- -m-a-t-e-r-i-a-l- -r-a-t-h-e-r- -t-h-a-n- -u-n-c-o-n-s-t-r-a-i-n-e-d- -m-o-d-e-l- -o-u-t-p-u-t-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -c-o-m-m-a-n-d---l-i-n-e- -i-n-t-e-r-f-a-c-e- -f-o-r- -i-n-t-e-r-a-c-t-i-n-g- -w-i-t-h- -a- -r-e-t-r-i-e-v-a-l---a-u-g-m-e-n-t-e-d- -g-e-n-e-r-a-t-i-o-n- -(-R-A-G-)- -c-h-a-t-b-o-t- -u-s-i-n-g- -A-m-a-z-o-n- -B-e-d-r-o-c-k-.- -T-h-e- -s-y-s-t-e-m- -e-x-i-s-t-s- -t-o- -v-a-l-i-d-a-t-e- -t-h-a-t- -k-n-o-w-l-e-d-g-e---b-a-s-e---b-a-c-k-e-d- -i-n-f-e-r-e-n-c-e- -c-a-n- -b-e- -i-n-v-o-k-e-d- -d-i-r-e-c-t-l-y- -f-r-o-m- -a- -t-e-r-m-i-n-a-l- -w-i-t-h-o-u-t- -r-e-l-y-i-n-g- -o-n- -a- -w-e-b- -o-r- -A-P-I- -l-a-y-e-r-.--
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -d-e-m-o-n-s-t-r-a-t-e-s- -t-h-r-e-e- -c-o-r-e- -c-o-n-c-e-r-n-s-:- -s-t-o-r-i-n-g- -r-e-f-e-r-e-n-c-e- -d-a-t-a- -i-n- -A-m-a-z-o-n- -S-3-,- -c-o-n-f-i-g-u-r-i-n-g- -a- -B-e-d-r-o-c-k- -K-n-o-w-l-e-d-g-e- -B-a-s-e- -f-o-r- -r-e-t-r-i-e-v-a-l-,- -a-n-d- -s-e-l-e-c-t-i-n-g- -B-e-d-r-o-c-k- -f-o-u-n-d-a-t-i-o-n- -m-o-d-e-l-s- -f-o-r- -r-e-s-p-o-n-s-e- -g-e-n-e-r-a-t-i-o-n-.- -T-h-e- -r-e-s-u-l-t- -i-s- -a- -s-c-r-i-p-t-a-b-l-e- -a-n-d- -r-e-p-e-a-t-a-b-l-e- -w-o-r-k-f-l-o-w- -f-o-r- -g-r-o-u-n-d-e-d- -m-o-d-e-l- -i-n-t-e-r-a-c-t-i-o-n- -v-i-a- -t-h-e- -A-W-S- -C-L-I-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -r-e-t-r-i-e-v-a-l---a-u-g-m-e-n-t-e-d- -g-e-n-e-r-a-t-i-o-n- -(-R-A-G-)- -c-h-a-t-b-o-t- -b-a-c-k-e-d- -b-y- -A-m-a-z-o-n- -B-e-d-r-o-c-k- -a-n-d- -e-x-p-o-s-e-d- -t-h-r-o-u-g-h- -a- -c-u-s-t-o-m- -A-P-I-.- -T-h-e- -s-y-s-t-e-m- -e-x-i-s-t-s- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -h-o-w- -e-x-t-e-r-n-a-l- -k-n-o-w-l-e-d-g-e- -c-a-n- -b-e- -r-e-t-r-i-e-v-e-d- -f-r-o-m- -o-b-j-e-c-t- -s-t-o-r-a-g-e- -a-n-d- -c-o-m-b-i-n-e-d- -w-i-t-h- -f-o-u-n-d-a-t-i-o-n- -m-o-d-e-l- -i-n-f-e-r-e-n-c-e- -t-o- -p-r-o-d-u-c-e- -g-r-o-u-n-d-e-d- -r-e-s-p-o-n-s-e-s-.--
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -f-o-c-u-s-e-s- -o-n- -c-o-n-f-i-g-u-r-i-n-g- -A-m-a-z-o-n- -B-e-d-r-o-c-k-,- -i-n-t-e-g-r-a-t-i-n-g- -a- -m-a-n-a-g-e-d- -k-n-o-w-l-e-d-g-e- -s-o-u-r-c-e-,- -a-n-d- -e-x-p-o-s-i-n-g- -m-o-d-e-l- -a-c-c-e-s-s- -t-h-r-o-u-g-h- -a- -l-i-g-h-t-w-e-i-g-h-t- -A-P-I- -l-a-y-e-r-.- -T-h-e- -r-e-s-u-l-t- -i-s- -a- -c-a-l-l-a-b-l-e- -i-n-t-e-r-f-a-c-e- -t-h-a-t- -c-l-e-a-n-l-y- -s-e-p-a-r-a-t-e-s- -r-e-t-r-i-e-v-a-l-,- -i-n-f-e-r-e-n-c-e-,- -a-n-d- -c-l-i-e-n-t- -a-c-c-e-s-s- -c-o-n-c-e-r-n-s-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Set Up a RAG Chatbot in Bedrock](./diagrams/01-rag-foundation-bedrock.md)**, RAG · Bedrock
- **[Interacting With My RAG Chatbot in the Terminal](./diagrams/02-rag-cloudshell-implementation.md)**, RAG · Bedrock · API · S3
- **[How I Built an API for My RAG Chatbot](./diagrams/03-rag-api-integration.md)**, API · RAG · Bedrock
- **[Building a RAG Chatbot with a Web Interface](./diagrams/04-rag-complete-webapp.md)**, RAG · API · Bedrock · IAM-scoped

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Set Up a RAG Chatbot in Bedrock](./documents/01-rag-foundation-bedrock.md)**, RAG · Bedrock
2. **[Interacting With My RAG Chatbot in the Terminal](./documents/02-rag-cloudshell-implementation.md)**, RAG · Bedrock · API · S3
3. **[How I Built an API for My RAG Chatbot](./documents/03-rag-api-integration.md)**, API · RAG · Bedrock
4. **[Building a RAG Chatbot with a Web Interface](./documents/04-rag-complete-webapp.md)**, RAG · API · Bedrock · IAM-scoped

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Set Up a RAG Chatbot in Bedrock
- ✅ Interacting With My RAG Chatbot in the Terminal
- ✅ How I Built an API for My RAG Chatbot
- ✅ Building a RAG Chatbot with a Web Interface
