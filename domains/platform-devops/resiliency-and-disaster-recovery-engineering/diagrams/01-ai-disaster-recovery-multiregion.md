# Build Multi-Region Apps on AWS

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-disaster-recovery-multiregion.md`](../documents/01-ai-disaster-recovery-multiregion.md).

```mermaid
---
title: Build Multi-Region Apps on AWS
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph SourceControl["Source Control & CI"]
        GitHub[("GitHub Repository")]
        ExpressApp("Express.js App")
    end

    subgraph RegionA["AWS Region A (Primary)"]
        AppRunnerA{{"App Runner Service A"}}
        EndpointA[/"Public Endpoint A"/]
    end

    subgraph RegionB["AWS Region B (Failover)"]
        AppRunnerB{{"App Runner Service B"}}
        EndpointB[/"Public Endpoint B"/]
    end

    subgraph Clients["Users"]
        User[/"End User Traffic"/]
    end

    ExpressApp -- "commit & push" --> GitHub
    GitHub -- "auto-deploy region A" --> AppRunnerA
    GitHub -- "auto-deploy region B" --> AppRunnerB
    AppRunnerA -- "serves requests" --> EndpointA
    AppRunnerB -- "serves requests" --> EndpointB
    User -- "primary path" --> EndpointA
    User -. "failover path" .-> EndpointB

    class GitHub datastore
    class ExpressApp service
    class AppRunnerA,AppRunnerB event
    class EndpointA,EndpointB,User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
