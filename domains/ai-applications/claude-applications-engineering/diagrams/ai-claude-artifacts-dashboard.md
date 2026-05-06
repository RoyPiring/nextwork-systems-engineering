# Build a Dashboard with Claude Artifacts

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-claude-artifacts-dashboard.md`](../documents/ai-claude-artifacts-dashboard.md).

```mermaid
---
title: Build a Dashboard with Claude Artifacts
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DataLayer["Data Layer"]
        CSV[("Raw CSV Data")]
        Schema[/"Column Schema"/]
    end

    subgraph PromptLayer["Prompt Engineering"]
        User[/"Builder"/]
        Prompt("Structured Prompt")
        Refine{{"Iteration Loop"}}
    end

    subgraph Generation["Claude Artifacts Runtime"]
        Claude("Claude.ai Artifacts")
        Recharts("Recharts Components")
    end

    subgraph Dashboard["Interactive Dashboard"]
        Filters[/"Filters and Controls"/]
        Charts[/"Live Charts"/]
    end

    CSV -- "rows and columns" --> Schema
    Schema -- "context for prompt" --> Prompt
    User -- "writes spec" --> Prompt
    Prompt -- "generation request" --> Claude
    Claude -- "renders artifact" --> Recharts
    Recharts -- "mounts UI" --> Charts
    Recharts -- "wires controls" --> Filters
    Filters -- "query state" --> Charts
    Charts -. "feedback on output" .-> Refine
    Refine -- "tighter prompt" --> Prompt
class CSV datastore
class Refine event

    class CSV datastore
    class Prompt,Claude,Recharts service
    class Refine event
    class Schema,User,Filters,Charts io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
