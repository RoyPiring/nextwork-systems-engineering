# Prompt Engineer a Lesson Plan

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-prompt-engineering-lesson.md`](../documents/ai-prompt-engineering-lesson.md).

```mermaid
---
title: Prompt Engineer a Lesson Plan
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    subgraph Inputs["Inputs"]
        Author[/"Prompt Author"/]
        Topic[/"Lesson Topic"/]
    end

    subgraph PromptDesign["Reusable Prompt Template"]
        RolePrompt("Role Prompt (Teacher)")
        XmlTags("XML-Style Tag Schema")
        StructRules("Structure Rules")
    end

    subgraph Generation["Claude Generation Layer"]
        Claude{{"Claude Model"}}
        Output[("Structured Lesson Plan")]
    end

    subgraph Refinement["Iterative Refinement"]
        Review("Output Review")
        TuneLoop{{"Iterate on Prompt"}}
    end

    Author -- "defines role" --> RolePrompt
    Topic -- "fills template" --> XmlTags
    RolePrompt -- "sets perspective" --> Claude
    XmlTags -- "enforces structure" --> Claude
    StructRules -- "shapes output" --> Claude
    Claude -- "generates plan" --> Output
    Output -- "quality check" --> Review
    Review -- "refine prompt" --> TuneLoop
    TuneLoop -- "update template" --> StructRules

    class Output datastore
    class RolePrompt,XmlTags,StructRules,Review service
    class Claude,TuneLoop event
    class Author,Topic io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
