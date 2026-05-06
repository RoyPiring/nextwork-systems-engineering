# Set Up Claude Code's Status Line

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-claude-code-statusline.md`](../documents/04-claude-code-statusline.md).

```mermaid
---
title: "Set Up Claude Code's Status Line"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Terminal["Terminal Environment"]
        User[/"Developer Terminal"/]
        ANSI{{"ANSI Escape Codes"}}
    end

    subgraph ClaudeCode["Claude Code Runtime"]
        CC("Claude Code CLI")
        Model("Active Model")
        Context("Context Window")
    end

    subgraph Statusline["Status Line Pipeline"]
        Script("statusline.sh Script")
        Metadata{{"Runtime Metadata JSON"}}
        Renderer[/"Live Status Display"/]
    end

    subgraph Observability["Observable Metrics"]
        TokenUse[("Token Usage")]
        CostEst[("Cost Estimate")]
        RateLimit[("Rate Limit State")]
    end

    User -- "invokes session" --> CC
    CC -- "emits state" --> Script
    Model -- "model id" --> Metadata
    Context -- "context size" --> Metadata
    Script -- "reads metadata" --> Metadata
    Metadata -- "tokens" --> TokenUse
    Metadata -- "cost calc" --> CostEst
    Metadata -- "limits" --> RateLimit
    Script -- "formatted line" --> ANSI
    ANSI -- "rendered output" --> Renderer
    Renderer -- "visible to dev" --> User
class TokenUse,CostEst,RateLimit datastore
class ANSI,Metadata event

    class TokenUse,CostEst,RateLimit datastore
    class CC,Model,Context,Script service
    class ANSI,Metadata event
    class User,Renderer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
