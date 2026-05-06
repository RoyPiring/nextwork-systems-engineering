# APIs with Lambda + API Gateway

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-api-layer-gateway-lambda.md`](../documents/02-api-layer-gateway-lambda.md).

```mermaid
---
title: APIs with Lambda + API Gateway
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Client["Client Layer"]
        HttpClient[/"HTTP Client"/]
    end

    subgraph EdgeApi["API Edge"]
        Gateway{{"Amazon API Gateway"}}
        Stage(("Deployment Stage"))
    end

    subgraph Compute["Serverless Compute"]
        Lambda{{"AWS Lambda Function"}}
        ExecRole("Lambda Execution Role")
    end

    subgraph Data["Persistent Storage"]
        DynamoDB[("Amazon DynamoDB Table")]
    end

    HttpClient -- "REST request" --> Gateway
    Gateway -- "routed via stage" --> Stage
    Stage -- "method integration" --> Lambda
    ExecRole -- "scoped IAM policy" --> Lambda
    Lambda -- "GetItem / PutItem" --> DynamoDB
    DynamoDB -- "item payload" --> Lambda
    Lambda -- "JSON response" --> Gateway
    Gateway -- "HTTP 200" --> HttpClient
class DynamoDB datastore
class Gateway,Lambda event

    class DynamoDB datastore
    class ExecRole service
    class Gateway,Lambda event
    class HttpClient io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
