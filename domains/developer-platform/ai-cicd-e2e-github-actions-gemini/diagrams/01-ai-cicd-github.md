# Your First GitHub Actions AI workflow

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-cicd-github.md`](../documents/01-ai-cicd-github.md).

```mermaid
---
title: Your First GitHub Actions AI workflow
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DevSource["Developer & Source"]
        Dev[/"Developer"/]
        Repo[("GitHub Repository")]
    end

    subgraph CIPipeline["GitHub Actions CI"]
        Trigger{{"push / pull_request event"}}
        Workflow("ci.yml Workflow")
        Runner("ubuntu-latest Runner")
    end

    subgraph TestStage["Python Test Stage"]
        PySetup("setup-python + pip install")
        Pytest("pytest Test Suite")
    end

    subgraph Outputs["Build Outputs"]
        Artifacts[(".pytest_cache / Artifacts")]
        Status[/"Pass-Fail Status Check"/]
    end

    Dev -- "git push" --> Repo
    Repo -- "fires event" --> Trigger
    Trigger -- "dispatches job" --> Workflow
    Workflow -- "runs on" --> Runner
    Runner -- "checkout + install deps" --> PySetup
    PySetup -- "invokes tests" --> Pytest
    Pytest -- "uploads results" --> Artifacts
    Pytest -- "reports outcome" --> Status
    Status -- "blocks bad merges" --> Repo
class Repo,Artifacts datastore
class Trigger event

    class Repo,Artifacts datastore
    class Workflow,Runner,PySetup,Pytest service
    class Trigger event
    class Dev,Status io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
