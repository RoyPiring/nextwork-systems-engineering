<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Claude Code Skills Basics

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-claude-code-skills)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code-skills_n2t8w6j4)

---

## Introducing Today's Project!

In this project I built Git-powered Claude Code Skills that automatically commit code changes and generate changelogs from repository history. The goal was to test how AI-assisted development fits into standard engineering workflows such as Git version control, structured commits, and automated documentation.

The project focused on configuring the environment, building the skill logic, and validating that the automation reliably reads repository history and produces usable changelog output.

### Key tools and concepts

This project used Git, Claude Code Skills, and Python tooling. The main concepts explored were Git-based automation, Conventional Commits, YAML frontmatter configuration, skill orchestration, and automation hooks.

Together these components show how AI can integrate into normal development workflows by automating commits, documentation, and code formatting.

### How long this project took

The project took about 60 minutes. The most time was spent initializing the Git repository and understanding how the YAML frontmatter controls skill execution.

Once configured, the automation pipeline worked consistently.

### Project reflection

This project demonstrated how AI-assisted workflows can automate repetitive development tasks such as commit creation and changelog documentation.

The next step is applying the same automation concepts to larger development workflows, including web application development and cloud-based deployments.

---

## Setting Up Claude Code and Git

I verified the Claude Code installation and ensured the environment was running the current version. I then created a project directory and initialized a Git repository to track all development changes.

After the repository was created, I added basic project files to establish a baseline code state. I committed these files to create the first entry in the repository history.

At this point the project consisted of a functioning Git repository, a working Claude Code environment, and an initial commit that serves as the baseline for later automation.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code-skills_c5r2w8j3)

### Setting up the Git repository

---

## Building a Changelog Generator Skill

I created a Claude Code Skill that generates changelogs from Git history. The skill directory contains a SKILL.md file that defines how Claude reads the repository log and converts commit data into documentation.

The skill parses commit messages, timestamps, and authorship information and writes the results to a CHANGELOG.md file.

After implementing the instructions, I invoked the skill and verified the output. The changelog accurately reflected the repository history and confirmed the automation works.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code-skills_g6q3l5c7)

### What Claude did when I invoked the skill

When /changelog was executed, Claude analyzed the Git log and extracted commit messages, authors, and timestamps. The system generated a CHANGELOG.md file listing the commits in reverse chronological order.

Each entry summarized the change and included commit metadata. The output produced a clean development history without manual documentation.

---

## Configuring Skill Frontmatter

I added YAML frontmatter to the SKILL.md file to define skill metadata. This included the skill name, description, and the allowed-tools field that specifies which tools the skill can access.

To test the configuration, I added more code and created a second commit so the changelog could process multiple entries.

I then triggered the skill using natural language. Claude interpreted the request and executed the skill automatically.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code-skills_k7v9x3m1)

### How allowed-tools works as a security boundary

The allowed-tools setting restricts which tools a Claude Code Skill can use during execution. Only the explicitly defined tools are available to the skill.

This prevents the skill from accessing unrelated system functions and keeps automation within a controlled scope. The result is predictable and safer execution behavior.

---

## Building a Dev Pipeline with Smart Commit

After validating the changelog automation, I expanded the project into a small development pipeline.

I created a smart-commit skill that stages files and generates commit messages using the Conventional Commits format. This standardizes commit history and removes manual message formatting.

I then built an orchestrator skill that runs multiple skills in sequence. The orchestrator first runs smart-commit to create the commit, then runs the changelog skill to update the CHANGELOG.md.

Testing confirmed the pipeline stages changes, creates structured commits, and updates documentation automatically.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code-skills_n2t8w6j4)

### How the orchestrator coordinates skills

The orchestrator manages the order of execution in the automation pipeline.

It begins by running /smart-commit, which stages files and creates a commit using the Conventional Commits structure. After the commit is created, the pipeline runs /changelog.

The changelog skill reads the updated Git history and regenerates the CHANGELOG.md. Every code change therefore produces both a commit and an updated changelog entry.

---

## Adding Hook Triggers

I extended the project by adding a hook trigger that runs after Claude Code executes a tool.

I installed Black, a Python code formatter, and configured a PostToolUse hook in the .claude/settings.json file. This hook runs automatically after tool execution.

To verify the hook, I generated poorly formatted Python code. The hook triggered Black, which reformatted the code to match Python style standards.

This confirmed automated formatting can be integrated into the Claude workflow.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-claude-code-skills_q3f7y2m5)

---

---
