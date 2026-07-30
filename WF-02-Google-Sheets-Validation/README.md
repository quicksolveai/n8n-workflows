# WF-02 – Google Sheets Auto Data Validation

## 📌 Workflow Overview

Automatically monitor Google Sheets for new or updated records, validate important fields, update the validation status back into the sheet, and send Gmail alerts whenever invalid data is detected.

---

# 🎯 Objective

Build an automated workflow that:

- Monitors Google Sheet updates
- Validates mandatory fields
- Detects invalid data automatically
- Updates validation results into Google Sheets
- Sends Gmail alerts for invalid records

---

# 🚀 Features

✅ Monitor Google Sheets automatically

✅ Validate Name field

✅ Validate Email availability

✅ Validate Email format

✅ Validate Phone Number (10 digits)

✅ Validate Age field

✅ Validate Age Range (18–100)

✅ Update Validation Status

✅ Store Error Messages

✅ Send Gmail Alert

---

# 💼 Real-World Use Cases

- CRM Data Validation
- Customer Registration Forms
- Employee Database Validation
- Student Admission Records
- Sales Lead Verification
- Marketing Contact Validation
- Internal Data Quality Checks

---

# 🔄 Workflow Architecture

Google Sheets Trigger

↓

Name Validation

↓

Email Empty Validation

↓

Email Format Validation

↓

Phone Validation

↓

Age Empty Validation

↓

Age Range Validation

↓

├── Valid Record
│   ├── Update Validation Status
│   └── Update Google Sheet
│
└── Invalid Record
    ├── Add Error Message
    ├── Merge Validation Results
    ├── Update Google Sheet
    └── Send Gmail Alert

---

# ⚙️ Validation Rules

## Name Validation

Checks whether the **Name** field is empty.

Example:

❌ Empty Name

---

## Email Empty Validation

Checks whether the **Email** field exists.

Example:

❌ Email is Empty

---

## Email Format Validation

Validates the email format.

Valid:

john@gmail.com

Invalid:

john@gmail

john@

gmail.com

---

## Phone Validation

Phone number must contain exactly **10 digits**.

Valid:

9876543210

Invalid:

12345

98765ABCD

---

## Age Empty Validation

Checks whether the **Age** field is empty.

Example:

❌ Age is Empty

---

## Age Range Validation

Allowed Age:

18 – 100

Example:

17 ❌

150 ❌

25 ✅

---

# 📊 Output

## Valid Record

Validation_Status

Valid

---

## Invalid Record

Validation_Status

Invalid

Error

Name is Empty

or

Email is Empty

or

Invalid Email Format

or

Invalid Phone Number

or

Age is Empty

or

Age must be between 18 and 100

---

# 📧 Gmail Alert

Whenever an invalid record is detected, the workflow automatically sends an email containing:

- Validation Status
- Error Message
- Name
- Email
- Phone
- City
- Age

---

# 🔐 Required Credentials

## Google Sheets OAuth2

Required for:

- Trigger
- Read Sheet
- Update Rows

---

## Gmail OAuth2

Required for:

- Sending Email Alerts

---

# 🧩 Nodes Used

1. Google Sheets Trigger
2. IF – Name Validation
3. Set – Name Error
4. IF – Email Empty Validation
5. Set – Email Empty Error
6. IF – Email Format Validation
7. Set – Email Format Error
8. IF – Phone Validation
9. Set – Phone Error
10. IF – Age Empty Validation
11. Set – Age Empty Error
12. IF – Age Range Validation
13. Set – Age Range Error
14. Set – Validation Status
15. Google Sheets Update (Valid Records)
16. Merge
17. Google Sheets Update (Invalid Records)
18. Gmail Alert

---

# 📥 Installation

1. Download the workflow JSON.
2. Open n8n.
3. Click **Import Workflow**.
4. Select the downloaded JSON file.
5. Configure Google Sheets OAuth2.
6. Configure Gmail OAuth2.
7. Replace the Spreadsheet ID with your own.
8. Activate the workflow.

---

# 📦 Requirements

- n8n
- Google Account
- Google Sheets
- Gmail
- Google OAuth Credentials

---

# 📄 License

This workflow is provided for educational purposes and may be freely modified for personal or commercial projects.

---

⭐ If you found this workflow helpful, consider starring this repository and subscribing to the **QuickSolve AI** YouTube channel for more practical n8n automation workflows.

