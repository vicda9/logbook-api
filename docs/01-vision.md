# Vision and Scope

## Problem
Tracking how you're doing (mood, sleep, gym, time with people) usually means handing personal data to an app you don't control. logbook-api is a simple, guided tracker you can use from any device or OS, built around data governance: you own your data, and it only collects what it needs (data minimization).

## Users
People who want to track their wellbeing without having to design their own system. Some people just want to be led, so v1 is a designed experience: a fixed set of things to log, kept short on purpose.

Multi-user. Users never see each other's data.

## In scope (v1)
- Accounts: sign up, log in, log out
- Guided check-in, at least once a day, with a fixed set of fields:
  - Mood: pick a word: happy, calm, grateful, tired, anxious, sad, angry, stressed
  - Sleep: manual entry, either hours or sleep/rise times
  - Rest: how rested you feel, 1-5 (instead of "sleep quality")
  - Movement: none, movement, stretch, or yoga. Simple and doable.
- Short optional note, with a length limit
- Users can export and delete all of their data
- View past check-ins
- Tiny web page: log in and fill out the check-in
- Hosted online with HTTPS so it works from phone and desktop

## Out of scope (for now)
- AI chat (this is not a chatbot)
- Native mobile app
- Photo and file attachments
- Custom trackers (users choosing what and how to log): v2
- Pocket recording ingestion: v2
- Apple Health sleep import: v2
- Complex mood states (LLM-assisted): later
- Per-user encryption of notes in the database: v2
- End-to-end encryption as an opt-in "private mode" (trades away AI features): later
- Weekly and monthly reviews and summaries: later
- A full front end: later

## Success looks like
- Sign up and log in from my phone
- Log a check-in from my phone at work (through my VPN)
- Log in on my desktop at home, see that check-in, log a new one
- See the new one on my phone
- A second user logs in and cannot see any of my check-ins

## Open questions
- Hosting: Railway Hobby (~$5/month) for the v1 demo. May First VPS or a home server (behind Cloudflare Tunnel) under evaluation for later. Emailing May First about VPS pricing and Docker support.
- Interactions: left open for now, to be decided with more context
