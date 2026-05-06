# Transcribe Audio Files with AI

> Architecture diagram for one validated build inside the parent domain. Source document: [`../documents/05-aws-ai-transcribe.md`](../documents/05-aws-ai-transcribe.md).

```mermaid
---
title: Transcribe Audio Files with AI
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart LR
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic




    subgraph Inputs["Audio Inputs"]
        AudioFile[/"Audio File"/]
        RealTimeStream[/"Real-Time Stream"/]
    end

    subgraph Storage["Amazon S3"]
        InputBucket[("Input Bucket")]
        OutputBucket[("Output Bucket")]
    end

    subgraph TranscribeCore["Amazon Transcribe"]
        BatchJob("Batch Transcription Job")
        StreamJob("Real-Time Transcription")
        CustomVocab{{"Custom Vocabulary"}}
        VocabFilter{{"Vocabulary Filter"}}
    end

    subgraph Outputs["Transcription Output"]
        TranscriptJSON[/"Transcript JSON"/]
    end

    AudioFile -- "upload audio" --> InputBucket
    InputBucket -- "start batch job" --> BatchJob
    RealTimeStream -- "stream audio" --> StreamJob
    BatchJob -- "apply domain terms" --> CustomVocab
    StreamJob -- "apply domain terms" --> CustomVocab
    CustomVocab -- "filter sensitive terms" --> VocabFilter
    VocabFilter -- "write transcript" --> OutputBucket
    OutputBucket -- "deliver result" --> TranscriptJSON
class InputBucket,OutputBucket datastore
class CustomVocab,VocabFilter event

    class InputBucket,OutputBucket datastore
    class BatchJob,StreamJob service
    class CustomVocab,VocabFilter event
    class AudioFile,RealTimeStream,TranscriptJSON io
```

The diagram is hand-prompted from the build's content (LLM-generated, post-normalized for the Purpose Engineering visual theme). The full narrative, with screenshots and command outputs, lives in the source document linked above.
