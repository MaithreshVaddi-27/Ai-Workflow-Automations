# Make.com Scenarios

[Make.com](https://www.make.com) is where I go for automations that are naturally a "trigger → transform → fan-out" shape and don't need custom code — its visual router and built-in AI Agent module cover that ground fast.

| Project | Trigger | AI step | Output |
|---|---|---|---|
| [Social Media Automation](social-media-automation) | Google Sheets (scheduled, every 15 min) | Gemini summarizer + 3 platform-specific rewrites | Posts to LinkedIn, Facebook Pages, Telegram |
| [Resume Evaluator](resume-evaluator) | Telegram message | Make AI Agent (tool-using, calls 3 sub-scenarios) | Reply via Email / Telegram |

All Gemini calls go through Google's Gemini API — [ai.google.dev](https://ai.google.dev).

---

**Maithresh Vaddi** — [GitHub](https://github.com/MaithreshVaddi-27) · [LinkedIn](https://www.linkedin.com/in/maithreshvaddi/)
