# Data Engineering Analytics Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **4 validated build(s)**.

## Overview

This domain captures **4 validated build(s)** in data analytics engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -p-r-o-v-i-s-i-o-n-s- -a- -P-o-s-t-g-r-e-S-Q-L- -d-a-t-a-b-a-s-e- -i-n-s-i-d-e- -a- -D-o-c-k-e-r- -c-o-n-t-a-i-n-e-r- -a-n-d- -e-x-p-o-s-e-s- -i-t- -f-o-r- -l-o-c-a-l- -i-n-t-e-r-a-c-t-i-o-n- -t-h-r-o-u-g-h- -M-C-P---e-n-a-b-l-e-d- -t-o-o-l-i-n-g-.- -T-h-e- -s-y-s-t-e-m- -s-u-p-p-o-r-t-s- -l-o-a-d-i-n-g- -a- -n-o-n---t-r-i-v-i-a-l- -d-a-t-a-s-e-t- -o-f- -o-v-e-r- -4-0-,-0-0-0- -r-o-w-s-,- -e-x-e-c-u-t-i-n-g- -a-n-a-l-y-t-i-c-a-l- -q-u-e-r-i-e-s-,- -v-i-s-u-a-l-i-z-i-n-g- -s-c-h-e-m-a- -r-e-l-a-t-i-o-n-s-h-i-p-s-,- -a-n-d- -a-p-p-l-y-i-n-g- -t-a-r-g-e-t-e-d- -p-e-r-f-o-r-m-a-n-c-e- -o-p-t-i-m-i-z-a-t-i-o-n-s-.- -P-o-s-t-g-r-e-S-Q-L- -p-r-o-v-i-d-e-s- -t-r-a-n-s-a-c-t-i-o-n-a-l- -c-o-n-s-i-s-t-e-n-c-y- -a-n-d- -S-Q-L- -c-o-m-p-l-i-a-n-c-e-.- -D-o-c-k-e-r- -i-s-o-l-a-t-e-s- -t-h-e- -d-a-t-a-b-a-s-e- -r-u-n-t-i-m-e- -t-o- -e-n-s-u-r-e- -r-e-p-e-a-t-a-b-l-e- -b-e-h-a-v-i-o-r- -a-c-r-o-s-s- -e-n-v-i-r-o-n-m-e-n-t-s-.--
--
-
--
-D-o-c-k-e-r- -D-e-s-k-t-o-p- -i-s- -u-s-e-d- -t-o- -r-u-n- -a-n-d- -m-a-n-a-g-e- -c-o-n-t-a-i-n-e-r-s- -l-o-c-a-l-l-y-.- -P-o-s-t-g-r-e-S-Q-L- -s-e-r-v-e-s- -a-s- -t-h-e- -r-e-l-a-t-i-o-n-a-l- -d-a-t-a-b-a-s-e- -e-n-g-i-n-e-.- -u-v- -i-n-i-t-i-a-l-i-z-e-s- -a-n-d- -m-a-n-a-g-e-s- -t-h-e- -P-y-t-h-o-n- -p-r-o-j-e-c-t- -u-s-e-d- -t-o- -i-n-t-e-r-a-c-t- -w-i-t-h- -t-h-e- -d-a-t-a-b-a-s-e-.- -C-u-r-s-o-r- -w-i-t-h- -M-C-P- -p-r-o-v-i-d-e-s- -d-a-t-a-b-a-s-e- -i-n-s-p-e-c-t-i-o-n- -a-n-d- -q-u-e-r-y- -e-x-e-c-u-t-i-o-n-.- -C-o-r-e- -c-o-n-c-e-p-t-s- -i-n-c-l-u-d-e- -c-o-n-t-a-i-n-e-r- -i-s-o-l-a-t-i-o-n-,- -d-a-t-a-b-a-s-e- -a-c-c-e-s-s- -c-o-n-t-r-o-l-,- -q-u-e-r-y- -p-e-r-f-o-r-m-a-n-c-e- -a-n-a-l-y-s-i-s-,- -a-n-d- -b-a-s-i-c- -P-y-t-h-o-n- -p-r-o-j-e-c-t- -s-t-r-u-c-t-u-r-e- -f-o-r- -d-a-t-a-b-a-s-e- -i-n-t-e-r-a-c-t-i-o-n-.--
--
-
--
-T-h-e- -p-r-i-m-a-r-y- -c-o-n-s-t-r-a-i-n-t- -w-a-s- -a-l-i-g-n-i-n-g- -l-o-c-a-l- -t-o-o-l-i-n-g- -v-e-r-s-i-o-n-s- -t-o- -e-n-s-u-r-e- -D-o-c-k-e-r-,- -u-v-,- -a-n-d- -M-C-P- -i-n-t-e-g-r-a-t-i-o-n- -w-o-r-k-e-d- -w-i-t-h-o-u-t- -c-o-n-f-l-i-c-t-s-.- -T-h-e- -m-o-s-t- -m-a-t-e-r-i-a-l- -o-u-t-c-o-m-e- -w-a-s- -v-a-l-i-d-a-t-i-n-g- -t-h-a-t- -q-u-e-r-y- -p-e-r-f-o-r-m-a-n-c-e- -i-s-s-u-e-s- -c-o-u-l-d- -b-e- -i-d-e-n-t-i-f-i-e-d- -a-n-d- -c-o-r-r-e-c-t-e-d- -t-h-r-o-u-g-h- -i-n-d-e-x-i-n-g-,- -w-i-t-h- -m-e-a-s-u-r-a-b-l-e- -c-h-a-n-g-e-s- -i-n- -e-x-e-c-u-t-i-o-n- -p-l-a-n-s-.--
--
-
--
-T-h-i-s- -p-r-o-j-e-c-t- -e-x-i-s-t-s- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -a- -c-o-n-t-r-o-l-l-e-d-,- -r-e-p-r-o-d-u-c-i-b-l-e- -a-p-p-r-o-a-c-h- -t-o- -s-t-a-n-d-i-n-g- -u-p- -a- -r-e-l-a-t-i-o-n-a-l- -d-a-t-a-b-a-s-e- -i-n- -a- -c-o-n-t-a-i-n-e-r-i-z-e-d- -e-n-v-i-r-o-n-m-e-n-t- -a-n-d- -v-a-l-i-d-a-t-i-n-g- -i-t-s- -b-e-h-a-v-i-o-r- -u-n-d-e-r- -r-e-a-l-i-s-t-i-c- -d-a-t-a- -v-o-l-u-m-e-.- -I-t- -f-o-c-u-s-e-s- -o-n- -u-n-d-e-r-s-t-a-n-d-i-n-g- -s-c-h-e-m-a- -d-e-s-i-g-n-,- -a-c-c-e-s-s- -b-o-u-n-d-a-r-i-e-s-,- -a-n-d- -t-h-e- -i-m-p-a-c-t- -o-f- -q-u-e-r-y- -s-t-r-u-c-t-u-r-e- -o-n- -p-e-r-f-o-r-m-a-n-c-e-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -i-m-p-l-e-m-e-n-t-s- -a- -r-e-p-r-o-d-u-c-i-b-l-e- -d-a-t-a- -t-r-a-n-s-f-o-r-m-a-t-i-o-n- -w-o-r-k-f-l-o-w- -t-h-a-t- -c-o-n-v-e-r-t-s- -r-a-w- -P-o-s-t-g-r-e-S-Q-L- -d-a-t-a- -i-n-t-o- -a-n-a-l-y-t-i-c-s---r-e-a-d-y- -t-a-b-l-e-s- -u-s-i-n-g- -d-b-t- -e-x-e-c-u-t-e-d- -t-h-r-o-u-g-h- -C-u-r-s-o-r- -w-i-t-h- -M-C-P- -i-n-t-e-g-r-a-t-i-o-n-.- -T-h-e- -s-y-s-t-e-m- -e-x-i-s-t-s- -t-o- -f-o-r-m-a-l-i-z-e- -t-r-a-n-s-f-o-r-m-a-t-i-o-n- -l-o-g-i-c-,- -e-n-f-o-r-c-e- -c-o-n-s-i-s-t-e-n-c-y-,- -a-n-d- -s-u-p-p-o-r-t- -d-o-w-n-s-t-r-e-a-m- -a-n-a-l-y-s-i-s- -t-h-r-o-u-g-h- -v-e-r-s-i-o-n-e-d-,- -t-e-s-t-a-b-l-e- -m-o-d-e-l-s- -r-a-t-h-e-r- -t-h-a-n- -a-d- -h-o-c- -S-Q-L-.--
--
-
--
-T-h-e- -p-r-i-m-a-r-y- -t-o-o-l-s- -i-n- -u-s-e- -a-r-e- -d-b-t- -f-o-r- -t-r-a-n-s-f-o-r-m-a-t-i-o-n- -a-n-d- -t-e-s-t-i-n-g-,- -P-o-s-t-g-r-e-S-Q-L- -a-s- -t-h-e- -s-o-u-r-c-e- -s-y-s-t-e-m-,- -a-n-d- -C-u-r-s-o-r- -w-i-t-h- -M-C-P- -f-o-r- -a-s-s-i-s-t-e-d- -d-e-v-e-l-o-p-m-e-n-t-.- -T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -r-e-l-i-e-s- -o-n- -S-Q-L- -c-o-n-s-t-r-u-c-t-s- -s-u-c-h- -a-s- -c-o-m-m-o-n- -t-a-b-l-e- -e-x-p-r-e-s-s-i-o-n-s-,- -a-g-g-r-e-g-a-t-e- -f-u-n-c-t-i-o-n-s-,- -a-n-d- -w-i-n-d-o-w- -f-u-n-c-t-i-o-n-s- -t-o- -s-t-r-u-c-t-u-r-e- -t-r-a-n-s-f-o-r-m-a-t-i-o-n-s- -i-n- -a- -m-a-i-n-t-a-i-n-a-b-l-e- -a-n-d- -a-u-d-i-t-a-b-l-e- -w-a-y-.--
--
-
--
-T-h-e- -m-a-i-n- -c-o-n-s-t-r-a-i-n-t- -e-n-c-o-u-n-t-e-r-e-d- -w-a-s- -e-n-f-o-r-c-i-n-g- -d-a-t-a- -q-u-a-l-i-t-y- -r-u-l-e-s- -t-h-r-o-u-g-h- -d-b-t- -t-e-s-t-s-,- -s-p-e-c-i-f-i-c-a-l-l-y- -v-a-l-u-e- -c-o-n-s-t-r-a-i-n-t-s- -o-n- -c-a-t-e-g-o-r-i-c-a-l- -f-i-e-l-d-s-.- -R-e-s-o-l-v-i-n-g- -t-e-s-t- -f-a-i-l-u-r-e-s- -v-a-l-i-d-a-t-e-d- -t-h-a-t- -t-r-a-n-s-f-o-r-m-a-t-i-o-n- -l-o-g-i-c- -a-n-d- -s-o-u-r-c-e- -d-a-t-a- -a-s-s-u-m-p-t-i-o-n-s- -w-e-r-e- -a-l-i-g-n-e-d-.- -T-h-e- -r-e-s-u-l-t-i-n-g- -d-b-t---g-e-n-e-r-a-t-e-d- -d-o-c-u-m-e-n-t-a-t-i-o-n- -p-r-o-v-i-d-e-s- -a- -s-y-s-t-e-m---l-e-v-e-l- -v-i-e-w- -o-f- -m-o-d-e-l-s- -a-n-d- -d-e-p-e-n-d-e-n-c-i-e-s- -r-a-t-h-e-r- -t-h-a-n- -r-e-l-y-i-n-g- -o-n- -t-r-i-b-a-l- -k-n-o-w-l-e-d-g-e-.--
--
-
--
-T-h-e- -p-u-r-p-o-s-e- -o-f- -t-h-i-s- -p-r-o-j-e-c-t- -w-a-s- -t-o- -p-r-a-c-t-i-c-e- -s-t-r-u-c-t-u-r-e-d- -d-a-t-a- -t-r-a-n-s-f-o-r-m-a-t-i-o-n- -u-s-i-n-g- -d-b-t- -a-g-a-i-n-s-t- -a- -r-e-l-a-t-i-o-n-a-l- -s-o-u-r-c-e- -a-n-d- -t-o- -e-s-t-a-b-l-i-s-h- -a- -b-a-s-e-l-i-n-e- -p-a-t-t-e-r-n- -f-o-r- -a-n-a-l-y-t-i-c-s- -p-i-p-e-l-i-n-e-s- -t-h-a-t- -c-a-n- -l-a-t-e-r- -b-e- -s-c-h-e-d-u-l-e-d- -a-n-d- -o-r-c-h-e-s-t-r-a-t-e-d- -b-y- -e-x-t-e-r-n-a-l- -w-o-r-k-f-l-o-w- -s-y-s-t-e-m-s-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -e-s-t-a-b-l-i-s-h-e-s- -a-n- -i-n-t-e-r-a-c-t-i-v-e- -a-n-a-l-y-s-i-s- -w-o-r-k-f-l-o-w- -u-s-i-n-g- -J-u-p-y-t-e-r- -n-o-t-e-b-o-o-k-s- -c-o-n-n-e-c-t-e-d- -t-o- -a- -P-o-s-t-g-r-e-S-Q-L- -d-a-t-a-b-a-s-e- -t-h-r-o-u-g-h- -M-C-P-.- -T-h-e- -s-y-s-t-e-m- -e-n-a-b-l-e-s- -S-Q-L---b-a-c-k-e-d- -a-n-a-l-y-s-i-s- -f-r-o-m- -P-y-t-h-o-n-,- -b-a-s-i-c- -v-i-s-u-a-l-i-z-a-t-i-o-n-,- -a-n-d- -t-h-e- -p-r-o-m-o-t-i-o-n- -o-f- -e-x-p-l-o-r-a-t-o-r-y- -q-u-e-r-i-e-s- -i-n-t-o- -a- -d-b-t---m-a-n-a-g-e-d- -t-r-a-n-s-f-o-r-m-a-t-i-o-n- -s-u-i-t-a-b-l-e- -f-o-r- -r-e-u-s-e- -a-n-d- -t-e-s-t-i-n-g-.--
--
-
--
-T-h-e- -i-m-p-l-e-m-e-n-t-a-t-i-o-n- -u-s-e-s- -J-u-p-y-t-e-r- -f-o-r- -i-n-t-e-r-a-c-t-i-v-e- -e-x-e-c-u-t-i-o-n-,- -P-o-s-t-g-r-e-S-Q-L- -a-s- -t-h-e- -d-a-t-a- -s-o-u-r-c-e-,- -M-a-t-p-l-o-t-l-i-b- -f-o-r- -b-a-s-i-c- -v-i-s-u-a-l-i-z-a-t-i-o-n-,- -C-u-r-s-o-r- -a-s- -t-h-e- -M-C-P- -c-l-i-e-n-t-,- -a-n-d- -d-b-t- -f-o-r- -m-a-n-a-g-e-d- -t-r-a-n-s-f-o-r-m-a-t-i-o-n-s-.- -T-h-e- -c-o-r-e- -c-o-n-c-e-p-t-s- -a-r-e- -d-a-t-a-b-a-s-e- -c-o-n-n-e-c-t-i-v-i-t-y- -f-r-o-m- -P-y-t-h-o-n-,- -n-o-t-e-b-o-o-k---b-a-s-e-d- -a-n-a-l-y-s-i-s-,- -v-i-s-u-a-l-i-z-a-t-i-o-n- -f-o-r- -i-n-s-p-e-c-t-i-o-n-,- -a-n-d- -t-r-a-n-s-i-t-i-o-n-i-n-g- -v-a-l-i-d-a-t-e-d- -l-o-g-i-c- -i-n-t-o- -a- -t-e-s-t-e-d- -d-a-t-a- -m-o-d-e-l-.--
--
-
--
-T-h-e- -p-r-i-m-a-r-y- -c-o-n-s-t-r-a-i-n-t- -w-a-s- -a-l-i-g-n-i-n-g- -d-b-t- -o-u-t-p-u-t-s- -w-i-t-h- -n-o-t-e-b-o-o-k---b-a-s-e-d- -q-u-e-r-i-e-s- -s-o- -t-h-e- -s-a-m-e- -d-a-t-a-s-e-t- -c-o-u-l-d- -b-e- -v-a-l-i-d-a-t-e-d- -a-n-d- -r-e-u-s-e-d- -a-c-r-o-s-s- -t-o-o-l-s-.- -T-h-e- -w-o-r-k- -f-o-c-u-s-e-d- -o-n- -e-n-s-u-r-i-n-g- -d-b-t- -m-o-d-e-l-s- -e-x-e-c-u-t-e-d- -c-o-r-r-e-c-t-l-y-,- -t-e-s-t-s- -p-a-s-s-e-d-,- -a-n-d- -r-e-s-u-l-t-s- -w-e-r-e- -q-u-e-r-y-a-b-l-e- -f-r-o-m- -t-h-e- -n-o-t-e-b-o-o-k- -w-i-t-h-o-u-t- -m-a-n-u-a-l- -d-a-t-a- -d-u-p-l-i-c-a-t-i-o-n-.--
--
-
--
-T-h-e- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -a- -s-t-a-n-d-a-r-d- -a-n-a-l-y-t-i-c-s- -f-l-o-w- -w-h-e-r-e- -e-x-p-l-o-r-a-t-o-r-y- -w-o-r-k- -i-n- -n-o-t-e-b-o-o-k-s- -f-e-e-d-s- -i-n-t-o- -s-t-r-u-c-t-u-r-e-d- -t-r-a-n-s-f-o-r-m-a-t-i-o-n-s-.- -I-t- -v-a-l-i-d-a-t-e-s- -h-o-w- -a-d- -h-o-c- -a-n-a-l-y-s-i-s- -c-a-n- -b-e- -c-o-n-s-t-r-a-i-n-e-d-,- -t-e-s-t-e-d-,- -a-n-d- -p-r-e-p-a-r-e-d- -f-o-r- -r-e-p-e-a-t-a-b-l-e- -u-s-e- -t-h-r-o-u-g-h- -d-b-t- -w-i-t-h-o-u-t- -t-r-e-a-t-i-n-g- -n-o-t-e-b-o-o-k-s- -a-s- -a- -p-r-o-d-u-c-t-i-o-n- -s-y-s-t-e-m-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Data Engineering with Postgres & Docker MCP](./diagrams/01-data-engineering-foundation.md)**, Postgres · Docker · MCP · PostgreSQL
- **[Data Engineering with DBT MCP](./diagrams/02-data-engineering-advanced.md)**, DBT · MCP · PostgreSQL · Cursor
- **[Data Engineering with Jupyter MCP](./diagrams/03-data-engineering-optimization.md)**, MCP · PostgreSQL · SQL-backed · Cursor
- **[Data Visualization with Grafana MCP](./diagrams/04-data-engineering-production.md)**, Grafana · MCP · PostgreSQL · Docker

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Data Engineering with Postgres & Docker MCP](./documents/01-data-engineering-foundation.md)**, Postgres · Docker · MCP · PostgreSQL
2. **[Data Engineering with DBT MCP](./documents/02-data-engineering-advanced.md)**, DBT · MCP · PostgreSQL · Cursor
3. **[Data Engineering with Jupyter MCP](./documents/03-data-engineering-optimization.md)**, MCP · PostgreSQL · SQL-backed · Cursor
4. **[Data Visualization with Grafana MCP](./documents/04-data-engineering-production.md)**, Grafana · MCP · PostgreSQL · Docker

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Data Engineering with Postgres & Docker MCP
- ✅ Data Engineering with DBT MCP
- ✅ Data Engineering with Jupyter MCP
- ✅ Data Visualization with Grafana MCP
