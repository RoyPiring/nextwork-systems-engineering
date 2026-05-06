# Build a Three-Tier Web App

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-complete-three-tier-application.md`](../documents/03-complete-three-tier-application.md).

```mermaid
---
title: Build a Three-Tier Web App
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Presentation["Presentation Tier"]
        User[/"End User Browser"/]
        CDN("Amazon CloudFront")
        Bucket[("Amazon S3 Static Assets")]
    end

    subgraph Logic["Logic Tier"]
        APIGW{{"Amazon API Gateway"}}
        Lambda("AWS Lambda Handler")
    end

    subgraph Data["Data Tier"]
        DDB[("Amazon DynamoDB")]
    end

    subgraph CrossCutting["Cross-Cutting Concerns"]
        CORS{{"CORS Policy"}}
    end

    User -- "loads SPA" --> CDN
    CDN -- "edge cache fetch" --> Bucket
    User -- "REST request" --> APIGW
    APIGW -- "invoke handler" --> Lambda
    Lambda -- "read / write item" --> DDB
    DDB -- "low-latency response" --> Lambda
    Lambda -- "JSON payload" --> APIGW
    CORS -- "enforces origin" --> APIGW
class Bucket,DDB datastore
class APIGW,CORS event

    class Bucket,DDB datastore
    class CDN,Lambda service
    class APIGW,CORS event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
