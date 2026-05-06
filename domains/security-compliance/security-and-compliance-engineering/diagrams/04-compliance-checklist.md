# Build a Security Monitoring System

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/04-compliance-checklist.md`](../documents/04-compliance-checklist.md).

```mermaid
---
title: Build a Security Monitoring System
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Activity["Activity Generation"]
        CLI[/"AWS CLI"/]
        Secrets("AWS Secrets Manager")
    end

    subgraph AuditLog["Audit Logging"]
        CloudTrail[("AWS CloudTrail")]
    end

    subgraph Detection["Metric Evaluation"]
        Metrics{{"CloudWatch Metric Filter"}}
        Alarm{{"CloudWatch Alarm"}}
    end

    subgraph Notification["Notification Delivery"]
        SNS("Amazon SNS Topic")
        Subscriber[/"Email Subscriber"/]
    end

    CLI -- "invoke API" --> Secrets
    Secrets -- "control plane events" --> CloudTrail
    CloudTrail -- "log stream" --> Metrics
    Metrics -- "metric data" --> Alarm
    Alarm -- "threshold breach" --> SNS
    SNS -- "notification" --> Subscriber

    class CloudTrail datastore
    class Secrets,SNS service
    class Metrics,Alarm event
    class CLI,Subscriber io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
