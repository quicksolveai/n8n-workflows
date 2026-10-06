
# Gmail Email Automation

## Overview

This n8n workflow converts a simple chat request into a professional email and sends it automatically through Gmail.

**Simple Chat → Professional Email**

## Workflow

Chat Message → AI Agent → Gmail

The workflow receives a chat request, uses an AI Agent to create a professional email, and sends the generated email through Gmail. :chatgpt-content-reference{index="0"}

## Features

- Receive email requests through chat
- Generate professional emails with AI
- Automatically create the recipient, subject, and message
- Send emails through Gmail
- Maintain conversation context with memory
- Use OpenAI as the AI language model :chatgpt-content-reference{index="1"} :chatgpt-content-reference{index="2"}

## Workflow Nodes

### 1. When chat message received
Receives the user's email request.

### 2. AI Agent
Understands the request and creates the professional email.

### 3. OpenAI Chat Model
Provides the AI language model for email generation.

### 4. Simple Memory
Maintains conversation context.

### 5. Send a message in Gmail
Sends the generated email automatically.

## How It Works

1. Enter a simple email request through the n8n chat.
2. The AI Agent processes the request.
3. AI generates the email subject and message.
4. AI provides the recipient, subject, and message dynamically to Gmail.
5. Gmail sends the professional email automatically.

## Example

**Chat Request:**

> Send an email to Krishna about our hotel booking confirmation.

**Result:**

The AI generates a properly structured professional email and sends it through Gmail.

## Requirements

- n8n
- OpenAI Chat Model
- Gmail account
- Gmail OAuth2 credentials

## Use Cases

This workflow can be adapted for:

- Business emails
- Booking confirmations
- Customer follow-ups
- Sales emails
- Service inquiries
- Appointment communication
- General business communication

## Workflow Structure

```text
When chat message received
          ↓
       AI Agent
       ↙     ↘
OpenAI      Simple
Chat Model   Memory
          ↓
Send a message in Gmail
