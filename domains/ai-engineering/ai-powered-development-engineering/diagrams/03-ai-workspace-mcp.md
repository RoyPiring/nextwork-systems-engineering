# Build a Database With Cursor and Supabase MCP

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-workspace-mcp.md`](../documents/03-ai-workspace-mcp.md).

```mermaid
---
title: Build a Database With Cursor and Supabase MCP
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Editor["AI Workspace"]
        Cursor[/"Cursor Editor"/]
        EnvVars("Environment Variables")
    end

    subgraph ControlPlane["MCP Control Plane"]
        MCP{{"Supabase MCP Interface"}}
        Ops("Structured DB Operations")
    end

    subgraph DataPlane["Supabase Backend"]
        Postgres[("Hosted PostgreSQL")]
        LikesTable[("Track Likes Table")]
    end

    subgraph Product["NextSound Feature"]
        UserAction[/"User Like Action"/]
    end

    Cursor -- "issue schema ops" --> MCP
    EnvVars -- "scoped credentials" --> MCP
    MCP -- "structured commands" --> Ops
    Ops -- "create schema" --> Postgres
    Ops -- "update like counts" --> LikesTable
    Postgres -- "persists" --> LikesTable
    UserAction -- "increment like" --> LikesTable
    LikesTable -. "verified mutations" .-> Cursor
class Postgres,LikesTable datastore
class MCP event

    class Postgres,LikesTable datastore
    class EnvVars,Ops service
    class MCP event
    class Cursor,UserAction io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
