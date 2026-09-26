
# AI Appointment Booking Agent

An n8n automation workflow that collects appointment details through a form, uses an AI Agent to process the appointment request, stores the booking information in Google Sheets, and sends a confirmation email automatically.

## Workflow Overview

The workflow follows this automation flow:

Appointment Form
→ AI Agent
→ Google Sheets
→ Gmail

The OpenAI Chat Model is connected to the AI Agent to power the appointment-processing step.

## Objective

Automatically schedule appointments and send confirmation emails.

## Scope

- Collect appointment details
- Assign appointment date
- Save booking data
- Send confirmation email

## How It Works

### 1. Appointment Form

The workflow starts with an appointment booking form.

The form collects:

- Full Name
- Mobile Number
- Email ID
- Type of Service

Available service options:

- General
- Dental
- Ortho

### 2. AI Agent

The submitted appointment information is passed to an AI Agent.

The AI Agent is configured as an AI appointment booking agent for a hospital.

Its main responsibility is to automatically assign the appointment date exactly 2 days after the form submission date.

The AI Agent uses the OpenAI Chat Model.

### 3. Google Sheets

After processing the appointment request, the workflow appends the booking information to Google Sheets.

The following information is stored:

| Field | Description |
|---|---|
| Name | Patient's full name |
| Mobile Number | Patient's mobile number |
| Email ID | Patient's email address |
| Service | Selected service |
| Submission Date | Date the form was submitted |
| Appointment Date | Automatically assigned appointment date |

The appointment date is calculated as 2 days after the current submission date.

### 4. Gmail Confirmation

After the appointment information is stored, the workflow sends a confirmation email to the submitted email address.

The email includes:

- Patient name
- Appointment date
- Submission date
- Type of service
- Appointment confirmation message
- Instructions to arrive 10–15 minutes early
- Instructions to contact the hospital for questions or rescheduling

## Workflow Structure

```text
APPOINTMENT FORM
       ↓
   AI AGENT
       ↓
GOOGLE SHEETS
       ↓
     GMAIL
AI Model Connection:

OpenAI Chat Model
       ↓
   AI Agent
Nodes Used
Appointment Form

Collects the patient's appointment details.

AI Agent

Processes the appointment request and handles appointment-date assignment.

OpenAI Chat Model

Provides the AI model used by the AI Agent.

Append Row in Sheet

Stores the appointment information in Google Sheets.

Send a Message

Sends the appointment confirmation email through Gmail.

Appointment Date Logic

The workflow automatically assigns the appointment date using:

$now.plus({days:2}).format('yyyy-MM-dd')

This schedules the appointment exactly 2 days after the workflow submission date.

Example
Form Submission
Full Name: Vihaan Kapoor
Mobile Number: 9876543210
Email ID: vihaan@example.com
Type of Service: DENTAL
Stored Record
Name: Vihaan Kapoor
Mobile Number: 9876543210
Email ID: vihaan@example.com
Service: DENTAL
Submission Date: 2026-09-25
Appointment Date: 2026-09-27
Confirmation Email
Subject:
APPOINTMENT DETAILS FOR Vihaan Kapoor

Dear Vihaan Kapoor,

Thank you for submitting your appointment request.
We are pleased to confirm your appointment has been scheduled.

Appointment Date: 2026-09-27
Submission Date: 2026-09-25
Type of Service: DENTAL

Kindly arrive at least 10–15 minutes early and carry
any relevant medical records.

If you have any questions or need to reschedule,
please contact us.

Wishing you good health.

Sincerely,
Team
Applications Used
n8n
OpenAI
Google Sheets
Gmail
Requirements

Before running the workflow, configure the required credentials for:

OpenAI
Google Sheets
Gmail
Use Cases

This workflow can be adapted for:

Hospital appointment booking
Dental clinic appointments
Medical consultations
General healthcare services
Clinic booking systems
Service appointment automation
Automation Benefits
Collects appointment information automatically
Assigns appointment dates automatically
Stores booking information in Google Sheets
Sends confirmation emails automatically
Reduces repetitive manual appointment processing
Workflow
Form Submission
      ↓
AI Processing
      ↓
Appointment Date Assignment
      ↓
Google Sheets Record
      ↓
Confirmation Email
Built With

n8n + OpenAI + Google Sheets + Gmail
