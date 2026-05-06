# Build a RAG API with FastAPI

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-devops-api.md`](../documents/01-ai-devops-api.md).

```mermaid
---
title: Build a RAG API with FastAPI
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Client["Client Layer"]
        User[/"User Question"/]
        HTTPClient[/"HTTP Client"/]
    end

    subgraph APILayer["FastAPI Service"]
        Uvicorn{{"Uvicorn ASGI Server"}}
        FastAPI("FastAPI App")
        RAGOrch("Python RAG Orchestrator")
    end

    subgraph Retrieval["Retrieval Layer"]
        Embedder("Embedding Function")
        Chroma[("Chroma Vector DB")]
        KnowledgeFiles[("Source Files")]
    end

    subgraph Generation["Local Generation"]
        Ollama{{"Ollama Runtime"}}
        LocalLLM("Local LLM")
    end

    User -- "question" --> HTTPClient
    HTTPClient -- "POST /query" --> Uvicorn
    Uvicorn -- "ASGI request" --> FastAPI
    FastAPI -- "invoke RAG" --> RAGOrch
    KnowledgeFiles -- "ingest + chunk" --> Embedder
    Embedder -- "store vectors" --> Chroma
    RAGOrch -- "semantic search" --> Chroma
    Chroma -. "top-k context" .-> RAGOrch
    RAGOrch -- "context + prompt" --> Ollama
    Ollama -- "load model" --> LocalLLM
    LocalLLM -. "grounded answer" .-> RAGOrch
    RAGOrch -- "JSON response" --> FastAPI

    class Chroma,KnowledgeFiles datastore
    class FastAPI,RAGOrch,Embedder,LocalLLM service
    class Uvicorn,Ollama event
    class User,HTTPClient io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
