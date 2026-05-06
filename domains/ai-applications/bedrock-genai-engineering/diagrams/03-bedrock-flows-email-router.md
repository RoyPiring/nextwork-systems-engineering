# AI Email Router with Bedrock Flows

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-bedrock-flows-email-router.md`](../documents/03-bedrock-flows-email-router.md).

```mermaid
---
title: AI Email Router with Bedrock Flows
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Input["Email Intake"]
        Customer[/"Customer Email"/]
        FlowInput("Flow Input Node")
    end

    subgraph Classify["Classification Stage"]
        ClassifyPrompt{{"Classify Prompt Node"}}
        BedrockLLM("Amazon Bedrock LLM")
        Condition{{"Condition Node"}}
    end

    subgraph Routing["Conditional Routing"]
        BillingPrompt{{"Billing Reply Prompt"}}
        SupportPrompt{{"Support Reply Prompt"}}
        GeneralPrompt{{"General Reply Prompt"}}
    end

    subgraph Output["Response Delivery"]
        FlowOutput("Flow Output Node")
        Reply[(Structured Reply)]
    end

    Customer -- "raw email text" --> FlowInput
    FlowInput -- "unstructured input" --> ClassifyPrompt
    ClassifyPrompt -- "invoke model" --> BedrockLLM
    BedrockLLM -- "category label" --> Condition
    Condition -- "billing branch" --> BillingPrompt
    Condition -- "support branch" --> SupportPrompt
    Condition -- "fallback branch" --> GeneralPrompt
    BillingPrompt -- "drafted response" --> FlowOutput
    SupportPrompt -- "drafted response" --> FlowOutput
    GeneralPrompt -- "drafted response" --> FlowOutput
    FlowOutput -- "actionable output" --> Reply
class Reply datastore
class ClassifyPrompt,Condition,BillingPrompt,SupportPrompt,GeneralPrompt event

    class Reply datastore
    class FlowInput,BedrockLLM,FlowOutput service
    class ClassifyPrompt,Condition,BillingPrompt,SupportPrompt,GeneralPrompt event
    class Customer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
