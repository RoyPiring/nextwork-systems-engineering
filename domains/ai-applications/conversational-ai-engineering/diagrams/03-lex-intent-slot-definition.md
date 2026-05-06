# Add Custom Slots to a Lex Chatbot

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-lex-intent-slot-definition.md`](../documents/03-lex-intent-slot-definition.md).

```mermaid
---
title: Add Custom Slots to a Lex Chatbot
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserInput["User Input Layer"]
        User[/"End User"/]
        Utterance[/"Raw Utterance"/]
    end

    subgraph LexNLU["Amazon Lex NLU"]
        ASR("Speech Recognition")
        IntentClassifier{{"Intent Classifier"}}
        SlotExtractor{{"Slot Extractor"}}
    end

    subgraph SlotConfig["Slot Configuration"]
        CustomSlot[("Custom Slot Type")]
        ValueConstraints[("Allowed Values")]
        Resolution{{"Resolution Behavior"}}
    end

    subgraph IntentRouting["Intent Fulfillment"]
        AccountRouter("Account Type Router")
        Fulfillment("Deterministic Handler")
    end

    User -- "speaks request" --> Utterance
    Utterance -- "audio stream" --> ASR
    ASR -- "transcribed text" --> IntentClassifier
    IntentClassifier -- "matched intent" --> SlotExtractor
    SlotExtractor -- "lookup type" --> CustomSlot
    CustomSlot -- "constrain values" --> ValueConstraints
    ValueConstraints -- "resolve input" --> Resolution
    Resolution -- "validated slots" --> AccountRouter
    AccountRouter -- "route by attribute" --> Fulfillment
class CustomSlot,ValueConstraints datastore
class IntentClassifier,SlotExtractor,Resolution event

    class CustomSlot,ValueConstraints datastore
    class ASR,AccountRouter,Fulfillment service
    class IntentClassifier,SlotExtractor,Resolution event
    class User,Utterance io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
