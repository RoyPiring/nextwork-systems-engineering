# Launch a Kubernetes Cluster

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/06-kubernetes-cluster-eks-part1.md`](../documents/06-kubernetes-cluster-eks-part1.md).

```mermaid
---
title: Launch a Kubernetes Cluster
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph IAMAccess["IAM and Access"]
        ClusterRole{{"EKS Cluster IAM Role"}}
        NodeRole{{"Worker Node IAM Role"}}
        Operator[/"Cluster Operator"/]
    end

    subgraph ControlPlane["EKS Control Plane"]
        APIServer("EKS API Server")
        Etcd[("etcd cluster state")]
    end

    subgraph DataPlane["Managed Worker Nodes"]
        NodeGroup("Managed Node Group")
        EC2Nodes("EC2 Worker Nodes")
    end

    subgraph NetworkLayer["VPC Networking"]
        VPC[/"VPC and Subnets"/]
    end

    Operator -- "kubectl auth" --> APIServer
    ClusterRole -- "assumed by" --> APIServer
    APIServer -- "persists state" --> Etcd
    APIServer -- "schedules pods" --> NodeGroup
    NodeGroup -- "provisions" --> EC2Nodes
    NodeRole -- "assumed by" --> EC2Nodes
    EC2Nodes -- "register via" --> VPC
    VPC -- "hosts endpoints" --> APIServer
class Etcd datastore
class ClusterRole,NodeRole event

    class Etcd datastore
    class APIServer,NodeGroup,EC2Nodes service
    class ClusterRole,NodeRole event
    class Operator,VPC io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
