# Build Your First AI Workflow

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-agent-nocode.md`](../documents/01-ai-agent-nocode.md).

```mermaid
---
title: Build Your First AI Workflow
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph EventSource["Event Source"]
        CalEvent[/"Calendar Event"/]
    end

    subgraph Orchestration["n8n Orchestration"]
        Trigger{{"n8n Trigger Node"}}
        WorkflowEngine("Workflow Engine")
        Transform("Data Transformation")
    end

    subgraph AILayer["AI Inference Layer"]
        ChatGPTNode("ChatGPT API Node")
        OpenAI[(OpenAI API)]
    end

    subgraph SystemOfRecord["System of Record"]
        GCalAPI("Google Calendar API")
        CalStore[(Google Calendar)]
    end

    CalEvent -- "event fires" --> Trigger
    Trigger -- "auth + payload" --> WorkflowEngine
    WorkflowEngine -- "build prompt" --> ChatGPTNode
    ChatGPTNode -- "API call" --> OpenAI
    OpenAI -- "scheduling decision" --> Transform
    Transform -- "mapped fields" --> GCalAPI
    GCalAPI -- "update event" --> CalStore
    CalStore -- "lifecycle change" --> CalEvent
class OpenAI,CalStore datastore
class Trigger event

    class OpenAI,CalStore datastore
    class WorkflowEngine,Transform,ChatGPTNode,GCalAPI service
    class Trigger event
    class CalEvent io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
