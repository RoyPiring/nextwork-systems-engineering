# Testing VPC Connectivity

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-routing-boundaries.md`](../documents/03-routing-boundaries.md).

```mermaid
---
title: Testing VPC Connectivity
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph External["External Networks"]
        Internet[/"Public Internet"/]
        Operator[/"Operator / Validator"/]
    end

    subgraph VPCBoundary["Amazon VPC (isolated boundary)"]
        IGW{{"Internet Gateway"}}
        RouteTable{{"Route Table"}}
        Subnet("Subnet (IP segment)")
        EC2[("EC2 Instance")]
    end

    subgraph TrafficControls["Traffic Control Points"]
        SG{{"Security Group"}}
        NACL{{"Network ACL"}}
    end

    Operator -- "reachability test" --> Internet
    Internet -- "ingress packets" --> IGW
    IGW -- "default route 0.0.0.0/0" --> RouteTable
    RouteTable -- "subnet association" --> Subnet
    Subnet -- "stateless filter" --> NACL
    NACL -- "stateful filter" --> SG
    SG -- "permitted flow" --> EC2
    EC2 -- "egress reply" --> RouteTable

    class EC2 datastore
    class Subnet service
    class IGW,RouteTable,SG,NACL event
    class Internet,Operator io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
