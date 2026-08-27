# AI Workflow Automations

A collection of production-style automations I've built to solve real problems in my own job search, content routine, and daily life — across three different automation platforms so I could learn where each one actually shines instead of forcing everything into one tool.

| Platform | What it's good at (why I used it here) | Website |
|---|---|---|
| **n8n** | Full control over logic, branching, code nodes, and LLM agents — my default for anything with an AI reasoning step | [n8n.io](https://n8n.io) |
| **Make.com** | Fast visual builds for straightforward "trigger → transform → post" pipelines and no-code AI Agents | [make.com](https://www.make.com) |
| **Automation Anywhere** | Deterministic, rule-based RPA where there's no judgment call to make — just structured data → action | [automationanywhere.com](https://www.automationanywhere.com) |

## Index

### n8n
| Project | Trigger | AI / Logic | Output |
|---|---|---|---|
| [Internship Applier](n8n/internship-applier) | Google Sheets row added | Gemini drafts the email | Gmail send |
| [LinkedIn Job Tracker](n8n/linkedin-job-tracker) | Daily schedule + RSS | Gemini extracts skills + drafts a cover letter | Row appended to Sheet |
| [News Summarizer](n8n/news-summarizer) | Daily schedule + RSS + SerpApi | Gemini writes a categorized digest | Gmail send |
| [Shopping Assistant](n8n/shopping-assistant) | Telegram — **text or voice only** | Groq Whisper (voice) + Gemini agent + Redis memory | Telegram reply |
| [Weather Daily Planner](n8n/weather-daily-planner) | Daily schedule + OpenWeather | Gemini writes a daily plan | Gmail send |
| [Historical Content Publisher](n8n/historical-content-publisher) | Daily schedule | Gemini finds + writes the post | LinkedIn post |
| [Podcast Generator](n8n/podcast-generator) | Webhook (from PodEase Pro) | Gemini script + MurfAI voice | Audio file returned |
| [Learning Journey Showcase](n8n/learning-journey-showcase) | Google Sheets row added | Gemini summarizes + drafts platform posts | LinkedIn + X posts |
| [Social Media Automation (n8n)](n8n/social-media-automation) | Google Sheets row added | Gemini summarizes an article + drafts posts | LinkedIn + X posts |
| [Learning Path Generator Agent](n8n/learning-path-generator) | Chat message | Gemini agent + SerpApi research | Google Doc + Calendar events |

### Make.com
| Project | Trigger | AI / Logic | Output |
|---|---|---|---|
| [Social Media Automation](make.com/social-media-automation) | Scheduled, every 15 min | AI summarizer + 3 platform personalizers | LinkedIn, Facebook, Telegram |
| [Resume Evaluator](make.com/resume-evaluator) | Telegram message | Make AI Agent (tool-using) | Email + Telegram reply |

### Automation Anywhere
| Project | Trigger | Logic | Output |
|---|---|---|---|
| [Email Notification System](automation-anywhere/email-notification-system) | Reads an Excel source | Row-by-row loop | Email reminders |

## APIs and services used across these projects

| Service | Used for | Website |
|---|---|---|
| Google Gemini | Primary LLM for summarization, drafting, and agent reasoning | [ai.google.dev](https://ai.google.dev) |
| Groq | Fast Whisper transcription (voice-to-text) for the Shopping Assistant | [groq.com](https://groq.com) |
| SerpApi | Google Events / web search results for News Summarizer and Learning Path Generator | [serpapi.com](https://serpapi.com) |
| ScraperAPI | Proxied HTML fetch (Amazon search results) for Shopping Assistant | [scraperapi.com](https://www.scraperapi.com) |
| MurfAI | Text-to-speech voice generation for the Podcast Generator | [murf.ai](https://murf.ai) |
| OpenWeatherMap | Live weather data for the Daily Planner | [openweathermap.org](https://openweathermap.org) |
| Redis | Per-user conversation memory for the Shopping Assistant | [redis.io](https://redis.io) |
| Telegram Bot API | Chat interface for Shopping Assistant and Resume Evaluator | [core.telegram.org/bots](https://core.telegram.org/bots) |

## A note on the workflow files

The actual workflow exports (`.json` for n8n, `.blueprint.json` for Make.com) are **not stored in this GitHub repo** — they live in the Drive folders below instead, redacted the same way (all API keys, document IDs, and chat IDs replaced with placeholders). Each project's README links to the relevant file directly. This repo holds the documentation, diagrams, and screenshots; Drive holds the importable source.

## Full workflow archives (Google Drive)

- **n8n:** [Drive folder](https://drive.google.com/drive/folders/16zvBvFm3g4V_ExoP4TraRaNTQBqnfw9B?usp=sharing)
- **Make.com:** [Drive folder](https://drive.google.com/drive/folders/1mZilmpQAg4ntFNuvWaaeqHy10Gbz8DF4?usp=sharing)
- **Automation Anywhere:** [Drive folder](https://drive.google.com/drive/folders/1mZilmpQAg4ntFNuvWaaeqHy10Gbz8DF4?usp=sharing)

## Stack

`n8n` · `Make.com` · `Automation Anywhere` · `Google Gemini` · `Groq` · `MurfAI` · `SerpApi` · `ScraperAPI` · `OpenWeatherMap` · `Redis` · `Google Sheets/Docs/Calendar` · `Telegram Bot API` · `Gmail` · `LinkedIn API` · `X (Twitter) API` · `Facebook Pages API`

## Author

**Maithresh Vaddi**
[GitHub](https://github.com/MaithreshVaddi-27) · [LinkedIn](https://www.linkedin.com/in/maithreshvaddi/)
