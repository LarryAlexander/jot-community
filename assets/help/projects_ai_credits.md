```markdown
# Projects AI: API Keys & Costs

Understand how bring-your-own-key and local AI setup works when you use Projects AI to turn raw text into a structured project.

---

## How Access Works

1. **Your API key** — Add your own AI API key in Settings -> AI.
2. **Local AI** — Connect Ollama or another OpenAI-compatible local endpoint if you do not want a hosted provider.
3. **No Jot credits** — Jot no longer sells or grants AI credits for Projects AI access.

---

## Costs in Plain English

- Costs scale with text size and model choice, but pricing depends on your own provider.
- Jot can estimate provider cost before running when your selected provider is configured.
- You are billed directly by your provider or local stack. Jot does not deduct Jot-managed credits.

**Using your own provider**

- You control the account, billing, and rate limits.
- Jot can still show estimated usage and token counts after a run.
- Failures do not create any Jot-side AI balance changes because Jot does not manage a balance anymore.

---

## Common Scenarios

- **I have no API key configured** -> Add one in Settings -> AI, or connect a local provider like Ollama.
- **I use a local model** -> Make sure the local server is reachable from this device before running Projects AI.
- **Large paste (multi-page)** -> Provider cost and latency will be higher, especially on hosted frontier models.

---

## Tips to Reduce Cost

- Keep inputs concise (remove duplicates/attachments before running).
- Run Projects AI once, then edit the generated project manually.
- Switch to a lighter model (e.g., Gemini Flash or GPT-4o mini) in AI settings for cheaper runs.
- Prefer local AI when privacy or hosted cost matters more than output quality.

---

## Quick Steps

1. Go to Projects AI and paste your raw text.
2. Review the estimated provider cost if available.
3. Run the AI conversion and review the structured project.

---

## Need Help?

- Open **Settings -> Help & Guides -> Projects AI: API Keys & Costs**
- Or check **Settings -> AI** to verify your provider configuration
```
