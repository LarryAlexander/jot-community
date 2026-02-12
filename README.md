# Jot (JID) - "Just Jot it Down"

A polished note-taking app built with Flutter that combines the clean, minimalist interface of Apple Notes with the powerful knowledge management features of Obsidian.

## About Jot

Jot is designed to be a beautiful, intuitive notes app that starts simple but scales with your needs. Built with a local-first approach, your notes are stored as plain Markdown files, ensuring you always own your data. As your collection grows, Jot offers powerful organization, search, and knowledge management features without compromising on simplicity or performance.

## 📋 **Project Status & TODOs**

📊 **Current Status:** Active development with 96 TODOs across 20 files  
🎯 **Priority Focus:** Settings integration, AI pricing updates, notification system  
📝 **Full Details:** See [Open Issues](docs/planning/OPEN_ISSUES.md) for prioritized tracking

## 🗂️ **Project Structure**

This project follows a feature-based architecture for improved maintainability:

### **📚 Documentation**

- [**Documentation Index**](docs/README.md) - Primary index for active technical documentation
- [**Folder Management Architecture**](docs/architecture/FOLDER_MANAGEMENT_ARCHITECTURE.md) - Canonical source tree structure and rules
- [**Important Docs Replacement Plan**](docs/planning/IMPORTANT_DOCS_REPLACEMENT_PLAN.md) - Plan to replace high-value legacy docs
- [**Legacy Root Docs Archive**](docs/archive/root-legacy/) - Historical docs moved out of repository root
- [**ML Ranking Architecture**](specs/011-hybrid-ml-ai-ranking/ranking-architecture.md) - Technical design of the hybrid ranking system

### **📂 Code Organization**

- [**Models**](lib/src/domain/models/models.md) - Data structures and domain entities (28 files)
- [**Services**](lib/src/services/services.md) - Business logic and external integrations (31 files)
- [**Widgets**](lib/src/widgets/widgets.md) - Reusable UI components (40 files)
- [**Screens**](lib/src/screens/screens.md) - Application screens and page-level components (20+ files)

## Key Features

### 🎯 **Current Features**

- ✏️ Rich text editing with Markdown support and live preview
- 📰 **RSS Intelligence Briefing** - AI-prioritized news feed with deep note integration
- 📋 **Smart Lists** - Apple Reminders-style intelligent task filtering (Today, This Week, High Priority, Overdue)
- 📊 **Intelligent Feed Ranking** - Hybrid ML + AI ranking identifies "Must Read" articles
- 🤖 AI-powered content enhancement (Gemini, OpenAI, Claude integration)
- 💰 AI Credits system _(ad monetization temporarily disabled for v1.0.10)_
- 🗂️ Advanced folder organization with smart folders
- 📎 Multi-media attachments (images, audio, documents)
- 🎤 Voice notes with transcription capabilities
- 🔍 Full-text search with content indexing
- 📊 Usage analytics and writing insights
- 🏷️ Tag system with auto-suggestions
- ⚙️ Comprehensive settings and preferences
- 🌙 Adaptive theming (light/dark mode)

### 🚀 **In Development**

- 🔔 Cross-platform notifications
- 📤 Multi-format data export (JSON, PDF, text)
- � Real-time analytics dashboard
- 🔒 Enhanced privacy and security controls
- ☁️ Cloud synchronization
- 🎨 Advanced customization options

## Technical Architecture

- **Framework:** Flutter 3.6.1+
- **State Management:** Riverpod with provider-based dependency injection
- **Database:** Isar (local)
- **ML/AI Ranking:** Local-first pipeline (TF-IDF, LDA) + Semantic AI Scoring with Privacy Controls
- **AI Integration:** Multi-provider system (Gemini, OpenAI, Anthropic)
- **Native iOS Integration:** Speech Recognition, Share Extension, Method Channels
- **Storage:** Local-first with optional cloud backup
- **Architecture:** Feature-based modular structure with clean separation of concerns

### Platform-Specific Features (Currently iOS)

- **Voice Transcription:** Native SFSpeechRecognizer for accurate file-based transcription
- **Share Extension:** Capture content from Safari, Photos, and other apps (requires Xcode setup)
- **Notifications:** Local notifications with proper permission handling
- **App Groups:** Shared data storage between app and extensions

See [iOS Share Extension Setup Guide](docs/guides/IOS_SHARE_EXTENSION_SETUP.md) and [iOS Features Testing Guide](docs/guides/IOS_FEATURES_TESTING_GUIDE.md) for details.

### 🔌 Model Context Protocol (MCP) Server

Jot includes a built-in MCP server that exposes note operations to AI assistants (VS Code Copilot, Claude Desktop, Cursor). Connect any MCP-enabled AI tool to create, search, and manage your Jot notes programmatically.

**One-Click Install for VS Code:**

[![Install Jot MCP Server](https://img.shields.io/badge/Install%20to%20VS%20Code-Jot%20MCP-0078D4?style=for-the-badge&logo=visualstudiocode)](vscode:extension/install-mcp?%7B%22name%22%3A%22jot%22%2C%22command%22%3A%22dart%22%2C%22args%22%3A%5B%22bin%2Fmcp_server.dart%22%5D%2C%22cwd%22%3A%22%24%7BworkspaceFolder%7D%22%7D)

**Manual Configuration:**

Add to your `.vscode/settings.json` or Claude Desktop config:

```json
{
  "mcp.servers": {
    "jot": {
      "command": "dart",
      "args": ["bin/mcp_server.dart"],
      "cwd": "/path/to/Jot"
    }
  }
}
```

**Available Tools:**
- `create_note` - Create notes with title, content, tags, folders
- `search_notes` - Search with relevance scoring
- `get_note_by_id` - Retrieve note details
- `update_note` - Modify existing notes
- `create_folder` - Organize with folders
- `list_folders` - Browse folder tree
- `add_tag` - Tag notes
- `link_notes` - Create wikilinks

See [MCP Installation Guide](docs/MCP_INSTALLATION.md) and [MCP Testing Guide](docs/MCP_TESTING_GUIDE.md) for full documentation.

## Development Roadmap

Jot is being developed in phases:

1. **Phase 0 (MVP):** Core note-taking with Markdown and basic organization
2. **Phase 1:** Enhanced editing with rich text and media support
3. **Phase 2:** Search and improved organization (tags, filters, pins)
4. **Phase 3:** Cloud sync and cross-device access
5. **Phase 4:** Customization and security features
6. **Phase 5:** Advanced note features (linking, backlinks, daily notes)

See [Feature Integration Roadmap](docs/planning/FEATURE_INTEGRATION_ROADMAP.md) for current development planning.

## Philosophy

Jot follows these key principles:

- **Local-first:** Your notes are stored on your device in open formats - no vendor lock-in
- **Simplicity first:** Clean, intuitive UI that stays out of your way
- **Progressive complexity:** Start simple, but scale with powerful features as needed
- **Privacy focused:** Your notes are yours alone - no tracking or data collection

## Getting Started

_Coming soon - development in progress_

## 🔐 Enhanced Backup & Restore

The app now includes a secure, version-aware backup and restoration flow:

- Encrypted backups using AES-GCM with PBKDF2 key derivation
- Progress updates during backup/restore operations
- Restore Preview Dialog shows backup metadata and lets you toggle version-history restore
- Share backups via the system share sheet (SharePlus)

Where to find it:

- Storage & Backup screen: create backups, view history, share files, and restore.
- Restore Preview is shown before restoring any backup to confirm contents and options.

Notes:

- Backups are encrypted-at-rest; keys are managed via a KeyManager abstraction (secure storage on device).
- Restore has an option to include/exclude version history.

## 💰 AI Credits & Ad System

> **⚠️ Note:** Ad-based monetization and Stripe payments are **temporarily disabled in v1.0.10** to focus on core stability. Infrastructure remains in codebase, controlled by feature flags. See issues [#195](https://github.com/LarryAlexander/jot/issues/195) (Google Ads) and [#103](https://github.com/LarryAlexander/jot/issues/103) (Stripe) for production roadmap.

Jot features a comprehensive monetization system that rewards users with AI credits for viewing ads:

### Earning Credits

- **Rewarded Ads**: 5.0 credits - Watch full ad in Settings
- **App Open Ads**: 1.0 credit - Once per day on app launch
- **Banner Ads**: 0.5 credits - Bottom of home screen
- **RSS Styled Ads**: 0.5 credits - Sponsored content in RSS feeds
- **Project Styled Ads**: 0.5 credits - Integrated in Projects folder

### Ad Controls

Users have complete control over ad visibility via **Settings → Ad Settings**:

- Toggle individual ad types on/off
- Credits balance displayed in Settings
- Watch rewarded ads on-demand for maximum credits

### Technical Details

**Architecture:**

- `AdDisplayService` - Manages App Open ads and credit distribution
- `AdCreditsService` - Handles Rewarded ads
- `CreditTransactionService` - Core credit operations with source tracking
- `AdSettings` - User preferences (Isar collection)
- Reactive Riverpod providers for real-time balance updates

**Documentation:**

- [AI Credits Guide](docs/features/AI_CREDITS_GUIDE.md) - Complete system documentation
- [Development Guide](docs/DEVELOPMENT_GUIDE.md#ad-system-architecture) - Implementation details

**Privacy:**
⚠️ UMP consent flow required before production release (GDPR/ATT compliance)

## 🧪 Dev quickstart

Analyze and tests:

- Run the analyzer task to verify the codebase is clean.
- Run unit/widget tests; Isar-dependent tests are skipped in environments without native Isar.

Code pointers:

- Core: `lib/src/services/database_backup_service.dart`, `lib/src/services/backup_encryption_service.dart`
- UI: `lib/src/widgets/dialogs/restore_preview_dialog.dart`, `lib/src/screens/storage_backup_screen.dart`
- Providers: `lib/src/providers/backup_progress_provider.dart`
- Specs: `specs/907-*.md` (implementation and notes)

## 📲 Install to device (iOS)

To install to a connected iOS device (e.g., LATHEKID):

- Ensure code signing is configured in Xcode for the Runner target (Team, Bundle ID, provisioning).
- Connect the device via USB and trust the computer.
- Select the device with `flutter devices` and install with `flutter install -d <device-id>`.

If your device shows as “LATHEKID,” you can target it directly once it appears in `flutter devices`.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Reporting issues and feedback

The app includes an in-app Feedback form (Settings → Feedback). Submissions are sent to a secure backend that files GitHub issues on your behalf.

- Deploy the function and set `FEEDBACK_ENDPOINT` in `.env` to the deployed URL (see `.env.example`)

# Force workflow trigger
