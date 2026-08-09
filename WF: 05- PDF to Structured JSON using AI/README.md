
# WF-05: PDF → Structured JSON Using AI

An n8n workflow that extracts structured invoice data from a PDF using AI and converts the result into a JSON file.

## Overview

This workflow automates the process of extracting important information from an invoice PDF.

Instead of manually reading a PDF and entering invoice details into a structured format, the workflow:

**PDF Upload → Extract Text → AI Agent → Structured JSON → JSON File**

The workflow uses an n8n Form to receive the PDF, extracts its text, sends the extracted invoice information to an AI Agent, formats the AI response using a Structured Output Parser, and converts the final result into a JSON file.

## Workflow Flow

```text
On form submission
        ↓
Extract from File
        ↓
     AI Agent
      ↙     ↘
OpenAI      Structured
Chat Model  Output Parser
        ↓
Convert to File
        ↓
    JSON File
What This Workflow Does
Receives a PDF invoice through an n8n form.
Extracts text from the uploaded PDF.
Sends the extracted invoice text to an AI Agent.
Uses an OpenAI Chat Model to process the invoice information.
Extracts predefined invoice fields.
Formats the AI response using a Structured Output Parser.
Converts the structured result into a JSON file.
Nodes Used
1. On form submission

Receives the PDF document through an n8n form.

Input: PDF file

Field: PDF

Purpose: Starts the workflow when a PDF is submitted.

2. Extract from File

Extracts text from the uploaded PDF.

Operation: PDF

Binary Property: PDF

Purpose: Converts the uploaded PDF content into text that can be processed by the AI Agent.

3. AI Agent

Processes the extracted invoice text and extracts the required invoice information.

The AI Agent is instructed to return only valid JSON containing the predefined invoice fields.

Purpose: Converts extracted invoice text into structured information.

4. OpenAI Chat Model

Provides the language model used by the AI Agent.

Model: gpt-4o-mini

Purpose: Processes the extracted invoice text and identifies the requested information.

5. Structured Output Parser

Formats the AI Agent response according to the expected JSON structure.

Purpose: Ensures the AI output follows the defined structured format.

6. Convert to File

Converts the structured result into a JSON file.

Operation: To JSON

Purpose: Creates the final JSON file from the structured output.

Extracted Invoice Fields

The AI Agent is configured to extract the following fields:

invoice_number
date
customer
email
phone
company
address
item
quantity
price
gst
total
Example Input

The workflow is designed to process an invoice PDF containing information such as:

Invoice Number: INV-2026-001
Date: 07-Aug-2026
Customer: Raji
Email: raji@example.com
Phone: +91-9876543210
Company: ABC Technologies Pvt Ltd
Address: 123 Main Street, Bengaluru, India
Item: AI Automation Setup
Quantity: 1
Price: 10000
GST: 1800
Total: 11800
Example Output

The workflow produces structured JSON similar to:

{
  "output": {
    "invoice_number": "INV-2026-001",
    "date": "07-Aug-2026",
    "customer": "Raji",
    "email": "raji@example.com",
    "phone": "+91-9876543210",
    "company": "ABC Technologies Pvt Ltd",
    "address": "123 Main Street, Bengaluru, India",
    "item": "AI Automation Setup",
    "quantity": 1,
    "price": 10000,
    "gst": 1800,
    "total": 11800
  }
}
Requirements

Before running this workflow, you need:

n8n
An OpenAI API connection configured in n8n
Access to the configured OpenAI Chat Model
A PDF invoice for testing
How to Use
Step 1 — Import the Workflow

Import the workflow JSON file into your n8n instance.

Step 2 — Configure OpenAI

Open the OpenAI Chat Model node and configure the required OpenAI credentials.

Step 3 — Execute the Workflow

Start the workflow and open the generated form.

Step 4 — Upload a PDF

Upload an invoice PDF using the form.

Step 5 — Process the PDF

The workflow automatically:

PDF
 ↓
Extract Text
 ↓
AI Agent
 ↓
Structured Output
 ↓
JSON File
Step 6 — Check the Result

The final Convert to File node generates the structured JSON file.

Use Cases

This workflow can be used as a foundation for:

Invoice data extraction
PDF data extraction
PDF-to-JSON conversion
AI document processing
Structured data extraction
Invoice automation
Document processing workflows
AI-powered data transformation
Key Features
PDF upload through n8n Form
Automatic PDF text extraction
AI-powered invoice data extraction
OpenAI Chat Model integration
Structured JSON output
JSON file generation
No manual data entry required after upload
Data Flow
PDF Invoice
    ↓
On form submission
    ↓
Extract from File
    ↓
Extracted Invoice Text
    ↓
AI Agent
    ↓
OpenAI Chat Model
    ↓
Structured Output Parser
    ↓
Structured Invoice Data
    ↓
Convert to File
    ↓
JSON File
Workflow File
WF-21-PDF-to-Structured-JSON-Using-AI.json
Important Notes
This workflow is configured specifically for invoice data extraction.
The AI Agent prompt defines the invoice fields that should be extracted.
The AI Agent is instructed to return valid JSON.
The Structured Output Parser is connected to the AI Agent.
The OpenAI Chat Model is connected to the AI Agent.
The final output is converted into a JSON file.
The workflow does not contain a database, CRM, Google Sheets, Airtable, or other external storage destination.
Workflow Nodes
On form submission
        ↓
Extract from File
        ↓
AI Agent
   ↙         ↘
OpenAI       Structured
Chat Model   Output Parser
        ↓
Convert to File
Learning Objective

This workflow demonstrates how n8n can combine:

File handling
PDF text extraction
AI processing
Structured output
JSON file generation

to automate document data extraction.

License

This workflow is provided for learning and automation development purposes.
