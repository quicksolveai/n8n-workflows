
Image → Data Extraction

An n8n automation workflow that accepts an image, extracts readable text using AI-powered OCR, cleans the extracted content, and stores the final result in an n8n Data Table.

🚀 Workflow Overview

Image Upload → OCR Extraction → Text Cleaning → Database Storage

Webhook
   ↓
Analyze Image
   ↓
Edit Fields
   ↓
Insert Row
🎯 Objective

Extract readable data from images automatically and store the cleaned text for later use.

✨ What This Workflow Does
📤 Accepts an uploaded image through a Webhook
🔍 Uses AI to extract readable text from the image
🧹 Cleans the extracted OCR text
🗄️ Stores the cleaned result in an n8n Data Table
⚡ Eliminates manual copy-pasting of information from images
🔄 Workflow Steps
1. Webhook

Receives the uploaded image through an HTTP POST request.

Binary field:

data

The uploaded image is passed to the next node as binary data.

2. Analyze Image

Uses OpenAI image analysis to extract readable text from the uploaded image.

Input Type:

Binary File(s)

Input Data Field Name:

data0

OCR instruction:

Extract all readable text from this image exactly as it appears. Return only the extracted text. Do not summarize or explain.

The result contains the text detected from the image.

3. Edit Fields

Creates a clean text field from the OCR response.

Field:

extracted_text

Expression:

{{ $json['0'].content[0].text }}

A second field is created:

clean_text

Expression:

{{ $json['0'].content[0].text.replace(/```/g, '').replace(/\n+/g, ' ').trim() }}

This removes unnecessary formatting and line breaks.

4. Insert Row

Stores the cleaned OCR result in an n8n Data Table.

Data Table:

image_ocr_results

Column:

clean_text

Mapped value:

{{ $json.clean_text }}

Each processed image creates a new row.

🗄️ Data Table Structure
Column	Purpose
id	Unique row identifier
createdAt	Record creation time
updatedAt	Record update time
clean_text	Cleaned OCR result
🧪 Example
Input

An image containing:

Invoice No: INV-2024-0687
Date: 20 May 2024
Bill To: ABC Enterprises
Total Amount: 59,000.00
OCR Output
Invoice No: INV-2024-0687
Date: 20 May 2024
Bill To: ABC Enterprises
Total Amount: 59,000.00
Stored Result

The cleaned text is inserted into:

image_ocr_results

as a new database row.

🛠️ Nodes Used
Webhook
OpenAI — Analyze Image
Edit Fields
Data Table — Insert Row
📌 Use Cases
Extracting text from invoices
Digitizing scanned documents
Extracting information from receipts
Converting image-based records into searchable text
Building document-processing automations
Preparing image data for downstream AI workflows
⚙️ Requirements
n8n
OpenAI image-analysis capability
An n8n Data Table
Postman or another HTTP client for testing
An image containing readable text
🧪 Testing

Send a POST request to the Webhook.

Use:

Body → form-data

Add:

Key: data
Type: File

Upload an image and execute the request.

The expected workflow is:

Image
  ↓
Webhook
  ↓
AI OCR
  ↓
Clean Text
  ↓
image_ocr_results
📊 Final Result

The workflow converts:

IMAGE
   ↓
READABLE TEXT
   ↓
CLEAN TEXT
   ↓
DATABASE RECORD
🔮 Possible Improvements

Future versions could extend this workflow to:

Extract structured JSON instead of plain text
Identify invoice fields automatically
Store individual fields such as invoice number, date, vendor, and total
Connect the result to Google Sheets
Connect the result to a CRM
Add validation and error handling
Process multiple images automatically
📁 Workflow Architecture
┌─────────────┐
│   Webhook   │
│ Image Upload│
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│  Analyze Image  │
│   AI + OCR      │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│   Edit Fields   │
│  Clean OCR Text │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│   Insert Row    │
│  Data Table     │
└─────────────────┘
⚡ Summary

Image OCR → Data Extraction automates the process of taking text trapped inside images and turning it into clean, storable data.

Upload → Extract → Clean → Store.
