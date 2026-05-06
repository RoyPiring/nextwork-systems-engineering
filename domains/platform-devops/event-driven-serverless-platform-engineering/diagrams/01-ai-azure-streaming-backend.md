# Build Your First Azure Function

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-azure-streaming-backend.md`](../documents/01-ai-azure-streaming-backend.md).

```mermaid
---
title: Build Your First Azure Function
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph DevTools["Local Dev Toolchain"]
        AzCLI[/"Azure CLI"/]
        CoreTools[/"Functions Core Tools"/]
        PyRuntime("Python Runtime")
    end

    subgraph AzureControl["Azure Resource Group"]
        FuncApp("Function App")
        HttpTrigger{{"HTTP Trigger"}}
        ConnStr{{"Connection String Secret"}}
    end

    subgraph Compute["Serverless Compute"]
        FuncCode("Streaming Handler Fn")
    end

    subgraph DataPlane["Persistence Layer"]
        Cosmos[("Cosmos DB Container")]
        PartKey[("Partition Key")]
    end

    AzCLI -- "provision rg" --> FuncApp
    CoreTools -- "deploy code" --> FuncApp
    PyRuntime -- "executes" --> FuncCode
    FuncApp -- "hosts" --> HttpTrigger
    HttpTrigger -- "invokes handler" --> FuncCode
    FuncCode -- "reads secret" --> ConnStr
    ConnStr -- "auth to db" --> Cosmos
    FuncCode -- "write event" --> Cosmos
    Cosmos -- "shards on" --> PartKey

    class Cosmos,PartKey datastore
    class PyRuntime,FuncApp,FuncCode service
    class HttpTrigger,ConnStr event
    class AzCLI,CoreTools io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
