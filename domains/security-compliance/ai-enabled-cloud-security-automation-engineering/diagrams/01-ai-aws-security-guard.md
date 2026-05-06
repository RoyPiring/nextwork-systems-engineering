# Build an AI Security Guard for AWS

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-aws-security-guard.md`](../documents/01-ai-aws-security-guard.md).

```mermaid
---
title: Build an AI Security Guard for AWS
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DevEnv["Local Dev Environment"]
        Cursor[/"Cursor IDE (AI agent)"/]
        UV("uv (Python 3.12 env)")
        Scanner("boto3 S3 Scanner")
    end

    subgraph AccessLayer["AWS Access Layer"]
        AwsMcp{{"AWS MCP Server"}}
        AwsCli("AWS CLI (credentials)")
    end

    subgraph CloudTarget["AWS Cloud Target"]
        S3[("Amazon S3 Buckets")]
        Findings[("Misconfig Findings")]
    end

    subgraph RemediationLoop["AI Remediation Loop"]
        Remediator{{"AI-Assisted Fixer"}}
    end

    Cursor -- "invoke tools" --> AwsMcp
    UV -- "runs scanner" --> Scanner
    AwsMcp -- "auth via CLI" --> AwsCli
    Scanner -- "list / get-policy" --> S3
    S3 -- "config + ACLs" --> Findings
    Findings -- "insecure config" --> Remediator
    Remediator -- "put-policy fix" --> S3
    Cursor -- "review + approve" --> Remediator
class S3,Findings datastore
class AwsMcp,Remediator event

    class S3,Findings datastore
    class UV,Scanner,AwsCli service
    class AwsMcp,Remediator event
    class Cursor io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
