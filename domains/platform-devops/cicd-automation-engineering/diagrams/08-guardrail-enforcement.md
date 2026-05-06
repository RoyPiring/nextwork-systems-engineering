# Build a CI/CD Pipeline with AWS

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/08-guardrail-enforcement.md`](../documents/08-guardrail-enforcement.md).

```mermaid
---
title: Build a CI/CD Pipeline with AWS
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Source["Source Control"]
        GitHub[/"GitHub Repository"/]
        Dev[/"Developer Push"/]
    end

    subgraph Orchestration["Pipeline Orchestration"]
        CodePipeline{{"AWS CodePipeline"}}
        IAM{{"AWS IAM Roles"}}
    end

    subgraph BuildDeploy["Build and Deploy"]
        CodeBuild("AWS CodeBuild")
        CodeDeploy("AWS CodeDeploy")
        CFN("AWS CloudFormation")
    end

    subgraph Runtime["Artifacts and Runtime"]
        S3[("Amazon S3 Artifacts")]
        EC2[("Amazon EC2 Fleet")]
    end

    Dev -- "git push" --> GitHub
    GitHub -- "source webhook" --> CodePipeline
    CodePipeline -- "invoke build stage" --> CodeBuild
    CodeBuild -- "store build artifact" --> S3
    CodePipeline -- "trigger deploy stage" --> CodeDeploy
    S3 -- "fetch artifact" --> CodeDeploy
    CodeDeploy -- "release to instances" --> EC2
    CFN -- "provision infra" --> EC2
    IAM -- "scoped permissions" --> CodePipeline
    CodeDeploy -- "rollback on failure" --> EC2
class S3,EC2 datastore
class CodePipeline,IAM event

    class S3,EC2 datastore
    class CodeBuild,CodeDeploy,CFN service
    class CodePipeline,IAM event
    class GitHub,Dev io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
