
# WhatsApp AI Automation for Any Business

An n8n workflow that receives WhatsApp messages, processes them through an AI Agent powered by Google Gemini, and automatically sends the generated response back through WhatsApp.

## Workflow Overview

```text
WhatsApp Message
       ↓
WhatsApp Trigger
       ↓
AI Agent
       ↑
Google Gemini Chat Model
       ↓
Send Message
       ↓
Automated WhatsApp Reply
Objective

Automatically respond to customer messages on WhatsApp using an AI Agent.

Scope
Receive incoming WhatsApp messages
Process the incoming message through an AI Agent
Use Google Gemini as the chat model
Generate a response based on the configured business information
Send the generated response back through WhatsApp
Workflow Nodes
1. WhatsApp Trigger

Receives incoming WhatsApp messages and passes the message content to the AI Agent.

2. AI Agent

Processes the customer's message and generates an appropriate response using the configured business information.

3. Google Gemini Chat Model

Provides the language model used by the AI Agent to understand the customer message and generate the response.

4. Send Message

Sends the AI-generated response back to the customer through WhatsApp.

Data Flow
Customer
   ↓
WhatsApp
   ↓
WhatsApp Trigger
   ↓
AI Agent
   ↓
Google Gemini
   ↓
AI-generated response
   ↓
WhatsApp
   ↓
Customer
Example Use Case

A customer sends a message through WhatsApp asking about:

Business timings
Menu or products
Pricing
Delivery
Pickup
Payment methods
Offers

The AI Agent uses the configured business knowledge to generate a response and the workflow automatically sends it back through WhatsApp.

Requirements
n8n
WhatsApp Business / WhatsApp API connection
Google Gemini API / Chat Model
Configured WhatsApp credentials
Setup
Import the workflow JSON into n8n.
Configure the WhatsApp Trigger credentials.
Configure the Google Gemini Chat Model credentials.
Configure the WhatsApp Send Message credentials.
Update the AI Agent's business information with your own business details.
Activate the workflow.
Send a WhatsApp message to test the automation.
Important

Replace the example business information in the AI Agent with your own:

Business name
Location
Business hours
Products or services
Pricing
Delivery information
Payment methods
Offers
Cancellation/refund policies

Do not publish API keys, access tokens, phone numbers, or other private credentials in your GitHub repository.

Workflow

WhatsApp → AI Agent → WhatsApp

The AI Agent uses Google Gemini to generate the response automatically.

License

This workflow is provided for learning and automation practice.
