# Claude Code Skills Basics

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-claude-code-skills.md`](../documents/02-claude-code-skills.md).

```mermaid
---
title: Claude Code Skills Basics
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DevInterface["Developer Interface"]
        Dev[/"Developer"/]
        CLI[/"Claude Code CLI"/]
    end

    subgraph SkillLayer["Claude Code Skills"]
        Skill("Git Commit Skill")
        Frontmatter{{"YAML Frontmatter Config"}}
        Hooks{{"Automation Hooks"}}
    end

    subgraph Tooling["Python Tooling"]
        PyTools("Python Helper Scripts")
        Conv("Conventional Commits")
    end

    subgraph GitRepo["Git Repository"]
        Repo[("Local Git Repo")]
        Changelog[("CHANGELOG.md")]
    end

    Dev -- "invokes skill" --> CLI
    CLI -- "loads skill" --> Frontmatter
    Frontmatter -- "configures" --> Skill
    Skill -- "runs scripts" --> PyTools
    PyTools -- "formats messages" --> Conv
    Conv -- "structured commit" --> Repo
    Hooks -- "trigger on event" --> Skill
    Repo -- "reads history" --> Skill
    Skill -- "generates entries" --> Changelog
class Repo,Changelog datastore
class Frontmatter,Hooks event

    class Repo,Changelog datastore
    class Skill,PyTools,Conv service
    class Frontmatter,Hooks event
    class Dev,CLI io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
