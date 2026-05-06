# Build an AI Second Brain with Claude Code

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/06-ai-second-brain-claude-code.md`](../documents/06-ai-second-brain-claude-code.md).

```mermaid
---
title: Build an AI Second Brain with Claude Code
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph RawCapture["Raw Input Layer"]
        Inbox[/"Unstructured Notes"/]
        WebClips[/"Web Clips & Sources"/]
    end

    subgraph Transform["Transformation Layer"]
        ClaudeCode("Claude Code CLI")
        Schema{{"CLAUDE.md Schema"}}
        WikiPattern("LLM Wiki Pipeline")
    end

    subgraph Persistence["Persistence Layer"]
        Vault[("Obsidian Vault")]
        Structured[("Linked Markdown Notes")]
    end

    subgraph Output["Knowledge Surface"]
        Queries[/"Synthesis Queries"/]
    end

    Inbox -- "raw capture" --> ClaudeCode
    WebClips -- "raw capture" --> ClaudeCode
    Schema -- "transform rules" --> ClaudeCode
    ClaudeCode -- "structured output" --> WikiPattern
    WikiPattern -- "linked artifacts" --> Structured
    Structured -- "persisted in" --> Vault
    Vault -- "queryable graph" --> Queries
    Queries -. "feedback loop" .-> Schema
class Vault,Structured datastore
class Schema event

    class Vault,Structured datastore
    class ClaudeCode,WikiPattern service
    class Schema event
    class Inbox,WebClips,Queries io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
