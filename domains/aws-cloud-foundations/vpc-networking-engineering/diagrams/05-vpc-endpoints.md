# VPC Endpoints

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-vpc-endpoints.md`](../documents/05-vpc-endpoints.md).

```mermaid
---
title: VPC Endpoints
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph VPC["Amazon VPC (Isolated Boundary)"]
        PrivateSubnet["Private Subnet"]
        EC2[/"EC2 Compute"/]
        RouteTable{{"Route Table"}}
    end

    subgraph Endpoints["VPC Endpoints"]
        GatewayEP("S3 Gateway Endpoint")
        InterfaceEP("Interface Endpoint (ENI)")
    end

    subgraph AWSBackbone["AWS Backbone (No Internet)"]
        S3[("Amazon S3")]
        ManagedSvc[("AWS-Managed Service")]
    end

    subgraph PublicEdge["Public Internet Edge"]
        Internet[/"Public Internet"/]
    end

    EC2 -- "private API call" --> PrivateSubnet
    PrivateSubnet -- "prefix-list lookup" --> RouteTable
    RouteTable -- "route to gateway EP" --> GatewayEP
    PrivateSubnet -- "DNS to ENI" --> InterfaceEP
    GatewayEP -- "private path" --> S3
    InterfaceEP -- "private path" --> ManagedSvc
    EC2 -. "blocked egress" .-x Internet

    class S3,ManagedSvc datastore
    class GatewayEP,InterfaceEP service
    class RouteTable event
    class EC2,Internet io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
