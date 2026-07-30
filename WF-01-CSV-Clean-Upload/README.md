# WF-17: CSV → Clean → Upload to Database

Automatically upload a CSV file, remove duplicate records, standardize column names, and store clean, structured data in Google Sheets using **n8n**.

---

## 📌 Overview

This workflow automates the complete CSV data cleaning process.

Instead of manually importing, cleaning, removing duplicate records, and formatting data, this workflow performs everything automatically.

### Workflow Process

- Upload a CSV file
- Read and convert CSV into JSON
- Remove duplicate records
- Standardize column names
- Store cleaned data in Google Sheets

---

## 🚀 Features

- 📤 Upload CSV via n8n Form
- 📄 Convert CSV into JSON
- 🚫 Remove duplicate records automatically
- 🧹 Normalize field names
- 📊 Append cleaned data to Google Sheets
- ⚡ Fully automated
- 🟢 Beginner Friendly

---

# 🏗 Workflow Architecture

```text
Form Trigger
      │
      ▼
Extract From File
      │
      ▼
Remove Duplicates
      │
      ▼
Edit Fields
      │
      ▼
Google Sheets
```

---

# 📦 Nodes Used

| Step | Node | Purpose |
|------|------|---------|
| 1 | Form Trigger | Upload CSV file |
| 2 | Extract From File | Convert CSV into JSON |
| 3 | Remove Duplicates | Remove duplicate records using the Email column |
| 4 | Edit Fields (Set) | Standardize field names |
| 5 | Google Sheets | Store cleaned data in Google Sheets |

---

# 📂 Input

### Supported File

- CSV (.csv)

### Example Input Columns

```text
Customer_ID
Full_Name
Email
Phone
City
Country
Department
```

---

# 📤 Output

The workflow converts the original columns into a standardized format before storing them in Google Sheets.

### Output Fields

```text
customer_id
full_name
email
phone
city
country
department
```

---

# ⚙ Prerequisites

Before importing this workflow, make sure you have:

- n8n (Cloud or Self-hosted)
- Google Sheets OAuth2 credentials
- A Google Spreadsheet
- Matching column headers in Google Sheets

---

# 🔧 Setup Instructions

## Step 1

Import the JSON workflow into n8n.

---

## Step 2

Open the **Google Sheets** node.

Replace the existing credentials with your own Google Sheets OAuth2 account.

---

## Step 3

Select your Google Spreadsheet.

---

## Step 4

Select the destination sheet.

---

## Step 5

Save the workflow.

---

## Step 6

Activate the workflow.

---

## Step 7

Open the Production URL.

Upload a CSV file.

The workflow will execute automatically.

---

# 🔄 Workflow Execution

```text
Upload CSV
      │
      ▼
Convert CSV → JSON
      │
      ▼
Remove Duplicate Records
      │
      ▼
Standardize Field Names
      │
      ▼
Append Data to Google Sheets
```

---

# 📸 Workflow Preview

> Add your workflow screenshot here.

Example

```
images/workflow-preview.png
```

---

# 💼 Use Cases

This workflow can be used for:

- Customer Database Imports
- CRM Lead Imports
- Sales Lead Management
- Marketing Contact Lists
- Employee Data Imports
- Business Reports
- Data Migration Projects
- E-commerce Customer Records

---

# 🎯 Benefits

- Saves manual effort
- Removes duplicate records automatically
- Standardizes inconsistent data
- Improves data quality
- Reduces human errors
- Speeds up CSV imports
- Easy to customize
- Beginner friendly

---

# 🛠 Technologies Used

- n8n
- Form Trigger
- Extract From File
- Remove Duplicates
- Set Node
- Google Sheets
- CSV
- JSON

---

# 📁 Repository Structure

```
WF-17-CSV-Clean-Upload-To-Database/
│
├── README.md
├── workflow.json
├── images/
│   └── workflow-preview.png
└── LICENSE
```

---

# 📥 Installation

1. Download the workflow JSON file.
2. Open n8n.
3. Click **Import Workflow**.
4. Select the JSON file.
5. Configure your Google Sheets credentials.
6. Save and activate the workflow.

---

# 📺 Video Tutorial

Watch the complete step-by-step tutorial on YouTube.

**Channel:** QuickSolve AI

---

# 🤝 Contributing

Contributions are welcome!

Feel free to:

- Improve the workflow
- Report bugs
- Suggest new features
- Submit pull requests

---

# ⭐ Support

If you found this workflow helpful:

⭐ Star this repository

🍴 Fork it

📢 Share it with others

---

# 📜 License

This project is available for learning and educational purposes.

---

# 👨‍💻 Author

**QuickSolve AI**

AI Automation • n8n • No-Code • Workflow Tutorials

YouTube:
https://www.youtube.com/@QuickSolveAI

Happy Automating! 🚀
