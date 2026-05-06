# AI Finance Agent with Amazon Bedrock

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-bedrock-agent.md`](../documents/02-bedrock-agent.md).

```mermaid
---
title: AI Finance Agent with Amazon Bedrock
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User Interaction Layer"]
        Analyst[/"Finance Analyst"/]
        Query[/"Natural Language Query"/]
    end

    subgraph AgentCore["Bedrock Agent Core"]
        Agent(("Bedrock Agent"))
        FoundationModel{{"Foundation Model (Reasoning)"}}
        CodeInterp{{"Code Interpreter"}}
    end

    subgraph DataPlane["Financial Data Plane"]
        FinData[("Financial Dataset")]
        Insights[("Structured Recommendations")]
    end

    subgraph Output["Output Layer"]
        Response[/"Insight Response"/]
    end

    Analyst -- "submits question" --> Query
    Query -- "invoke agent" --> Agent
    Agent -- "reasoning step" --> FoundationModel
    FoundationModel -- "plan analysis" --> CodeInterp
    CodeInterp -- "load dataset" --> FinData
    FinData -- "tabular data" --> CodeInterp
    CodeInterp -- "computed result" --> Insights
    Insights -- "format reply" --> Agent
    Agent -- "return insight" --> Response
    Response -- "deliver to user" --> Analyst
class FinData,Insights datastore
class Analyst,Query,Response io

    class FinData,Insights datastore
    class FoundationModel,CodeInterp event
    class Analyst,Query,Response io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
