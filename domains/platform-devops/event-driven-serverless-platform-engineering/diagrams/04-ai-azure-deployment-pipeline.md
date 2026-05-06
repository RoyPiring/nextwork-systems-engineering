# GitHub to Azure DevOps Pipeline

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-ai-azure-deployment-pipeline.md`](../documents/04-ai-azure-deployment-pipeline.md).

```mermaid
---
title: GitHub to Azure DevOps Pipeline
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Source["Source Control"]
        GitHub[/"GitHub Repository"/]
        YAML("azure-pipelines.yml")
    end

    subgraph Orchestration["Azure DevOps Orchestration"]
        Pipeline("Azure DevOps Pipeline")
        Agent{{"Self-Hosted Agent"}}
        SvcConn{{"Azure Service Connection"}}
    end

    subgraph Environments["Environment Separation"]
        Staging[("Staging Functions")]
        Gate{{"Deployment Gate"}}
        Prod[("Production Functions")]
    end

    GitHub -- "push triggers CI" --> Pipeline
    YAML -- "pipeline definition" --> Pipeline
    Pipeline -- "dispatches job" --> Agent
    Agent -- "auth via OIDC" --> SvcConn
    SvcConn -- "deploy artifact" --> Staging
    Staging -- "smoke tests pass" --> Gate
    Gate -- "manual approval" --> Prod

    class Staging,Prod datastore
    class YAML,Pipeline service
    class Agent,SvcConn,Gate event
    class GitHub io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
