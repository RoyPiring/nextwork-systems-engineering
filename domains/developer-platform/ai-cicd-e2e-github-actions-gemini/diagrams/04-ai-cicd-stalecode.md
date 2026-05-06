# Stale Code Handling (Execution 04)

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-ai-cicd-stalecode.md`](../documents/04-ai-cicd-stalecode.md).

```mermaid
---
title: Stale Code Handling (Execution 04)
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic





    subgraph DevSurface["Developer Surface"]
        Dev[/"Developer"/]
        PR[/"Pull Request"/]
    end

    subgraph SourceCtl["Source Control"]
        Repo[("GitHub Repository")]
        StaleBranch[("Stale Branch / Old PR")]
    end

    subgraph CICD["GitHub Actions CI/CD"]
        StaleScan{{"stale-code-scan workflow"}}
        AgeCheck(("commit-age & churn check"))
        GeminiReview("Gemini AI Reviewer")
    end

    subgraph Outcomes["Triage Outcomes"]
        Comment[/"PR Comment / Annotation"/]
        IssueLog[("stale-findings.md")]
    end

    Dev -- "opens PR" --> PR
    PR -- "triggers workflow" --> StaleScan
    StaleScan -- "scans branches" --> StaleBranch
    StaleBranch -- "metadata" --> AgeCheck
    AgeCheck -- "stale candidate diff" --> GeminiReview
    GeminiReview -- "AI verdict + rationale" --> Comment
    GeminiReview -- "logs finding" --> IssueLog
    Comment -- "feedback to author" --> Dev
    IssueLog --> Repo
class Repo,StaleBranch,IssueLog datastore
class StaleScan event

    class Repo,StaleBranch,IssueLog datastore
    class GeminiReview service
    class StaleScan event
    class Dev,PR,Comment io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
