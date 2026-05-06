# Fetch Data with AWS Lambda

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-serverless-foundation-lambda.md`](../documents/01-serverless-foundation-lambda.md).

```mermaid
---
title: Fetch Data with AWS Lambda
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Caller["Caller / Test Surface"]
        Invoker[/"Test Invocation"/]
        Event[/"Event Payload (partition key)"/]
    end

    subgraph IAMScope["IAM Boundary"]
        ExecRole{{"Lambda Execution Role"}}
        Policy{{"Scoped DynamoDB Policy"}}
    end

    subgraph Compute["Serverless Compute"]
        LambdaFn("Lambda Read Function")
        SDK("AWS SDK GetItem Call")
    end

    subgraph Data["Data Layer"]
        Table[("DynamoDB User Table")]
    end

    Response[/"JSON Response"/]

    Invoker -- "invoke with event" --> LambdaFn
    Event -- "partition key input" --> LambdaFn
    ExecRole -- "assumes role" --> LambdaFn
    Policy -- "grants GetItem only" --> ExecRole
    LambdaFn -- "SDK GetItem request" --> SDK
    SDK -- "key-conditioned read" --> Table
    Table -- "item or empty" --> SDK
    SDK -- "structured result" --> LambdaFn
    LambdaFn -- "returns JSON" --> Response
class Table datastore
class ExecRole,Policy event

    class Table datastore
    class LambdaFn,SDK service
    class ExecRole,Policy event
    class Invoker,Event,Response io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
