# Increase Test Coverage with AI

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-cicd-testgen.md`](../documents/03-ai-cicd-testgen.md).

```mermaid
---
title: Increase Test Coverage with AI
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph SourceTrigger["Source & Trigger"]
        Dev[/"Developer Push / PR"/]
        Repo[("GitHub Repo (Python src)")]
    end

    subgraph CIPipeline["GitHub Actions CI"]
        Workflow{{"ci.yml workflow"}}
        Pytest("pytest + coverage")
        Gate{{"Coverage Gate (threshold)"}}
    end

    subgraph AIGen["AI Test Generation"]
        AST("AST module (parse src)")
        Gemini("Gemini API client")
        TestFiles[("tests/ generated")]
    end

    subgraph QualityOut["Quality & Output"]
        Report[/"Coverage Report"/]
    end

    Dev -- "push commits" --> Repo
    Repo -- "trigger on push" --> Workflow
    Workflow -- "run unit tests" --> Pytest
    Pytest -- "coverage %" --> Gate
    Gate -- "below threshold" --> AST
    Gate -- "above threshold" --> Report
    AST -- "function signatures" --> Gemini
    Gemini -- "synthesized tests" --> TestFiles
    TestFiles -- "re-run pytest" --> Pytest
    Pytest -- "final metrics" --> Report
class Repo,TestFiles datastore
class Workflow,Gate event

    class Repo,TestFiles datastore
    class Pytest,AST,Gemini service
    class Workflow,Gate event
    class Dev,Report io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
