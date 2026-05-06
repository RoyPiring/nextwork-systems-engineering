# Infrastructure as Code with CloudFormation

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-infrastructure-cloudformation.md`](../documents/04-infrastructure-cloudformation.md).

```mermaid
---
title: Infrastructure as Code with CloudFormation
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph IaCLayer["IaC Orchestration"]
        Template[/"CloudFormation Template"/]
        Stack{{"Stack Deployment Event"}}
    end

    subgraph IdentityCompute["Identity and Compute"]
        IAM("AWS IAM Roles")
        EC2("Amazon EC2 Instance")
    end

    subgraph PipelineServices["CI/CD Pipeline Services"]
        CodeArtifact("AWS CodeArtifact")
        CodeBuild("AWS CodeBuild")
        CodeDeploy("AWS CodeDeploy")
    end

    subgraph Storage["Artifact Storage"]
        S3[("Amazon S3 Bucket")]
    end

    Template -- "submit stack" --> Stack
    Stack -- "provisions roles" --> IAM
    IAM -- "grants permissions" --> EC2
    Stack -- "creates bucket" --> S3
    Stack -- "provisions repo" --> CodeArtifact
    CodeArtifact -- "supplies dependencies" --> CodeBuild
    CodeBuild -- "publishes artifacts" --> S3
    S3 -- "deploy package" --> CodeDeploy
    CodeDeploy -- "releases to" --> EC2
class S3 datastore
class Stack event

    class S3 datastore
    class IAM,EC2,CodeArtifact,CodeBuild,CodeDeploy service
    class Stack event
    class Template io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
