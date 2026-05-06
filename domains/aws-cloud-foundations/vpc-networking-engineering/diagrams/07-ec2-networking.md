# Launching VPC Resources

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/07-ec2-networking.md`](../documents/07-ec2-networking.md).

```mermaid
---
title: Launching VPC Resources
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph External["External Network"]
        Internet[/"Internet Traffic"/]
        Admin[/"Operator / SSH Client"/]
    end

    subgraph VPCBoundary["Amazon VPC (Isolated Boundary)"]
        IGW{{"Internet Gateway"}}
        RouteTable{{"Route Table"}}
        subgraph PublicSubnet["Public Subnet"]
            EC2(("EC2 Instance"))
            SG{{"Security Group"}}
            NACL{{"Network ACL"}}
        end
    end

    subgraph IPPlane["Address & Identity Plane"]
        CIDR[("VPC CIDR Block")]
        ENI[("Elastic Network Interface")]
    end

    Internet -- "ingress request" --> IGW
    Admin -- "SSH on port 22" --> IGW
    IGW -- "0.0.0.0/0 default route" --> RouteTable
    RouteTable -- "subnet association" --> NACL
    NACL -- "stateless allow/deny" --> SG
    SG -- "stateful inbound rule" --> EC2
    EC2 -- "egress via route table" --> IGW
    CIDR -- "subnet allocation" --> PublicSubnet
    ENI -- "attaches to" --> EC2

    class CIDR,ENI datastore
    class IGW,RouteTable,SG,NACL event
    class Internet,Admin io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
