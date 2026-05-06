# Give Your Assistant a Memory

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-openclaw-memory.md`](../documents/02-openclaw-memory.md).

```mermaid
---
title: Give Your Assistant a Memory
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph UserChannel["User Channel"]
        User[/"Telegram User"/]
        TgBot[/"Telegram Bot"/]
    end

    subgraph Execution["Execution Layer"]
        Gateway("OpenClaw Gateway")
        Loop("Interaction Loop")
    end

    subgraph MemoryLayer["Memory Layer"]
        Identity[("system-identity.md")]
        UserCtx[("user-context.md")]
        History[("interaction-history")]
    end

    subgraph Behavior["Behavioral Control"]
        PromptCtl{{"Prompt Composer"}}
        LLM("LLM Inference")
    end

    User -- "message" --> TgBot
    TgBot -- "request" --> Gateway
    Gateway -- "invoke" --> Loop
    Loop -- "load identity" --> Identity
    Loop -- "load user data" --> UserCtx
    Loop -- "append turn" --> History
    Identity -- "persona" --> PromptCtl
    UserCtx -- "context" --> PromptCtl
    History -- "prior turns" --> PromptCtl
    PromptCtl -- "structured prompt" --> LLM
    LLM -- "stateful reply" --> TgBot

    class Identity,UserCtx,History datastore
    class Gateway,Loop,LLM service
    class PromptCtl event
    class User,TgBot io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
