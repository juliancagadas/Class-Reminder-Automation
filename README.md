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
1. Trigger the workflow automatically.
2. Retrieve today's schedule from Google Sheets.
3. Filter today's class schedule.
4. Check if the current time matches the reminder time.
5. If matched, fetch the current weather from the Open-Meteo API.
6. Merge the schedule and weather information.
7. Convert the weather code into a readable description.
8. Generate the reminder message.
9. Send the notification via Telegram.
