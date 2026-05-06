# Build a New App Feature With Claude Code

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-workspace-claude-code.md`](../documents/02-ai-workspace-claude-code.md).

```mermaid
---
title: Build a New App Feature With Claude Code
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic





    subgraph DevWorkspace["Local Dev Workspace"]
        Developer[/"Developer"/]
        IDE("Local IDE")
        NodeRT{{"Node.js Runtime"}}
    end

    subgraph AIAssist["AI Assist Layer"]
        ClaudeCode("Claude Code CLI")
        ModelHigh{{"High-Capability Model"}}
        ModelLow{{"Low-Cost Model"}}
    end

    subgraph NextSoundApp["NextSound App"]
        TrackBrowse("Track Browsing")
        ThemeToggle("Light/Dark Toggle")
        FeatureCode[("Feature Module")]
    end

    subgraph Iteration["Iteration Loop"]
        IntegErrors{{"Integration Errors"}}
        Repo[("App Codebase")]
    end

    Developer -- "prompts feature spec" --> IDE
    IDE -- "delegates to assist" --> ClaudeCode
    ClaudeCode -- "complex logic gen" --> ModelHigh
    ClaudeCode -- "constrained tasks" --> ModelLow
    ModelHigh -- "generated code" --> FeatureCode
    ModelLow -- "boilerplate edits" --> FeatureCode
    FeatureCode -- "extends UI" --> ThemeToggle
    FeatureCode -- "extends discovery" --> TrackBrowse
    NodeRT -- "runs app" --> NextSoundApp
    NextSoundApp -- "surfaces failures" --> IntegErrors
    IntegErrors -- "loop back to fix" --> ClaudeCode
    FeatureCode -- "commit on green" --> Repo
class FeatureCode,Repo datastore
class NodeRT,ModelHigh,ModelLow,IntegErrors event

    class FeatureCode,Repo datastore
    class IDE,ClaudeCode,TrackBrowse,ThemeToggle service
    class NodeRT,ModelHigh,ModelLow,IntegErrors event
    class Developer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
