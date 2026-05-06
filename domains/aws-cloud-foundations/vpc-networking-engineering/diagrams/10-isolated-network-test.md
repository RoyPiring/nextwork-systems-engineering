# Creating a Private Subnet

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/10-isolated-network-test.md`](../documents/10-isolated-network-test.md).

```mermaid
---
title: Creating a Private Subnet
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph VPC["Amazon VPC (Isolated Network)"]
        PrivateSubnet[/"Private Subnet (CIDR)"/]
        RouteTable{{"Dedicated Route Table"}}
        SecurityGroup{{"Security Groups"}}
    end

    subgraph Workloads["Internal Workloads"]
        Instance("EC2 Workload")
        InternalSvc("Internal Service")
    end

    subgraph Egress["Controlled Outbound Path"]
        NATGateway[/"NAT Gateway"/]
        IGW[/"Internet Gateway"/]
    end

    PrivateSubnet -- "association" --> RouteTable
    PrivateSubnet -- "applies filter" --> SecurityGroup
    Instance -- "deployed in" --> PrivateSubnet
    InternalSvc -- "east-west traffic" --> Instance
    SecurityGroup -- "permits egress" --> NATGateway
    RouteTable -- "0.0.0.0/0 via NAT" --> NATGateway
    NATGateway -- "outbound only" --> IGW
    IGW -. "no inbound exposure" .-x PrivateSubnet

    class Instance,InternalSvc service
    class RouteTable,SecurityGroup event
    class PrivateSubnet,NATGateway,IGW io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
