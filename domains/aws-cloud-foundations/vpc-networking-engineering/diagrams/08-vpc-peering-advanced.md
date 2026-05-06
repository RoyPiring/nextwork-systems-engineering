# VPC Peering

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/08-vpc-peering-advanced.md`](../documents/08-vpc-peering-advanced.md).

```mermaid
---
title: VPC Peering
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph VPC_A["VPC A (Requester)"]
        SubnetA[/"Subnet A"/]
        EC2_A("EC2 Instance A")
        RouteA{{"Route Table A"}}
    end

    subgraph VPC_B["VPC B (Accepter)"]
        SubnetB[/"Subnet B"/]
        EC2_B("EC2 Instance B")
        RouteB{{"Route Table B"}}
    end

    subgraph PeeringPlane["VPC Peering Plane"]
        Peering[("Peering Connection")]
        CIDR("CIDR Plan (non-overlap)")
    end

    subgraph Validation["Validation Layer"]
        PingTest("EC2 Ping/SSH Test")
    end

    EC2_A -- "private IP egress" --> SubnetA
    SubnetA -- "lookup peer CIDR" --> RouteA
    RouteA -- "route via pcx-id" --> Peering
    Peering -- "approved request" --> RouteB
    RouteB -- "deliver to subnet" --> SubnetB
    SubnetB -- "private IP ingress" --> EC2_B
    CIDR -. "constrains routes" .-> RouteA
    CIDR -. "constrains routes" .-> RouteB
    EC2_B -- "echo reply" --> PingTest
    PingTest -. "validates path" .-> EC2_A

    class Peering datastore
    class EC2_A,EC2_B,CIDR,PingTest service
    class RouteA,RouteB event
    class SubnetA,SubnetB io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
