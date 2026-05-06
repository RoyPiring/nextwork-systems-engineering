# Set Up Claude Code Guardrails

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-claude-code-safety-guardrails.md`](../documents/03-claude-code-safety-guardrails.md).

```mermaid
---
title: Set Up Claude Code Guardrails
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Developer["Developer Surface"]
        Dev[/"Developer Prompt"/]
        CLI[/"Claude Code CLI"/]
    end

    subgraph PermissionLayer["Permission Layer"]
        AllowList{{"Allow / Deny Rules"}}
        JqInspect("jq config inspector")
    end

    subgraph RuntimeHooks["Runtime Hook Layer"]
        PreHook{{"PreToolUse Hook"}}
        PolicyEngine("Policy Engine")
        PostHook{{"PostToolUse Hook"}}
    end

    subgraph Execution["Execution and Audit"]
        ToolExec("Tool Executor")
        AuditLog[("Audit Log")]
    end

    Dev -- "issues request" --> CLI
    CLI -- "check static rules" --> AllowList
    JqInspect -- "validates config" --> AllowList
    AllowList -- "permitted call" --> PreHook
    PreHook -- "evaluate intent" --> PolicyEngine
    PolicyEngine -- "block unsafe op" --> PreHook
    PreHook -- "approved invoke" --> ToolExec
    ToolExec -- "result event" --> PostHook
    PostHook -- "write audit trail" --> AuditLog
class AuditLog datastore
class AllowList,PreHook,PostHook event

    class AuditLog datastore
    class JqInspect,PolicyEngine,ToolExec service
    class AllowList,PreHook,PostHook event
    class Dev,CLI io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
