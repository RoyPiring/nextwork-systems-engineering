# Building a RAG Chatbot with a Web Interface

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-rag-complete-webapp.md`](../documents/04-rag-complete-webapp.md).

```mermaid
---
title: Building a RAG Chatbot with a Web Interface
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ClientLayer["Client Layer"]
        Browser[/"User Browser"/]
        QueryUI[/"Query Form"/]
    end

    subgraph WebApp["FastAPI Web Layer"]
        Router("FastAPI Router")
        QueryHandler("Query Handler")
    end

    subgraph IdentityRetrieval["Identity & Retrieval"]
        IAM{{"AWS IAM (scoped creds)"}}
        KB[("S3 Knowledge Base")]
    end

    subgraph Inference["Bedrock Inference"]
        Bedrock("Amazon Bedrock")
        RAGEngine("Retrieval-Augmented Gen")
    end

    Browser -- "user query" --> QueryUI
    QueryUI -- "HTTP POST" --> Router
    Router -- "route request" --> QueryHandler
    QueryHandler -- "assume role" --> IAM
    IAM -. "scoped token" .-> Bedrock
    QueryHandler -- "retrieve context" --> KB
    KB -- "grounding chunks" --> RAGEngine
    RAGEngine -- "augmented prompt" --> Bedrock
    Bedrock -. "grounded response" .-> QueryHandler
    QueryHandler -- "rendered answer" --> Browser

    class KB datastore
    class Router,QueryHandler,Bedrock,RAGEngine service
    class IAM event
    class Browser,QueryUI io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
