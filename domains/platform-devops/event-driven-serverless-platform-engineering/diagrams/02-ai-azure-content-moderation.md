# Build AI Chat Moderator with Gemini

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-azure-content-moderation.md`](../documents/02-ai-azure-content-moderation.md).

```mermaid
---
title: Build AI Chat Moderator with Gemini
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ChatClients["Chat Clients"]
        User[/"Chat User"/]
        Moderator[/"Moderator Dashboard"/]
    end

    subgraph ServerlessAPI["Azure Functions API"]
        ModerateFn("moderate-message Function")
        DashboardFn("dashboard-query Function")
        KeyVault{{"Key Vault (Gemini API key)"}}
    end

    subgraph AIInference["Gemini Inference"]
        Gemini("Gemini API (toxicity scoring)")
        FailOpen{{"Fail-Open Handler"}}
    end

    subgraph Storage["Cosmos DB"]
        Decisions[("moderation-decisions container")]
    end

    User -- "incoming message" --> ModerateFn
    ModerateFn -- "fetch secret" --> KeyVault
    ModerateFn -- "classify text" --> Gemini
    Gemini -. "toxicity verdict" .-> ModerateFn
    Gemini -. "error or timeout" .-> FailOpen
    FailOpen -- "allow message" --> ModerateFn
    ModerateFn -- "persist decision" --> Decisions
    Moderator -- "review query" --> DashboardFn
    DashboardFn -- "read decisions" --> Decisions

    class Decisions datastore
    class ModerateFn,DashboardFn,Gemini service
    class KeyVault,FailOpen event
    class User,Moderator io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
