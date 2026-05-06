# Join the 7 Day DevOps Challenge!

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-cicd-introduction.md`](../documents/01-cicd-introduction.md).

```mermaid
---
title: "Join the 7 Day DevOps Challenge!"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph SourceIntegration["Source Integration"]
        Developer[/"Developer Commit"/]
        SourceRepo[("Source Repository")]
    end

    subgraph BuildAndTest["Build & Automated Testing"]
        BuildJob("Build Job")
        TestSuite{{"Automated Test Suite"}}
        ArtifactStore[("Artifact Store")]
    end

    subgraph IaCAlignment["Infrastructure-as-Code"]
        IaCTemplate("IaC Template")
        CloudEnv("Cloud Environment")
    end

    subgraph DeliveryControl["Controlled Deployment"]
        PromotionGate{{"Promotion Gate"}}
        DeployJob("Deployment Job")
        ProdTarget[/"Production Target"/]
    end

    Developer -- "git push" --> SourceRepo
    SourceRepo -- "trigger pipeline" --> BuildJob
    BuildJob -- "run tests" --> TestSuite
    TestSuite -- "publish artifact" --> ArtifactStore
    ArtifactStore -- "request promotion" --> PromotionGate
    IaCTemplate -- "provision env" --> CloudEnv
    PromotionGate -- "approved release" --> DeployJob
    DeployJob -- "deploy to cloud" --> CloudEnv
    CloudEnv -- "serve traffic" --> ProdTarget
class SourceRepo,ArtifactStore datastore
class TestSuite,PromotionGate event

    class SourceRepo,ArtifactStore datastore
    class BuildJob,IaCTemplate,CloudEnv,DeployJob service
    class TestSuite,PromotionGate event
    class Developer,ProdTarget io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
