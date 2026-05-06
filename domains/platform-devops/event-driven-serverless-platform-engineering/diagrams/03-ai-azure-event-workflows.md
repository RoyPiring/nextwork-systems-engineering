# Orchestrating Parallel Event Streams with Azure

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-azure-event-workflows.md`](../documents/03-ai-azure-event-workflows.md).

```mermaid
---
title: Orchestrating Parallel Event Streams with Azure
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Producers["Event Producers"]
        Source[/"Stream Event Source"/]
        Producer("Event Publisher")
    end

    subgraph Buffer["Queue-Based Load Leveling"]
        Queue[("Azure Storage Queue")]
        DLQ[("Dead-Letter Queue")]
    end

    subgraph Orchestration["Durable Functions Workflow"]
        Trigger("Queue Trigger Function")
        Orchestrator{{"Durable Orchestrator"}}
        ActivityA("Activity Function A")
        ActivityB("Activity Function B")
    end

    subgraph Persistence["Cosmos DB Persistence"]
        EventStore[("Event History Container")]
        Aggregates[("Real-Time Aggregates")]
    end

    Source -- "publish event" --> Producer
    Producer -- "enqueue message" --> Queue
    Queue -- "queue trigger" --> Trigger
    Trigger -- "start orchestration" --> Orchestrator
    Orchestrator -- "fan-out parallel" --> ActivityA
    Orchestrator -- "fan-out parallel" --> ActivityB
    ActivityA -- "write event" --> EventStore
    ActivityB -- "upsert by partition" --> Aggregates
    Trigger -. "poison message" .-> DLQ

    class Queue,DLQ,EventStore,Aggregates datastore
    class Producer,Trigger,ActivityA,ActivityB service
    class Orchestrator event
    class Source io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
