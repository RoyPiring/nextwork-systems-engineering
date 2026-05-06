<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build an AI Meeting Prep Assistant

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-cowork-meeting-assistant)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_a2g6d8e1)

---

## Introducing Today's Project!

In this project, I built an automated meeting preparation system using Claude Desktop in Cowork mode. The goal was to transform fragmented inputs such as emails, calendar events, and documents into structured, actionable meeting briefings.

The system acts as a workflow engine that ingests data, organizes it, and generates outputs that reduce preparation time while improving context and decision readiness.

### Key tools and concepts

Claude Desktop in Cowork mode was used as the orchestration layer, with Gmail and Google Calendar acting as external data sources.

The concepts applied include autonomous task decomposition through sub-agents, context-aware processing using folder-level instructions, and workflow automation through scheduled execution and mobile triggers.

### Challenges and wins

This project took about 45 minutes. The main challenge was structuring prompts so sub-agents produce consistent and useful outputs instead of fragmented summaries.

Once refined, the system generated structured briefings with relevant insights. The key win was building a workflow that converts unstructured data into decision-ready outputs.

### Why I did this project

The goal was to reduce manual effort in meeting preparation and replace it with a repeatable system.

This reflects how AI systems are used in practice, where multiple inputs are aggregated and transformed into structured outputs that support decisions.

---

## Configuring Claude Desktop in Cowork Mode

I configured Claude Desktop in Cowork mode and connected a working directory to serve as the execution context.

This establishes a shared workspace where files, instructions, and outputs are processed and maintained across tasks.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_w3n8t5q1)

### Setting up the working folder

The working folder acts as the system boundary for all meeting preparation tasks.

It stores source files, generated outputs, and instructions, allowing the assistant to operate within a defined and controlled environment.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_f6j1v8x3)

---

## Organizing Files with Autonomous Sub-Agents

I tested Cowork’s ability to organize unstructured data by introducing mixed file types and requesting structured organization.

The system decomposed the task into smaller operations, categorizing files, extracting key details, and generating summaries. This demonstrates how sub-agents coordinate to process complex inputs.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_h8c3f6a1)

### Preparing sample files for the task

I introduced realistic data such as meeting agendas, reports, and research notes.

Using unstructured inputs validates that the system can handle real-world scenarios instead of idealized datasets.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_q3j8n5v2)

### How sub-agents coordinate work

The system distributes work across sub-agents that analyze content, apply categorization logic, and generate summaries.

This creates a pipeline where raw data is progressively refined into structured information, improving usability and clarity.

---

## Connecting Gmail and Google Calendar

I integrated Gmail and Google Calendar to provide real-time data inputs.

This allows the system to access meeting details, email threads, and scheduling context, which are required to generate accurate briefings.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_w4n7p1j6)

### Why Cowork needs real data access

Access to live data enables the system to generate outputs based on current information rather than static inputs.

This is required for producing relevant and timely meeting briefings.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_q6y2d5h8)

---

## Generating AI-Powered Meeting Briefings

I designed a prompt that instructs the system to generate structured meeting briefings from available data.

The output includes objectives, discussion points, action items, and risks, transforming raw inputs into a usable format.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_q8f4w1t6)

### Designing the meeting prep prompt

The prompt defines expected structure, scope, and output format.

This ensures consistency across executions and prevents variation in how the briefing is generated.

### Reviewing and iterating on output

Initial outputs exposed inconsistencies in action item accuracy.

Iteration improved alignment and ensured outputs were both structured and reliable.

---

## Automating Daily Meeting Briefings

I configured the system to generate meeting briefings on a recurring schedule.

This removes manual preparation and ensures consistent readiness for daily meetings.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_p4w9t6n1)

### Folder instructions vs. global instructions

Folder-level instructions were used to scope behavior to meeting preparation tasks.

This improves precision by limiting context to relevant data instead of applying broad instructions across unrelated workflows.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_m2b6y9d4)

---

## Triggering Meeting Prep from Mobile with Dispatch

I extended the system by integrating Dispatch to allow mobile-triggered execution.

This enables the workflow to be initiated from a phone while execution occurs on the desktop environment.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_h5j8n4p6)

### Connecting Dispatch to my phone

I connected the mobile app to the desktop environment to enable cross-device communication.

This allows real-time triggering of workflows without manual interaction with the desktop.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-cowork-meeting-assistant_r7f3d9b5)

### The full Dispatch loop

The workflow begins with a mobile trigger, retrieves relevant data from connected sources, processes it through the Cowork system, and returns a structured meeting briefing.

This demonstrates a complete pipeline from input to output, with orchestration handled across devices.

---

---
