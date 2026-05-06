# Automate Your Email Briefing with Claude

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-claude-email-briefing.md`](../documents/03-ai-claude-email-briefing.md).

```mermaid
---
title: Automate Your Email Briefing with Claude
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Source["Data Source"]
        Gmail[/"Gmail Inbox"/]
        Scheduler{{"Scheduled Trigger"}}
    end

    subgraph Orchestration["Claude Desktop Orchestration"]
        Connector("Gmail Connector")
        PromptLib("Briefing Prompt Template")
        Claude("Claude Desktop Agent")
    end

    subgraph Processing["Prompt-Driven Categorization"]
        Categorizer("Email Categorizer")
        StyleMatch("Style Matcher")
    end

    subgraph Output["Storage & Output"]
        NotionConn("Notion Connector")
        Briefing[("Daily Briefing Page")]
    end

    Scheduler -- "daily run" --> Claude
    Gmail -- "raw email data" --> Connector
    Connector -- "ingested messages" --> Claude
    PromptLib -- "structured prompt" --> Claude
    Claude -- "intent parsing" --> Categorizer
    Categorizer -- "categorized items" --> StyleMatch
    StyleMatch -- "formatted summary" --> NotionConn
    NotionConn -- "writes briefing" --> Briefing

    class Briefing datastore
    class Connector,PromptLib,Claude,Categorizer,StyleMatch,NotionConn service
    class Scheduler event
    class Gmail io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
