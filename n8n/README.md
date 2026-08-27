# n8n Workflows

[n8n](https://n8n.io) is the platform I reach for whenever an automation needs real branching logic, code nodes, or an LLM agent with tools — ten workflows live here, covering scheduled jobs, webhooks, and chat/Telegram-triggered agents.

| Project | Trigger | AI step | Output |
|---|---|---|---|
| [Internship Applier](internship-applier) | Google Sheets Trigger | Gemini (structured output) | Gmail send |
| [LinkedIn Job Tracker](linkedin-job-tracker) | Schedule + RSS | Gemini (structured output) | Append row to Sheet |
| [News Summarizer](news-summarizer) | Schedule + RSS + SerpApi | Gemini summarizer | Gmail send |
| [Shopping Assistant](shopping-assistant) | Telegram — text or voice only | Groq Whisper + Gemini agent + Redis memory | Telegram reply |
| [Weather Daily Planner](weather-daily-planner) | Schedule + OpenWeather | Gemini summarizer | Gmail send |
| [Historical Content Publisher](historical-content-publisher) | Schedule | Gemini | LinkedIn post |
| [Podcast Generator](podcast-generator) | Webhook | Gemini + MurfAI TTS | Audio file returned |
| [Learning Journey Showcase](learning-journey-showcase) | Google Sheets Trigger | Gemini (summarize + 2 post generators) | LinkedIn + X posts |
| [Social Media Automation](social-media-automation) | Google Sheets Trigger | Gemini (summarize + 2 post generators) | LinkedIn + X posts |
| [Learning Path Generator Agent](learning-path-generator) | Chat message | Gemini agent + SerpApi tool | Google Doc + Calendar events |

All Gemini calls use Google's Gemini API — [ai.google.dev](https://ai.google.dev).

---

**Maithresh Vaddi** — [GitHub](https://github.com/MaithreshVaddi-27) · [LinkedIn](https://www.linkedin.com/in/maithreshvaddi/)
