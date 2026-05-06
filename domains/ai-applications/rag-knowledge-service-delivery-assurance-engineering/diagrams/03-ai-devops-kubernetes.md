# Deploy a RAG API to Kubernetes

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-devops-kubernetes.md`](../documents/03-ai-devops-kubernetes.md).

```mermaid
---
title: Deploy a RAG API to Kubernetes
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph BuildLayer["Container Build"]
        FastAPI[/"FastAPI RAG App"/]
        Docker("Docker Image Build")
    end

    subgraph ControlPlane["Minikube Control Plane"]
        Kubectl[/"kubectl CLI"/]
        APIServer("Kubernetes API Server")
        DeploySpec{{"Deployment YAML"}}
        SvcSpec{{"Service YAML"}}
    end

    subgraph Runtime["Cluster Runtime"]
        Deployment("RAG Deployment")
        Pods[("RAG API Pods")]
        Service("ClusterIP Service")
    end

    FastAPI -- "packaged into" --> Docker
    Docker -- "image pulled by" --> Pods
    Kubectl -- "apply manifests" --> APIServer
    APIServer -- "schedules" --> Deployment
    DeploySpec -- "defines replicas" --> Deployment
    SvcSpec -- "exposes" --> Service
    Deployment -- "manages lifecycle" --> Pods
    Service -- "routes traffic" --> Pods
    Pods -. "self-heal on failure" .-> Deployment

    class Pods datastore
    class Docker,APIServer,Deployment,Service service
    class DeploySpec,SvcSpec event
    class FastAPI,Kubectl io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
