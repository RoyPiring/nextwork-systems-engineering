# Prompt Engineering for Research

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-prompt-engineering-research.md`](../documents/ai-prompt-engineering-research.md).

```mermaid
---
title: Prompt Engineering for Research
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Inputs["Inputs"]
        Researcher[/"Researcher"/]
        Dataset[/"Sample Dataset"/]
    end

    subgraph PromptLib["Prompt Technique Library"]
        RolePrompt("Role Prompting")
        CoTPrompt("Chain-of-Thought")
        AdvPrompt("Adversarial Critique")
    end

    subgraph Workflow["Iterative Refinement Workflow"]
        Composer{{"Prompt Composer"}}
        Claude("Claude LLM")
        Refiner{{"Iterative Refiner"}}
    end

    subgraph Outputs["Outputs"]
        Insights[("Structured Insights")]
    end

    Researcher -- "research task" --> Composer
    Dataset -- "sample inputs" --> Composer
    Composer -- "role + CoT prompt" --> Claude
    RolePrompt --> Composer
    CoTPrompt --> Composer
    AdvPrompt -- "critique pass" --> Refiner
    Claude -- "draft response" --> Refiner
    Refiner -- "refined prompt" --> Claude
    Refiner -- "final output" --> Insights

    class Insights datastore
    class RolePrompt,CoTPrompt,AdvPrompt,Claude service
    class Composer,Refiner event
    class Researcher,Dataset io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
