# Data Engineering with Postgres & Docker MCP

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-data-engineering-foundation.md`](../documents/01-data-engineering-foundation.md).

```mermaid
---
title: "Data Engineering with Postgres & Docker MCP"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph DevClient["Developer Client"]
        Cursor[/"Cursor IDE + MCP"/]
        Analyst[/"Analyst (SQL queries)"/]
    end

    subgraph PythonRuntime["Python Project (uv-managed)"]
        UvEnv("uv venv + pyproject")
        DbClient("Postgres client script")
    end

    subgraph DockerHost["Docker Desktop Runtime"]
        PgContainer("postgres container")
        PgEngine[("PostgreSQL 16 engine")]
        Dataset[("40k+ row dataset")]
    end

    subgraph PerfLoop["Query Performance Loop"]
        Explain{{"EXPLAIN ANALYZE"}}
        Index{{"CREATE INDEX"}}
    end

    Analyst -- "writes SQL" --> Cursor
    Cursor -- "MCP inspect schema" --> PgEngine
    DbClient -- "psycopg connect" --> PgContainer
    UvEnv --> DbClient
    PgContainer --> PgEngine
    PgEngine --> Dataset
    Cursor -- "run EXPLAIN" --> Explain
    Explain -- "slow plan signal" --> Index
    Index -- "rebuild plan" --> PgEngine

    class PgEngine,Dataset datastore
    class UvEnv,DbClient,PgContainer service
    class Explain,Index event
    class Cursor,Analyst io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
