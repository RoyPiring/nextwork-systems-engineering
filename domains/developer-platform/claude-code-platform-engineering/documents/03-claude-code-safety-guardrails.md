<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Claude Code Guardrails

**Project Link:** [View Project](http://learn.nextwork.org/projects/claude-code-safety-guardrails)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_m7r4k9w2)

---

## Introducing Today's Project!

In this project, I implemented security guardrails for Claude Code by combining permission controls, runtime hooks, and a policy layer. The goal was to move from basic access control to a layered security model that protects against misuse during code generation and execution.

The implementation focused on enforcing restrictions, identifying gaps, and adding interception logic to prevent unsafe operations in real time.

### Key tools and concepts

Claude Code was used as the execution environment, with jq supporting inspection and manipulation of configuration data.

The concepts applied include permission enforcement, runtime interception through hooks, and defense-in-depth. The focus was understanding how each layer contributes to controlling model behavior and preventing unsafe actions.

### Challenges and wins

This project took about 45 minutes. The main challenge was understanding the limitations of permission rules and how easily they can be bypassed without additional controls.

The key win was implementing layered guardrails that combine static restrictions with runtime enforcement, making the system more resilient.

---

## Setting Up the Security Testing Environment

I created a controlled test environment with Claude Code, jq, and a sample project containing simulated sensitive files.

This setup allowed testing guardrails without risk while validating how the system behaves under realistic conditions.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_h9c1y7b3)

### Understanding jq

jq was used to inspect and modify JSON configuration files.

This made it easier to verify guardrail settings and adjust rules without manual parsing.

### Creating sensitive test files

I created mock credential and configuration files to simulate sensitive data.

This provided a realistic target for testing access restrictions and validating that guardrails prevent exposure or modification.

---

## Configuring Permission Deny Rules

I configured deny rules in the Claude Code settings to block network access and prevent modification of sensitive files.

These rules restrict what actions the system can perform at a baseline level and act as the first layer of control.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_w3n8t5q1)

### How deny rules protect your project

Deny rules prevent outbound network calls and block operations that modify or delete critical files.

This limits the system to a controlled environment and reduces the risk of data exposure or unintended changes.

---

## Discovering the Permission Gap

When I asked Claude to list all files, it revealed the entire project directory structure, including the sensitive credential files. This tells me that deny rules alone are insufficient to protect against unauthorized access, as Claude Code can bypass them by simply listing files.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_d9f2a7c3)

---

## Writing the Safety Hook Scripts

To address the gap, I implemented hooks that intercept commands before execution.

These hooks validate actions in real time and block unsafe operations such as modifying protected files or executing risky commands.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_w3n8v5j1)

### Protecting sensitive files

The file protection hook prevents access to credential files, configuration data, and other sensitive resources.

This ensures that even if permissions are bypassed, critical data remains protected.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_m7r4k9w2)

### Blocking dangerous commands

The command validation hook blocks high-risk patterns such as destructive file operations and execution of remote scripts.

This prevents actions that could compromise the environment or result in data loss.

---

## Testing the Hooks in Action

Testing confirmed that hooks provide real-time enforcement while permissions act as baseline restrictions.

Together, they form a layered control model that reduces the likelihood of unsafe behavior.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_t4h7c2y8)

---

## Adding a CLAUDE.md Security Policy

I added a CLAUDE.md file to define security expectations and coding guidelines.

This serves as a policy layer that guides behavior but does not enforce it directly.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_w4n8x1q6)

### Advisory vs enforced guardrails

The CLAUDE.md policy defines expected behavior, while permissions and hooks enforce it.

This distinction is important because advisory controls alone do not prevent unsafe actions.

---

## Red-Teaming the Defense Layers

Testing showed that the policy layer was the easiest to bypass, while hooks provided the strongest control.

This confirmed that enforcement must happen at runtime, not just through guidance.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/claude-code-safety-guardrails_b9c4d2a7)

### Project reflection

This project took approximately 45 minutes. The main challenge was implementing hooks that effectively close the gaps left by permission rules.

The result is a defense-in-depth model that combines policy, restriction, and interception to control system behavior.

---

---
