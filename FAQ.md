# Frequently Asked Questions

## General

### What is Jot?

Jot is a privacy-first, local-first note-taking app designed for iOS. It combines fast, offline-first notes with AI features, Markdown support, voice transcription, and smart daily planning.

### Is Jot free?

Jot is free to download and use. AI features use a credits system that can be earned through optional, respectful ads or (in future versions) purchased directly.

### Does Jot work offline?

Yes! Jot is local-first, meaning all your notes are stored on your device and work completely offline. Cloud sync and AI features require an internet connection.

---

## Privacy & Security

### Where are my notes stored?

All notes are stored locally on your device using the Isar database. We never have access to your note content.

### Is my data encrypted?

Backups can be encrypted using AES-256-GCM. iCloud sync uses Apple's built-in encryption. API keys are stored in the iOS Keychain.

### Do you track my usage?

We collect minimal, anonymized analytics to improve the app (feature usage, crash reports). No note content is ever collected.

### What about AI features?

When you use AI features, your selected text is sent to the AI provider you choose (Gemini, OpenAI, or Claude). We don't store this data.

---

## Features

### What Markdown features are supported?

- Headers (H1-H6)
- Bold, italic, strikethrough
- Checklists and bullet lists
- Code blocks with syntax highlighting
- Wikilinks ([[note name]])
- Obsidian-style callouts (> [!note], > [!tip], etc.)
- Tables
- And more!

### Can I use my own AI API keys?

Yes! You can add your own API keys for OpenAI, Anthropic (Claude), or Google Gemini in Settings. This bypasses the credits system.

### How does Plan My Day work?

Plan My Day helps you start each morning with an AI-assisted daily plan. It includes focus mode, break reminders, and task tracking. You can use it in Quick List mode (manual) or Smart Plan mode (AI-assisted).

### Can I lock individual notes?

Yes! You can enable biometric lock (Face ID/Touch ID) for individual notes or entire folders through the note or folder settings.

---

## Troubleshooting

### The app is crashing. What should I do?

1. Make sure you're on the latest version of Jot
2. Try restarting the app
3. If the issue persists, [report a bug](../../issues/new?template=bug_report.md)

### My notes aren't syncing to iCloud

1. Check that iCloud is enabled in iOS Settings
2. Verify you have sufficient iCloud storage
3. Go to Jot Settings → Storage → Enable iCloud Sync
4. Try toggling sync off and on again

### AI features aren't working

1. Check your internet connection
2. Verify you have AI credits available (Settings → AI Dashboard)
3. If using your own API key, verify it's correctly entered
4. Try switching to a different AI provider

---

## Support

Still have questions?
- [Start a Discussion](../../discussions) — Best for questions and general help
- [Open an Issue](../../issues/new?template=question.md) — For specific questions
