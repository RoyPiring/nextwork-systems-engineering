# Multi-Cloud Data Transfer with AWS and GCP

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-aws-multicloud-storage.md`](../documents/02-aws-multicloud-storage.md).

```mermaid
---
title: Multi-Cloud Data Transfer with AWS and GCP
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph AWSSource["AWS Source Cloud"]
        S3[("S3 Source Bucket")]
        IAMRole{{"AWS IAM Role"}}
    end

    subgraph IdentityFederation["Identity Federation"]
        TrustRel{{"Trust Relationship"}}
        GCPIdentity{{"GCP Service Identity"}}
    end

    subgraph GCPTransfer["GCP Transfer Plane"]
        STS("Storage Transfer Service")
        SQS[/"Amazon SQS Queue"/]
    end

    subgraph GCPDest["GCP Destination Cloud"]
        GCS[("GCS Destination Bucket")]
    end

    GCPIdentity -- "assume role request" --> TrustRel
    TrustRel -- "scoped read access" --> IAMRole
    IAMRole -- "list and get objects" --> S3
    STS -- "federated read" --> S3
    STS -- "track transfer state" --> SQS
    SQS -- "object coordination" --> STS
    STS -- "write transferred objects" --> GCS
class S3,GCS datastore
class IAMRole,TrustRel,GCPIdentity event

    class S3,GCS datastore
    class STS service
    class IAMRole,TrustRel,GCPIdentity event
    class SQS io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
