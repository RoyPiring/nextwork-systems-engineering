# Deploy a Web App with CodeDeploy

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/09-rollback-procedure.md`](../documents/09-rollback-procedure.md).

```mermaid
---
title: Deploy a Web App with CodeDeploy
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Source["Source & Identity"]
        GitHub[/"GitHub Repository"/]
        IAMRole{{"IAM Service Role"}}
    end

    subgraph Orchestration["Deployment Orchestration"]
        CodeDeploy("AWS CodeDeploy")
        AppSpec("appspec.yml Lifecycle")
    end

    subgraph Runtime["EC2 Runtime"]
        EC2[("EC2 Instance")]
        WebApp("Deployed Web App")
    end

    subgraph Recovery["Rollback Path"]
        PrevRevision[("Previous Revision")]
        RollbackEvent{{"Rollback Trigger"}}
    end

    GitHub -- "source revision" --> CodeDeploy
    IAMRole -- "assume role" --> CodeDeploy
    CodeDeploy -- "deploy bundle" --> EC2
    AppSpec -- "lifecycle hooks" --> EC2
    EC2 -- "serves traffic" --> WebApp
    WebApp -- "health check fail" --> RollbackEvent
    RollbackEvent -- "redeploy last good" --> PrevRevision
    PrevRevision -- "restore revision" --> CodeDeploy
class EC2,PrevRevision datastore
class IAMRole,RollbackEvent event

    class EC2,PrevRevision datastore
    class CodeDeploy,AppSpec,WebApp service
    class IAMRole,RollbackEvent event
    class GitHub io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
