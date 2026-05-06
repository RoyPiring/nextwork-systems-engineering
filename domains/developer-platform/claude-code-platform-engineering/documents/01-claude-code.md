<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Get Started with Claude Code

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-claude-code)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_y3n7t1f5)

---

## Introducing Today's Project!

In this project, I built a personal portfolio website using Claude Code from the terminal. The objective was to understand how a CLI-based AI coding assistant operates inside a structured project environment. This was not just about generating HTML and CSS. It was about controlling configuration, permissions, cost, and context while iterating on a real deliverable. The result is a portfolio site built through disciplined prompting and environment management.

### Key tools and concepts

The primary tool was Claude Code, a CLI interface that integrates Claude models directly into a local project directory. I used a code editor with an integrated terminal and a package manager such as npm or pip for installation.

Key concepts included project folder structure, CLAUDE.md configuration, permission modes, token usage tracking, and context window limits. I used directory referencing such as @projects/ to dynamically incorporate content. This required understanding both LLM behavior and standard web development practices.

### Challenges and wins

The build took approximately one hour. The main challenge was understanding how @projects/ references allow Claude Code to treat folder contents as contextual inputs. Once that was clear, iteration became predictable and efficient. The biggest win was learning how to control scope and behavior instead of relying on generic prompts.

---

## Installing Claude Code

I installed Claude Code using the official documentation and a supported package manager. After authentication, I validated CLI functionality before associating it with a project folder.

Running Claude Code without a project directory demonstrated its dependency on structured environments. It operates with limited awareness outside a defined folder. This reinforces that it is designed for scoped development work, not open-ended interaction.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_w5j9t3f7)

### Claude Code vs Claude.ai

Claude Code is a terminal-based development tool. Claude.ai is a browser-based conversational interface. Claude Code operates within a local filesystem and interacts with project files under defined permissions. Claude.ai focuses on text-based interaction.

Claude Code is built for execution inside a development workflow. Claude.ai is built for dialogue.

---

## Understanding the Trust Prompt

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_j6w2n8r4)

### Why a project folder matters

Claude Code depends on directory context to operate correctly. A defined project folder establishes boundaries, limits file access, and ensures predictable behavior.

Without a project folder, the tool lacks environmental awareness. With one, it can reason over files, configuration, and structure. The project folder is the operational boundary.

---

## Having My First Conversation with Claude Code

When I initiated a session without a project folder, Claude Code responded by indicating that it required directory context. This confirmed that the tool enforces structure before execution.

That behavior aligns with secure development practices. It does not assume scope. It requires it.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_g3r7v1k5)

---

## Setting Up Project Memory with CLAUDE.md

I created a CLAUDE.md file to define model behavior and project settings. This file acts as the control plane for Claude Code within the project.

It allows configuration of model selection, thinking mode, permission mode, and context window size. Centralizing these settings ensures consistent behavior across sessions and prevents accidental drift in configuration.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_d8k2n6q4)

### How CLAUDE.md works

CLAUDE.md defines how Claude Code operates within the project. I specified the model version, selected a creative thinking mode, set permissions to read-only, and adjusted the context window to 20,000 tokens.

Read-only mode prevents unintended file modification. The context window size supports larger reasoning tasks. Defining these parameters upfront creates predictable execution.

---

## Configuring Claude Code

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_k7m3q9v5)

### Settings and permission modes

Configuration was performed directly inside CLAUDE.md. Permission modes include read-only, read-write, and admin. I selected read-only to enforce safety while generating code.

This ensured that outputs were reviewed before any structural changes were made to the project files.

---

## Building My Portfolio with Claude Code

I instructed Claude Code to generate a structured portfolio with sections for About Me, Skills, Projects, and Contact. After generation, I refined layout, styling, and responsiveness through iterative prompts.

Each iteration was validated against token usage and context size to avoid unnecessary cost or truncation. The workflow was generate, review, adjust, repeat.

---

## Checking Token Usage

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_u8c2f6j4)

### Understanding /cost and /context

The /cost command provides visibility into token usage and estimated cost. The /context command displays the active context window and configuration parameters.

These controls are critical for managing scale, especially as prompts grow in complexity.

---

## Building and Iterating on the Portfolio

### How I built my portfolio

I began with a basic layout structure. After validating output, I refined styling with custom CSS, added interactive components such as skill indicators, and ensured mobile responsiveness.

Iteration was controlled and incremental. Each change was intentional and reviewed before proceeding to the next refinement.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_y3n7t1f5)

---

## Adding Real Projects (Secret Mission)

For the extension, I created a projects/ directory and stored individual project files within it. The goal was to separate content from layout and make updates modular.

This structure allows new projects to be added without rewriting the entire portfolio.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code_v9h3c7p1)

### Using @ folder references

I used @projects/ to reference project files dynamically within the portfolio. This allowed Claude Code to ingest content from the directory and integrate it into the Projects section.

This approach makes the site easier to maintain and scale. Project data lives in one place. The layout consumes it.

---

## What I Learned

This project clarified how to integrate an LLM into a structured development workflow. The key takeaway is that environment control, permission management, and cost awareness matter as much as prompt quality.

Next, I plan to deepen front-end capability through advanced CSS animation and 3D transformations to improve visual engagement without sacrificing performance.

---

---
