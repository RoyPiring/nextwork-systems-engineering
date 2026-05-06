# Prompt Engineering for Healthcare

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-prompt-engineering-healthcare.md`](../documents/ai-prompt-engineering-healthcare.md).

```mermaid
---
title: Prompt Engineering for Healthcare
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ClinicianUI["Clinician Interface"]
        Clinician[/"Clinician Query"/]
        Response[/"Structured Response"/]
    end

    subgraph PromptLayer["Prompt Engineering Layer"]
        SystemPrompt("Clinical System Prompt")
        FewShot("Few-Shot Examples")
        OutputSchema{{"Output Schema (JSON)"}}
    end

    subgraph SafetyControls["Safety Guardrails"]
        ScopeCheck{{"Scope Check"}}
        Disclaimer("Assistive-Only Disclaimer")
        RefusalRules("Refusal Rules")
    end

    subgraph ModelRuntime["Claude Runtime"]
        Claude("Claude API")
        AuditLog[("Prompt Audit Log")]
    end

    Clinician -- "free-text query" --> SystemPrompt
    SystemPrompt -- "compose template" --> FewShot
    FewShot -- "schema-bound prompt" --> OutputSchema
    OutputSchema -- "validated prompt" --> ScopeCheck
    ScopeCheck -- "in-scope only" --> Claude
    ScopeCheck -. "out-of-scope" .-x RefusalRules
    Claude -- "model output" --> Disclaimer
    Disclaimer -- "wrapped response" --> Response
    Claude -- "trace" --> AuditLog
    RefusalRules -- "safe refusal" --> Response

    class AuditLog datastore
    class SystemPrompt,FewShot,Disclaimer,RefusalRules,Claude service
    class OutputSchema,ScopeCheck event
    class Clinician,Response io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
