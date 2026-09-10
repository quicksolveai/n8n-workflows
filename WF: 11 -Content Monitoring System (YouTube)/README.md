
# YouTube Content Monitoring System

An automated n8n workflow that monitors selected YouTube channels for new videos, prevents duplicate entries, stores new content in Google Sheets, and sends a Gmail notification when new content is detected.

## Workflow Overview

The workflow automatically:

1. Runs on a schedule.
2. Retrieves previously tracked video records.
3. Retrieves the list of YouTube channels to monitor.
4. Processes each channel individually.
5. Fetches the latest videos through the YouTube RSS feed.
6. Compares incoming Video IDs with existing records.
7. Determines whether the video is new.
8. Stores new videos in Google Sheets.
9. Sends a Gmail notification.
10. Continues monitoring the remaining channels.

## Workflow Flow

```text
Schedule Trigger
       ↓
Get row(s) in sheet
       ↓
Get row(s) in sheet1
       ↓
Loop Over Items
       ↓
RSS Read
       ↓
Code in JavaScript
       ↓
If
   ┌───┴───┐
 TRUE     FALSE
   ↓        ↓
Append     Skip
 Row       Duplicate
   ↓
Send a message
   ↓
Loop Over Items

Key Features
Automated YouTube channel monitoring
YouTube RSS feed integration
Multiple channel support
Automatic duplicate detection
Video ID-based content tracking
Google Sheets content logging
Gmail notifications for new content
Automatic channel-by-channel processing
Continuous scheduled monitoring
Google Sheets Structure
Channel Sheet

The workflow uses a Google Sheet containing the YouTube channels that should be monitored.

Channel Name
Channel ID

The Channel ID is used to generate the YouTube RSS feed URL for each channel.

Content Sheet

The workflow stores detected videos using the following fields:

Video ID
Channel Name
Title
Published At
Link
Duplicate Detection

The workflow checks the incoming YouTube Video ID against the Video IDs already stored in the content sheet.

Incoming Video ID
       ↓
Compare with existing Video IDs
       ↓
Is it new?
   ┌───┴───┐
 YES      NO
  ↓        ↓
Store    Skip
  ↓
Notify

This prevents previously tracked videos from being added again.

Notification

When a new video is detected, the workflow sends a Gmail notification containing:

New content detected:

Title: [Video Title]

Published: [Publication Date]

Watch here: [Video Link]
Nodes Used
Node	Purpose
Schedule Trigger	Runs the workflow every minute
Get row(s) in sheet	Retrieves previously tracked content
Get row(s) in sheet1	Retrieves selected YouTube channels
Loop Over Items	Processes each channel individually
RSS Read	Fetches videos from YouTube RSS
Code in JavaScript	Detects previously unseen videos
If	Checks whether content is new
Append row in sheet	Stores newly detected content
Send a message	Sends a new-content notification
Requirements
n8n
Google Sheets account
Gmail account
YouTube channel IDs
Google Sheets document for channel and content tracking
Setup
1. Create the Google Sheet

Create a Google Spreadsheet with two sheets:

channels
content

Add the YouTube channels you want to monitor to the channels sheet.

2. Add Channel IDs

Enter the YouTube Channel IDs that should be monitored.

Example:

Channel Name        Channel ID
Example Channel     UCxxxxxxxxxxxxxxxx
Another Channel     UCyyyyyyyyyyyyyyyy
3. Configure Google Sheets

Connect your Google Sheets account to the workflow and select the spreadsheet containing the channels and content sheets.

4. Configure Gmail

Connect your Gmail account to the notification node.

5. Import the Workflow

Import the provided n8n workflow JSON into your n8n instance.

6. Activate the Workflow

Once the required credentials and spreadsheet are configured, activate the workflow.

The Schedule Trigger will periodically start the monitoring process.

How It Works

Every scheduled execution retrieves the existing content records and the configured YouTube channels.

Each channel is processed individually.

The RSS feed returns the channel's video information. The workflow then compares each incoming Video ID with the Video IDs already stored in Google Sheets.

If the Video ID already exists, the workflow skips it.

If the Video ID is new:

New Video
   ↓
Detect New Content
   ↓
Add to Google Sheets
   ↓
Send Gmail Alert

After processing the current channel, the workflow continues with the remaining channels.

Example Result

When a new video is published:

YouTube Channel
       ↓
YouTube RSS Feed
       ↓
New Video Detected
       ↓
Google Sheets
       ↓
Gmail Notification

The new video is recorded with its:

Video ID
Channel Name
Title
Published At
Link
Use Cases

This workflow can be used to monitor:

YouTube creators
Competitor channels
Educational channels
Technology channels
News channels
Industry-specific channels
Multiple channels from a single dashboard
Automation Benefits

Instead of manually checking multiple YouTube channels, this workflow automatically monitors them on a schedule.

It helps you:

Detect new videos automatically
Avoid duplicate records
Maintain a centralized content database
Receive immediate email notifications
Monitor multiple channels from one workflow
Workflow Status
YouTube Monitoring: Automated
Duplicate Detection: Enabled
Google Sheets Logging: Enabled
Gmail Notifications: Enabled
Built With
n8n
YouTube RSS
Google Sheets
Gmail
JavaScript
