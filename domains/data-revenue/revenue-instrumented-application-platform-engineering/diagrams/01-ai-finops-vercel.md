# Ship a Landing Page with v0 and Vercel

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-ai-finops-vercel.md`](../documents/01-ai-finops-vercel.md).

```mermaid
---
title: Ship a Landing Page with v0 and Vercel
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph DesignLayer["AI-Assisted Design"]
        Designer[/"Frontend Designer"/]
        V0("v0.dev UI Generator")
    end

    subgraph LocalDev["Local Development"]
        Cursor("Cursor 2.0 IDE")
        Repo[("Git Repository")]
    end

    subgraph VercelPlatform["Vercel Managed Platform"]
        Build{{"Build Pipeline"}}
        EdgeCDN("Edge CDN (HTTPS)")
        RUM{{"Real User Monitoring"}}
    end

    subgraph EndUser["End User Layer"]
        Visitor[/"Site Visitor"/]
        Landing("E-commerce Landing Page")
    end

    Designer -- "AI prompt" --> V0
    V0 -- "generated UI code" --> Cursor
    Cursor -- "git push" --> Repo
    Repo -- "deploy trigger" --> Build
    Build -- "static + edge bundle" --> EdgeCDN
    EdgeCDN -- "HTTPS delivery" --> Landing
    Visitor -- "page request" --> Landing
    Landing -. "perf telemetry" .-> RUM
    RUM -. "real user metrics" .-> Designer

    class Repo datastore
    class V0,Cursor,EdgeCDN,Landing service
    class Build,RUM event
    class Designer,Visitor io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
