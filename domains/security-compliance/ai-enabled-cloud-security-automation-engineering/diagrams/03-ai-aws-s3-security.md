# AI Security Scanner for AWS S3

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-aws-s3-security.md`](../documents/03-ai-aws-s3-security.md).

```mermaid
---
title: AI Security Scanner for AWS S3
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Schedule["Scheduled Trigger"]
        EventBridge{{"EventBridge Rule"}}
    end

    subgraph Compute["Serverless Scanner"]
        Lambda("Lambda: S3 Scanner")
        Boto3("boto3 AWS SDK")
        IAMRole[/"Least-Privilege IAM Role"/]
        EnvSecret[/"Env Var: GEMINI_API_KEY"/]
    end

    subgraph Target["Scan Target"]
        S3[("Amazon S3 Buckets")]
    end

    subgraph Analysis["AI Analysis"]
        Gemini{{"Google Gemini AI"}}
        Findings[("Encryption Findings")]
    end

    EventBridge -- "cron invoke" --> Lambda
    IAMRole -- "assumed by" --> Lambda
    Lambda -- "boto3 call" --> Boto3
    Boto3 -- "GetBucketEncryption" --> S3
    S3 -- "config payload" --> Lambda
    EnvSecret -- "inject at runtime" --> Lambda
    Lambda -- "prompt + config" --> Gemini
    Gemini -- "risk insights" --> Findings
class S3,Findings datastore
class EventBridge,Gemini event

    class S3,Findings datastore
    class Lambda,Boto3 service
    class EventBridge,Gemini event
    class IAMRole,EnvSecret io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
