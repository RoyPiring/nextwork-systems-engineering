# Connect Amazon Lex with Lambda

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-lex-lambda-integration.md`](../documents/04-lex-lambda-integration.md).

```mermaid
---
title: Connect Amazon Lex with Lambda
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph UserChannel["User Channel"]
        User[/"End User (text/voice)"/]
    end

    subgraph LexLayer["Amazon Lex (Dialogue)"]
        Bot(["Lex Bot"])
        Intent{{"Intent: FinancialPlanning"}}
        Slots(["Slot Resolution"])
    end

    subgraph BackendLogic["AWS Lambda (Compute)"]
        Fulfillment[/"Fulfillment Function"/]
        IAMRole[("Lex Invoke Permission")]
    end

    subgraph Response["Response Path"]
        Reply(["Generated Response"])
    end

    User -- "utterance" --> Bot
    Bot -- "matches intent" --> Intent
    Intent -- "fills slots" --> Slots
    Slots -- "invokes function" --> Fulfillment
    IAMRole -. "grants invoke" .-> Fulfillment
    Fulfillment -- "returns payload" --> Reply
    Reply -- "spoken/text reply" --> User

    class IAMRole datastore
    class Bot,Slots,Reply service
    class Intent event
    class User,Fulfillment io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
