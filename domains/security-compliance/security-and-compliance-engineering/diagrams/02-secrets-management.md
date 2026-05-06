# Secure Secrets with Secrets Manager

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-secrets-management.md`](../documents/02-secrets-management.md).

```mermaid
---
title: Secure Secrets with Secrets Manager
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph SourceControl["Source Control"]
        Developer[/"Developer"/]
        GitHubRepo[("GitHub Repository")]
    end

    subgraph RuntimeApp["Application Runtime"]
        WebApp("Web Application")
        SDKClient("AWS SDK Client")
    end

    subgraph SecretsPlane["AWS Secrets Plane"]
        SecretsManager[("AWS Secrets Manager")]
        IAMPolicy{{"IAM Access Policy"}}
        RotationJob{{"Rotation Schedule"}}
    end

    subgraph RejectedPath["Rejected Pattern"]
        Hardcoded("Hardcoded Credentials")
    end

    Developer -- "commit code" --> GitHubRepo
    GitHubRepo -- "deploys runtime" --> WebApp
    WebApp -- "request secret" --> SDKClient
    SDKClient -- "GetSecretValue" --> SecretsManager
    IAMPolicy -- "authorizes access" --> SDKClient
    SecretsManager -. "scheduled rotation" .-> RotationJob
    Hardcoded -. "blocked: exposure risk" .-x GitHubRepo

    class GitHubRepo,SecretsManager datastore
    class WebApp,SDKClient,Hardcoded service
    class IAMPolicy,RotationJob event
    class Developer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
