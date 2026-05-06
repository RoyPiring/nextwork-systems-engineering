# Get Hands on with Cloud Networking!

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-networking-introduction.md`](../documents/01-networking-introduction.md).

```mermaid
---
title: "Get Hands on with Cloud Networking!"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph AddressPlan["Address Planning"]
        CIDR[/"VPC CIDR Block"/]
        Subnets("Public/Private Subnets")
    end

    subgraph VPCCore["Amazon VPC Core"]
        VPC[("Virtual Private Cloud")]
        RouteTbl{{"Route Tables"}}
        IGW("Internet Gateway")
    end

    subgraph Workloads["Cloud Workloads"]
        Compute("Compute Instances")
        Platform("Platform Services")
    end

    subgraph Posture["Operational Posture"]
        Isolation{{"Software-Defined Isolation"}}
        Policy("Policy-Driven Control")
    end

    CIDR -- "address ranges" --> VPC
    VPC -- "carves into" --> Subnets
    Subnets -- "attached to" --> RouteTbl
    RouteTbl -- "default route" --> IGW
    Subnets -- "host workloads" --> Compute
    Compute -- "consumes" --> Platform
    VPC -- "enforces" --> Isolation
    Isolation -- "shapes" --> Policy
    Policy -. "guards" .-> Compute

    class VPC datastore
    class Subnets,IGW,Compute,Platform,Policy service
    class RouteTbl,Isolation event
    class CIDR io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
