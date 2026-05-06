# Data Engineering with Jupyter MCP

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-data-engineering-optimization.md`](../documents/03-data-engineering-optimization.md).

```mermaid
---
title: Data Engineering with Jupyter MCP
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Client["Analyst Workstation"]
        Cursor[/"Cursor (MCP Client)"/]
        Notebook("Jupyter Notebook")
    end

    subgraph Analysis["Interactive Analysis"]
        SQLCell("SQL Query Cell")
        Matplotlib{{"Matplotlib Charts"}}
    end

    subgraph Transform["dbt Transformation Layer"]
        DbtModel("dbt Model")
        DbtTests{{"dbt Tests"}}
    end

    subgraph Storage["Data Source"]
        Postgres[("PostgreSQL DB")]
    end

    Cursor -- "MCP connect" --> Notebook
    Notebook -- "exploratory SQL" --> SQLCell
    SQLCell -- "query" --> Postgres
    Postgres -- "result rows" --> SQLCell
    SQLCell -- "plot dataframe" --> Matplotlib
    SQLCell -- "promote logic" --> DbtModel
    DbtModel -- "materialize table" --> Postgres
    DbtModel -- "validate" --> DbtTests
    DbtTests -- "passing model" --> Notebook

    class Postgres datastore
    class Notebook,SQLCell,DbtModel service
    class Matplotlib,DbtTests event
    class Cursor io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
