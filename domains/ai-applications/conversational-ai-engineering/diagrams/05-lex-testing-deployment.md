# Save User Info with a Lex Chatbot

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-lex-testing-deployment.md`](../documents/05-lex-testing-deployment.md).

```mermaid
---
title: Save User Info with a Lex Chatbot
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph UserChannel["User Channel"]
        User[/"User (text/voice)"/]
    end

    subgraph LexBot["Amazon Lex Bot"]
        IntentRecog("Intent Recognition")
        SlotCapture{{"Slot Capture (name/email/contact)"}}
        ContextMgr("Context Manager")
    end

    subgraph ConvFlow["Conversation Flow"]
        ActiveIntent("Active Intent")
        FollowUp("Follow-up Intent")
        ExpiryClock{{"Context Expiry Clock"}}
    end

    subgraph SessionState["Session State"]
        SessionAttrs[("Session Attributes")]
    end

    User -- "utterance" --> IntentRecog
    IntentRecog -- "matched intent" --> SlotCapture
    SlotCapture -- "captured slots" --> ContextMgr
    ContextMgr -- "scoped context" --> ActiveIntent
    ActiveIntent -- "chains to" --> FollowUp
    ContextMgr -- "TTL countdown" --> ExpiryClock
    ExpiryClock -. "invalidate on expiry" .-x FollowUp
    ContextMgr -- "transient values" --> SessionAttrs
    SessionAttrs -- "prior inputs" --> FollowUp

    class SessionAttrs datastore
    class IntentRecog,ContextMgr,ActiveIntent,FollowUp service
    class SlotCapture,ExpiryClock event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
