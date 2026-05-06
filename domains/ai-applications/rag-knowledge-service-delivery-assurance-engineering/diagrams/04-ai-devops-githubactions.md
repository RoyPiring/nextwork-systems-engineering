# Automate Testing with GitHub Actions

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-ai-devops-githubactions.md`](../documents/04-ai-devops-githubactions.md).

```mermaid
---
title: Automate Testing with GitHub Actions
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph SourceControl["Source Control"]
        Dev[/"Developer"/]
        Repo[("Git Repository")]
    end

    subgraph CIPipeline["GitHub Actions CI"]
        Trigger{{"Push / PR Event"}}
        Workflow("Actions Workflow")
        TestRunner("Semantic Test Runner")
    end

    subgraph RAGApp["RAG Application"]
        FastAPI("FastAPI Service")
        LLM("LLM (deterministic mode)")
        KB[("Knowledge Base")]
    end

    subgraph Outcomes["Build Outcomes"]
        Pass(["Pass: merge ready"])
        Fail(["Fail: block merge"])
    end

    Dev -- "commit / push" --> Repo
    Repo -- "trigger event" --> Trigger
    Trigger -- "start workflow" --> Workflow
    Workflow -- "run tests" --> TestRunner
    TestRunner -- "query API" --> FastAPI
    FastAPI -- "retrieve context" --> KB
    FastAPI -- "deterministic call" --> LLM
    LLM -. "validated output" .-> TestRunner
    TestRunner -- "all green" --> Pass
    TestRunner -- "drift detected" --> Fail

    class Repo,KB datastore
    class Workflow,TestRunner,FastAPI,LLM,Pass,Fail service
    class Trigger event
    class Dev io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
