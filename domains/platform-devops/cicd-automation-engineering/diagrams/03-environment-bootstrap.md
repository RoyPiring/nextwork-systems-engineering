# Set Up a Web App in the Cloud

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-environment-bootstrap.md`](../documents/03-environment-bootstrap.md).

```mermaid
---
title: Set Up a Web App in the Cloud
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Developer["Developer Workstation"]
        VSCode[/"VS Code + Remote SSH"/]
        SSHKey(("SSH Key Pair"))
    end

    subgraph AWSCloud["AWS Cloud (EC2 Host)"]
        EC2{{"EC2 Instance"}}
        SecGroup{{"Security Group (port 22)"}}
        Runtime("Java App Runtime")
    end

    subgraph BuildLayer["Build & Source"]
        Maven("Apache Maven")
        SrcTree[("Project Source Tree")]
        Artifact[("Built JAR Artifact")]
    end

    VSCode -- "SSH session" --> SecGroup
    SecGroup -- "ingress allow" --> EC2
    SSHKey -- "key auth" --> EC2
    VSCode -- "edit in place" --> SrcTree
    SrcTree -- "mvn package" --> Maven
    Maven -- "produces" --> Artifact
    Artifact -- "runs on" --> Runtime
    Runtime -- "hosted by" --> EC2
class SrcTree,Artifact datastore
class EC2,SecGroup event

    class SrcTree,Artifact datastore
    class Runtime,Maven service
    class EC2,SecGroup event
    class VSCode io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
