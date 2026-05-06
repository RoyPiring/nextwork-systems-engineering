# Join the Cloud Beginner Challenge!

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-aws-beginners-challenge.md`](../documents/02-aws-beginners-challenge.md).

```mermaid
---
title: "Join the Cloud Beginner Challenge!"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph OnPrem["On-Premises Model"]
        DataCenter[("Owned Data Center")]
        CapEx{{"Capital Expenditure"}}
    end

    subgraph AWSPrimitives["AWS Managed Primitives"]
        Compute[/"Compute"/]
        Storage[/"Storage"/]
        Database[/"Databases"/]
        Network[/"Networking"/]
    end

    subgraph Consumers["Technical Roles"]
        InfraEng("Infrastructure Engineer")
        DevOps("DevOps / Security")
        DataEng("Data Disciplines")
    end

    DataCenter -- "shifted to cloud" --> Compute
    CapEx -- "becomes elastic opex" --> Storage
    Compute -- "on-demand access" --> InfraEng
    Storage -- "managed services" --> DevOps
    Database -- "shared primitives" --> DataEng
    Network -- "delivered over internet" --> InfraEng
class DataCenter datastore
class CapEx event

    class DataCenter datastore
    class InfraEng,DevOps,DataEng service
    class CapEx event
    class Compute,Storage,Database,Network io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
