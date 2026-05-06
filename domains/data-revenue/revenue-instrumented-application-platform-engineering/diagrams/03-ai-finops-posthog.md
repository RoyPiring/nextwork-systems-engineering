# Privacy-First Checkout Analytics

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/03-ai-finops-posthog.md`](../documents/03-ai-finops-posthog.md).

```mermaid
---
title: Privacy-First Checkout Analytics
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph CheckoutFlow["Checkout Flow"]
        User[/"Shopper"/]
        CartPage("Cart Page")
        PaymentPage("Payment Page")
        ConfirmPage("Confirmation Page")
    end

    subgraph Instrumentation["Privacy-First Capture"]
        PostHogSDK("PostHog SDK")
        EventFilter{{"PII Scrubber"}}
        SessionReplay("Session Replay (masked)")
    end

    subgraph Analytics["PostHog Analytics"]
        Funnel[("Conversion Funnel")]
        Segments[("Browser Segments")]
    end

    subgraph Optimization["Iterative Feedback Loop"]
        Hypothesis("Drop-off Hypotheses")
        Remediation("Remediation Backlog")
    end

    User -- "browses cart" --> CartPage
    CartPage -- "step event" --> PostHogSDK
    PaymentPage -- "step event (no PAN)" --> PostHogSDK
    ConfirmPage -- "success event" --> PostHogSDK
    PostHogSDK -- "scrub payment data" --> EventFilter
    EventFilter -- "safe events" --> Funnel
    PostHogSDK -- "DOM masking" --> SessionReplay
    SessionReplay -- "compliant replay" --> Segments
    Funnel -- "drop-off signals" --> Hypothesis
    Segments -- "browser friction" --> Hypothesis
    Hypothesis -- "test ideas" --> Remediation
    Remediation -- "fixes shipped" --> CartPage

    class Funnel,Segments datastore
    class CartPage,PaymentPage,ConfirmPage,PostHogSDK,SessionReplay,Hypothesis,Remediation service
    class EventFilter event
    class User io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
