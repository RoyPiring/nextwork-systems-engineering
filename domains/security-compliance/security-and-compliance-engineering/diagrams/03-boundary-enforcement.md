# Encrypt Data with AWS KMS

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-boundary-enforcement.md`](../documents/03-boundary-enforcement.md).

```mermaid
---
title: Encrypt Data with AWS KMS
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph IdentityLayer["Identity & Access"]
        IAMUser[/"IAM Principal"/]
        IAMPolicy("IAM Policy")
    end

    subgraph KMSBoundary["AWS KMS Boundary"]
        CMK{{"Customer-Managed Key"}}
        KeyPolicy("KMS Key Policy")
        DataKey{{"Envelope Data Key"}}
    end

    subgraph DataPlane["DynamoDB Data Plane"]
        DDBService("DynamoDB Service")
        DDBTable[("Encrypted Table")]
    end

    subgraph AuditLayer["Audit & Lifecycle"]
        CloudTrail("CloudTrail Key Usage")
    end

    IAMUser -- "PutItem request" --> DDBService
    IAMPolicy -- "authorizes principal" --> IAMUser
    DDBService -- "GenerateDataKey call" --> CMK
    KeyPolicy -- "gates key access" --> CMK
    CMK -- "returns data key" --> DataKey
    DataKey -- "encrypts at rest" --> DDBTable
    DDBService -- "writes ciphertext" --> DDBTable
    CMK -. "logs every use" .-> CloudTrail

    class DDBTable datastore
    class IAMPolicy,KeyPolicy,DDBService,CloudTrail service
    class CMK,DataKey event
    class IAMUser io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
