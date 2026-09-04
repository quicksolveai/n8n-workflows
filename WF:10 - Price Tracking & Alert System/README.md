
# 💰 Price Tracking & Alert System

An n8n automation workflow that automatically monitors a product price, compares it with the previously stored price, sends an email alert when the price changes, and updates the stored price in Google Sheets.

## 🚀 Workflow Overview

The workflow runs automatically on a schedule and performs the following steps:

1. Get the product URL and previous price from Google Sheets
2. Fetch the product webpage
3. Extract the current price
4. Compare the current price with the previous price
5. Send an email alert if the price has changed
6. Update the stored price in Google Sheets

## 🔄 Workflow

```text
Schedule Trigger
       ↓
Get row(s) in sheet
       ↓
HTTP Request
       ↓
HTML
       ↓
If
   ┌───┴───┐
 TRUE    FALSE
   ↓       ↓
Send      End
a message
   ↓
Update row
in sheet

🧩 Nodes Used
1. Schedule Trigger

Starts the price-check workflow automatically according to the configured schedule.

2. Get row(s) in sheet

Retrieves the product URL and previously stored price from Google Sheets.

3. HTTP Request

Fetches the product webpage using the product URL.

4. HTML

Extracts the current product price from the webpage.

5. If

Compares the current price with the previously stored price.

Current Price ≠ Previous Price

If the prices are different, the workflow continues through the TRUE branch.

6. Send a message

Sends an email notification containing:

Current Price
Previous Price
Product URL
7. Update row in sheet

Updates the stored Previous Price with the newly detected Current Price.

📊 Google Sheets Structure

The workflow uses these columns:

Product URL	Previous Price
Product URL	50.00

After a price change, the Previous Price value is automatically updated to the latest detected price.

✉️ Price Change Alert

When a price change is detected, an email is sent with the following information:

The product price has changed!

Current Price: £51.77
Previous Price: £50.00

Product URL: [Product URL]
⚙️ How It Works

The workflow periodically checks the product webpage and extracts its current price.

The extracted price is compared against the price stored in Google Sheets.

If the price changed:
Current Price ≠ Previous Price
        ↓
Send Email Alert
        ↓
Update Previous Price
If the price did not change:
Current Price = Previous Price
        ↓
No Alert
        ↓
Workflow Ends
🛠️ Requirements
n8n
Google Sheets account
Gmail account
A product webpage with an accessible price
Google Sheet containing the product URL and previous price
🎯 Use Cases
Product price monitoring
Price change notifications
E-commerce price tracking
Personal shopping alerts
Automated price monitoring
📌 Important Note

This workflow detects price changes, not specifically price drops. An alert is triggered whenever the current price is different from the previously stored price.

📄 Workflow JSON

The included n8n workflow JSON can be imported directly into n8n and configured with your own Google Sheets and Gmail credentials.

🔗 Workflow Logic
Scheduled Check
      ↓
Read Product Data
      ↓
Fetch Product Page
      ↓
Extract Current Price
      ↓
Compare Prices
      ↓
Price Changed?
   ↙          ↘
 YES           NO
  ↓             ↓
Email Alert    End
  ↓
Update Stored Price
