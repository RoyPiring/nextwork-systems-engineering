# Create S3 Buckets with Terraform

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/07-idempotent-provisioning.md`](../documents/07-idempotent-provisioning.md).

```mermaid
---
title: Create S3 Buckets with Terraform
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Authoring["Authoring & Config"]
        Engineer[/"Engineer (CLI)"/]
        TFConfig("main.tf - S3 Resource Block")
        AWSCreds{{"AWS CLI Credentials"}}
    end

    subgraph Terraform["Terraform Control Plane"]
        Init("terraform init - Provider Download")
        Plan("terraform plan - Diff Calc")
        Apply("terraform apply - Reconcile")
        State[("terraform.tfstate")]
    end

    subgraph AWS["AWS Provider"]
        Provider{{"AWS Provider Plugin"}}
        S3Bucket[("Amazon S3 Bucket")]
    end

    Engineer -- "writes HCL" --> TFConfig
    Engineer -- "configures" --> AWSCreds
    TFConfig -- "feeds config" --> Init
    Init -- "loads provider" --> Provider
    Init -- "next step" --> Plan
    AWSCreds -- "auth context" --> Provider
    Plan -- "approved diff" --> Apply
    Apply -- "create or update" --> Provider
    Provider -- "API call" --> S3Bucket
    Apply -- "writes state" --> State
    State -- "reads prior state" --> Plan
class State,S3Bucket datastore
class AWSCreds,Provider event

    class State,S3Bucket datastore
    class TFConfig,Init,Plan,Apply service
    class AWSCreds,Provider event
    class Engineer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
