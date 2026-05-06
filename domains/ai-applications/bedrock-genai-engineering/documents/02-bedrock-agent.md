<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# AI Finance Agent with Amazon Bedrock

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-genai-bedrock-agent)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

---

## Introducing Today's Project!

In this project, I built a basic AI finance agent using Amazon Bedrock and the Code Interpreter capability. The goal was to understand how an agent can combine natural language interaction with data processing to generate financial insights.

The agent uses a foundation model for reasoning and a code execution layer for analysis, allowing it to process financial data and return structured recommendations.

### Key services and concepts

### Challenges and wins

---

## Exploring Amazon Bedrock and Foundation Models

I accessed Amazon Bedrock through the AWS console and reviewed the available models and agent capabilities. This step focused on understanding how Bedrock provides managed access to foundation models and how agents extend those models with execution capabilities.

I selected Amazon Nova 2 Lite for this project due to its low latency and cost efficiency, which makes it suitable for lightweight analytical workloads.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_w5x8n1q4)

### Understanding foundation models

Foundation models are pre-trained models capable of handling a wide range of language and reasoning tasks. They provide the base layer for generating responses and interpreting user input.

In this project, the model handled natural language understanding and response generation, while the agent framework extended its capabilities with structured execution.

### Discovering Bedrock Agents

Bedrock Agents add an execution layer on top of foundation models. Instead of only generating text, the agent can perform actions such as running code and processing external data.

This allows the system to move beyond static responses and produce results based on actual data analysis, which is required for financial use cases

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_h4t7y1a5)

---

## Creating the AI Finance Agent

I created a Bedrock Agent configured as a finance assistant with instructions focused on budgeting, spending analysis, and basic financial guidance.

The agent was enabled with Code Interpreter, allowing it to execute Python code during interactions. This capability is required for analyzing datasets, performing calculations, and generating structured outputs.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_q4j6r2m8)

### Crafting the agent instructions

The instructions defined how the agent should interpret financial data and respond to user input.

The focus was on analyzing spending behavior, identifying trends, and generating recommendations based on user data. Clear instructions improved consistency and ensured the agent produced actionable outputs instead of generic responses.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_f2d8g4l6)

---

## Analyzing Spending Data with Code Interpreter

I uploaded a transaction dataset in CSV format and used the agent to analyze spending patterns.

The agent processed the data through the Code Interpreter, calculated totals by category, identified trends, and generated summaries based on the dataset. I then refined the prompts to improve the quality of the recommendations.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_p4r7t9v1)

### How Code Interpreter processed the data

The agent executed Python code to aggregate and analyze transaction data.

It grouped spending by category, calculated totals and percentages, identified recurring expenses, and generated summaries that reflect spending behavior over time. This allowed the output to be based on actual data instead of assumptions.

---

## Iterating on Agent Instructions with Traces

I updated the agent instructions to focus on identifying recurring expenses and generating cost reduction recommendations.

The output improved by shifting from general summaries to specific actions, such as identifying subscriptions and suggesting ways to reduce or eliminate unnecessary spending. This made the responses more practical and directly usable.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_q5s8u2w4)

---

## Enabling Cross-Session Agent Memory

I enabled cross-session memory so the agent could retain key information between interactions.

This allows the agent to maintain context such as spending habits and financial goals, improving continuity across sessions and making responses more relevant over time.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_n5m3k7j1)

### Session summarization vs full history

I configured memory using session summarization instead of storing full conversation history.

Summarization preserves key information while reducing storage and keeping responses focused. This approach balances context retention with efficiency.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-agent_t8h1g5f3)

### Testing cross-session recall

I tested memory by setting financial preferences in one session and verifying that the agent recalled them in a later interaction.

The agent successfully retained and reused the information, confirming that cross-session memory was working as expected.

---

## Wrapping Up

---

---
