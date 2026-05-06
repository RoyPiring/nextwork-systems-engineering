# Data Engineering with DBT MCP

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-data-engineering-advanced.md`](../documents/02-data-engineering-advanced.md).

```mermaid
---
title: Data Engineering with DBT MCP
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph DevEnv["Developer Environment"]
        Cursor[/"Cursor IDE"/]
        MCP("MCP Integration")
    end

    subgraph Source["Source System"]
        Postgres[("PostgreSQL Raw Tables")]
    end

    subgraph DbtLayer["dbt Transformation Layer"]
        Models("dbt Models (CTEs)")
        WindowFns("Window/Aggregate SQL")
        Tests{{"dbt Tests (value rules)"}}
    end

    subgraph Outputs["Analytics Artifacts"]
        Marts[("Analytics-Ready Tables")]
        Docs("dbt-Generated Docs")
    end

    Cursor -- "assisted authoring" --> MCP
    MCP -- "compile and run" --> Models
    Postgres -- "raw rows" --> Models
    Models -- "structured SQL" --> WindowFns
    WindowFns -- "materialize" --> Marts
    Models -- "validate constraints" --> Tests
    Tests -- "block bad data" --> Marts
    Models -- "lineage and schema" --> Docs

    class Postgres,Marts datastore
    class MCP,Models,WindowFns,Docs service
    class Tests event
    class Cursor io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
