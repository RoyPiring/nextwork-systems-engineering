# Set Up Multiple Slots in a Lex Chatbot

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/06-lex-advanced-conversations.md`](../documents/06-lex-advanced-conversations.md).

```mermaid
---
title: Set Up Multiple Slots in a Lex Chatbot
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph UserChannel["User Channel"]
        User[/"End User"/]
        Utterance[/"Natural Language Input"/]
    end

    subgraph LexControlPlane["Amazon Lex Control Plane"]
        Intent("TransferMoney Intent")
        SlotElicit("Slot Elicitation")
        SlotReuse("Slot Reuse Confirmation")
        Validation{{"Required Slot Validation"}}
    end

    subgraph SlotData["Captured Slots"]
        Slots[("Structured Slot Values")]
    end

    subgraph IaC["Infrastructure as Code"]
        CFN("CloudFormation Template")
        VisualBuilder("Lex Visual Builder")
    end

    User -- "types or speaks" --> Utterance
    Utterance -- "intent classification" --> Intent
    Intent -- "prompt for slot" --> SlotElicit
    SlotElicit -- "captured value" --> Slots
    Slots -- "check completeness" --> Validation
    Validation -- "reuse for confirm" --> SlotReuse
    SlotReuse -- "final values" --> Slots
    CFN -- "provisions bot" --> Intent
    VisualBuilder -- "defines prompts" --> SlotElicit

    class Slots datastore
    class Intent,SlotElicit,SlotReuse,CFN,VisualBuilder service
    class Validation event
    class User,Utterance io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
