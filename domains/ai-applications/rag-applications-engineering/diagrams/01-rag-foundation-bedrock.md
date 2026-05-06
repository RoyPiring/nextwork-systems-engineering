# Set Up a RAG Chatbot in Bedrock

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-rag-foundation-bedrock.md`](../documents/01-rag-foundation-bedrock.md).

```mermaid
---
title: Set Up a RAG Chatbot in Bedrock
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph UserLayer["User Layer"]
        User[/"End User Query"/]
        Answer[/"Grounded Answer"/]
    end

    subgraph SourceData["Source Data & Ingestion"]
        Docs[("S3 Document Store")]
        Chunker{{"Chunking Pipeline"}}
        Embedder{{"Embedding Model"}}
    end

    subgraph KnowledgeBase["Bedrock Knowledge Base"]
        KB("Bedrock KB Sync")
        VectorStore[("OpenSearch Serverless")]
    end

    subgraph Inference["Retrieval & Inference"]
        Retriever("Semantic Search")
        FoundationModel("Bedrock Foundation Model")
    end

    Docs -- "raw documents" --> Chunker
    Chunker -- "text chunks" --> Embedder
    Embedder -- "vector embeddings" --> VectorStore
    KB -- "sync index" --> VectorStore

    User -- "question" --> Retriever
    Retriever -- "top-k vectors" --> VectorStore
    VectorStore -- "matched context" --> FoundationModel
    FoundationModel -- "grounded response" --> Answer

    class Docs,VectorStore datastore
    class KB,Retriever,FoundationModel service
    class Chunker,Embedder event
    class User,Answer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
