Workflow Documentation
CSV → Clean → Upload to Google Sheets


1. Objective
Build an automated workflow that:
	• Accepts a CSV upload 
	• Reads the CSV 
	• Converts it into JSON 
	• Removes duplicate records 
	• Cleans (normalizes) the data 
	• Stores the clean data into Google Sheets 

2. Real-world Use Cases
	• CRM Lead Import 
	• Customer Database Upload 
	• Employee Import 
	• Sales Report Upload 
	• Product Catalog Import 
	• Student Record Upload 
	• Vendor List Upload 
	• Marketing Contact List 

3. Final Workflow Architecture

Manual Trigger
      │
      ▼
Form Trigger
      │
      ▼
Extract from File
      │
      ▼
Remove Duplicates
      │
      ▼
Set (Normalize Data)
      │
      ▼
Google Sheets

STEP 1 — Manual Trigger
Purpose
Starts the workflow manually while testing.
Node

Manual Trigger
Configuration
No configuration required.
Output

Workflow starts.

STEP 2 — Form Trigger
Purpose
Allows users to upload a CSV file through a web form.
Node

Form Trigger
Configuration
Form Element

Type:
File
Field Name

csv_file
Label

Upload CSV File
Required

True
Everything else remains default.

Output
Produces

1 Item
Binary property

csv_file
Example

Binary

csv_file

STEP 3 — Upload CSV
Click

Listen for Test Event
Open

Test URL
Upload

customers.csv
Click

Submit

Expected Output

Binary Data Received

STEP 4 — Extract CSV
Node

Extract from File
Purpose
Converts CSV into JSON.

Configuration
Operation

Extract From CSV
Input Binary Field

csv_file
Everything else

Default

Expected Output
10 Items
Example

{
"Customer_ID":"1001",
"Full_Name":"John Smith",
"Email":"john.smith@gmail.com",
"Phone":"9876543210",
"City":"Bangalore",
"Country":"India",
"Department":"Sales"
}

STEP 5 — Remove Duplicates
Node

Remove Duplicates
Purpose
Remove duplicate customer records.

Configuration
Operation

Remove Duplicate Items
Comparison

Selected Fields
Compare Field

Email

Expected Output

8 Items
Removed

John Smith duplicate
Rahul Kumar duplicate

STEP 6 — Normalize Data
Node

Set
Purpose
Rename fields and standardize values.

Configuration
Keep Only Set

ON

Fields
customer_id

{{ $json.Customer_ID }}

full_name

{{ $json.Full_Name.trim() }}

email

{{ $json.Email.toLowerCase() }}

phone

{{ $json.Phone }}

city

{{ $json.City.trim() }}

country

{{ $json.Country.trim() }}

department

{{ $json.Department.trim() }}

Expected Output

{
"customer_id":"1001",
"full_name":"John Smith",
"email":"john.smith@gmail.com",
"phone":"9876543210",
"city":"Bangalore",
"country":"India",
"department":"Sales"
}

STEP 7 — Google Sheets
Node

Google Sheets
Purpose
Save cleaned records.

Configuration
Resource

Sheet Within Document
Operation

Append Row
Spreadsheet

Select your Google Sheet
Worksheet

Sheet1
Mapping

Map Automatically
or map manually.

Columns
Google Sheet	n8n Field
customer_id	customer_id
full_name	full_name
email	email
phone	phone
city	city
country	country
department	department

Expected Output

8 rows added

Final Data Flow

CSV File

↓

Binary Data

↓

JSON

↓

Duplicate Removal

↓

Normalized Fields

↓

Google Sheet

Sample CSV

Customer_ID,Full_Name,Email,Phone,City,Country,Department
1001,John Smith,john.smith@gmail.com,9876543210,Bangalore,India,Sales
1002,Sarah Johnson,sarah.johnson@yahoo.com,9123456780,Hyderabad,India,Marketing
1003,Rahul Kumar,rahul.kumar@gmail.com,9988776655,Chennai,India,IT
1004,Priya Sharma,priya.sharma@gmail.com,9876501234,Mumbai,India,HR
1005,John Smith,john.smith@gmail.com,9876543210,Bangalore,India,Sales
1006,Anita Verma,anita.verma@gmail.com,9001122334,Pune,India,Finance
1007,David Lee,david.lee@gmail.com,9556677889,Delhi,India,Operations
1008,Sneha Reddy,sneha.reddy@gmail.com,9445566778,Hyderabad,India,Marketing
1009,Rahul Kumar,rahul.kumar@gmail.com,9988776655,Chennai,India,IT
1010,Michael Brown,michael.brown@gmail.com,9112233445,Kolkata,India,Support

Expected Results
Stage	Records
CSV Upload	10
Extract CSV	10
Remove Duplicates	8
Normalize	8
Google Sheets	8

Common Errors & Fixes
Error	Cause	Fix
No binary file	Wrong binary field name	Use csv_file
0 records extracted	Invalid CSV or wrong operation	Ensure Extract From CSV is selected
Duplicates not removed	Wrong comparison field	Compare using Email
Empty values in Google Sheets	Column mapping mismatch	Match Google Sheet headers with Set node fields
File not found	Using local file path in n8n Cloud	Use Form Trigger upload instead of local file paths

Skills 
	• File upload handling 
	• Working with binary data 
	• CSV parsing 
	• JSON transformation 
	• Duplicate detection 
	• Field normalization 
	• Expression usage 
	• Google Sheets integration 
	• End-to-end ETL (Extract → Transform → Load) workflow design 

Workflow Complexity
	• Difficulty: Beginner → Intermediate 
	• Estimated Build Time: 20–30 minutes 
	• Nodes Used: 6 
	• Execution Pattern: Linear (no branching) 

Suggested Enhancements (Next Level)
Once you're comfortable with this workflow, you can extend it by adding:
	1. Data validation (reject invalid emails or missing required fields). 
	2. AI-powered data cleanup (standardize names, cities, or departments using an LLM). 
	3. Database storage (MySQL, PostgreSQL, Airtable, Supabase) instead of or in addition to Google Sheets. 
	4. Error handling with notifications (Slack/Email) for failed imports. 
	5. Execution logging to keep a history of every import, including file name, record count, duplicates removed, and timestamp. 
This gives you a solid reference for rebuilding or extending the workflow in the future.
