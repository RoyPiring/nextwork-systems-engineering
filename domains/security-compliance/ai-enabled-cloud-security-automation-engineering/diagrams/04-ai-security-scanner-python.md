# AI Security Scanner for Python

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-ai-security-scanner-python.md`](../documents/04-ai-security-scanner-python.md).

```mermaid
---
title: AI Security Scanner for Python
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DevInput["Developer Input Layer"]
        Dev[/"Developer CLI Invocation"/]
        PySrc[/"Target Python Source"/]
    end

    subgraph ScannerCore["AI Scanner Core (Python CLI)"]
        CLI("scanner.py CLI Entrypoint")
        PromptEng("Security Prompt Template")
        Parser("Structured Output Parser")
    end

    subgraph SecretsAndModel["Credentials & Model API"]
        EnvVars{{".env / GEMINI_API_KEY"}}
        Gemini("Gemini API Analyzer")
    end

    subgraph FindingsOut["Findings & Severity Output"]
        Findings[("Vulnerability Findings JSON")]
        Report[/"Severity-Classified Report"/]
    end

    Dev -- "scan command" --> CLI
    PySrc -- "code under review" --> CLI
    CLI -- "build prompt" --> PromptEng
    EnvVars -- "load API key" --> CLI
    PromptEng -- "analysis request" --> Gemini
    Gemini -- "raw AI response" --> Parser
    Parser -- "structured findings" --> Findings
    Findings -- "render to stdout" --> Report
    Report -- "fixes & severities" --> Dev
class Findings datastore
class EnvVars event

    class Findings datastore
    class CLI,PromptEng,Parser,Gemini service
    class EnvVars event
    class Dev,PySrc,Report io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
