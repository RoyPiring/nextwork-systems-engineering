# Build a Calorie Tracker with Claude

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-claude-notion-calorie.md`](../documents/ai-claude-notion-calorie.md).

```mermaid
---
title: Build a Calorie Tracker with Claude
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User Layer"]
        User[/"User Input"/]
        Goals[/"User-Defined Goals"/]
    end

    subgraph ReasoningLayer["Claude Reasoning Layer"]
        ProjectInstr("Project Instructions")
        Claude{{"Claude (Reasoning)"}}
        PromptEng("Prompt Engineering")
    end

    subgraph IntegrationLayer["System Integration"]
        Connector{{"Notion Connector"}}
    end

    subgraph DataLayer["Notion Data Layer"]
        CalorieDB[("Calorie Database")]
    end

    User -- "log entry" --> Claude
    Goals -- "persistent context" --> ProjectInstr
    ProjectInstr -- "guardrails" --> Claude
    PromptEng -- "controlled prompts" --> Claude
    Claude -- "structured write" --> Connector
    Connector -- "create or update row" --> CalorieDB
    CalorieDB -- "stored entries" --> Connector
    Connector -- "fetch context" --> Claude
    Claude -- "insights and feedback" --> User
class CalorieDB datastore
class Claude,Connector event

    class CalorieDB datastore
    class ProjectInstr,PromptEng service
    class Claude,Connector event
    class User,Goals io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
