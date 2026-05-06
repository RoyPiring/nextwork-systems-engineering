# Claude Code with Git Worktrees

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-ai-git-worktrees.md`](../documents/04-ai-git-worktrees.md).

```mermaid
---
title: Claude Code with Git Worktrees
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Developer["Developer Layer"]
        Dev[/"Engineer"/]
        ClaudeCode("Claude Code Generator")
    end

    subgraph Control["Git Control Layer"]
        MainRepo[("Main Repository")]
        Worktree1("Worktree A: Feature X")
        Worktree2("Worktree B: Feature Y")
        Worktree3("Worktree C: Experiment")
    end

    subgraph Coordination["Branch Coordination"]
        BranchOps{{"Branch Isolation Event"}}
        MergeGate("Merge / Integration Gate")
    end

    subgraph Output["Stable Codebase"]
        MainBranch[("main branch")]
    end

    Dev -- "prompt for feature" --> ClaudeCode
    ClaudeCode -- "generates code into" --> Worktree1
    ClaudeCode -- "generates code into" --> Worktree2
    ClaudeCode -- "generates code into" --> Worktree3
    MainRepo -- "spawns isolated worktree" --> Worktree1
    MainRepo -- "spawns isolated worktree" --> Worktree2
    MainRepo -- "spawns isolated worktree" --> Worktree3
    Worktree1 -- "emits branch event" --> BranchOps
    Worktree2 -- "emits branch event" --> BranchOps
    Worktree3 -- "emits branch event" --> BranchOps
    BranchOps -- "routes to gate" --> MergeGate
    MergeGate -- "fast-forward merge" --> MainBranch
    MergeGate -. "rejected: conflict" .-> Dev
class MainRepo,MainBranch datastore
class BranchOps event

    class MainRepo,MainBranch datastore
    class ClaudeCode,Worktree1,Worktree2,Worktree3,MergeGate service
    class BranchOps event
    class Dev io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
