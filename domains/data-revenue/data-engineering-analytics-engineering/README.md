# Data Engineering Analytics Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **4 validated build(s)**.

## Overview

This domain captures **4 validated build(s)** in data analytics engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

This project provisions a PostgreSQL database inside a Docker container and exposes it for local interaction through MCP-enabled tooling. This project implements a reproducible data transformation workflow that converts raw PostgreSQL data into analytics-ready tables using dbt executed through Cursor with MCP integration. This project establishes an interactive analysis workflow using Jupyter notebooks connected to a PostgreSQL database through MCP.

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Data Engineering with Postgres & Docker MCP](./diagrams/01-data-engineering-foundation.md)** — Postgres · Docker · MCP · PostgreSQL
- **[Data Engineering with DBT MCP](./diagrams/02-data-engineering-advanced.md)** — DBT · MCP · PostgreSQL · Cursor
- **[Data Engineering with Jupyter MCP](./diagrams/03-data-engineering-optimization.md)** — MCP · PostgreSQL · SQL-backed · Cursor
- **[Data Visualization with Grafana MCP](./diagrams/04-data-engineering-production.md)** — Grafana · MCP · PostgreSQL · Docker

## Implementation

**Build sequence.** Ordered builds — each step is a complete system the next builds on:

1. **[Data Engineering with Postgres & Docker MCP](./documents/01-data-engineering-foundation.md)** — Postgres · Docker · MCP · PostgreSQL
2. **[Data Engineering with DBT MCP](./documents/02-data-engineering-advanced.md)** — DBT · MCP · PostgreSQL · Cursor
3. **[Data Engineering with Jupyter MCP](./documents/03-data-engineering-optimization.md)** — MCP · PostgreSQL · SQL-backed · Cursor
4. **[Data Visualization with Grafana MCP](./documents/04-data-engineering-production.md)** — Grafana · MCP · PostgreSQL · Docker

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Data Engineering with Postgres & Docker MCP
- ✅ Data Engineering with DBT MCP
- ✅ Data Engineering with Jupyter MCP
- ✅ Data Visualization with Grafana MCP
