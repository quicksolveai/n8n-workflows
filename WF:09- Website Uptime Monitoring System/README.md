# Website Uptime Monitoring System

An n8n automation workflow that continuously monitors multiple websites, checks their HTTP status, sends an alert when a website is unavailable, and logs the monitoring results in Google Sheets.

## Workflow Overview

The workflow runs automatically on a schedule and processes multiple website URLs one by one.

```text
Schedule Trigger
       ↓
Get Websites from Google Sheets
       ↓
Loop Over Items
       ↓
HTTP Request
       ↓
Check HTTP Status
      / \
   200   Not 200
    ↓       ↓
  Log     Send Alert
 Online      ↓
    ↓      Log Down
    └──→ Loop

Features
Automatically checks websites on a schedule
Supports monitoring multiple website URLs
Processes websites one by one
Checks the HTTP response status code
Detects successful and failed responses
Sends a Gmail alert when a website does not return HTTP 200
Logs website status in Google Sheets
Continuously updates monitoring logs
Workflow Nodes
1. Schedule Trigger

Starts the website monitoring workflow automatically according to the configured schedule.

2. Get row(s) in sheet

Retrieves the list of website URLs from the Google Sheets website list.

3. Loop Over Items

Processes each website URL individually.

4. HTTP Request

Sends a GET request to the current website URL and receives its HTTP response.

The URL is dynamically taken from the Google Sheets data:

{{ $json.Website }}
5. If

Checks whether the HTTP response status code is equal to 200.

Status Code = 200
TRUE → Website is treated as Online
FALSE → Website is treated as Down
6. Append row in sheet

Records successful website checks in the monitoring log.

The log contains:

Timestamp
Website
Status

Status:

Online
7. Send a message

Sends a Gmail alert when a website does not return HTTP 200.

Example alert:

🚨 Website Down Alert

The website [WEBSITE URL] is not returning HTTP 200.

Please check the website.
8. Append row in sheet1

Records failed website checks in the monitoring log.

Status:

Down
Google Sheets Setup
Website List

Create a Google Sheet containing a Website column.

Example:

Website
https://www.n8n.io
https://www.google.com
https://github.com

You can add additional websites to the list without changing the HTTP Request node.

Monitoring Log

Create another Google Sheet with these columns:

Timestamp	Website	Status
2026-09-01 10:00	https://www.n8n.io	Online
2026-09-01 10:00	https://www.google.com	Online
2026-09-01 10:00	https://example.com	Down

The workflow automatically appends new monitoring results.

Requirements

Before running the workflow, configure:

n8n
Google Sheets credentials
Gmail credentials
Website list Google Sheet
Monitoring log Google Sheet
Important Configuration

The HTTP Request node uses:

Method: GET
URL: {{ $json.Website }}

The response is configured to return the full response and continue without stopping on HTTP errors.

The IF node checks:

{{ $json.statusCode }} = 200
How It Works
The Schedule Trigger starts the workflow.
Website URLs are retrieved from Google Sheets.
The Loop Over Items node processes each URL individually.
HTTP Request checks the website.
The IF node evaluates the HTTP status code.
A successful response is logged as Online.
A failed response triggers a Gmail alert and is logged as Down.
The workflow returns to the loop and checks the next website.
The process repeats automatically according to the schedule.
Use Cases

This workflow can be used to monitor:

Business websites
Landing pages
Client websites
Web applications
APIs or endpoints that return HTTP status codes
Testing
Test Online Status

Add a working website URL to the Website List and execute the workflow.

Expected result:

Status: Online
Test Down Status

Use a real domain with a deliberately invalid path, for example:

https://www.n8n.io/this-page-does-not-exist

Expected result:

Status: Down

A Gmail downtime alert should also be generated.

Workflow Logic
Website URL
    ↓
HTTP GET Request
    ↓
HTTP Status Code
    ↓
Is Status Code 200?
    ├── YES → Log Online
    │
    └── NO  → Send Gmail Alert
                  ↓
               Log Down
Built With
n8n
Google Sheets
Gmail
HTTP Request
