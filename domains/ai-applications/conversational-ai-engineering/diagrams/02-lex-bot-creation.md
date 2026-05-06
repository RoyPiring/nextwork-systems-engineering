# Build a Chatbot with Amazon Lex

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-lex-bot-creation.md`](../documents/02-lex-bot-creation.md).

```mermaid
---
title: Build a Chatbot with Amazon Lex
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User Input Layer"]
        User[/"End User"/]
        Utterance[/"Utterance Text"/]
    end

    subgraph LexBot["Amazon Lex Bot"]
        NLU{{"NLU Classifier"}}
        Intent("Intent Definition")
        Slots("Slot Extraction")
        Fallback{{"FallbackIntent"}}
    end

    subgraph DialogControl["Dialog & Confidence"]
        Threshold{{"Confidence Threshold"}}
        Response("Bot Response")
    end

    subgraph IAM["Access Control"]
        Role[("IAM Role")]
    end

    User -- "types message" --> Utterance
    Utterance -- "raw input" --> NLU
    NLU -- "match intent" --> Intent
    Intent -- "extract values" --> Slots
    NLU -- "score check" --> Threshold
    Threshold -- "below threshold" --> Fallback
    Slots -- "fulfilled" --> Response
    Fallback -- "default reply" --> Response
    Role -- "authorizes bot" --> NLU
class Role datastore
class NLU,Fallback,Threshold event

    class Role datastore
    class Intent,Slots,Response service
    class NLU,Fallback,Threshold event
    class User,Utterance io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
