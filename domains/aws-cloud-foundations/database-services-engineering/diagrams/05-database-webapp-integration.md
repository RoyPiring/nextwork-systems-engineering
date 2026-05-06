# Connect a Web App with Aurora

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-database-webapp-integration.md`](../documents/05-database-webapp-integration.md).

```mermaid
---
title: Connect a Web App with Aurora
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ClientLayer["Client Layer"]
        User[/"End User Browser"/]
    end

    subgraph AppTier["Application Tier (EC2)"]
        EC2[["EC2 Web App Instance"]]
        AppSG{{"App Security Group"}}
    end

    subgraph DataTier["Data Tier (Aurora)"]
        Endpoint("Aurora Cluster Endpoint")
        Aurora[("Aurora DB Cluster")]
        DBSG{{"DB Security Group"}}
    end

    subgraph AWSManaged["AWS-Managed Resilience"]
        MultiAZ("Multi-AZ Replication")
        Backups[("Automated Backups")]
    end

    User -- "HTTPS request" --> EC2
    EC2 -- "uses credentials" --> Endpoint
    Endpoint -- "SQL over DB port" --> Aurora
    AppSG -- "allows egress" --> DBSG
    DBSG -- "scoped inbound rule" --> Aurora
    Aurora -- "replicates across AZs" --> MultiAZ
    Aurora -- "snapshots to" --> Backups

    class Aurora,Backups datastore
    class Endpoint,MultiAZ service
    class AppSG,DBSG event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
