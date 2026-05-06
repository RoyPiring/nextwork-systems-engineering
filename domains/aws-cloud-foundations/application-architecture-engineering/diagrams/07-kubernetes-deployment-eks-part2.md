# Set Up Kubernetes Deployment

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/07-kubernetes-deployment-eks-part2.md`](../documents/07-kubernetes-deployment-eks-part2.md).

```mermaid
---
title: Set Up Kubernetes Deployment
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Source["Source Control"]
        Git[/"Git Repository"/]
    end

    subgraph BuildPublish["Build & Publish"]
        Docker{{"Docker Build"}}
        Image("Container Image")
        ECR[("Amazon ECR Registry")]
    end

    subgraph EKSCluster["Amazon EKS Cluster"]
        Deployment("Kubernetes Deployment")
        Pod("Backend Pod")
        Service("Kubernetes Service")
        NetPolicy{{"Network Policy"}}
    end

    subgraph ClusterNet["Cluster Network"]
        Client[/"In-Cluster Client"/]
    end

    Git -- "source checkout" --> Docker
    Docker -- "produces image" --> Image
    Image -- "docker push" --> ECR
    ECR -- "image pull" --> Deployment
    Deployment -- "manages replicas" --> Pod
    Pod -- "exposed via" --> Service
    NetPolicy -- "restricts traffic" --> Pod
    Client -- "service request" --> Service
class ECR datastore
class Docker,NetPolicy event

    class ECR datastore
    class Image,Deployment,Pod,Service service
    class Docker,NetPolicy event
    class Git,Client io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
