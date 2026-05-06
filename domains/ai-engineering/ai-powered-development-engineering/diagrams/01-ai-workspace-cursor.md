# Build a Mini Spotify with Cursor

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-workspace-cursor.md`](../documents/01-ai-workspace-cursor.md).

```mermaid
---
title: Build a Mini Spotify with Cursor
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Developer["Developer Workspace"]
        Dev[/"Developer (human review)"/]
        Cursor("Cursor AI-Assisted IDE")
    end

    subgraph Codebase["Mini Spotify Codebase"]
        WebApp[("Existing Web App Repo")]
        NewFeature("Scaffolded Feature")
    end

    subgraph SourceControl["Source Control"]
        GitLocal{{"Git (local commits)"}}
        GitHub[("GitHub Remote")]
    end

    subgraph LocalRuntime["Local Validation"]
        LocalRun{{"Local Execution"}}
        Docs("Generated Documentation")
    end

    Dev -- "natural language prompt" --> Cursor
    Cursor -- "code comprehension query" --> WebApp
    Cursor -- "scaffold feature" --> NewFeature
    NewFeature -- "stage diff" --> GitLocal
    GitLocal -- "push commits" --> GitHub
    Cursor -- "emit docs" --> Docs
    NewFeature -- "run + observe" --> LocalRun
    LocalRun -. "behavior feedback" .-> Dev
    Dev -. "approve / reject" .-x Cursor
class WebApp,GitHub datastore
class GitLocal,LocalRun event

    class WebApp,GitHub datastore
    class Cursor,NewFeature,Docs service
    class GitLocal,LocalRun event
    class Dev io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
