<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Telegram AI Bot with OpenClaw

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-openclaw-setup)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-openclaw-setup_k3m8n2q5)

---

## Introducing Today's Project

In this project, I installed OpenClaw, connected it to Telegram, and deployed a basic AI assistant that can respond to messages in real time. The goal was to validate how quickly an AI bot can be stood up using an existing framework and integrated with a messaging platform.

The bot runs through OpenClaw as the gateway, connects to an LLM provider through an API key, and exposes the assistant through Telegram for direct interaction.

### Key tools and concepts

This project used OpenClaw as the bot framework and gateway layer, Node.js and npm for installation and runtime, and the Telegram Bot API for messaging integration.

The concepts demonstrated include AI bot deployment, API-based model integration, Telegram bot configuration, access control through allowlists, and basic automation using cron jobs.

### Challenges and wins

This project took about one hour. The main challenge was configuring the tokens correctly, specifically aligning the Claude API key with the Telegram bot token inside the OpenClaw configuration.

Once the configuration was correct, the bot responded immediately. The key takeaway was how quickly a working AI assistant can be deployed when the framework handles routing and integration.

### Project Reflection

This project demonstrated how to deploy a working AI assistant using OpenClaw and expose it through Telegram with minimal setup.

The implementation covered core components including model integration, messaging, access control, and basic automation. Future improvements would focus on refining prompt behavior and extending the bot’s functionality beyond simple responses.

---

## Installing OpenClaw and Running the Gateway

I installed OpenClaw using npm on a Node.js environment and followed the setup prompts to configure the gateway.

The gateway acts as the central service that routes incoming Telegram messages to the AI model and returns responses. Once installed and configured, the service runs locally and listens for incoming requests.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-openclaw-setup_w4x9c2d7)

### Verifying the Gateway

After installation, I confirmed the gateway was running by checking the OpenClaw dashboard and verifying that it was active and ready to process requests.

This step ensured the bot backend was operational before connecting external services.

---

## My First Conversation with an AI Assistant

I accessed the OpenClaw control interface through the browser and initiated a test conversation with the assistant.

This validated that the model integration was working and that the system could process prompts and return responses.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-openclaw-setup_g8h3k6n1)

### Testing the assistant

I tested the assistant with a basic prompt and received a structured response from the model.

This confirmed that the OpenClaw gateway, API integration, and response handling were functioning correctly.

---

## Connecting Telegram for Mobile Access

I created a Telegram bot using BotFather and retrieved the bot token. This token was added to the OpenClaw configuration to enable communication between Telegram and the OpenClaw gateway.

Once configured, messages sent through Telegram were routed to the AI assistant and returned as responses in the chat.

### Configuring the Telegram channel

The Telegram bot token was placed in the OpenClaw configuration file under the Telegram integration settings.

This allowed OpenClaw to authenticate with the Telegram Bot API and send and receive messages on behalf of the bot.

---

## Securing the Assistant with Allowlists

To restrict access, I configured an allowlist using my Telegram user ID.

This ensures that only approved users can interact with the assistant and prevents unauthorized access to the bot.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-openclaw-setup_j5l9n3p7)

### Implementing security controls

The allowFrom configuration was used to define which user IDs are permitted to interact with the bot.

This acts as a simple access control mechanism and is necessary when exposing an AI assistant through a public messaging platform.

---

## Automating with Cron Jobs

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-openclaw-setup_d4f8h2k6)

### Building proactive automation

The cron job runs at 16:30 CST each day and sends a usage summary to email.

This introduces basic observability into the system without requiring additional monitoring infrastructure.

---

---
