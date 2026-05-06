# Transcribe Audio Files with AI

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-transcribe)

## Business Context

### Problem Statement
The scope includes batch transcription, real-time transcription, and accuracy controls such as custom vocabularies and vocabulary filters. The system is used to evaluate how configuration choices affect transcription quality, data handling, and output usability, rather than to deliver an end-user application.

### Use Cases
- Audio file transcription
- Speech-to-text conversion
- Custom vocabulary for domain-specific terms
- Content filtering for sensitive information

### Prerequisites
- AWS account with Transcribe access
- Audio files for transcription
- S3 bucket for storage
- Basic understanding of transcription concepts

### Scope
- Amazon Transcribe service setup
- Batch transcription jobs
- Custom vocabulary configuration
- Vocabulary filters for content control
- Real-time transcription evaluation

### Non-Goals
- Custom model training
- Production application development
- Advanced speaker diarization
- Multi-language transcription

## Architecture

### Components
- **Amazon S3:** Storage for audio inputs and transcription outputs
- **Amazon Transcribe:** Managed speech-to-text processing service
- **Custom Vocabularies:** Domain-specific term recognition
- **Vocabulary Filters:** Content suppression mechanisms

### System Design
```
Audio File (S3)
    ↓
Transcribe Job
    ↓
Custom Vocabulary
    ↓
Vocabulary Filter
    ↓
Transcription Output (S3)
```

### Integration Points
- S3 for audio storage
- Transcribe API for job management
- Custom vocabulary configuration
- Vocabulary filter application

## Implementation

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_o2p3q4r1)

---

## Introducing Today's Project!

The scope includes batch transcription, real-time transcription, and accuracy controls such as custom vocabularies and vocabulary filters. The system is used to evaluate how configuration choices affect transcription quality, data handling, and output usability, rather than to deliver an end-user application.

### Tools and concepts

Amazon S3 provides durable storage for audio inputs and transcription outputs. Amazon Transcribe performs managed speech-to-text processing. Key concepts exercised include custom vocabularies, vocabulary filters, and real-time transcription modes.

### Project reflection

The transcription workflow spans audio upload, baseline transcription, and enhanced transcription through configuration refinement. Most effort is concentrated on tuning vocabularies and filters to correct recognition errors while avoiding unintended suppression of valid terms.

The outcome demonstrates that transcription accuracy and reliability are driven by domain alignment and configuration discipline rather than raw service usage. The system highlights the tradeoffs between precision, coverage, and content control.

---

## S3 and Transcribe

Amazon S3 is used as the storage boundary for raw audio and transcription results. Amazon Transcribe processes a recorded customer service call stored in S3 and produces structured transcription output without requiring application-managed compute or custom model training.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_k1l4m7n0)

---

## Run A Transcription Job

A transcription job is initiated by referencing an audio object in S3 and selecting language, model type, and output parameters in Amazon Transcribe. Job execution is asynchronous, with status monitoring until completion and results written back to S3.

Amazon Transcribe model selection influences recognition accuracy based on audio characteristics such as domain language, speaker variability, and background noise. Supported scenarios include general-purpose, domain-optimized, and real-time transcription.

Optional features such as subtitling and speaker partitioning enrich the output by adding time-aligned text and speaker attribution, improving readability and downstream analysis without altering recognition behavior.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_g0h1i2j3)

---

## Baseline Transcript Review

A baseline transcription is generated using default Amazon Transcribe settings to establish an unmodified reference output. This baseline serves as a control for evaluating recognition accuracy prior to customization.

The baseline transcript contains inaccuracies in names and domain-specific terms, reflecting the limitations of generic language models when applied to customer service audio with specialized terminology.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_s3t6u9v2)

---

## Custom Vocabulary

Custom vocabularies extend Amazon Transcribe by defining domain-specific terms and their pronunciations. This capability improves recognition accuracy for technical jargon and proper nouns that are consistently misinterpreted by default models.

Effective vocabulary configuration requires identifying recurring transcription errors and mapping each term to an accurate phonetic representation. This constrains recognition behavior without modifying the underlying acoustic model.

The configured vocabulary targets customer service terminology and technical phrases observed in the baseline transcript, improving consistency and precision in subsequent transcription runs.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_e3f4g5h6)

---

## Vocabulary Filters

Vocabulary filters suppress specified words or phrases from transcription output without changing speech recognition behavior. This mechanism is used for content control rather than accuracy improvement.

The configured filter removes customer-identifying information such as names and payment details using a predefined keyword list, reducing exposure of sensitive data in transcription artifacts.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_u7v8w9x0)

---

## Enhanced Transcription

### I ran a new transcription with my custom vocabulary and filtering settings

A subsequent transcription job is executed using both the custom vocabulary and vocabulary filter configurations.

The enhanced output demonstrates improved recognition of domain-specific terms while excluding filtered content, resulting in a transcript better aligned with accuracy and data handling requirements than the baseline.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_k1l2m3n4)

---

## Real Time Transcription

Real-time transcription is evaluated to observe recognition behavior during live audio processing. This mode prioritizes low-latency output and provides immediate visibility into recognition performance.

Custom vocabularies and filters are applied during real-time transcription to address accuracy and data protection concerns. Compared to batch transcription, this approach enables faster configuration feedback while operating under streaming constraints.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-ai-transcribe_a5b6c7d8)

---

## Validation

### Expected Results
- Audio files uploaded to S3
- Transcription jobs execute successfully
- Baseline transcription generated
- Custom vocabulary improves accuracy
- Vocabulary filters suppress sensitive content
- Enhanced transcription shows improvements
- Real-time transcription functional

### Verification Steps
1. **S3 Setup:** Verify audio file storage
   - Check audio files in S3
   - Verify file accessibility
2. **Transcription Job:** Verify job execution
   - Check job status
   - Verify output in S3
3. **Baseline Review:** Analyze baseline accuracy
   - Identify recognition errors
   - Document improvement areas
4. **Custom Vocabulary:** Verify vocabulary application
   - Check vocabulary configuration
   - Compare accuracy improvements
5. **Vocabulary Filter:** Verify filter application
   - Check filtered content removal
   - Verify sensitive data suppression
6. **Enhanced Transcription:** Compare with baseline
   - Measure accuracy improvements
   - Verify filter effectiveness
7. **Real-Time Transcription:** Test real-time mode
   - Verify low-latency output
   - Check configuration application

### Observed Results
TODO: capture S3 file upload confirmation, transcription job execution results, baseline accuracy analysis, custom vocabulary effectiveness, filter application results, enhanced transcription comparison, and real-time transcription test results

### Known Failure Conditions
- **Audio Format Issues:** Unsupported format, convert to supported format
- **S3 Access Errors:** IAM permissions, verify bucket access
- **Transcription Job Failures:** Check job status and error messages
- **Vocabulary Configuration Errors:** Verify vocabulary format and syntax
- **Filter Over-Suppression:** Too many terms filtered, adjust filter list

---

## Navigation

| Previous |
|----------|
| [AI Prompt Engineering](./ai-promptengineering.md) |