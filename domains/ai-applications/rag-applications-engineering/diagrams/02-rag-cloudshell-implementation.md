# Interacting With My RAG Chatbot in the Terminal

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-rag-cloudshell-implementation.md`](../documents/02-rag-cloudshell-implementation.md).

```mermaid
---
title: Interacting With My RAG Chatbot in the Terminal
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Operator["Operator Surface"]
        User[/"Engineer Terminal"/]
        CLI(("AWS CLI"))
    end

    subgraph Execution["CloudShell Execution"]
        Shell["CloudShell Session"]
        IAM{{"IAM-Scoped Role"}}
    end

    subgraph DataPlane["Knowledge Data Plane"]
        S3[("Amazon S3 Bucket")]
        KB[("Bedrock Knowledge Base")]
    end

    subgraph Inference["Bedrock Inference"]
        Retriever("Retrieve API")
        Model("Foundation Model")
    end

    User -- "invoke command" --> CLI
    CLI -- "executes in" --> Shell
    Shell -- "assumes role" --> IAM
    IAM -- "scoped access" --> Retriever
    S3 -- "indexed docs" --> KB
    Retriever -- "query KB" --> KB
    KB -- "grounded chunks" --> Model
    Model -- "generated answer" --> Shell
    Shell -- "stdout response" --> User

    class S3,KB datastore
    class Retriever,Model service
    class IAM event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
