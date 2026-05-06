# Host a Website on Amazon S3

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/01-aws-host-a-website-on-s3.md`](../documents/01-aws-host-a-website-on-s3.md).

```mermaid
---
title: Host a Website on Amazon S3
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph ClientLayer["Client Layer"]
        Browser[/"Web Browser"/]
    end

    subgraph WebsiteEndpoint["S3 Static Website Hosting"]
        Endpoint(("S3 Website Endpoint"))
        HostingFeature{{"Static Website Hosting"}}
    end

    subgraph BucketLayer["S3 Bucket (Public Read)"]
        Bucket[("Amazon S3 Bucket")]
        IndexDoc[/"index.html"/]
        Assets[("Static Assets (CSS/Images)")]
    end

    subgraph AccessControl["Access Control"]
        BucketPolicy{{"Bucket Policy (JSON)"}}
        ACL{{"Object ACLs"}}
        PublicAccess{{"Public Access Config"}}
    end

    Browser -- "HTTP GET request" --> Endpoint
    Endpoint -- "routes to bucket" --> Bucket
    HostingFeature -- "enables HTTP access" --> Endpoint
    Bucket -- "serves index doc" --> IndexDoc
    Bucket -- "serves assets" --> Assets
    BucketPolicy -- "grants public read" --> Bucket
    ACL -- "object permissions" --> Assets
    PublicAccess -- "unblocks public" --> BucketPolicy
    IndexDoc -- "HTML response" --> Browser
class Bucket,Assets datastore
class Browser,IndexDoc io

    class Bucket,Assets datastore
    class HostingFeature,BucketPolicy,ACL,PublicAccess event
    class Browser,IndexDoc io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
