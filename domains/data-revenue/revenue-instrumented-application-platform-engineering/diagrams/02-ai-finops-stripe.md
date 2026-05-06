# Secure Payments with Stripe

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/02-ai-finops-stripe.md`](../documents/02-ai-finops-stripe.md).

```mermaid
---
title: Secure Payments with Stripe
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph ClientLayer["Client Layer (Next.js on Vercel)"]
        Browser[/"Customer Browser"/]
        StripeJS("Stripe.js Library")
    end

    subgraph ServerLayer["Server-Side Enforcement"]
        CheckoutAPI("Checkout Session API")
        PriceCatalog[("Server Pricing Catalog")]
        EnvVault[("Vercel Env Vars (Secret Keys)")]
    end

    subgraph StripeCloud["Stripe Cloud"]
        StripeAPI("Stripe API")
        Hosted[/"Stripe Hosted Checkout"/]
    end

    subgraph WebhookSecurity["Webhook Verification"]
        WebhookEP("Webhook Endpoint")
        SigVerify{{"Signature Verifier"}}
        OrderDB[("Order Ledger")]
    end

    Browser -- "init checkout" --> StripeJS
    StripeJS -- "request session" --> CheckoutAPI
    CheckoutAPI -- "lookup price" --> PriceCatalog
    CheckoutAPI -- "read secret" --> EnvVault
    CheckoutAPI -- "create session" --> StripeAPI
    StripeAPI -- "redirect URL" --> Hosted
    Browser -- "pay on Stripe" --> Hosted
    Hosted -- "payment_intent event" --> WebhookEP
    WebhookEP -- "verify HMAC sig" --> SigVerify
    SigVerify -. "rejects unsigned" .-x WebhookEP
    SigVerify -- "fulfill order" --> OrderDB

    class PriceCatalog,EnvVault,OrderDB datastore
    class StripeJS,CheckoutAPI,StripeAPI,WebhookEP service
    class SigVerify event
    class Browser,Hosted io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
