# Build an AI Chatbot with Amazon Bedrock

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-bedrock-chatbot.md`](../documents/01-bedrock-chatbot.md).

```mermaid
---
title: Build an AI Chatbot with Amazon Bedrock
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph DevEnv["Developer Environment"]
        Dev[/"Developer"/]
        CloudShell[/"AWS CloudShell"/]
    end

    subgraph AppLayer["Python Application"]
        Script("chatbot.py Script")
        Boto3{{"AWS Boto3 SDK"}}
        History[("Conversation History")]
    end

    subgraph BedrockSvc["Amazon Bedrock"]
        Converse{{"Bedrock Converse API"}}
        SysPrompt("System Prompt + Params")
        FM[("Foundation Model")]
    end

    subgraph Safety["Safety Controls"]
        Guardrails("Bedrock Guardrails")
    end

    Dev -- "writes prompt" --> CloudShell
    CloudShell -- "runs script" --> Script
    Script -- "build payload" --> Boto3
    Boto3 -- "Converse request" --> Converse
    SysPrompt -- "behavior config" --> Converse
    Converse -- "invoke model" --> FM
    FM -- "generated reply" --> Converse
    Converse -- "filtered output" --> Guardrails
    Guardrails -- "safe response" --> Script
    Script -- "append turn" --> History
    History -- "prior context" --> Boto3
class History,FM datastore
class Boto3,Converse event

    class History,FM datastore
    class Script,SysPrompt,Guardrails service
    class Boto3,Converse event
    class Dev,CloudShell io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
