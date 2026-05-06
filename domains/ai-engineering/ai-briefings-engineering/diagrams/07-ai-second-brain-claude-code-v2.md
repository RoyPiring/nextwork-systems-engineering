# Automate Your AI Second Brain

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/07-ai-second-brain-claude-code-v2.md`](../documents/07-ai-second-brain-claude-code-v2.md).

```mermaid
---
title: Automate Your AI Second Brain
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User & Inputs"]
        User[/"Daily User Capture"/]
        Slash[/"Slash Commands"/]
    end

    subgraph ExecutionLayer["Execution Layer"]
        ClaudeCode{{"Claude Code Desktop"}}
        DailyLoop{{"Scheduled Daily Loop"}}
        MCP{{"MCP Connectors"}}
    end

    subgraph StateLayer["State & Storage"]
        Vault[("Obsidian Vault")]
        Repo[("GitHub Repo")]
    end

    subgraph OutputLayer["Surfaced Knowledge"]
        Surfaced("Surfaced Notes & Logs")
    end

    User -- "raw capture" --> Vault
    Slash -- "structured ops" --> ClaudeCode
    DailyLoop -- "triggers run" --> ClaudeCode
    ClaudeCode -- "ingest and query" --> Vault
    ClaudeCode -- "tool calls" --> MCP
    MCP -- "external fetch" --> ClaudeCode
    Vault -- "version sync" --> Repo
    ClaudeCode -- "writes updates" --> Surfaced
    Surfaced -- "stored back" --> Vault
class Vault,Repo datastore
class ClaudeCode,DailyLoop,MCP event

    class Vault,Repo datastore
    class Surfaced service
    class ClaudeCode,DailyLoop,MCP event
    class User,Slash io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
