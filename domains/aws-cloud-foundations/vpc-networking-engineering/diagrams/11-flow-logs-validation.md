# VPC Monitoring with Flow Logs

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/11-flow-logs-validation.md`](../documents/11-flow-logs-validation.md).

```mermaid
---
title: VPC Monitoring with Flow Logs
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph VPC["Isolated VPC"]
        EC2A[/"EC2 Source Instance"/]
        EC2B[/"EC2 Target Instance"/]
        ENI("Elastic Network Interface")
    end

    subgraph Capture["Flow Log Capture"]
        FlowLogs{{"VPC Flow Logs"}}
        IAMRole("Flow Logs IAM Role")
    end

    subgraph Telemetry["CloudWatch Telemetry"]
        LogGroup[("CloudWatch Log Group")]
        Insights("Logs Insights Queries")
        Alarms{{"CloudWatch Alarms"}}
    end

    subgraph Analyst["Operator View"]
        Engineer[/"Network Engineer"/]
    end

    EC2A -- "ICMP / TCP probe" --> EC2B
    EC2B -- "flow metadata" --> ENI
    ENI -- "captured records" --> FlowLogs
    IAMRole -- "publish permission" --> FlowLogs
    FlowLogs -- "log stream" --> LogGroup
    LogGroup -- "ad hoc query" --> Insights
    LogGroup -- "metric filter" --> Alarms
    Insights -- "ACCEPT vs REJECT" --> Engineer
    Alarms -- "alert on REJECT" --> Engineer

    class LogGroup datastore
    class ENI,IAMRole,Insights service
    class FlowLogs,Alarms event
    class EC2A,EC2B,Engineer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
