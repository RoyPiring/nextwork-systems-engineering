# Website Delivery with CloudFront

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/09-cloudfront-integration.md`](../documents/09-cloudfront-integration.md).

```mermaid
---
title: Website Delivery with CloudFront
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph EndUsers["End Users"]
        Viewer[/"Web Browser"/]
    end

    subgraph EdgeLayer["CloudFront CDN"]
        Distribution("CloudFront Distribution")
        EdgeCache[("Edge Location Cache")]
    end

    subgraph OriginLayer["S3 Origin"]
        S3Bucket[("S3 Static Assets Bucket")]
        BucketPolicy{{"S3 Bucket Policy"}}
    end

    subgraph AccessControl["Access Boundary"]
        OAC("Origin Access Control")
        PublicBlock{{"Public Access Block"}}
    end

    Viewer -- "HTTPS request" --> Distribution
    Distribution -- "cache lookup" --> EdgeCache
    EdgeCache -. "cache hit" .-> Viewer
    Distribution -- "cache miss fetch" --> OAC
    OAC -- "signed origin request" --> S3Bucket
    BucketPolicy -- "allow CloudFront only" --> S3Bucket
    PublicBlock -- "deny direct access" --> S3Bucket
    S3Bucket -- "static object" --> EdgeCache

    class EdgeCache,S3Bucket datastore
    class Distribution,OAC service
    class BucketPolicy,PublicBlock event
    class Viewer io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
