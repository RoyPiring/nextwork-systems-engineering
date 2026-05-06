# Explore Claude.ai, Code, and Cowork

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-claude-compare.md`](../documents/ai-claude-compare.md).

```mermaid
---
title: "Explore Claude.ai, Code, and Cowork"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Inputs["Inputs"]
        Analyst[/"Analyst"/]
        Dataset[("Cloud Salary Dataset")]
    end

    subgraph ClaudeTools["Claude Tool Suite"]
        ClaudeAi("Claude.ai Chat")
        ClaudeCode("Claude Code CLI")
        ClaudeCowork("Claude Cowork")
    end

    subgraph Workflow["AI-Assisted Workflow"]
        Explore{{"Data Exploration"}}
        Dashboard{{"Interactive Dashboard"}}
        Summary{{"Project Summary"}}
    end

    subgraph Outputs["Portfolio Artifacts"]
        Repo[("Project Repo")]
    end

    Analyst -- "uploads CSV" --> Dataset
    Dataset -- "conversational query" --> ClaudeAi
    Dataset -- "code interface" --> ClaudeCode
    ClaudeAi -- "quick visualization" --> Explore
    ClaudeCode -- "builds chart app" --> Dashboard
    ClaudeCowork -- "organizes outputs" --> Summary
    Explore -- "insights" --> ClaudeCowork
    Dashboard -- "dashboard files" --> ClaudeCowork
    Summary -- "publishes" --> Repo
class Dataset,Repo datastore
class Explore,Dashboard,Summary event

    class Dataset,Repo datastore
    class ClaudeAi,ClaudeCode,ClaudeCowork service
    class Explore,Dashboard,Summary event
    class Analyst io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
