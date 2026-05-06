# Review GitHub Pull Requests with Gemini

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-cicd-codereview.md`](../documents/02-ai-cicd-codereview.md).

```mermaid
---
title: Review GitHub Pull Requests with Gemini
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DeveloperLayer["Developer Layer"]
        Dev[/"Developer"/]
        PR[/"Pull Request"/]
    end

    subgraph CIAutomation["GitHub Actions CI"]
        Workflow{{"PR-trigger Workflow"}}
        DiffStep("Diff Extraction Step")
        Secrets[("Encrypted Secrets Store")]
    end

    subgraph ReviewEngine["AI Review Engine"]
        Orchestrator("Python Orchestrator")
        PromptBuilder("Prompt Builder")
        Gemini("Gemini API")
        ErrorGuard{{"Defensive Error Handler"}}
    end

    subgraph PRSurface["PR Feedback Surface"]
        ReviewComment[/"Inline Review Comment"/]
        Reviewer[/"Human Reviewer"/]
    end

    Dev -- "opens PR" --> PR
    PR -- "pull_request event" --> Workflow
    Workflow -- "checkout + diff" --> DiffStep
    Secrets -- "GEMINI_API_KEY" --> Orchestrator
    DiffStep -- "structured diff" --> Orchestrator
    Orchestrator -- "build review prompt" --> PromptBuilder
    PromptBuilder -- "prompt + diff" --> Gemini
    Gemini -- "AI findings" --> ErrorGuard
    ErrorGuard -- "safe response" --> Orchestrator
    Orchestrator -- "post review" --> ReviewComment
    ReviewComment -- "augments review" --> Reviewer
class Secrets datastore
class Workflow,ErrorGuard event

    class Secrets datastore
    class DiffStep,Orchestrator,PromptBuilder,Gemini service
    class Workflow,ErrorGuard event
    class Dev,PR,ReviewComment,Reviewer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
