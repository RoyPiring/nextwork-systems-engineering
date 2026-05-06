# Prompt Engineering For ChatGPT

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-ai-promptengineering.md`](../documents/04-ai-promptengineering.md).

```mermaid
---
title: Prompt Engineering For ChatGPT
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User Intent Layer"]
        User[/"User Intent"/]
        Refiner[/"Iterative Refiner"/]
    end

    subgraph PromptDesign["Prompt Engineering"]
        Templates(("Prompt Templates"))
        Techniques("Role / Format / Chaining")
        MetaPrompt{{"Meta-Prompt Generator"}}
    end

    subgraph Execution["ChatGPT Execution"]
        ChatGPT("ChatGPT LLM")
        Response[/"Structured Response"/]
    end

    subgraph QualityLoop["Evaluation Loop"]
        Evaluator{{"Response Evaluator"}}
        Library[("Template Library")]
    end

    User -- "raw goal" --> Templates
    Templates -- "framework prompt" --> Techniques
    MetaPrompt -- "generates template" --> Templates
    Techniques -- "scoped prompt" --> ChatGPT
    ChatGPT -- "model output" --> Response
    Response -- "score relevance" --> Evaluator
    Evaluator -- "refine signal" --> Refiner
    Refiner -- "revised intent" --> User
    Evaluator -- "promote winners" --> Library
    Library -- "reuse pattern" --> Templates
class Library datastore
class MetaPrompt,Evaluator event

    class Library datastore
    class Techniques,ChatGPT service
    class MetaPrompt,Evaluator event
    class User,Refiner,Response io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
