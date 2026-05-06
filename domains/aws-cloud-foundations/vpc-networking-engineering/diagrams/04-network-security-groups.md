# VPC Traffic Flow and Security

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-network-security-groups.md`](../documents/04-network-security-groups.md).

```mermaid
---
title: VPC Traffic Flow and Security
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Ingress["Ingress Boundary"]
        Client[/"External Client"/]
        IGW{{"Internet Gateway"}}
    end

    subgraph VPCFabric["VPC Routing Fabric"]
        RouteTbl{{"Route Table"}}
        Subnet(["Subnet"])
        NACL{{"Network ACL"}}
    end

    subgraph Workload["Instance-Level Controls"]
        SG{{"Security Group"}}
        EC2[("EC2 Instance")]
        Logs[("VPC Flow Logs")]
    end

    subgraph Governance["Design Intent"]
        Policy(["Explicit Rule Policy"])
        DropSink[/"Silent Drop Sink"/]
    end

    Client -- "inbound traffic" --> IGW
    IGW -- "route lookup" --> RouteTbl
    RouteTbl -- "directs to subnet" --> Subnet
    Subnet -- "subnet-level filter" --> NACL
    NACL -- "stateless allow" --> SG
    SG -- "stateful allow" --> EC2
    EC2 -- "emits flow record" --> Logs
    NACL -. "misaligned rule" .-> DropSink
    Policy -- "constrains" --> SG
    Policy -- "constrains" --> NACL

    class EC2,Logs datastore
    class Subnet,Policy service
    class IGW,RouteTbl,NACL,SG event
    class Client,DropSink io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
