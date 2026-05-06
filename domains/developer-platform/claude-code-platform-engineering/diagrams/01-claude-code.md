# Get Started with Claude Code

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-claude-code.md`](../documents/01-claude-code.md).

```mermaid
---
title: Get Started with Claude Code
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Developer["Developer Workstation"]
        Dev[/"Developer"/]
        Editor[/"Editor + Terminal"/]
    end

    subgraph CLI["Claude Code CLI"]
        ClaudeCLI("Claude Code CLI")
        PermMode{{"Permission Mode"}}
        TokenMeter{{"Token Usage Meter"}}
    end

    subgraph ProjectCtx["Project Context"]
        ClaudeMd("CLAUDE.md Config")
        ProjectsDir[("@projects/ Directory")]
        PkgMgr("npm / pip Installer")
    end

    subgraph Output["Build Output"]
        Portfolio[("Portfolio Site Repo")]
    end

    Dev -- "prompt input" --> Editor
    Editor -- "invoke CLI" --> ClaudeCLI
    ClaudeCLI -- "load config" --> ClaudeMd
    ClaudeCLI -- "reference @projects" --> ProjectsDir
    PkgMgr -- "install runtime" --> ClaudeCLI
    PermMode -- "gate actions" --> ClaudeCLI
    ClaudeCLI -- "track context window" --> TokenMeter
    ClaudeCLI -- "generate HTML/CSS" --> Portfolio
    ProjectsDir -- "contextual inputs" --> ClaudeCLI
class ProjectsDir,Portfolio datastore
class PermMode,TokenMeter event

    class ProjectsDir,Portfolio datastore
    class ClaudeCLI,ClaudeMd,PkgMgr service
    class PermMode,TokenMeter event
    class Dev,Editor io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
