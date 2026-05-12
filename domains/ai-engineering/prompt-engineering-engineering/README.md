# Prompt Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **3 validated build(s)**.

## Overview

This domain captures **3 validated build(s)** in prompt engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-I-n- -t-h-i-s- -p-r-o-j-e-c-t-,- -I- -b-u-i-l-t- -a- -c-l-i-n-i-c-a-l- -A-I- -a-s-s-i-s-t-a-n-t- -u-s-i-n-g- -C-l-a-u-d-e- -w-i-t-h- -e-m-b-e-d-d-e-d- -s-a-f-e-t-y- -g-u-a-r-d-r-a-i-l-s-.- -T-h-e- -o-b-j-e-c-t-i-v-e- -w-a-s- -t-o- -a-p-p-l-y- -p-r-o-m-p-t- -e-n-g-i-n-e-e-r-i-n-g- -i-n- -a- -h-i-g-h---r-i-s-k- -d-o-m-a-i-n- -w-h-e-r-e- -o-u-t-p-u-t- -q-u-a-l-i-t-y-,- -c-o-n-s-t-r-a-i-n-t-s-,- -a-n-d- -s-a-f-e-t-y- -c-o-n-t-r-o-l-s- -a-r-e- -r-e-q-u-i-r-e-d-.-
-
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -f-o-c-u-s-e-d- -o-n- -s-t-r-u-c-t-u-r-i-n-g- -r-e-s-p-o-n-s-e-s-,- -e-n-f-o-r-c-i-n-g- -s-a-f-e-t-y- -b-o-u-n-d-a-r-i-e-s-,- -a-n-d- -e-n-s-u-r-i-n-g- -t-h-e- -s-y-s-t-e-m- -o-p-e-r-a-t-e-s- -a-s- -a-n- -a-s-s-i-s-t-i-v-e- -l-a-y-e-r- -r-a-t-h-e-r- -t-h-a-n- -a- -d-e-c-i-s-i-o-n---m-a-k-i-n-g- -a-u-t-h-o-r-i-t-y-.-
-
-
-
-
-
-
-
------- -I-n- -t-h-i-s- -p-r-o-j-e-c-t-,- -I- -b-u-i-l-t- -a- -r-e-u-s-a-b-l-e- -p-r-o-m-p-t- -t-e-m-p-l-a-t-e- -t-h-a-t- -g-e-n-e-r-a-t-e-s- -s-t-r-u-c-t-u-r-e-d- -l-e-s-s-o-n- -p-l-a-n-s- -u-s-i-n-g- -C-l-a-u-d-e-.- -T-h-e- -o-b-j-e-c-t-i-v-e- -w-a-s- -t-o- -c-o-n-t-r-o-l- -o-u-t-p-u-t- -q-u-a-l-i-t-y- -t-h-r-o-u-g-h- -p-r-o-m-p-t- -d-e-s-i-g-n- -i-n-s-t-e-a-d- -o-f- -r-e-l-y-i-n-g- -o-n- -d-e-f-a-u-l-t- -m-o-d-e-l- -b-e-h-a-v-i-o-r-.-
-
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -f-o-c-u-s-e-d- -o-n- -d-e-f-i-n-i-n-g- -r-o-l-e-,- -e-n-f-o-r-c-i-n-g- -s-t-r-u-c-t-u-r-e-,- -a-n-d- -i-t-e-r-a-t-i-n-g- -o-n- -o-u-t-p-u-t-s- -u-n-t-i-l- -t-h-e- -r-e-s-u-l-t- -w-a-s- -c-o-n-s-i-s-t-e-n-t- -a-n-d- -u-s-a-b-l-e-.- -T-h-i-s- -s-h-i-f-t-s- -c-o-n-t-e-n-t- -g-e-n-e-r-a-t-i-o-n- -f-r-o-m- -a-d- -h-o-c- -p-r-o-m-p-t-i-n-g- -t-o- -a- -r-e-p-e-a-t-a-b-l-e- -s-y-s-t-e-m-.-
-
-
-
-C-l-a-u-d-e- -w-a-s- -u-s-e-d- -a-s- -t-h-e- -g-e-n-e-r-a-t-i-o-n- -l-a-y-e-r-,- -w-i-t-h- -X-M-L---s-t-y-l-e- -t-a-g-s- -e-n-f-o-r-c-i-n-g- -o-u-t-p-u-t- -s-t-r-u-c-t-u-r-e-.-
-
-T-h-e- -c-o-r-e- -c-o-n-c-e-p-t-s- -a-p-p-l-i-e-d- -w-e-r-e- -r-o-l-e- -p-r-o-m-p-t-i-n-g- -t-o- -c-o-n-t-r-o-l- -p-e-r-s-p-e-c-t-i-v-e-,- -s-t-r-u-c-t-u-r-e-d- -o-u-t-p-u-t-s- -t-o- -e-n-f-o-r-c-e- -c-o-n-s-i-s-t-e-n-c-y-,- -a-n-d- -i-t-e-r-a-t-i-v-e- -r-e-f-i-n-e-m-e-n-t- -t-o- -i-m-p-r-o-v-e- -a-c-c-u-r-a-c-y- -a-n-d- -c-o-m-p-l-e-t-e-n-e-s-s- -o-v-e-r- -t-i-m-e-.-
-
-
-
-T-h-i-s- -p-r-o-j-e-c-t- -t-o-o-k- -a-b-o-u-t- -o-n-e- -h-o-u-r-.- -T-h-e- -m-a-i-n- -c-h-a-l-l-e-n-g-e- -w-a-s- -b-a-l-a-n-c-i-n-g- -s-t-r-u-c-t-u-r-e- -w-i-t-h- -f-l-e-x-i-b-i-l-i-t-y-.- -O-v-e-r---s-t-r-u-c-t-u-r-i-n-g- -d-e-g-r-a-d-e-d- -o-u-t-p-u-t-,- -w-h-i-l-e- -u-n-d-e-r---s-t-r-u-c-t-u-r-i-n-g- -p-r-o-d-u-c-e-d- -g-e-n-e-r-i-c- -r-e-s-u-l-t-s-.-
-
-O-n-c-e- -t-h-e- -s-t-r-u-c-t-u-r-e- -w-a-s- -s-t-a-b-i-l-i-z-e-d-,- -o-u-t-p-u-t- -q-u-a-l-i-t-y- -b-e-c-a-m-e- -c-o-n-s-i-s-t-e-n-t-.- -T-h-e- -r-e-s-u-l-t- -i-s- -a- -p-r-o-m-p-t- -t-h-a-t- -p-r-o-d-u-c-e-s- -u-s-a-b-l-e- -l-e-s-s-o-n- -p-l-a-n-s- -w-i-t-h-o-u-t- -a-d-d-i-t-i-o-n-a-l- -c-o-r-r-e-c-t-i-o-n-.-
-
-
-
-T-h-e- -g-o-a-l- -w-a-s- -t-o- -r-e-p-l-a-c-e- -o-n-e---o-f-f- -p-r-o-m-p-t-i-n-g- -w-i-t-h- -a- -r-e-p-e-a-t-a-b-l-e- -p-a-t-t-e-r-n- -f-o-r- -g-e-n-e-r-a-t-i-n-g- -s-t-r-u-c-t-u-r-e-d- -c-o-n-t-e-n-t-.-
-
-T-h-i-s- -a-p-p-r-o-a-c-h- -r-e-d-u-c-e-s- -v-a-r-i-a-b-i-l-i-t-y-,- -i-m-p-r-o-v-e-s- -r-e-l-i-a-b-i-l-i-t-y-,- -a-n-d- -a-l-l-o-w-s- -o-u-t-p-u-t-s- -t-o- -b-e- -r-e-u-s-e-d- -a-c-r-o-s-s- -m-u-l-t-i-p-l-e- -c-o-n-t-e-x-t-s- -w-i-t-h-o-u-t- -r-e-w-o-r-k-.-
-
------- -I-n- -t-h-i-s- -p-r-o-j-e-c-t-,- -I- -a-p-p-l-i-e-d- -p-r-o-m-p-t- -e-n-g-i-n-e-e-r-i-n-g- -t-e-c-h-n-i-q-u-e-s- -t-o- -i-m-p-r-o-v-e- -h-o-w- -A-I- -s-u-p-p-o-r-t-s- -r-e-s-e-a-r-c-h- -w-o-r-k-f-l-o-w-s-.- -T-h-e- -g-o-a-l- -w-a-s- -t-o- -t-e-s-t- -h-o-w- -d-i-f-f-e-r-e-n-t- -p-r-o-m-p-t-i-n-g- -s-t-r-a-t-e-g-i-e-s- -i-n-f-l-u-e-n-c-e- -o-u-t-p-u-t- -q-u-a-l-i-t-y- -a-n-d- -t-o- -b-u-i-l-d- -a- -r-e-u-s-a-b-l-e- -a-p-p-r-o-a-c-h- -f-o-r- -g-e-n-e-r-a-t-i-n-g- -s-t-r-u-c-t-u-r-e-d- -r-e-s-e-a-r-c-h- -i-n-s-i-g-h-t-s-.-
-
-T-h-e- -w-o-r-k- -f-o-c-u-s-e-d- -o-n- -c-o-m-b-i-n-i-n-g- -m-u-l-t-i-p-l-e- -p-r-o-m-p-t-i-n-g- -m-e-t-h-o-d-s- -i-n-t-o- -a- -s-i-n-g-l-e- -w-o-r-k-f-l-o-w- -t-h-a-t- -c-a-n- -g-u-i-d-e- -a-n-a-l-y-s-i-s-,- -c-r-i-t-i-q-u-e- -r-e-s-u-l-t-s-,- -a-n-d- -i-m-p-r-o-v-e- -o-u-t-p-u-t-s- -t-h-r-o-u-g-h- -i-t-e-r-a-t-i-o-n-.-
-
-
-
-T-h-i-s- -p-r-o-j-e-c-t- -u-s-e-d- -C-l-a-u-d-e- -a-s- -t-h-e- -p-r-i-m-a-r-y- -A-I- -s-y-s-t-e-m- -a-l-o-n-g- -w-i-t-h- -a- -s-a-m-p-l-e- -d-a-t-a-s-e-t- -f-o-r- -t-e-s-t-i-n-g- -p-r-o-m-p-t-s-.-
-
-T-h-e- -c-o-n-c-e-p-t-s- -e-x-p-l-o-r-e-d- -i-n-c-l-u-d-e-d- -r-o-l-e- -p-r-o-m-p-t-i-n-g-,- -a-d-v-e-r-s-a-r-i-a-l- -p-r-o-m-p-t-i-n-g-,- -c-h-a-i-n---o-f---t-h-o-u-g-h-t- -p-r-o-m-p-t-i-n-g-,- -a-n-d- -i-t-e-r-a-t-i-v-e- -r-e-f-i-n-e-m-e-n-t-.- -E-a-c-h- -t-e-c-h-n-i-q-u-e- -w-a-s- -u-s-e-d- -t-o- -c-o-n-t-r-o-l- -h-o-w- -t-h-e- -m-o-d-e-l- -i-n-t-e-r-p-r-e-t-s- -t-a-s-k-s- -a-n-d- -g-e-n-e-r-a-t-e-s- -r-e-s-p-o-n-s-e-s-.-
-
-
-
-T-h-i-s- -p-r-o-j-e-c-t- -t-o-o-k- -a-b-o-u-t- -o-n-e- -h-o-u-r-.- -T-h-e- -m-a-i-n- -c-h-a-l-l-e-n-g-e- -w-a-s- -c-o-m-b-i-n-i-n-g- -m-u-l-t-i-p-l-e- -p-r-o-m-p-t-i-n-g- -t-e-c-h-n-i-q-u-e-s- -i-n-t-o- -a- -s-i-n-g-l-e- -s-t-r-u-c-t-u-r-e- -w-i-t-h-o-u-t- -d-e-g-r-a-d-i-n-g- -o-u-t-p-u-t- -q-u-a-l-i-t-y-.-
-
-O-n-c-e- -s-t-r-u-c-t-u-r-e-d- -c-o-r-r-e-c-t-l-y-,- -t-h-e- -p-r-o-m-p-t-s- -p-r-o-d-u-c-e-d- -m-o-r-e- -c-o-n-s-i-s-t-e-n-t- -a-n-d- -u-s-e-f-u-l- -o-u-t-p-u-t-s-.- -T-h-e- -k-e-y- -w-i-n- -w-a-s- -b-u-i-l-d-i-n-g- -a- -r-e-u-s-a-b-l-e- -a-p-p-r-o-a-c-h- -t-h-a-t- -i-m-p-r-o-v-e-s- -r-e-s-p-o-n-s-e- -c-l-a-r-i-t-y- -a-n-d- -d-e-p-t-h- -w-i-t-h-o-u-t- -i-n-c-r-e-a-s-i-n-g- -c-o-m-p-l-e-x-i-t-y-.-
-
-
-
-T-h-e- -g-o-a-l- -w-a-s- -t-o- -u-n-d-e-r-s-t-a-n-d- -h-o-w- -p-r-o-m-p-t- -s-t-r-u-c-t-u-r-e- -d-i-r-e-c-t-l-y- -a-f-f-e-c-t-s- -o-u-t-p-u-t- -q-u-a-l-i-t-y- -a-n-d- -t-o- -c-r-e-a-t-e- -a- -r-e-p-e-a-t-a-b-l-e- -m-e-t-h-o-d- -f-o-r- -r-e-s-e-a-r-c-h- -t-a-s-k-s-.-
-
-T-h-i-s- -w-o-r-k- -a-l-s-o- -s-u-p-p-o-r-t-s- -b-u-i-l-d-i-n-g- -m-o-r-e- -r-e-l-i-a-b-l-e- -A-I---a-s-s-i-s-t-e-d- -w-o-r-k-f-l-o-w-s- -w-h-e-r-e- -o-u-t-p-u-t-s- -c-a-n- -b-e- -e-v-a-l-u-a-t-e-d-,- -r-e-f-i-n-e-d-,- -a-n-d- -r-e-u-s-e-d- -i-n-s-t-e-a-d- -o-f- -t-r-e-a-t-e-d- -a-s- -o-n-e---o-f-f- -r-e-s-p-o-n-s-e-s-.-
-
-
-
-U-s-i-n-g- -s-t-r-u-c-t-u-r-e-d- -p-r-o-m-p-t-s- -s-i-g-n-i-f-i-c-a-n-t-l-y- -i-m-p-r-o-v-e-s- -o-u-t-p-u-t- -c-o-n-s-i-s-t-e-n-c-y- -a-n-d- -u-s-e-f-u-l-n-e-s-s-.- -R-o-l-e- -p-r-o-m-p-t-i-n-g- -n-a-r-r-o-w-s- -t-h-e- -r-e-s-p-o-n-s-e- -t-o- -a- -s-p-e-c-i-f-i-c- -p-e-r-s-p-e-c-t-i-v-e-.- -A-d-v-e-r-s-a-r-i-a-l- -p-r-o-m-p-t-i-n-g- -e-x-p-o-s-e-s- -w-e-a-k-n-e-s-s-e-s-.- -C-h-a-i-n---o-f---t-h-o-u-g-h-t- -i-m-p-r-o-v-e-s- -t-r-a-n-s-p-a-r-e-n-c-y-.- -I-t-e-r-a-t-i-v-e- -r-e-f-i-n-e-m-e-n-t- -i-m-p-r-o-v-e-s- -a-c-c-u-r-a-c-y- -o-v-e-r- -m-u-l-t-i-p-l-e- -p-a-s-s-e-s-.-
-
-C-o-m-b-i-n-i-n-g- -t-h-e-s-e- -t-e-c-h-n-i-q-u-e-s- -p-r-o-d-u-c-e-s- -m-o-r-e- -c-o-n-t-r-o-l-l-e-d- -a-n-d- -r-e-l-i-a-b-l-e- -r-e-s-u-l-t-s- -t-h-a-n- -u-s-i-n-g- -a- -s-i-n-g-l-e- -p-r-o-m-p-t- -s-t-y-l-e-.-
-
-
-
-T-h-i-s- -p-r-o-j-e-c-t- -t-o-o-k- -a-p-p-r-o-x-i-m-a-t-e-l-y- -o-n-e- -h-o-u-r-.- -T-h-e- -m-a-j-o-r-i-t-y- -o-f- -t-h-e- -t-i-m-e- -w-a-s- -s-p-e-n-t- -t-e-s-t-i-n-g- -h-o-w- -d-i-f-f-e-r-e-n-t- -p-r-o-m-p-t-i-n-g- -t-e-c-h-n-i-q-u-e-s- -i-n-t-e-r-a-c-t- -w-h-e-n- -c-o-m-b-i-n-e-d- -i-n-t-o- -a- -s-i-n-g-l-e- -p-r-o-m-p-t-.-
-
-T-h-e- -g-o-a-l- -w-a-s- -t-o- -i-n-t-e-g-r-a-t-e- -r-o-l-e- -p-r-o-m-p-t-i-n-g-,- -a-d-v-e-r-s-a-r-i-a-l- -p-r-o-m-p-t-i-n-g-,- -c-h-a-i-n---o-f---t-h-o-u-g-h-t- -p-r-o-m-p-t-i-n-g-,- -a-n-d- -i-t-e-r-a-t-i-v-e- -r-e-f-i-n-e-m-e-n-t- -i-n-t-o- -a- -r-e-u-s-a-b-l-e- -a-p-p-r-o-a-c-h- -f-o-r- -r-e-s-e-a-r-c-h- -t-a-s-k-s-.- -A- -n-e-x-t- -a-r-e-a- -o-f- -f-o-c-u-s- -i-s- -i-m-p-r-o-v-i-n-g- -h-o-w- -r-e-s-u-l-t-s- -a-r-e- -p-r-e-s-e-n-t-e-d- -t-h-r-o-u-g-h- -m-o-r-e- -e-f-f-e-c-t-i-v-e- -d-a-t-a- -v-i-s-u-a-l-i-z-a-t-i-o-n-.-
-
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Prompt Engineering for Healthcare](./diagrams/ai-prompt-engineering-healthcare.md)**, AI · Claude
- **[Prompt Engineer a Lesson Plan](./diagrams/ai-prompt-engineering-lesson.md)**, Claude · XML-style
- **[Prompt Engineering for Research](./diagrams/ai-prompt-engineering-research.md)**, AI · Claude

## Implementation

**Build catalog.** Independent builds in this domain:

- **[Prompt Engineering for Healthcare](./documents/ai-prompt-engineering-healthcare.md)**, AI · Claude
- **[Prompt Engineer a Lesson Plan](./documents/ai-prompt-engineering-lesson.md)**, Claude · XML-style
- **[Prompt Engineering for Research](./documents/ai-prompt-engineering-research.md)**, AI · Claude

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Prompt Engineering for Healthcare
- ✅ Prompt Engineer a Lesson Plan
- ✅ Prompt Engineering for Research
