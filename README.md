# Class-Reminder-Automation
- Export json file in Docker

                    EVERY 1 MINUTE
                           │
                           ▼
                 Schedule Trigger
                           │
                           ▼
               Google Sheets (Get Rows)
                           │
                           ▼
          Filter (Today's Schedule Only)
                           │
                           ▼
          Code (Compute Time Difference)
                           │
                           ▼
             IF (difference == 30?)
                   /             \
              TRUE               FALSE
                │                  │
                ▼                  ▼
        Send Telegram         End Workflow
