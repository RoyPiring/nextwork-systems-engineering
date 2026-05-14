<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build an AI Second Brain with Claude Code

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-second-brain-claude-code)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

---

## Introducing Today's Project!

In this project, I built an AI-powered knowledge system using the LLM Wiki pattern, combining Claude Code with Obsidian to create a structured, queryable, and continuously evolving knowledge base. The goal was to move beyond static note-taking and establish a system that can ingest, organize, and synthesize information over time.

The system separates raw input from structured knowledge, enabling transformation pipelines that convert unprocessed information into linked, reusable artifacts.

### Key tools and concepts

Obsidian serves as the persistence layer where knowledge is stored and linked, while Claude Code acts as the transformation layer that processes and structures information.

The core concept is the LLM Wiki pattern, which separates raw input from structured knowledge. Markdown is used as the format that allows both readability and consistent processing across the system.

### Challenges and wins

This project took me approximately 60 minutes. The most challenging part was ensuring the CLAUDE.md schema produced the expected transformations and consistent formatting across all generated content.

### Why I did this project

The main challenge was maintaining structure while keeping the system flexible enough to scale.

Once the separation between raw and structured data was enforced, the system produced consistent and reusable outputs. The key win was establishing a repeatable process where information is transformed into organized, linked knowledge.

---

## Installing Obsidian and Claude Code

This phase establishes the foundation of the system by configuring both the storage and reasoning layers.

Obsidian functions as the persistence layer where knowledge is stored and linked, while Claude Code operates as the transformation layer that processes, restructures, and enriches that knowledge. The setup ensures that the system is not just storing information, but actively shaping it into usable formats.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_qw9n3t5y)

### Verifying my Claude Code install

The installation phase defines the system boundary.

Obsidian provides the vault, which acts as the single source of truth for all stored knowledge. Claude Code introduces the ability to interpret and modify that data. Verifying Claude Code ensures that the transformation layer is operational before introducing structured workflows.

---

## Building the Vault Architecture

Connecting Claude Code to the vault establishes the interface between storage and processing.

The separation between raw/ and wiki/ introduces a pipeline model. Raw content represents unstructured input, while the wiki layer represents processed, structured knowledge. This separation prevents contamination of curated knowledge with unvalidated data.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_v2b7n4p2)

### Inside the wiki/ folder

The vault structure defines how knowledge is categorized and retrieved.

The Concepts folder captures reusable ideas, Projects tracks applied work, Documentation stores reference material, and Index Logs provide entry points into the system. This layout mirrors how knowledge systems separate abstraction, execution, and reference layers.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_v2d1s6t4)

---

## Configuring CLAUDE.md and Slash Commands

The graph view exposes how knowledge connects across the system.

At this stage, the graph is sparse, which is expected. The value emerges as ingestion and linking increase, turning isolated notes into a connected network. This visualization reflects system maturity rather than initial setup.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_v3n8q1w6)

### The four slash command workflows

The CLAUDE.md file acts as the control layer for how the AI interacts with the system.

It defines structure, formatting, and domain expectations. Instead of relying on implicit behavior, the schema enforces consistency across all generated and modified content. This ensures that the system scales without degrading in quality or structure.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_p6x2m9k4)

### Scaffolding the slash commands

Claude Code turns each file into a node in a knowledge graph, enabling quick navigation and connection of ideas. When I type /name, it executes a pre-defined command, allowing for quick access to specific functionalities within my AI second brain.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_a9c4e7g1)

---

## Converting Source Notes Into the raw/ Folder

Testing validates that the schema produces predictable transformations.

Exporting existing data and converting it into Markdown ensures that legacy content can be integrated into the system. This step confirms that the ingestion process aligns with the defined structure.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_k8n4y1q3)

### How many files Claude Code converted

Importing data introduces real-world variability into the system.

By converting existing conversations into Markdown, the system begins operating on actual knowledge rather than synthetic examples. This is where the pipeline transitions from setup to active use.

### Checking the converted files in Obsidian

Verification ensures that transformation outputs meet structural requirements.

Clear headings, consistent tagging, and internal linking confirm that the data is not just stored, but organized in a way that supports retrieval and navigation. This step prevents long-term degradation of the knowledge base.

---

## Running the First Ingest Cycle

The ingest cycle is the core transformation process.

Raw inputs are processed, structured, and linked into the wiki layer. This is where the system begins to behave like a knowledge engine rather than a storage repository. Each cycle increases the density and usefulness of the knowledge graph.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_p3r8w5n1)

### The pages Claude Code created

The compiled index represents the system’s current state of knowledge.

It aggregates key areas such as concepts, projects, and documentation into accessible entry points. This allows navigation without requiring direct search, which improves usability as the system grows.

### Exploring a wiki page

Cross-linking transforms isolated notes into a network.

Projects link to underlying concepts, documentation supports implementation details, and related ideas reinforce each other. This interconnected structure enables the system to surface context instead of just individual data points.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_k9g4z6c2)

---

## Querying and Verifying My Wiki

### How my wiki answered with cited sources

---

## Logging Daily Progress

---

## Secret Mission: Dogfooding /lint and /log

In this project extension, I'm going to test the slash commands by running:

*   `/query` to synthesize an answer from your wiki.
*   `/lint` to health-check the wiki and fix any issues.
*   `/log` to capture a thought that isn't worth a full source.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_b3h7k9r2)

### What /lint found and how Claude fixed it

In this project extension, /lint reported several formatting inconsistencies and potential code style issues. I asked Claude to automatically fix these problems, and it successfully made the necessary adjustments to ensure the code adheres to the project's style guidelines and improves overall readability.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-second-brain-claude-code_g2j8v5x1)

### Capturing a thought with /log

In this project extension, I captured a thought with /log about the cross-linking between the "Projects" page, which lists ongoing and completed projects, and the "Documentation" page, which provides reference materials. Claude also updated the index.md file to reflect these changes, ensuring the index links every project page and every documentation page, with cross-references between them.

---

---
