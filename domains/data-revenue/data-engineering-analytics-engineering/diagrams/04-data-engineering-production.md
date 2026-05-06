# Data Visualization with Grafana MCP

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-data-engineering-production.md`](../documents/04-data-engineering-production.md).

```mermaid
---
title: Data Visualization with Grafana MCP
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Client["Operator Workstation"]
        Cursor[/"Cursor (MCP Client)"/]
        Browser[/"Grafana UI"/]
    end

    subgraph Container["Docker Compose Stack"]
        Grafana("Grafana Server")
        MCP("Grafana MCP Endpoint")
        Postgres[("PostgreSQL DB")]
    end

    subgraph Modeling["dbt Transformation"]
        DbtModel("dbt Model")
        Marts[("Reporting Marts")]
    end

    subgraph Dashboards["Visualization Layer"]
        Datasource{{"Data Source Config"}}
        Panel{{"SQL Panel Query"}}
        Health("Health & Signal Dashboard")
    end

    Cursor -- "MCP commands" --> MCP
    MCP -- "provision dashboard" --> Grafana
    Grafana -- "register source" --> Datasource
    Datasource -- "SQL query" --> Postgres
    DbtModel -- "materialize" --> Marts
    Marts -- "stable schema" --> Postgres
    Postgres -- "result rows" --> Panel
    Panel -- "render panel" --> Health
    Health -- "live updates" --> Browser

    class Postgres,Marts datastore
    class Grafana,MCP,DbtModel,Health service
    class Datasource,Panel event
    class Cursor,Browser io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
