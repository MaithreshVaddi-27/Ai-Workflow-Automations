# Learning Path Generator Agent

**Platform:** [n8n](https://n8n.io)

*(No screenshot yet — this one's documented straight from the workflow export.)*

## Why I built it

"Learn X in N days" is a request I make of ChatGpt-style tools constantly, and I always end up manually copying the plan into a doc and manually blocking out calendar time for it. This agent does both steps itself: chat it a goal, and it researches real resources, writes the whole curriculum into a fresh Google Doc, and puts study blocks on the calendar — one chat message, zero manual copy-pasting.

## How it works

```
When chat message received
        │
        ▼
AI Agent ── Model: Google Gemini
        │     Tools: SerpAPI · Create Google Doc · Update Google Doc · Create Google Calendar event
        ▼
(Google Doc + Calendar events, created/updated by the agent itself)
```

This is a true tool-using agent, not a fixed pipeline — Gemini decides which tools to call and in what order, guided by a structured system prompt:

1. **Parse the request** — extract the learning goal/topic, number of days, and start date from the chat message. If no date is given, default to today; "tomorrow" and "next Monday" are resolved relative to `Asia/Kolkata` time.
2. **Build the curriculum** — generate a beginner-to-advanced, day-by-day plan for exactly N days: each day gets a topic, a 2–3 sentence description, 3 key learning points, a video URL, an article/doc URL, and a fixed 2-hour duration. Dates increase by exactly one day per entry.
3. **Research (bounded)** — the prompt explicitly caps tool use to 2–3 web searches total via the **SerpAPI** tool, and instructs the agent to never invent a URL — only cite what search actually returned.
4. **Write the doc** — calls **Create a document in Google Docs** exactly once, titled `"[N]-Day [Topic] Learning Path"`, then calls **Update a document in Google Docs** exactly once to insert the full curriculum text.
5. **Schedule it** — calls **Create an event in Google Calendar** for each day's study block, using the agent-computed start/end times.

## Setup

1. Add credentials for **Google Gemini**, **SerpApi** ([serpapi.com](https://serpapi.com)), **Google Docs**, and **Google Calendar**.
2. Get `workflow.json` from the [n8n Drive folder](https://drive.google.com/drive/folders/16zvBvFm3g4V_ExoP4TraRaNTQBqnfw9B?usp=sharing) and import it into n8n.
3. Set the `folderId` on the **Create a document in Google Docs** node to a Drive folder you own.
4. Set the calendar on the **Create an event in Google Calendar** node to your own calendar.
5. Open the chat trigger (n8n's built-in chat UI, or wire it to Telegram/Slack) and try: *"Teach me LangChain in 5 days starting tomorrow."*

## Gotchas / what I'd improve

- "Use web search only 2–3 times total" is a prompt-level constraint, not an enforced limit — a system prompt that phrases it as a hard rule rather than a request would be more robust against the agent over-searching on longer curriculums.
- "Create exactly ONE Google Doc... update it exactly ONCE" exists to stop the agent from creating duplicate docs across retries — worth keeping in mind as a pattern for any tool-using agent that does side-effecting writes: be explicit about idempotency in the prompt, because the agent has no other way to know not to repeat itself.
- No error handling if the Calendar or Docs API call fails mid-agent-run — a partially-completed learning path (doc created, some/no calendar events) is possible.
