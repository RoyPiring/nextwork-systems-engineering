# Query Data with DynamoDB

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-query-optimization.md`](../documents/03-query-optimization.md).

```mermaid
---
title: Query Data with DynamoDB
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Operator["Operator Surface"]
        Analyst[/"CLI Analyst"/]
        CloudShell[/"AWS CloudShell"/]
    end

    subgraph KeySchema["Key Schema Design"]
        PartitionKey{{"Partition Key"}}
        SortKey{{"Sort Key"}}
        GSI{{"Secondary Index"}}
    end

    subgraph AccessAPI["DynamoDB Access API"]
        GetItem("GetItem")
        Query("Query")
        Scan("Scan")
    end

    subgraph Storage["Managed NoSQL Store"]
        Table[("DynamoDB Table")]
    end

    Analyst -- "issues commands" --> CloudShell
    CloudShell -- "single-item lookup" --> GetItem
    CloudShell -- "key-range read" --> Query
    CloudShell -- "full-table read" --> Scan

    PartitionKey -- "shards data" --> Table
    SortKey -- "orders items" --> Table
    GSI -- "alt access path" --> Table

    GetItem -- "by primary key" --> Table
    Query -- "uses partition+sort" --> Table
    Scan -. "inefficient fallback" .-> Table

    class Table datastore
    class GetItem,Query,Scan service
    class PartitionKey,SortKey,GSI event
    class Analyst,CloudShell io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
