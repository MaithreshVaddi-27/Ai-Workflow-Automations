# Automated Email Notification System

**Platform:** [Automation Anywhere](https://www.automationanywhere.com) (RPA)

## Why I built it

A batch of reminder emails to send on a schedule is about as deterministic as automation gets — no judgment calls, just "for each row, send an email." That's exactly the kind of task RPA is built for, and building it in Automation Anywhere (rather than reaching for n8n/Make again) was also a deliberate choice to get hands-on with a dedicated RPA tool rather than only ever using AI-centric automation platforms.

## What it does

1. The bot opens [`AutomatedEmail.xlsx`](AutomatedEmail.xlsx) and reads it row by row.
2. For each row, it composes the corresponding email (recipient, subject/body pulled from the row's fields) and sends it.
3. Loops until every row has been processed, then finishes.

Full process documentation: [`documentation.pdf`](documentation.pdf)
Screen-recorded run: [`demo.mov`](demo.mov)

## Setup

1. Install [Automation Anywhere Community Edition](https://www.automationanywhere.com/products/automation-anywhere-community-edition) (or Enterprise, if available).
2. Import the bot logic described in [`documentation.pdf`](documentation.pdf).
3. Point the Excel-read action at your own copy of a workbook shaped like [`AutomatedEmail.xlsx`](AutomatedEmail.xlsx).
4. Configure the bot's email action with your own SMTP/Outlook credentials.
5. Run once manually to verify, then schedule via the Automation Anywhere Control Room's task scheduler if you want it recurring.

## Why RPA here (and not n8n/Make)

Straightforward, deterministic, rule-based row → email mapping — a good fit for RPA over an AI/agentic approach since there's no judgment call involved, just structured data → action. It's also a useful contrast point next to the n8n/Make projects in this repo: those lean on an LLM because the task genuinely needs reasoning (drafting, summarizing, deciding what to search for); this one deliberately doesn't, because it doesn't need to.

## Gotchas / what I'd improve

- No duplicate-send protection — re-running the bot against the same unmodified spreadsheet would resend every email. A "sent" status column, checked and updated per row, would fix that.
- Credentials for the email action live in the local Automation Anywhere bot configuration rather than a secrets vault — fine for a personal/demo bot, not how I'd wire this for anything shared with a team.
