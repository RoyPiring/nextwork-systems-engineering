# Continuous Integration with CodeBuild

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-build-automation-codebuild.md`](../documents/05-build-automation-codebuild.md).

```mermaid
---
title: Continuous Integration with CodeBuild
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph SourceControl["Source Control"]
        GitHubRepo[/"GitHub Repository"/]
        Webhook(("Push Webhook"))
    end

    subgraph BuildExecution["Build Execution"]
        CodeBuildProj{{"AWS CodeBuild Project"}}
        BuildSpec("buildspec.yml")
    end

    subgraph IdentityLayer["Identity and Permissions"]
        ServiceRole{{"CodeBuild Service Role"}}
        IAMPolicy("S3 Write Policy")
    end

    subgraph ArtifactPersistence["Artifact Persistence"]
        ArtifactBucket[("Amazon S3 Artifact Bucket")]
        BuildLogs[("CloudWatch Build Logs")]
    end

    GitHubRepo -- "source change" --> Webhook
    Webhook -- "triggers build" --> CodeBuildProj
    CodeBuildProj -- "reads steps" --> BuildSpec
    CodeBuildProj -- "assumes role" --> ServiceRole
    ServiceRole -- "grants access" --> IAMPolicy
    IAMPolicy -- "allows put-object" --> ArtifactBucket
    CodeBuildProj -- "uploads package" --> ArtifactBucket
    CodeBuildProj -- "streams output" --> BuildLogs
class ArtifactBucket,BuildLogs datastore
class CodeBuildProj,ServiceRole event

    class ArtifactBucket,BuildLogs datastore
    class BuildSpec,IAMPolicy service
    class CodeBuildProj,ServiceRole event
    class GitHubRepo io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
