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
             IF (warning == daytime)
                   /             \
              TRUE               FALSE
                │                  │
                ▼                  ▼
        Send Telegram         End Workflow


Step 1 - Tinanggal natin ang lumang n8n container

Sa CMD:

docker stop n8n

Pagkatapos:

docker rm n8n

Bakit?

Dahil ang lumang container ay ginawa nang walang timezone settings, kaya gumagamit ito ng UTC/America time.

Step 2 - Gumawa tayo ng bagong container

Ito ang pinakamahalagang ginawa natin.

Sa CMD:

docker run -d ^
--name n8n ^
-p 5678:5678 ^
-v n8n_data:/home/node/.n8n ^
-e TZ=Asia/Manila ^
-e GENERIC_TIMEZONE=Asia/Manila ^
n8nio/n8n
Ito ang dalawang pinakamahalagang line
-e TZ=Asia/Manila

at

-e GENERIC_TIMEZONE=Asia/Manila
Ano ang ginagawa ng bawat isa?
1.
TZ=Asia/Manila

Ito ang nagsasabi sa Linux operating system sa loob ng Docker na Philippine Time ang gamitin.

Kapag wala ito,

new Date()
docker exec n8n date

madalas UTC ang lalabas.

2.
GENERIC_TIMEZONE=Asia/Manila

Ito naman ang nagsasabi sa n8n application na Philippine Time ang gamitin sa:

Schedule Trigger
$now
Cron jobs
Date & Time nodes

Ito ang dahilan kung bakit naging tama ang Schedule Trigger.

Step 3 - Chineck natin

Pagkatapos gumawa ng bagong container:

docker exec n8n printenv | findstr TZ

Lumabas

TZ=Asia/Manila

Pagkatapos

docker exec n8n printenv | findstr GENERIC

Lumabas

GENERIC_TIMEZONE=Asia/Manila
Step 4 - Pinatunayan natin sa n8n

Binuksan natin ang Schedule Trigger.

Lumabas

Timezone

Asia/Manila (UTC+08:00)

at

Readable Time

8:34 AM

Dito natin napatunayan na gumagana na ang timezone.

#Ito ang pinakaimportanteng ginawa natin

Hindi natin inayos ang timezone gamit ang JavaScript.

Hindi rin sa Google Sheets.

Hindi rin sa Telegram.

Ang tunay na solution ay:

✅ Nirecreate ang Docker container

at nilagyan ng

TZ=Asia/Manila

at

GENERIC_TIMEZONE=Asia/Manila

Pagkatapos, ginamit natin ang built-in na oras ng n8n ($now) sa IF node para siguradong ang comparison ay laging naka-base sa Philippine Time.

Kapag ililipat mo ang project sa ibang PC

Ito lang ang tandaan mo:

Gumawa ng bagong n8n container.
Huwag kalimutang idagdag:
-e TZ=Asia/Manila
-e GENERIC_TIMEZONE=Asia/Manila
Buksan ang Schedule Trigger at tiyaking ang output ay:
Timezone: Asia/Manila (UTC+08:00)

Kapag nakita mo iyan, alam mong maayos na ang timezone at hindi na babalik ang problema sa UTC o America time.
