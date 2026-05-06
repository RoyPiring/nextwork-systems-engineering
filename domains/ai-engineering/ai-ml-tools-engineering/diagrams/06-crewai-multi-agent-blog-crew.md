# Build a Blog Writing Crew with CrewAI

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/06-crewai-multi-agent-blog-crew.md`](../documents/06-crewai-multi-agent-blog-crew.md).

```mermaid
---
title: Build a Blog Writing Crew with CrewAI
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Inputs["Inputs & Config"]
        Topic[/"Blog Topic Input"/]
        AgentsYaml("agents.yaml (roles)")
        TasksYaml("tasks.yaml (chain)")
    end

    subgraph Orchestration["CrewAI Orchestration"]
        Crew{{"Crew Runtime"}}
        PyBinder("Python Binder")
    end

    subgraph AgentPipeline["Agent Pipeline"]
        Researcher("Researcher Agent")
        Writer("Writer Agent")
        Editor("Editor Agent")
    end

    subgraph Output["Output"]
        BlogPost[(Final Blog Post)]
    end

    Topic -- "topic input" --> Crew
    AgentsYaml -- "role definitions" --> PyBinder
    TasksYaml -- "task sequence" --> PyBinder
    PyBinder -- "binds config" --> Crew
    Crew -- "kickoff research" --> Researcher
    Researcher -- "research notes" --> Writer
    Writer -- "draft handoff" --> Editor
    Editor -- "refined output" --> BlogPost
class BlogPost datastore
class Crew event

    class BlogPost datastore
    class AgentsYaml,TasksYaml,PyBinder,Researcher,Writer,Editor service
    class Crew event
    class Topic io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
