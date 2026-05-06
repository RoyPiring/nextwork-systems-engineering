# Build an AI Meeting Prep Assistant

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-cowork-meeting-assistant.md`](../documents/02-ai-cowork-meeting-assistant.md).

```mermaid
---
title: Build an AI Meeting Prep Assistant
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Sources["External Data Sources"]
        Gmail[/"Gmail Inbox"/]
        Calendar[/"Google Calendar"/]
        Docs[/"Reference Documents"/]
    end

    subgraph Orchestration["Cowork Orchestration"]
        Claude("Claude Desktop (Cowork)")
        FolderCtx("Folder-Level Instructions")
        SubAgents("Decomposed Sub-Agents")
    end

    subgraph Triggers["Workflow Triggers"]
        Schedule{{"Scheduled Run"}}
        Mobile{{"Mobile Trigger"}}
    end

    subgraph Output["Briefing Output"]
        Briefing[("Structured Meeting Brief")]
    end

    Schedule -- "kick off run" --> Claude
    Mobile -- "on-demand trigger" --> Claude
    Gmail -- "thread context" --> Claude
    Calendar -- "event metadata" --> Claude
    Docs -- "background material" --> Claude
    Claude -- "loads guardrails" --> FolderCtx
    FolderCtx -- "scoped prompts" --> SubAgents
    SubAgents -- "decision-ready summary" --> Briefing
class Briefing datastore
class Schedule,Mobile event

    class Briefing datastore
    class Claude,FolderCtx,SubAgents service
    class Schedule,Mobile event
    class Gmail,Calendar,Docs io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
