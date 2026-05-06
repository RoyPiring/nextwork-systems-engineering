# Welcome to the Lex Chatbot series!

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-conversational-ai-introduction.md`](../documents/01-conversational-ai-introduction.md).

```mermaid
---
title: "Welcome to the Lex Chatbot series!"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserChannel["User Channel"]
        Customer[/"Banking Customer"/]
        ChatUI[/"Text Chat Interface"/]
    end

    subgraph LexNLP["Amazon Lex NLP Layer"]
        IntentRec("Intent Recognition")
        SlotFill("Slot Filling")
        RespOrch("Response Orchestration")
    end

    subgraph BotConfig["Bot Configuration"]
        Intents{{"Banking Intents"}}
        Slots{{"Slot Definitions"}}
    end

    subgraph BoundaryScope["Scope Boundary"]
        CoreBank[("Core Banking Systems")]
    end

    Customer -- "types inquiry" --> ChatUI
    ChatUI -- "utterance" --> IntentRec
    Intents -- "defines intents" --> IntentRec
    IntentRec -- "matched intent" --> SlotFill
    Slots -- "required slots" --> SlotFill
    SlotFill -- "filled slots" --> RespOrch
    RespOrch -- "text reply" --> ChatUI
    RespOrch -. "out of scope" .-x CoreBank
class CoreBank datastore
class Intents,Slots event

    class CoreBank datastore
    class IntentRec,SlotFill,RespOrch service
    class Intents,Slots event
    class Customer,ChatUI io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
