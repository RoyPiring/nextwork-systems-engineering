# Aurora Database with EC2

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-relational-aurora.md`](../documents/04-relational-aurora.md).

```mermaid
---
title: Aurora Database with EC2
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ClientTier["Client Tier"]
        Client[/"Web Client"/]
    end

    subgraph ComputeTier["Compute Tier (VPC)"]
        EC2["EC2 App Instance"]
        AppSG{{"App Security Group"}}
    end

    subgraph DataTier["Data Tier (Aurora Cluster)"]
        Writer[("Aurora Writer")]
        Reader[("Aurora Reader")]
        DBSG{{"DB Security Group"}}
        Backups[("Automated Backups")]
    end

    subgraph Ops["Ops & Failover"]
        Failover("Managed Failover")
    end

    Client -- "HTTPS request" --> EC2
    EC2 -- "ingress allowed" --> AppSG
    AppSG -- "app-to-db traffic" --> DBSG
    DBSG -- "writes" --> Writer
    Writer -- "replication" --> Reader
    EC2 -- "scalable reads" --> Reader
    Writer -- "snapshots" --> Backups
    Failover -. "promote on fault" .-> Reader

    class Writer,Reader,Backups datastore
    class Failover service
    class AppSG,DBSG event
    class Client io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
