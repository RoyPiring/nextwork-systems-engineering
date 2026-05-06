# Create Kubernetes Manifests

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/08-kubernetes-scaling-eks-part3.md`](../documents/08-kubernetes-scaling-eks-part3.md).

```mermaid
---
title: Create Kubernetes Manifests
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Operator["Operator Tooling"]
        Dev[/"Developer / Operator"/]
        Eksctl("eksctl + AWS CLI")
        Kubectl("kubectl client")
    end

    subgraph Manifests["Declarative Manifests"]
        Deploy("Deployment manifest")
        Service("Service manifest")
        Image[("Docker image registry")]
    end

    subgraph EKSCluster["Amazon EKS Cluster"]
        APIServer{{"EKS API Server"}}
        Pods("Application Pods")
    end

    subgraph Consumer["External Access"]
        ExtUser[/"External Client"/]
    end

    Dev -- "provision cluster" --> Eksctl
    Eksctl -- "create control plane" --> APIServer
    Dev -- "apply manifests" --> Kubectl
    Kubectl -- "declare desired state" --> APIServer
    Deploy -- "pod spec" --> APIServer
    Service -- "expose endpoint" --> APIServer
    APIServer -- "schedule workloads" --> Pods
    Image -- "pull container" --> Pods
    ExtUser -- "reach service endpoint" --> Service
class Image datastore
class APIServer event

    class Image datastore
    class Eksctl,Kubectl,Deploy,Service,Pods service
    class APIServer event
    class Dev,ExtUser io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
