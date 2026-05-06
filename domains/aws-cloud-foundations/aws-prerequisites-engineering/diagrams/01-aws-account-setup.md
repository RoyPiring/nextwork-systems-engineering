# Set Up An AWS Account

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-aws-account-setup.md`](../documents/01-aws-account-setup.md).

```mermaid
---
title: Set Up An AWS Account
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserInputs["User Inputs"]
        Email[/"Valid Email Address"/]
        Card[/"Credit Card (verify)"/]
    end

    subgraph AccountSetup["AWS Account Setup"]
        Signup("AWS Signup Flow")
        Verify{{"Account Verification"}}
        RootAcct("Root Account Identity")
    end

    subgraph BillingBoundary["Billing Boundary"]
        FreeTier("AWS Free Tier")
        BillAlert{{"Billing Alert Threshold"}}
        UsageLog[("Usage and Cost Log")]
    end

    subgraph SecurityFoundation["Security Foundation"]
        BasicSec("Basic Security Config")
        IamFuture("IAM (deferred to next doc)")
    end

    Email -- "signup credential" --> Signup
    Card -- "verification token" --> Signup
    Signup -- "creates identity" --> RootAcct
    Signup -- "triggers check" --> Verify
    Verify -- "activates tier" --> FreeTier
    RootAcct -- "scopes charges" --> BillAlert
    FreeTier -- "metered usage" --> UsageLog
    BillAlert -- "watches log" --> UsageLog
    RootAcct -- "applies baseline" --> BasicSec
    BasicSec -- "hands off scope" --> IamFuture
class UsageLog datastore
class Verify,BillAlert event

    class UsageLog datastore
    class Signup,RootAcct,FreeTier,BasicSec,IamFuture service
    class Verify,BillAlert event
    class Email,Card io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
