````markdown
# AI-Powered Project Creation

Turn any raw text into a structured, actionable project with one tap.

---

## What It Does

Paste unstructured content—an email thread, meeting notes, voice-memo transcript, brainstorm dump—and let AI:

1. Extract a clear **project title** and summary
2. Identify **goals and milestones**
3. Break content into **phases** or **sections**
4. Generate **task lists** with suggested dates, priorities, and assignments
5. Produce a ready-to-edit **README** in Jot's project format

---

## How to Use

1. Open **Projects tab → + → AI Conversion** (or long-press **+** and choose _Convert Text_).
2. Paste or type your raw text.
3. (Optional) Select a template style: _Sprint_, _Campaign_, _Research_, _Event_, or _Custom_.
4. Tap **Convert**.
5. Review the generated project preview.
6. Edit if needed, then tap **Create Project**.

---

## What Happens Under the Hood

| Step         | Description                                                                                             |
| ------------ | ------------------------------------------------------------------------------------------------------- |
| **Tokenize** | Your text is sent securely to the configured AI provider.                                               |
| **Prompt**   | A tailored system prompt guides the model to output Jot-compatible markdown.                            |
| **Parse**    | The response is parsed: title, frontmatter, goals, task lists.                                          |
| **Preview**  | You see a rendered preview before committing.                                                           |
| **Save**     | On confirmation, Jot creates the project README, folders, and optionally initial tasks in the database. |

---

## Supported Input Types

- **Emails / Slack messages** — threads with action items, decisions
- **Meeting notes** — agendas, minutes, follow-ups
- **Voice transcripts** — dictated ideas or recordings
- **Brainstorm lists** — bullet points, mind-dump text
- **Existing documents** — copy-paste from Docs, Notion, etc.

---

## Template Styles

| Template | Best For                                   |
| -------- | ------------------------------------------ |
| Sprint   | Software or product development cycles     |
| Campaign | Marketing launches, social media pushes    |
| Research | Academic or exploratory projects           |
| Event    | Conferences, releases, meetups             |
| Custom   | Freeform; AI infers structure from content |

---

## Example

### Input

```
Hey team,

Just got off the call with the client. They want the landing page live by Jan 15.
Key points:
- Hero section needs new copy emphasizing speed
- Add testimonial carousel (pull 3 quotes from Slack)
- Mobile optimization is priority
- Sarah will handle design, Mike on dev
- Need legal sign-off on privacy policy link

Let's sync Monday to finalize timeline.
```

### Output (Preview)

```markdown
# Client Landing Page Launch

> Status: active
> Due: 2025-01-15
> Tags: #client #web #urgent

## Overview

Launch redesigned landing page with updated hero copy, testimonial carousel, and mobile-first optimization.

## Goals

- Go live by Jan 15
- Improve conversion with speed-focused messaging
- Mobile-first experience

## Tasks

### Design

- [ ] Create new hero section copy @sarah due:2025-01-08 prio:high
- [ ] Design testimonial carousel @sarah due:2025-01-10

### Development

- [ ] Implement hero section @mike due:2025-01-10
- [ ] Build testimonial carousel @mike due:2025-01-12
- [ ] Mobile optimization pass @mike due:2025-01-13 prio:high

### Legal

- [ ] Get sign-off on privacy policy link due:2025-01-14

## Notes

- Pull 3 testimonial quotes from Slack channel
- Monday sync to finalize timeline
```

---

## Credits & Cost

AI conversion uses Jot credits. Cost scales with input length and chosen model.

- **Typical cost:** 2–5 credits for short inputs; 5–15 for longer documents.
- **Low on credits?** Watch a rewarded ad to earn 5 credits instantly.
- **Using your own API key?** No Jot credits are charged.

See [Projects AI: Credits & Ads](projects_ai_credits.md) for details.

---

## Tips

- **Keep inputs focused.** Remove signatures, disclaimers, and unrelated threads before pasting.
- **Add hints.** Prefix your paste with "Project name: …" or "Due date: …" to guide output.
- **Pick the right template.** A _Campaign_ template surfaces different sections than _Sprint_.
- **Edit after.** AI output is a starting point—fine-tune dates, owners, and wording.

---

## Privacy

- Text is sent to the configured AI provider (OpenAI, Anthropic, or Google).
- Jot does not store your raw input after conversion completes.
- For maximum privacy, use your own API key and review your provider's data policies.

---

## FAQ

**Can I undo after creating the project?**
Yes. Delete the project or restore from version history.

**What if the AI misses something?**
Edit the generated README before or after creation—Jot treats it as a normal project.

**Does it work offline?**
No. AI conversion requires an internet connection.

**Can I convert multiple texts into one project?**
Combine them into a single paste first, or create separate projects and link via wikilinks.

---

## Need Help?

- Open **Settings → Help & Guides**
- Check [Projects AI: Credits & Ads](projects_ai_credits.md)
- Contact support via **Settings → Report Issue / Feedback**
````
