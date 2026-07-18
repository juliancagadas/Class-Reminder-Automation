<p align="center">
  <img src="Asset/class-reminder-banner.png" alt="Class Reminder with Weather Checker" width="100%">
</p>

## Workflow

```text
Schedule Trigger
      │
      ▼
Retrieve Today's Schedule (Google Sheets)
      │
      ▼
Filter Today's Classes
      │
      ▼
Check Reminder Time
      │
      ├── No ─────────────► End Workflow
      │
      ▼ Yes
Fetch Current Weather (Open-Meteo API)
      │
      ▼
Merge Schedule & Weather Data
      │
      ▼
Convert Weather Code to Readable Description
      │
      ▼
Generate Reminder Message
      │
      ▼
Send Notification via Telegram Bot
```
