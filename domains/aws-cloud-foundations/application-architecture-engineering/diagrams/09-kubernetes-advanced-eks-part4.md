# Deploy Backend with Kubernetes

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/09-kubernetes-advanced-eks-part4.md`](../documents/09-kubernetes-advanced-eks-part4.md).

```mermaid
---
title: Deploy Backend with Kubernetes
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph ControlPlane["Control Plane"]
        Kubectl[/"kubectl CLI"/]
        Manifests("Deployment & Service Manifests")
    end

    subgraph EKSCluster["Amazon EKS Cluster"]
        APIServer{{"EKS API Server"}}
        WorkerNodes("EC2 Worker Nodes")
        Pods("Backend Pods")
    end

    subgraph AWSServices["AWS-Managed Services"]
        ECR[("Amazon ECR Registry")]
        IAM{{"IAM Roles & Policies"}}
        ELB("Elastic Load Balancer")
    end

    Kubectl -- "apply manifests" --> APIServer
    Manifests -- "desired state" --> APIServer
    APIServer -- "schedule pods" --> WorkerNodes
    WorkerNodes -- "run containers" --> Pods
    Pods -- "pull image" --> ECR
    IAM -- "cluster access" --> APIServer
    Pods -- "expose service" --> ELB
class ECR datastore
class APIServer,IAM event

    class ECR datastore
    class Manifests,WorkerNodes,Pods,ELB service
    class APIServer,IAM event
    class Kubectl io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
