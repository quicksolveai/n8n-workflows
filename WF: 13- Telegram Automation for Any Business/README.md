
# Telegram AI Auto-Reply

An n8n automation workflow that receives messages from Telegram, processes them using an AI Agent powered by Google Gemini, and automatically sends the generated response back to the Telegram user.

## Workflow Overview

Telegram Message  
↓  
Telegram Trigger  
↓  
AI Agent  
├── Google Gemini Chat Model  
└── Simple Memory  
↓  
Send a Text Message  
↓  
Telegram Reply

## Objective

Automatically respond to Telegram messages using AI.

## Scope

- Receive incoming Telegram messages
- Process user messages through an AI Agent
- Generate AI-powered responses using Google Gemini
- Use Simple Memory with the AI Agent
- Send the generated response back through Telegram

## Workflow Nodes

### 1. Telegram Trigger

Receives incoming Telegram messages and starts the workflow.

### 2. AI Agent

Processes the incoming message and generates a suitable response based on the configured system instructions.

### 3. Google Gemini Chat Model

Provides AI language processing for the AI Agent.

### 4. Simple Memory

Provides memory functionality to the AI Agent.

### 5. Send a Text Message

Sends the AI-generated response back to the Telegram chat.

## How It Works

1. A user sends a message to the Telegram bot.
2. The Telegram Trigger receives the message.
3. The message is passed to the AI Agent.
4. Google Gemini processes the message and helps generate the response.
5. Simple Memory is available to the AI Agent.
6. The generated response is passed to the Telegram message node.
7. The response is automatically sent back to the user.

## Example

### User

```text
What are the latest AI agent news?
AI Agent
Here are some recent developments in AI agents...
Telegram

The generated response is automatically sent back to the user.

Requirements
n8n
Telegram Bot
Telegram API credentials
Google Gemini API credentials
Setup
1. Create a Telegram Bot

Create a Telegram bot using BotFather and obtain the bot access token.

2. Configure Telegram Credentials

Add your Telegram bot credentials to the Telegram Trigger and Telegram message nodes in n8n.

3. Configure Google Gemini

Add your Google Gemini API credentials to the Google Gemini Chat Model node.

4. Import the Workflow

Import the provided JSON workflow file into your n8n instance.

5. Configure the AI Agent

Customize the AI Agent system message according to your business requirements.

For example:

Act as a friendly Telegram assistant. Read each message carefully and give a direct answer that is easy for anyone to understand. Keep responses concise and avoid adding information that the user did not ask for. For a first-time greeting, welcome the user and ask how you can assist them. Maintain a professional and helpful tone throughout the conversation.
6. Activate the Workflow

Save the workflow and activate it.

Send a message to your Telegram bot to test the automation.

Use Cases

This workflow can be adapted for:

Customer support
Business enquiries
FAQ automation
Service information
Product enquiries
General AI assistance
Telegram-based business communication
Workflow Architecture
                    ┌──────────────────────┐
                    │   Telegram Trigger   │
                    │  Incoming Message    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      AI Agent        │
                    │  Message Processing  │
                    └───────┬───────┬──────┘
                            │       │
                 ┌──────────┘       └──────────┐
                 ▼                             ▼
        ┌──────────────────┐          ┌─────────────────┐
        │ Google Gemini    │          │  Simple Memory  │
        │  Chat Model      │          │                 │
        └──────────────────┘          └─────────────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Send a Text Message  │
                 └──────────┬───────────┘
                            │
                            ▼
                    Telegram User
Benefits
Automatic Telegram responses
AI-powered message processing
Simple workflow architecture
Easy to customize
Suitable for different business use cases
Reduces repetitive manual responses
Tech Stack
n8n — Workflow automation
Telegram — Messaging platform
Google Gemini — AI language model
AI Agent — Message processing and response generation
Simple Memory — AI agent memory
Important

Keep your Telegram bot token and Google Gemini API credentials private.

Do not publish API keys or access tokens in your GitHub repository.

Workflow File

Import the included .json file into n8n to recreate the workflow.

License

This workflow is provided for learning and automation purposes.
