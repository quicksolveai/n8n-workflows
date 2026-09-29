
# Customer Feedback Classification & Alert System

An n8n workflow that automatically collects customer feedback, uses AI to classify the feedback, stores it in the appropriate Google Sheets category, and sends the feedback to the corresponding Slack channel.

## Workflow Overview

Customer submits feedback through a form → AI analyzes the feedback → Feedback is classified → Switch routes it → Google Sheets stores it → Slack sends the notification.

## Objective

Automatically classify customer feedback and route it to the appropriate destination.

## Workflow Scope

- Collect customer feedback
- Classify feedback using AI
- Route feedback by category
- Store feedback in Google Sheets
- Send Slack notifications

## Feedback Categories

The AI Agent classifies feedback into three categories:

### 1. Compliment
Positive feedback expressing satisfaction, appreciation, or praise.

### 2. Complaint
Negative feedback expressing dissatisfaction, issues, or problems.

### 3. Future Addition Request
Suggestions, feature requests, or improvements requested for the future.

## Workflow Flow

```text
Customer Feedback Form
        ↓
     AI Agent
        ↓
Structured Output Parser
        ↓
      Switch
   ↙     ↓      ↘
Compliment Complaint Future Addition Request
   ↓       ↓             ↓
Google   Google        Google
Sheets   Sheets        Sheets
   ↓       ↓             ↓
Slack    Slack         Slack

Nodes Used
Customer Feedback Form

Collects:

Name
Contact Number
Email ID
Feedback
AI Agent

Analyzes the submitted feedback and classifies it as:

Compliment
Complaint
Future Addition Request
Google Gemini Chat Model

Provides the AI model used by the AI Agent for feedback classification.

Structured Output Parser

Structures the AI classification output into a defined category format.

Switch

Routes the feedback according to the AI-generated category.

Google Sheets

Feedback is stored in separate sheets:

Compliment
Complaint
Future Addition Request
Slack

Feedback is sent to separate Slack channels:

Compliment
Complaint
Future Addition Request
Example Feedback
Compliment
Great service!
Complaint
The app keeps crashing.
Future Addition Request
Please add dark mode.
Example Workflow Result

A customer submits:

Please add dark mode.

The AI classifies it as:

Future Addition Request

The Switch routes the feedback to the Future Addition Request branch.

The workflow then:

Stores the feedback in the corresponding Google Sheet.
Sends the feedback to the corresponding Slack channel.
Requirements

Before running the workflow, configure:

n8n
Google Gemini credentials
Google Sheets credentials
Slack credentials
A Google Sheet with separate category sheets
Slack channels for each feedback category
Setup
1. Import the Workflow

Import the provided JSON workflow into your n8n instance.

2. Configure Google Gemini

Connect your Google Gemini credentials to the Google Gemini Chat Model node.

3. Configure Google Sheets

Connect your Google Sheets account and select the spreadsheet containing the feedback category sheets.

Required category sheets:

Compliment
Complaint
Future Addition Request
4. Configure Slack

Connect your Slack account and configure the destination channels:

Compliment
Complaint
Future Addition Request
5. Test the Workflow

Submit different feedback examples through the Customer Feedback Form and verify that:

The AI identifies the correct category.
The Switch selects the correct branch.
The feedback is added to the correct Google Sheet.
The feedback is sent to the correct Slack channel.
Workflow Architecture
FORM
  ↓
AI CLASSIFICATION
  ↓
CATEGORY DETECTION
  ↓
SWITCH
  ├── Compliment
  │      ├── Google Sheets
  │      └── Slack
  │
  ├── Complaint
  │      ├── Google Sheets
  │      └── Slack
  │
  └── Future Addition Request
         ├── Google Sheets
         └── Slack
Use Cases

This workflow can be used to organize customer feedback automatically and separate positive feedback, complaints, and feature requests into dedicated destinations.

Built With
n8n
Google Gemini
Google Sheets
Slack
AI Agent
Structured Output Parser
Switch
Workflow

Customer Feedback Classification & Alert System

Built with n8n for automated AI-powered feedback classification and routing.
