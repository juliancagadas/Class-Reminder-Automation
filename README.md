# Class-Reminder-Automation Flow

Schedule Trigger
      │
      ▼
Read Google Sheets
      │
      ▼
Filter Today's Schedule
      │
      ▼
Check Time (IF)
      │
      ├────────────── No
      │               │
      │               ▼
      │          End Workflow
      │
      ▼ Yes
Fetch Current Weather
(Open-Meteo API)
      │
      ▼
Merge Schedule + Weather
      │
      ▼
Convert Weather Code
(JavaScript)
      │
      ▼
Format Telegram Message
      │
      ▼
Send Telegram Notification

