# Jot Documentation

> **Complete documentation for Jot - Local-First Flutter Note-Taking App**

---

## 📚 Documentation Overview

Welcome to the Jot documentation! This comprehensive set of guides covers all aspects of the application architecture, development practices, and integration patterns.

The documentation is organized into the following categories:

- **[Architecture](architecture/)**: High-level design, data flow, and core system documentation.
- **[Database](database/)**: Isar database usage, strategies, and fork maintenance.
- **[Features](features/)**: Documentation for specific features like Theming, Markdown, Voice Notes, etc.
- **[Guides](guides/)**: Developer guides, setup instructions, testing, and best practices.
- **[Planning](planning/)**: Roadmaps, implementation plans, and issue tracking.
- **[Archive](archive/)**: Deprecated or superseded documentation.
- **[Root Legacy Archive](archive/root-legacy/)**: Historical markdown files moved from repository root.

---

## 🗺️ Documentation Map

### 🏗️ Architecture ([architecture/](architecture/))

Core system design and patterns.

- **[Master Architecture Reference](architecture/ARCHITECTURE.md)**: Complete architectural overview covering all layers and systems. Start here!
- **[Data Flow Diagrams](architecture/DATA_FLOW_DIAGRAMS.md)**: Visual flows of data through the system (ASCII diagrams).
- **[Checkpoint System](architecture/CHECKPOINT_SYSTEM_IMPLEMENTATION.md)**: Implementation details of the checkpoint system for data integrity.
- **[Version History](architecture/VERSION_HISTORY_CENTRALIZATION.md)**: Centralized version history architecture.
- **[Frontmatter](architecture/FRONTMATTER_IMPLEMENTATION.md)**: Implementation of YAML frontmatter for notes.
- **[Folder Management Architecture](architecture/FOLDER_MANAGEMENT_ARCHITECTURE.md)**: Source tree layout and folder governance.
- **[Butler → AI Migration Notes](architecture/BUTLER_TO_AI_SERVICE_MIGRATION_NOTES.md)**: What to preserve from Butler deletions when rebuilding AI service capabilities.

### 🗄️ Database ([database/](database/))

Isar database integration and fork management.

- **[Isar Usage Patterns](database/ISAR_USAGE_PATTERNS.md)**: Best practices for using Isar in Jot.
- **[Isar In-Repo Strategy](database/ISAR_IN_REPO_STRATEGY.md)**: Strategy for managing the Isar fork.
- **[Isar Fork Documentation](database/isar_fork/ISAR_FORK_README.md)**: Detailed guide for the Isar fork.

### ✨ Features ([features/](features/))

Specific feature documentation and specs.

- **[Theming System](features/FEATURE_THEMING_SYSTEM.md)**: Implementation of the theming system.
- **[Voice Note Transcription](features/VOICE_NOTE_TRANSCRIPTION.md)**: Voice note recording and transcription features.
- **[Markdown Improvements](features/MARKDOWN_IMPROVEMENTS.md)**: Enhancements to Markdown rendering and editing.
- **[Auto-Wikilinks](features/AUTO_WIKILINK_IMPLEMENTATION.md)**: Implementation of automatic wikilinking.
- **[Navigation Updates](features/NAVIGATION_UPDATES.md)**: Navigation patterns and updates.
- **[Plan My Day](features/plan_my_day/PLAN_MY_DAY_SUMMARY.md)**: "Plan My Day" feature documentation.
- **[Subscription](features/subscription/SUBSCRIPTION_IMPLEMENTATION_SUMMARY.md)**: Subscription system implementation.

### 📘 Guides ([guides/](guides/))

Developer guides, setup, and workflows.

- **[Development Guide](guides/DEVELOPMENT_GUIDE.md)**: General development practices and workflows.
- **[Testing Guide](guides/TESTING_GUIDE.md)**: Testing strategies and examples.
- **[Quick Start](guides/QUICKSTART_PROJECT_CREATION.md)**: How to create a new project/note quickly.
- **[Dev Logs](guides/DEV_LOGS_IMPLEMENTATION.md)**: How to use the developer logging system.
- **[Import Guide](guides/IMPORT_GUIDE.md)**: Guide for importing data.

### 📅 Planning ([planning/](planning/))

Roadmaps and implementation plans.

- **[Roadmap](planning/FEATURE_INTEGRATION_ROADMAP.md)**: Feature integration roadmap.
- **[Issues to Create](planning/GITHUB_ISSUES_TO_CREATE.md)**: List of planned GitHub issues.
- **[Implementation Summary](planning/IMPLEMENTATION_SUMMARY.md)**: Summary of implemented features.
- **[Phase 3 Summary](planning/PHASE3_IMPLEMENTATION_SUMMARY.md)**: Summary of Phase 3 implementation.
- **[Important Docs Replacement Plan](planning/IMPORTANT_DOCS_REPLACEMENT_PLAN.md)**: Canonical rewrite plan for high-value legacy docs.
- **[Large File Decomposition Plan](planning/LARGE_FILE_DECOMPOSITION_PLAN.md)**: Ongoing plan for splitting oversized source files.

### 🗃️ Legacy Root Docs ([archive/root-legacy/](archive/root-legacy/))

Historical markdown files previously stored in repository root were moved on February 10, 2026 to reduce top-level clutter and centralize project documentation.

- Read-only references remain in `archive/root-legacy/`.
- Active docs should be created under the standard `architecture/`, `features/`, `guides/`, and `planning/` sections.
- Replacement priorities are tracked in [planning/IMPORTANT_DOCS_REPLACEMENT_PLAN.md](planning/IMPORTANT_DOCS_REPLACEMENT_PLAN.md).

---

## 🔍 Searching Documentation

You can search this documentation using your IDE's "Find in Files" feature, scoping the search to the `docs/` directory.
