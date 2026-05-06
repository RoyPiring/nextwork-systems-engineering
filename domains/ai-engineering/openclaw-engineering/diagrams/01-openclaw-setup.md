# Build a Telegram AI Bot with OpenClaw

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-openclaw-setup.md`](../documents/01-openclaw-setup.md).

```mermaid
---
title: Build a Telegram AI Bot with OpenClaw
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph UserLayer["User Layer"]
        User[/"Telegram User"/]
        Allowlist[/"Allowlist (user IDs)"/]
    end

    subgraph MessagingPlatform["Messaging Platform"]
        TGBot("Telegram Bot API")
        BotToken{{"Telegram Bot Token"}}
    end

    subgraph OpenClawRuntime["OpenClaw Runtime (Node.js)"]
        Gateway("OpenClaw Gateway")
        Config[("openclaw config")]
        Cron{{"cron job scheduler"}}
    end

    subgraph ModelProvider["Model Provider"]
        ClaudeAPI("Claude LLM API")
        APIKey{{"Claude API Key"}}
    end

    User -- "sends message" --> TGBot
    BotToken -- "auth bot session" --> TGBot
    TGBot -- "webhook event" --> Gateway
    Allowlist -- "permits user" --> Gateway
    Config -- "loads tokens" --> Gateway
    Gateway -- "prompt request" --> ClaudeAPI
    APIKey -- "auth model call" --> ClaudeAPI
    ClaudeAPI -- "completion text" --> Gateway
    Gateway -- "reply payload" --> TGBot
    TGBot -- "delivers reply" --> User
    Cron -- "scheduled trigger" --> Gateway

    class Config datastore
    class TGBot,Gateway,ClaudeAPI service
    class BotToken,Cron,APIKey event
    class User,Allowlist io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
