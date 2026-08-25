
# Auto File Organizer (Drive System)

Automatically organize files in Google Drive based on their file type using n8n.

## Overview

This n8n workflow monitors a specific Google Drive folder for newly created files.

When a new file is detected, the workflow checks its MIME type and routes it to the appropriate destination folder.

Supported file types:

- PDF
- Images
- Documents
- Excel
- PowerPoint
- Other / Unsupported files

## Workflow

Google Drive Trigger
        ↓
      Switch
        ↓
 ┌──────┼──────┬──────────┬────────┬──────────┐
 PDF  Images  Documents  Excel  PowerPoint  Fallback
  ↓      ↓        ↓        ↓        ↓           ↓
Move   Move     Move     Move     Move        Move
File   File1    File2    File3    File4       File5

## How It Works

### 1. Google Drive Trigger

The workflow checks a specific Google Drive folder for newly created files.

The trigger runs every minute and starts the workflow when a new file is created.

### 2. Switch

The Switch node checks the file's `mimeType` and determines which category the file belongs to.

The workflow contains rules for:

- `application/pdf` → PDF
- `image/` → Images
- `application/vnd.openxmlformats-officedocument.wordprocessingml.document` → Documents
- `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet` → Excel
- `application/vnd.openxmlformats-officedocument.presentationml.presentation` → PowerPoint

There is also a fallback output for files that do not match these rules.

### 3. Move File

After the file type is identified, the corresponding Google Drive node moves the file into its destination folder.

| File Type | Destination |
|---|---|
| PDF | PDF |
| Images | Images |
| Documents | Documents |
| Excel | Excel |
| PowerPoint | PowerPoint |
| Other / Unsupported | Auto File Organizer |

## Workflow Structure

```text
New File Created
       │
       ▼
Google Drive Trigger
       │
       ▼
     Switch
       │
       ├── PDF ───────────────► Move file
       │
       ├── Images ────────────► Move file1
       │
       ├── Documents ─────────► Move file2
       │
       ├── Excel ─────────────► Move file3
       │
       ├── PowerPoint ────────► Move file4
       │
       └── Fallback ──────────► Move file5
