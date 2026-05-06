# How to Use DeepSeek

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-llm-deepseek.md`](../documents/03-ai-llm-deepseek.md).

```mermaid
---
title: How to Use DeepSeek
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph ClientLayer["Client Layer"]
        User[/"User Prompt"/]
        Chatbox("Chatbox Client")
    end

    subgraph LocalRuntime["Local Runtime (Ollama)"]
        Ollama{{"Ollama Orchestrator"}}
        DeepSeek("DeepSeek R1 (7B/14B/68B)")
        ModelStore[("Local Model Store")]
    end

    subgraph HostedBaseline["Hosted Baseline"]
        OpenAI("OpenAI ChatGPT API")
    end

    subgraph EvalHarness["Evaluation Harness"]
        Compare{{"Capability + Latency Compare"}}
        Report[("Eval Report")]
    end

    User -- "prompt text" --> Chatbox
    Chatbox -- "local serve request" --> Ollama
    Ollama -- "load variant" --> ModelStore
    ModelStore -- "weights" --> DeepSeek
    Ollama -- "inference call" --> DeepSeek
    DeepSeek -- "local response" --> Compare
    Chatbox -- "baseline prompt" --> OpenAI
    OpenAI -- "hosted response" --> Compare
    Compare -- "scored deltas" --> Report
    Report -- "viable within limits" --> User
class ModelStore,Report datastore
class Ollama,Compare event

    class ModelStore,Report datastore
    class Chatbox,DeepSeek,OpenAI service
    class Ollama,Compare event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
