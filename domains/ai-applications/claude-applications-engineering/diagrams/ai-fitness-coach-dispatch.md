# Build a Fitness Coach with Claude

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/ai-fitness-coach-dispatch.md`](../documents/ai-fitness-coach-dispatch.md).

```mermaid
---
title: Build a Fitness Coach with Claude
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph UserLayer["User Layer"]
        User[/"User Profile Input"/]
        Goals[/"Goals and Constraints"/]
    end

    subgraph PromptLayer["Structured Prompting"]
        ContextMgr("Context Manager")
        PromptTpl{{"Prompt Template"}}
        OutputSchema{{"Output Schema"}}
    end

    subgraph CoachCore["Claude Coach Core"]
        Claude("Claude Model")
        WorkoutGen("Workout Plan Generator")
        MealGen("Meal Plan Generator")
        GroceryGen("Grocery Workflow")
    end

    subgraph Persistence["Iteration and Memory"]
        SessionLog[("Session Log")]
        EvalNotes[("Eval Iteration Notes")]
    end

    User -- "profile and prefs" --> ContextMgr
    Goals -- "targets and limits" --> ContextMgr
    ContextMgr -- "structured context" --> PromptTpl
    PromptTpl -- "task-oriented prompt" --> Claude
    Claude -- "workout request" --> WorkoutGen
    Claude -- "meal request" --> MealGen
    MealGen -- "ingredients" --> GroceryGen
    WorkoutGen -- "schema check" --> OutputSchema
    MealGen -- "schema check" --> OutputSchema
    OutputSchema -- "validated plan" --> SessionLog
    SessionLog -- "feedback loop" --> EvalNotes
    EvalNotes -- "refined prompt" --> PromptTpl
class SessionLog,EvalNotes datastore
class PromptTpl,OutputSchema event

    class SessionLog,EvalNotes datastore
    class ContextMgr,Claude,WorkoutGen,MealGen,GroceryGen service
    class PromptTpl,OutputSchema event
    class User,Goals io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
