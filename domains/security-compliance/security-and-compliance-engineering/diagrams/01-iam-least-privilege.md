# Cloud Security with AWS IAM

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-iam-least-privilege.md`](../documents/01-iam-least-privilege.md).

```mermaid
---
title: Cloud Security with AWS IAM
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph AccountScope["AWS Account Scope"]
        Alias[/"Account Alias"/]
        RootUser[/"Root User"/]
    end

    subgraph IdentityLayer["IAM Identities"]
        IAMUser("IAM User")
        IAMGroup("IAM Group")
    end

    subgraph PolicyLayer["IAM Policies"]
        AllowPolicy{{"Allow Policy"}}
        DenyPolicy{{"Explicit Deny"}}
    end

    subgraph TargetResources["EC2 Resources"]
        EC2Instance[("EC2 Instance")]
        EC2Console("EC2 Console")
    end

    Alias -- "names sign-in URL" --> RootUser
    IAMGroup -- "assigns membership" --> IAMUser
    AllowPolicy -- "attaches to group" --> IAMGroup
    DenyPolicy -- "overrides allow" --> IAMGroup
    IAMUser -- "calls API" --> EC2Console
    EC2Console -- "evaluates policy" --> AllowPolicy
    AllowPolicy -- "permits action" --> EC2Instance
    DenyPolicy -. "blocks action" .-x EC2Instance

    class EC2Instance datastore
    class IAMUser,IAMGroup,EC2Console service
    class AllowPolicy,DenyPolicy event
    class Alias,RootUser io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
