# How I Built an API for My RAG Chatbot

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-rag-api-integration.md`](../documents/03-rag-api-integration.md).

```mermaid
---
title: How I Built an API for My RAG Chatbot
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ClientLayer["Client & API Layer"]
        Client[/"API Client"/]
        FastAPI("FastAPI Service")
    end

    subgraph KnowledgeStore["Knowledge Store"]
        S3[("Amazon S3 Documents")]
        VectorIdx[("Vector Index")]
    end

    subgraph BedrockCore["Amazon Bedrock Core"]
        Retriever("Retrieval Component")
        KB("Bedrock Knowledge Base")
        FM{{"Foundation Model"}}
    end

    subgraph DevTooling["Dev & Config Tooling"]
        AwsCli("AWS CLI / SDK")
    end

    Client -- "HTTP query" --> FastAPI
    FastAPI -- "retrieve request" --> Retriever
    Retriever -- "similarity search" --> VectorIdx
    VectorIdx -- "doc refs" --> S3
    S3 -- "source chunks" --> KB
    KB -- "grounded prompt" --> FM
    FM -- "inference response" --> FastAPI
    FastAPI -- "JSON answer" --> Client
    AwsCli -- "configure" --> KB

    class S3,VectorIdx datastore
    class FastAPI,Retriever,KB,AwsCli service
    class FM event
    class Client io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
