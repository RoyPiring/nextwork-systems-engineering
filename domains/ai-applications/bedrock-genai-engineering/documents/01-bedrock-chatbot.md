<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build an AI Chatbot with Amazon Bedrock

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-genai-bedrock-chatbot)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_t4w8n1x5)

---

## Introducing Today's Project

In this project, I built a simple AI chatbot using Amazon Bedrock and Python directly from AWS CloudShell. The goal was to understand how to interact with a foundation model through the Bedrock Converse API and generate responses programmatically.

The chatbot sends prompts to an Amazon Bedrock foundation model and receives generated responses through a Python script using the AWS Boto3 SDK. This project demonstrates the basic workflow for integrating generative AI capabilities into a cloud application without managing model infrastructure.

### Key tools and concepts

This project used Amazon Bedrock to access a hosted foundation model. AWS CloudShell provided a browser-based environment to write and execute Python code without local setup. Python and the AWS Boto3 SDK were used to interact with the Bedrock API.

The implementation introduced foundation models, the Bedrock Converse API, system prompts, inference parameters, guardrails, and conversation history. These components allow an application to send prompts, receive responses, control model behavior, and apply safety controls.

### Challenges and wins

This project took about 45 minutes to complete. The main challenge was understanding the request format required by the Bedrock Converse API and structuring the message payload correctly.

Once the API structure was clear, sending prompts and receiving responses from the model worked immediately. The biggest takeaway was how quickly a basic conversational application can be built when the model infrastructure is fully managed.

---

## Discovering Amazon Bedrock

The first step was navigating to Amazon Bedrock in the AWS console and exploring the model catalog. This provided visibility into the available foundation models and their capabilities.

I used the Bedrock playground to test the Amazon Nova 2 Lite model and observe how it responded to prompts. This helped confirm the model’s behavior before integrating it into code.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_j5k8m3n6)

### Understanding Foundation Models

Foundation models are large pre-trained AI models capable of generating text, answering questions, and performing other language tasks. They are trained on large datasets and can handle many tasks without additional training.

Amazon Bedrock provides access to these models through managed APIs, allowing developers to use them directly without hosting or maintaining machine learning infrastructure.

---

## Chatting with an AI Model

Using the Bedrock playground, I sent a prompt asking about the capabilities of foundation models available in Amazon Bedrock.

The model responded with an explanation of how different models can support conversational applications and recommended choosing models optimized for dialogue when building chatbots.

This confirmed the model could interpret prompts and produce structured responses.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_b3c6d8f1)

---

## Writing My First AI API Call

Using AWS CloudShell, I wrote a Python script that sends a prompt to Amazon Bedrock using the Boto3 SDK.

The script initializes a Bedrock client, sends a request through the Converse API, and prints the response returned by the foundation model.

Running the script demonstrated how an application can programmatically interact with a Bedrock model.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_m4r9w2t6)

### Understanding the Converse API

The Bedrock Converse API allows applications to send conversational prompts to foundation models. Messages are passed as structured input containing the user prompt and any previous messages.

This format allows the model to understand the conversation context and generate responses accordingly.

---

## Running the Bedrock Script

After creating the script, I ran it in CloudShell. The request was sent to the Amazon Nova 2 Lite model and returned a generated response.

The output confirmed the script successfully connected to Amazon Bedrock and processed the prompt through the foundation model.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_b6d1g5k9)

---

## Building a Multi-Turn Chatbot

Next, I modified the script to support multiple interactions. Conversation history was stored in a messages list so previous prompts and responses were included in each request.

This allows the chatbot to maintain context and respond based on the ongoing conversation instead of treating each prompt independently.

### System Prompt and Inference Parameters

A system prompt was added to guide the chatbot’s behavior and keep responses clear and helpful.

Inference parameters were configured to control response generation. The temperature was set to 0.7 to allow some variation in responses, and the maximum token limit was set to 512 to prevent excessively long outputs.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_h5f2c8y7)

---

## Adding Guardrails for Responsible AI

Amazon Bedrock Guardrails were added to filter harmful or inappropriate content.

The guardrail was attached to the Converse API call so prompts and responses were evaluated before being returned to the user.

This ensures the chatbot follows responsible AI guidelines.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_s6n3p9w1)

### Testing Content Safety

I tested the guardrail by submitting prompts designed to trigger harmful responses.

The chatbot correctly blocked or redirected these requests, confirming that the guardrail configuration was working as expected.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-genai-bedrock-chatbot_t2j7q5x8)

---

## Project Wrap-Up

This project demonstrated how to build a basic AI chatbot using Amazon Bedrock and Python in a short amount of time. By using the Bedrock Converse API, a Python script can send prompts to a foundation model and receive generated responses.

The exercise showed how conversation history, system prompts, inference parameters, and guardrails can be combined to create a functional and controlled chatbot interaction.

Future work will focus on improving prompt design and integrating this type of chatbot into larger applications.

---

---
