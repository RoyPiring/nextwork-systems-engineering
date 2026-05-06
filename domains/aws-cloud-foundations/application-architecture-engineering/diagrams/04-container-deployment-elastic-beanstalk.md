# Deploy an App with Docker

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-container-deployment-elastic-beanstalk.md`](../documents/04-container-deployment-elastic-beanstalk.md).

```mermaid
---
title: Deploy an App with Docker
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph SourceLayer["Source & Build"]
        Dev[/"Developer"/]
        AppCode("Web App Source")
        Dockerfile{{"Dockerfile (CMD/ENTRYPOINT)"}}
    end

    subgraph BuildArtifacts["Container Artifacts"]
        Image[("Docker Image")]
        Registry[("Image Registry")]
    end

    subgraph AWSDeploy["AWS Elastic Beanstalk"]
        EBEnv("Beanstalk Environment")
        Container("Running Container")
    end

    subgraph Runtime["Runtime"]
        EndUser[/"End User"/]
    end

    Dev -- "writes app" --> AppCode
    AppCode -- "packaged by" --> Dockerfile
    Dockerfile -- "docker build" --> Image
    Image -- "push" --> Registry
    Registry -- "pull on deploy" --> EBEnv
    EBEnv -- "starts container" --> Container
    Container -- "serves HTTP" --> EndUser
    Dockerfile -. "startup contract" .-> Container
class Image,Registry datastore
class Dockerfile event

    class Image,Registry datastore
    class AppCode,EBEnv,Container service
    class Dockerfile event
    class Dev,EndUser io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
