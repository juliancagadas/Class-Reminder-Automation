# Class-Reminder-Automation
- Export json file in Docker

                 Schedule Trigger (Set to every 1 minute checking)
                           │
                           ▼
               Google Sheets (Get Rows)
                           │
                           ▼
          Filter (Today's Schedule Only)
                           │
                           ▼
             IF (warning == daytime)
                   /             \
              TRUE               FALSE
                │                  │
                ▼                  ▼
        Send Telegram         End Workflow


