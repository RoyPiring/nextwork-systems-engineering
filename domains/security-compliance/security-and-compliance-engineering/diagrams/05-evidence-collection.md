# Threat Detection with GuardDuty

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-evidence-collection.md`](../documents/05-evidence-collection.md).

```mermaid
---
title: Threat Detection with GuardDuty
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Edge["Edge & Ingress"]
        Attacker[/"Simulated Attacker"/]
        ALB("Application Load Balancer")
    end

    subgraph Workload["Vulnerable Workload"]
        CFN{{"CloudFormation Stack"}}
        EC2("EC2 Vulnerable App")
        S3[("S3 Artifact Bucket")]
    end

    subgraph Detection["Threat Detection"]
        Logs[("AWS Logs & Runtime Signals")]
        GuardDuty("Amazon GuardDuty")
        Findings[/"GuardDuty Findings"/]
    end

    CFN -- "provisions" --> EC2
    CFN -- "provisions" --> ALB
    Attacker -- "SQLi / cmd injection" --> ALB
    ALB -- "forwards traffic" --> EC2
    EC2 -- "writes artifacts" --> S3
    EC2 -- "emits telemetry" --> Logs
    ALB -- "access logs" --> Logs
    Logs -- "ingested signals" --> GuardDuty
    GuardDuty -- "surfaces alerts" --> Findings

    class S3,Logs datastore
    class ALB,EC2,GuardDuty service
    class CFN event
    class Attacker,Findings io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
