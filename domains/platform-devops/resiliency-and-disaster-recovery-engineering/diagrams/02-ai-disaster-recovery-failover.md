# Build Instant Failover with CloudFront Origin Groups

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-disaster-recovery-failover.md`](../documents/02-ai-disaster-recovery-failover.md).

```mermaid
---
title: Build Instant Failover with CloudFront Origin Groups
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph EdgeLayer["Edge Routing"]
        User[/"End User Request"/]
        CloudFront("CloudFront Distribution")
        OriginGroup{{"Origin Group Failover"}}
    end

    subgraph PrimaryRegion["Primary Region"]
        AppRunnerA("App Runner - Primary")
        HealthA{{"Health Check A"}}
    end

    subgraph SecondaryRegion["Secondary Region"]
        AppRunnerB("App Runner - Backup")
        HealthB{{"Health Check B"}}
    end

    subgraph Observability["Monitoring and Alerts"]
        CWAlarm[("CloudWatch Alarms")]
        SNSTopic("SNS Failover Notify")
    end

    User -- "HTTPS request" --> CloudFront
    CloudFront -- "route via" --> OriginGroup
    OriginGroup -- "primary path" --> AppRunnerA
    OriginGroup -. "failover path" .-> AppRunnerB
    AppRunnerA -- "status probe" --> HealthA
    AppRunnerB -- "status probe" --> HealthB
    HealthA -- "5xx threshold" --> CWAlarm
    HealthB -- "recovery signal" --> CWAlarm
    CWAlarm -- "publish event" --> SNSTopic
    SNSTopic -. "failback notice" .-> CloudFront

    class CWAlarm datastore
    class CloudFront,AppRunnerA,AppRunnerB,SNSTopic service
    class OriginGroup,HealthA,HealthB event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
