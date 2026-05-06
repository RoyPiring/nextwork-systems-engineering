# Containerize a RAG API with Docker

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-devops-docker.md`](../documents/02-ai-devops-docker.md).

```mermaid
---
title: Containerize a RAG API with Docker
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Client["Client Layer"]
        User[/"API Caller"/]
    end

    subgraph AppRuntime["App Runtime (Container)"]
        Uvicorn{{"Uvicorn ASGI Server"}}
        FastAPI("FastAPI RAG API")
    end

    subgraph RAGCore["RAG Core Services"]
        Chroma[("Chroma Vector DB")]
        Ollama("Ollama Local LLM")
    end

    subgraph DockerPlane["Docker Build & Run"]
        Dockerfile{{"Dockerfile"}}
        Image[("RAG API Image")]
    end

    User -- "HTTP request" --> Uvicorn
    Uvicorn -- "ASGI dispatch" --> FastAPI
    FastAPI -- "similarity search" --> Chroma
    FastAPI -- "augmented prompt" --> Ollama
    Ollama -. "generated answer" .-> FastAPI
    Chroma -. "retrieved chunks" .-> FastAPI
    Dockerfile -- "docker build" --> Image
    Image -- "docker run" --> Uvicorn

    class Chroma,Image datastore
    class FastAPI,Ollama service
    class Uvicorn,Dockerfile event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
