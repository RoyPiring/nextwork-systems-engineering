# Tailor Your Resume with Claude Dispatch

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-claude-dispatch-resume.md`](../documents/ai-claude-dispatch-resume.md).

```mermaid
---
title: Tailor Your Resume with Claude Dispatch
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph MobileLayer["Mobile Input Layer"]
        User[/"User (Job Seeker)"/]
        MobileApp("Claude Mobile App")
        JobDesc[/"Job Description Input"/]
    end

    subgraph DispatchBridge["Cross-Device Bridge"]
        Dispatch{{"Claude Dispatch"}}
        PairingAuth{{"Device Pairing & Permissions"}}
    end

    subgraph DesktopExec["Desktop Execution"]
        Desktop("Claude Desktop")
        ResumeSkill("Resume Tailor Skill")
    end

    subgraph Artifacts["Artifacts"]
        BaseResume[("Base Resume Source")]
        TailoredResume[("Tailored Resume Output")]
    end

    User -- "submits JD on phone" --> MobileApp
    MobileApp -- "captures job description" --> JobDesc
    JobDesc -- "dispatch payload" --> Dispatch
    Dispatch -- "auth handshake" --> PairingAuth
    PairingAuth -- "permitted session" --> Desktop
    Desktop -- "invokes tailor skill" --> ResumeSkill
    BaseResume -- "source content" --> ResumeSkill
    ResumeSkill -- "structured output" --> TailoredResume
    TailoredResume -- "delivered to user" --> User
class BaseResume,TailoredResume datastore
class Dispatch,PairingAuth event

    class BaseResume,TailoredResume datastore
    class MobileApp,Desktop,ResumeSkill service
    class Dispatch,PairingAuth event
    class User,JobDesc io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
