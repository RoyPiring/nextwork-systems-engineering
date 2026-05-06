# Secure Packages with CodeArtifact

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/06-package-management-codeartifact.md`](../documents/06-package-management-codeartifact.md).

```mermaid
---
title: Secure Packages with CodeArtifact
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph SourceControl["Source Control"]
        GitHub[/"GitHub Repo (Java app)"/]
    end

    subgraph BuildEnv["Build Environment (EC2)"]
        EC2{{"Amazon EC2 Instance"}}
        Maven("Maven Build Tool")
        InstanceProfile("EC2 Instance Profile")
    end

    subgraph IdentityAccess["Identity and Access"]
        IAMRole("IAM Role + Policy")
        AuthToken[/"CodeArtifact Auth Token"/]
    end

    subgraph ArtifactPlane["AWS CodeArtifact"]
        PrivateRepo[("Private Java Repo")]
        Upstream[("Upstream Public Mirror")]
    end

    GitHub -- "clone source" --> EC2
    EC2 -- "assumes role" --> InstanceProfile
    InstanceProfile -- "grants permissions" --> IAMRole
    IAMRole -- "issues short-lived token" --> AuthToken
    Maven -- "authenticated pull" --> PrivateRepo
    AuthToken -. "bearer auth" .-> PrivateRepo
    PrivateRepo -- "cache miss fetch" --> Upstream
    Upstream -. "cached dependency" .-> PrivateRepo
    PrivateRepo -- "resolved JARs" --> Maven
    EC2 -- "runs build" --> Maven
class PrivateRepo,Upstream datastore
class EC2 event

    class PrivateRepo,Upstream datastore
    class Maven,InstanceProfile,IAMRole service
    class EC2 event
    class GitHub,AuthToken io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
