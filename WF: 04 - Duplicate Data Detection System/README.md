# WF-04: Duplicate Data Detection System

## 📌 Overview

The **Duplicate Data Detection System** is an n8n workflow that automatically identifies duplicate records within a dataset by comparing customer information. It generates a duplicate key using **Name + Email**, groups matching records, flags duplicate entries, and separates unique records.

This workflow helps improve data quality before importing records into CRMs, databases, or spreadsheets. It **detects and flags duplicates only**—it does not automatically remove or merge duplicate records. :contentReference[oaicite:0]{index=0}

---

## 🚀 Features

- ✅ Detect duplicate records automatically
- ✅ Generate duplicate keys using Name + Email
- ✅ Group matching records
- ✅ Separate duplicate and unique records
- ✅ Flag duplicates using a Boolean field
- ✅ Merge processed records into a single output
- ✅ Beginner-friendly n8n workflow
- ✅ Easily customizable duplicate matching logic

---

## 🛠 Workflow Flow

```text
Manual Trigger
      │
      ▼
Load Sample Records
      │
      ▼
Split Records
      │
      ▼
Generate Duplicate Key
      │
      ▼
Group Matching Records
      │
      ▼
Duplicate Check
     / \
    /   \
Duplicate  Unique
    \     /
     \   /
      Merge
        │
        ▼
Final Duplicate Verification
```

---

## 📂 Workflow Steps

### 1️⃣ Manual Trigger
Starts the workflow manually.

### 2️⃣ Load Sample Records
Loads customer records into the workflow.

### 3️⃣ Split Records
Converts the dataset into individual records.

### 4️⃣ Generate Duplicate Key
Creates a comparison key using:
- Name
- Email

### 5️⃣ Group Matching Records
Groups records sharing the same duplicate key.

### 6️⃣ Duplicate Check
Checks whether a group contains more than one matching record.

### 7️⃣ Mark Duplicate
Sets:

```text
is_duplicate = true
```

for duplicate records.

### 8️⃣ Mark Unique
Sets:

```text
is_duplicate = false
```

for unique records.

### 9️⃣ Merge Results
Combines duplicate and unique records into a single output.

### 🔟 Final Verification
Performs a final duplicate status check before completing the workflow.

---

## 📊 Example Input

| ID | Name | Email |
|----|------|-------------------|
| 1 | John | john@example.com |
| 2 | Alice | alice@example.com |
| 3 | John | john@example.com |
| 4 | Bob | bob@example.com |
| 5 | Alice | alice@example.com |

---

## ✅ Example Output

| ID | Name | Email | is_duplicate |
|----|------|-------------------|--------------|
| 1 | John | john@example.com | ✅ true |
| 3 | John | john@example.com | ✅ true |
| 2 | Alice | alice@example.com | ✅ true |
| 5 | Alice | alice@example.com | ✅ true |
| 4 | Bob | bob@example.com | ❌ false |

---

## 💼 Real-World Use Cases

- CRM data cleansing
- Customer database validation
- Email list deduplication
- Sales lead management
- Contact management
- Spreadsheet cleanup
- Data migration projects
- Master data quality checks

---

## 🎯 Benefits

- Improves database quality
- Prevents duplicate customer records
- Reduces manual verification
- Saves processing time
- Keeps datasets organized
- Easy to customize for different business needs

---

## 🔧 Customization Ideas

Modify the workflow to compare:

- Email only
- Phone Number
- Customer ID
- Name + Phone
- Name + Company
- Any custom combination of fields

You can also extend the workflow to:

- Automatically remove duplicates
- Merge duplicate records
- Send duplicate reports via Email
- Update Google Sheets
- Update CRM records
- Store reports in a database

---

## 📦 Requirements

- n8n (Latest Version)
- Basic knowledge of workflow automation
- Dataset containing customer records

---

## 📁 Included Files

```text
WF-03-Duplicate-Data-Detection-System.json
README.md
```

---

## ⭐ Support

If you found this workflow helpful, consider giving the repository a **⭐ Star** to support future n8n workflow tutorials and automation projects.

Happy Automating! 🚀
