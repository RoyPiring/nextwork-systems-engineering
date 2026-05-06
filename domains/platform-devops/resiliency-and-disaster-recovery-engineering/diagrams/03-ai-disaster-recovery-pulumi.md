# Multi-Cloud Disaster Recovery with Pulumi

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-disaster-recovery-pulumi.md`](../documents/03-ai-disaster-recovery-pulumi.md).

```mermaid
---
title: Multi-Cloud Disaster Recovery with Pulumi
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph IaCControl["IaC Control Plane"]
        Pulumi("Pulumi Project")
        TSCode[/"TypeScript Definitions"/]
        StateFile[("Pulumi State")]
    end

    subgraph AWSRegion["AWS Primary Region"]
        AppRunner("AWS App Runner")
        AWSCreds{{"AWS Credentials"}}
    end

    subgraph GCPRegion["GCP Failover Region"]
        CloudRun("GCP Cloud Run")
        GCPCreds{{"GCP Credentials"}}
    end

    subgraph FailoverFlow["Three-Way Failover"]
        Imports("Resource Imports")
        Failover[/"Traffic Failover"/]
    end

    TSCode -- "declares resources" --> Pulumi
    Pulumi -- "deploys via" --> AWSCreds
    Pulumi -- "deploys via" --> GCPCreds
    AWSCreds -- "provisions" --> AppRunner
    GCPCreds -- "provisions" --> CloudRun
    Imports -- "syncs live infra" --> StateFile
    Pulumi -- "tracks state" --> StateFile
    AppRunner -- "primary traffic" --> Failover
    CloudRun -- "backup traffic" --> Failover

    class StateFile datastore
    class Pulumi,AppRunner,CloudRun,Imports service
    class AWSCreds,GCPCreds event
    class TSCode,Failover io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
