# Get Hands On with AWS Databases!

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-databases-introduction.md`](../documents/01-databases-introduction.md).

```mermaid
---
title: "Get Hands On with AWS Databases!"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph CloudPlatform["AWS Cloud Platform"]
        IAM("IAM Access Control")
        VPC("VPC Network Boundary")
    end

    subgraph RelationalTier["Relational Database Tier"]
        RDS[("Amazon RDS")]
        Aurora[("Amazon Aurora")]
    end

    subgraph NoSQLTier["NoSQL Database Tier"]
        DynamoDB[("Amazon DynamoDB")]
        DocumentDB[("Amazon DocumentDB")]
    end

    subgraph AppLayer["Cloud-Native Application"]
        AppSvc{{"Application Service"}}
        Eval[/"Service Selection Eval"/]
    end

    Eval -- "selects engine" --> AppSvc
    AppSvc -- "transactional writes" --> RDS
    AppSvc -- "high-throughput reads" --> Aurora
    AppSvc -- "key-value lookups" --> DynamoDB
    AppSvc -- "document queries" --> DocumentDB
    VPC -- "network isolation" --> RelationalTier
    VPC -- "network isolation" --> NoSQLTier
    IAM -- "managed scaling policy" --> AppSvc

    class RDS,Aurora,DynamoDB,DocumentDB datastore
    class IAM,VPC service
    class AppSvc event
    class Eval io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
