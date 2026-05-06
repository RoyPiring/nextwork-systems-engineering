---
original_filename: legendary-ai-security-audit-copy.md
renamed_at: 2026-05-04
renamed_from: legendary-ai-security-audit-copy.md
renamed_to: ai-briefings-engineering/docs/03-ai-security-audit.md
schema: nextwork-verified
rerouted_at: 2026-05-04
rerouted_from: ai-briefings-engineering/docs/03-ai-security-audit.md
rerouted_to: ai-enabled-cloud-security-automation-engineering/docs/04-ai-security-scanner-python.md
---

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# AI Security Scanner for Python

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-security-audit-copy)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_tz9xp5km)

---

## Introducing Today's Project!

In this project, I built a command-line security scanner that uses a generative AI model to analyze Python code for vulnerabilities. The goal was to evaluate how AI can augment traditional static analysis by identifying security issues through pattern recognition and contextual reasoning.

The system takes Python code as input, sends it to a model for analysis, and returns structured findings that highlight potential vulnerabilities and recommended fixes. This shifts security analysis from purely rule-based detection to a hybrid model that incorporates reasoning and context awareness.

### Key tools and concepts

Python was used as the execution layer, with the Gemini API providing the analysis capability.

The concepts applied include prompt engineering for security analysis, secure credential management, CLI-based tooling, and vulnerability detection. The system also incorporates structured outputs and severity classification to make results actionable.

### Challenges and wins

This project took about 60 minutes. The main challenge was designing a prompt that produces consistent, relevant, and actionable security findings.

Once refined, the model identified multiple classes of vulnerabilities and returned structured output. The key win was building a working scanner that can analyze real code and surface risks with minimal setup.

---

## Generating the Gemini API Key

I generated and configured an API key to authenticate requests to the model.

This establishes the trust boundary between the application and the external AI service and enables secure access to analysis capabilities.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_h3ymx6kd)

---

## Setting Up the Python Environment

I created an isolated Python environment to manage dependencies and execution.

This ensures reproducibility and prevents conflicts with other projects, which is required for maintaining consistent behavior in CLI-based tools.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_rb4kj7mz)

### Installing the required packages

I installed the required libraries to support environment configuration and API interaction.

These libraries handle credential loading, API communication, and optional output formatting, enabling the scanner to operate as a standalone tool.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_pw6dq3ck)

---

## Connecting to the Gemini API

I configured the application to connect to the Gemini model and validate communication.

This step ensures the system can send code for analysis and receive responses, forming the core interaction loop of the scanner.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_yw8dt2jh)

### Securing the API key with a .env file

I moved the API key into a .env file to prevent exposure in the codebase.

This aligns with standard security practices by separating secrets from application logic and allowing environment-specific configuration.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_kn3jm8tb)

### Verifying the connection

I tested the connection with a simple request to confirm the model was accessible.

A valid response confirmed that authentication and communication were correctly configured.

---

## Engineering the Security Prompt

I designed a prompt that instructs the model to act as a security expert and analyze Python code for common vulnerabilities.

The prompt defines scope, expected output, and focus areas such as injection risks, unsafe input handling, and improper data storage. This ensures the analysis remains targeted and consistent.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_rk9mb7ys)

---

## Building the File Scanner

I extended the tool to read Python files and pass their contents to the model.

This allows the scanner to operate on real codebases instead of isolated snippets, making it usable in practical scenarios.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_jt7px3na)

---

## Running the Security Audit

I tested the scanner using sample files containing known vulnerabilities.

This validated that the system can detect issues and return meaningful findings under controlled conditions.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_ub6ry1wf)

### Analyzing the vulnerability report

The scanner identified multiple vulnerabilities, including SQL injection risks and cross-site scripting patterns.

The output demonstrated that the model can detect both obvious and less visible issues, providing insight beyond basic pattern matching.

---

## Adding Color-Coded Severity Ratings

I added severity classification to the output to improve readability and prioritization.

This allows users to quickly identify critical issues and focus remediation efforts where they matter most.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-security-audit-copy_mj7rc2vy)

### How the color system works

Severity levels are mapped to color-coded output in the terminal.

This improves usability by making results easier to interpret during execution without requiring additional tools.

---

## Wrapping Up

This project shows how AI can extend security analysis beyond static rules by adding context-aware reasoning. The scanner processes code, identifies vulnerabilities, and returns structured findings that can be acted on immediately. The same pattern can be applied to CI/CD pipelines or pre-commit checks, where AI augments existing security controls rather than replacing them.

---

---
