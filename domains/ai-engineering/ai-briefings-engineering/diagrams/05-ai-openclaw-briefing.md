# Build an Automated AI Briefing

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-ai-openclaw-briefing.md`](../documents/05-ai-openclaw-briefing.md).

```mermaid
---
title: Build an Automated AI Briefing
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Scheduling["Scheduling Layer"]
        Cron{{"Cron Trigger (daily)"}}
    end

    subgraph Discovery["Discovery & Retrieval"]
        WebSearch[/"Web Search Function"/]
        Extractor("Content Extractor")
    end

    subgraph Execution["OpenClaw Execution Layer"]
        OpenClaw("OpenClaw Runtime")
        Curator("Personalized Curator")
        BriefStore[("Briefing Cache")]
    end

    subgraph Delivery["Delivery Interface"]
        TelegramBot("Telegram Bot")
        User[/"End User Chat"/]
    end

    Cron -- "fires daily schedule" --> OpenClaw
    OpenClaw -- "issues query" --> WebSearch
    WebSearch -- "raw results" --> Extractor
    Extractor -- "cleaned content" --> Curator
    Curator -- "structured briefing" --> BriefStore
    BriefStore -- "formatted message" --> TelegramBot
    TelegramBot -- "daily briefing" --> User
class BriefStore datastore
class Cron event

    class BriefStore datastore
    class Extractor,OpenClaw,Curator,TelegramBot service
    class Cron event
    class WebSearch,User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
