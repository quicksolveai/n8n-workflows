
# Invoice Parser Automation

An n8n workflow that automatically extracts key financial information from invoice PDFs and stores the structured data in Google Sheets.

## Workflow Overview

Invoice PDF → Webhook → Extract from File → Information Extractor → Edit Fields → Google Sheets

## What This Workflow Does

- Receives an invoice PDF through a webhook
- Extracts text from the PDF
- Uses AI to extract important invoice details
- Extracts:
  - Vendor
  - Amount
  - Date
- Structures the extracted fields
- Appends the structured data to Google Sheets

## Nodes Used

| Node | Purpose |
|---|---|
| Webhook | Receives the uploaded invoice |
| Extract from File | Extracts text from the invoice PDF |
| Information Extractor | Extracts vendor, amount, and date |
| OpenAI Chat Model | Provides the AI model for extraction |
| Edit Fields | Structures the extracted invoice fields |
| Append row in sheet | Stores the processed data in Google Sheets |

## Extracted Data

The workflow extracts three key invoice fields:

```text
vendor
amount
date
These fields are then mapped to the corresponding columns in Google Sheets.

Google Sheets Structure

Create a Google Sheet with the following headers:

vendor | amount | date

Each processed invoice is added as a new row.

Testing With Postman

You can test the webhook using Postman:

Start the n8n Webhook in test mode.
Copy the Webhook Test URL.
Create a POST request in Postman.
Go to Body → form-data.
Add a field named:
data
Change the field type from Text to File.
Select your invoice PDF.
Send the request.
Check the n8n execution.
Verify the extracted data in Google Sheets.
Example Output
Vendor: TechNova Solutions Pvt. Ltd.
Amount: 64900
Date: 29 August 2026
Requirements
n8n
OpenAI Chat Model
OpenAI credentials
Google Sheets account
Google Sheets spreadsheet
Postman for testing
Use Cases
Invoice data extraction
Invoice processing automation
Accounts payable automation
PDF data extraction
Financial document processing
Invoice-to-Google-Sheets automation
AI-powered document processing
