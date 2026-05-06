# Deploy an App Across Accounts

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-container-registry-ecr.md`](../documents/05-container-registry-ecr.md).

```mermaid
---
title: Deploy an App Across Accounts
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph PublisherAccount["Publisher AWS Account"]
        Developer[/"Developer / AWS CLI"/]
        Docker{{"Docker Build and Tag"}}
        ECR[("Amazon ECR Repository")]
    end

    subgraph AccessControl["Cross-Account Access Control"]
        RepoPolicy{{"ECR Repository Policy"}}
        IAMActions("ecr:BatchGetImage etc")
    end

    subgraph ConsumerAccount["Consumer AWS Account"]
        ConsumerCLI[/"Consumer AWS CLI"/]
        PullClient("Docker Pull Client")
    end

    subgraph Validation["Validation Outcomes"]
        PullOK("Authorized Image Pull")
        PullFail("Pull Failure on Gap")
    end

    Developer -- "build image" --> Docker
    Docker -- "push tagged image" --> ECR
    ECR -- "guarded by" --> RepoPolicy
    RepoPolicy -- "grants actions" --> IAMActions
    ConsumerCLI -- "auth token request" --> PullClient
    PullClient -- "GetDownloadUrlForLayer" --> ECR
    IAMActions -- "allow read" --> PullOK
    RepoPolicy -- "missing action" --> PullFail
class ECR datastore
class Docker,RepoPolicy event

    class ECR datastore
    class IAMActions,PullClient,PullOK,PullFail service
    class Docker,RepoPolicy event
    class Developer,ConsumerCLI io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
