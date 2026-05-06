# Load Data into DynamoDB

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-nosql-dynamodb.md`](../documents/02-nosql-dynamodb.md).

```mermaid
---
title: Load Data into DynamoDB
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Operator["Operator Console"]
        User[/"AWS Account User"/]
        CloudShell{{"AWS CloudShell"}}
        CLI{{"AWS CLI"}}
    end

    subgraph ControlPlane["DynamoDB Control Plane"]
        TableDef("Table Definition")
        Capacity("Read/Write Capacity")
        PrimaryKey("Primary Key Attrs")
    end

    subgraph DataPlane["DynamoDB Data Plane"]
        Table[("DynamoDB Table")]
        Items[("Sample Items")]
    end

    User -- "opens session" --> CloudShell
    CloudShell -- "invokes" --> CLI
    CLI -- "create-table" --> TableDef
    TableDef -- "defines schema" --> PrimaryKey
    TableDef -- "provisions" --> Capacity
    Capacity -- "allocates" --> Table
    PrimaryKey -- "indexes" --> Table
    CLI -- "put-item batch" --> Items
    Items -- "stored in" --> Table

    class Table,Items datastore
    class TableDef,Capacity,PrimaryKey service
    class CloudShell,CLI event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
