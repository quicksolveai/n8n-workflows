# 🚀 WF-19: API Data Fetch → Transform → Store

Automatically fetch data from an external API, transform raw JSON into a clean structure, map the required fields, and store the processed records in Google Sheets using **n8n**.

---

## 📌 Workflow Overview

This workflow demonstrates a common automation pattern used in real-world integrations.

Instead of manually copying data from an API, the workflow automatically:

- 🌐 Fetches data from an external REST API
- 🔄 Transforms raw JSON into a structured format
- 🏷️ Maps only the required fields
- 📄 Stores clean records in Google Sheets

This workflow is perfect for beginners learning API integrations and data processing in n8n.

---

## 🎯 Objective

Convert external API data into a structured internal format automatically.

---

## ⚙️ Workflow Flow

```text
Manual Trigger
      │
      ▼
HTTP Request
      │
      ▼
Edit Fields
      │
      ▼
Google Sheets
```

---

## 🧩 Nodes Used

| Node | Purpose |
|------|---------|
| **Manual Trigger** | Starts the workflow manually. |
| **HTTP Request** | Fetches user data from an external API. |
| **Edit Fields** | Extracts and maps only the required fields. |
| **Google Sheets** | Appends the transformed data into a spreadsheet. |

---

## 📊 Data Transformation

The workflow converts the API response into a simplified structure.

### Input (API Response)

```json
{
  "id": 1,
  "name": "Leanne Graham",
  "email": "leanne@example.com",
  "address": {
    "city": "Gwenborough"
  }
}
```

### Output

```json
{
  "user_id": 1,
  "full_name": "Leanne Graham",
  "email": "leanne@example.com",
  "city": "Gwenborough"
}
```

---

## 📋 Fields Mapped

| API Field | Output Field |
|-----------|--------------|
| `id` | `user_id` |
| `name` | `full_name` |
| `email` | `email` |
| `address.city` | `city` |

---

## ✨ Features

- REST API Integration
- JSON Data Processing
- Field Mapping
- Structured Data Transformation
- Google Sheets Integration
- Beginner-Friendly Workflow
- End-to-End Automation

---

## 💼 Real-World Use Cases

- Import customer data from external systems
- Sync REST API data into Google Sheets
- Create reporting dashboards
- Prepare data for analytics
- Build automated ETL pipelines
- Centralize third-party application data

---

## 📸 Workflow Preview

> Add your workflow screenshot here.

Example:

```
images/workflow-preview.png
```

---

## ▶️ How to Use

1. Import the workflow JSON into n8n.
2. Configure your Google Sheets credentials.
3. Open the HTTP Request node.
4. Replace the API URL if required.
5. Execute the workflow.
6. Verify the data in Google Sheets.

---

## 📦 Requirements

- n8n
- Google Sheets OAuth Credentials
- Internet connection
- Public REST API (or your own API)

---

## 🎓 Learning Outcomes

After completing this workflow, you'll understand how to:

- Work with HTTP Request nodes
- Consume REST APIs
- Process JSON responses
- Extract nested fields
- Map data into a custom structure
- Store processed data in Google Sheets
- Build beginner-friendly ETL workflows

---

## 📁 Repository Structure

```text
WF-19-API-Data-Fetch-Transform-Store/
│
├── workflow.json
├── README.md
├── images/
│   └── workflow-preview.png
└── thumbnails/
    └── thumbnail.png
```

---

## 🏷️ Tags

`n8n` `API` `REST API` `HTTP Request` `JSON` `Google Sheets` `Automation` `Workflow` `ETL` `Data Transformation` `No-Code`

---

## ⭐ Connect With Me

If this workflow helped you, consider:

⭐ Starring this repository

🍴 Forking it for your own projects

📺 Watching the full tutorial on **QuickSolve AI**

Happy Automating! 🚀
