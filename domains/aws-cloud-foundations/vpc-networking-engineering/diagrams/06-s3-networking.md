# Access S3 from a VPC

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/06-s3-networking.md`](../documents/06-s3-networking.md).

```mermaid
---
title: Access S3 from a VPC
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph VPC["Amazon VPC (Network Boundary)"]
        Subnet[/"Private Subnet"/]
        RouteTable{{"Route Table"}}
        SG{{"Security Group"}}
        EC2("EC2 Workload")
    end

    subgraph IAMLayer["IAM Access Control"]
        Role("EC2 Instance Role")
        Policy{{"S3 Access Policy"}}
    end

    subgraph PrivateConn["Private S3 Connectivity"]
        Endpoint("VPC Gateway Endpoint")
        EndpointPolicy{{"Endpoint Policy"}}
    end

    subgraph AWSServices["AWS Managed Services"]
        S3[("Amazon S3 Bucket")]
        Internet[/"Public Internet (avoided)"/]
    end

    EC2 -- "assumes role" --> Role
    Role -- "grants access" --> Policy
    EC2 -- "egress check" --> SG
    Subnet -- "route to endpoint" --> RouteTable
    RouteTable -- "private route" --> Endpoint
    Endpoint -- "scoped by policy" --> EndpointPolicy
    Endpoint -- "private S3 traffic" --> S3
    EC2 -. "no public path" .-x Internet
    Policy -- "authorizes GetObject" --> S3

    class S3 datastore
    class EC2,Role,Endpoint service
    class RouteTable,SG,Policy,EndpointPolicy event
    class Subnet,Internet io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
