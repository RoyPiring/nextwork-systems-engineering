# Automate Your Browser with AI Agents

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-agent-webui.md`](../documents/02-ai-agent-webui.md).

```mermaid
---
title: Automate Your Browser with AI Agents
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User Control Layer"]
        UserTask[/"User Task Definition"/]
        WebUI("WebUI Local Interface")
    end

    subgraph AgentRuntime["Agent Execution Loop"]
        Agent("AI Agent Runtime")
        ApiKey{{"API Key Config"}}
    end

    subgraph LLMInference["External LLM Inference"]
        GoogleAI("Google AI Studio API")
    end

    subgraph BrowserControl["Browser Automation"]
        Playwright("Playwright Driver")
        Chromium[(Chromium Runtime)]
        PageState[/"Page State / DOM"/]
    end

    UserTask -- "task prompt" --> WebUI
    WebUI -- "agent invocation" --> Agent
    ApiKey -- "auth secret" --> Agent
    Agent -- "inference request" --> GoogleAI
    GoogleAI -- "next action" --> Agent
    Agent -- "navigate / click" --> Playwright
    Playwright -- "drives session" --> Chromium
    Chromium -- "rendered DOM" --> PageState
    PageState -- "observation" --> Agent
    Agent -- "structured results" --> WebUI
class Chromium datastore
class ApiKey event

    class Chromium datastore
    class WebUI,Agent,GoogleAI,Playwright service
    class ApiKey event
    class UserTask,PageState io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
