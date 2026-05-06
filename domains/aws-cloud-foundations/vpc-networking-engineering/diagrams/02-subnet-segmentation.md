# Build a Virtual Private Cloud

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-subnet-segmentation.md`](../documents/02-subnet-segmentation.md).

```mermaid
---
title: Build a Virtual Private Cloud
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph AddressSpace["VPC Address Space"]
        VPC[/"Amazon VPC (CIDR Block)"/]
        RouteDomain("Routing Domain")
    end

    subgraph SubnetPlacement["Subnet Segmentation"]
        PublicSub("Public Subnet")
        PrivateSub("Private Subnet")
    end

    subgraph TrafficControl["Traffic Control Points"]
        RouteTable{{"Route Table"}}
        SecurityCtrl{{"Security Controls"}}
        IGW[("Internet Gateway")]
    end

    subgraph Reachability["External Connectivity"]
        DependentSvc[/"Dependent AWS Services"/]
    end

    VPC -- "defines IP space" --> PublicSub
    VPC -- "defines IP space" --> PrivateSub
    RouteDomain -- "binds to" --> RouteTable
    PublicSub -- "egress route" --> RouteTable
    PrivateSub -- "isolated route" --> RouteTable
    RouteTable -- "public traffic" --> IGW
    IGW -- "controlled egress" --> DependentSvc
    SecurityCtrl -- "enforces isolation" --> PrivateSub
    SecurityCtrl -- "enforces isolation" --> PublicSub

    class IGW datastore
    class RouteDomain,PublicSub,PrivateSub service
    class RouteTable,SecurityCtrl event
    class VPC,DependentSvc io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
