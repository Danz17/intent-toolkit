# FRP Research Project Rules

> Project-specific rules for the FRP Intent Toolkit

---

## Data Flow Architecture

```
Raw Research Sources          Research Folder (LOCAL)           Production Site
─────────────────────         ────────────────────────          ────────────────
Web searches          ───►    intents-master.md (ALL)    ───►   index.html
GitHub repos          ───►    approaches.md (methods)           (curated only)
Session findings      ───►    journal.md (notes)
Agent research        ───►    *.md (temp files)
```

**Key Principle:** Research folder contains EVERYTHING. Production site contains only CURATED, TESTED intents.

---

## Research Tables

### 1. `research/intents-master.md` - Complete Intent Database
- **Contains:** EVERY intent URL ever discovered
- **Purpose:** Historical archive, future reference, basis for production curation
- **NOT displayed** on main site

### 2. `research/approaches.md` - Bypass Methods Table
- **Contains:** Step-by-step approaches with KPIs and device compatibility
- **Purpose:** Track what works, what doesn't, and on which devices
- **NOT displayed** on main site

### 3. `research/journal.md` - Session Notes
- **Contains:** Agent notes, findings, exploration paths
- **Purpose:** Continuity between sessions

---

## Digest Workflow

When new research is added (e.g., codex.md, gemini.md):

1. **Read** the source file
2. **Extract** intents → add to `intents-master.md`
3. **Extract** approaches → add to `approaches.md`
4. **Delete** the source file after digesting
5. **Mark** in journal.md that file was digested

This keeps the research folder clean while preserving all data.

---

## Curation Criteria for Production (index.html)

An intent should be included in the production site if:

| Criteria | Include? |
|----------|----------|
| Confirmed working on ANY device | ✅ YES |
| High theoretical value (security, lock, account) | ✅ YES |
| Samsung-specific (our target device) | ✅ YES |
| Untested but from reliable source | ✅ YES (mark as untested) |
| Confirmed 100% broken on Android 14+ | ❌ NO |
| Obsolete method (patched universally) | ❌ NO |
| Duplicate of existing intent | ❌ NO |

---

## Table Schemas

### approaches.md Schema

| Column | Description | Example |
|--------|-------------|---------|
| Approach | Method name | "Keyboard Gear Method" |
| Steps | Numbered steps (one per line) | "1. Tap email 2. Find gear..." |
| KPI per Step | Result per step | "1. ✅ 2. ❓ 3. ❌" |
| Working On | Model, Device, OS where works | "SM-A125F, A12" |
| NOT Working On | Model, Device, OS where fails | "SM-S721B, A14" |

### intents-master.md Schema

| Column | Description | Example |
|--------|-------------|---------|
| ID | Unique identifier | 1, 2, 3... |
| Category | Intent category | "security", "samsung", "google" |
| Label | Human-readable name | "Galaxy Store" |
| Intent URL | Full intent:// URL | `intent://com.sec...` |
| Purpose | What it does | "Open Galaxy Store app" |
| Source | Where discovered | "gemini.md", "esc0rtd3w" |
| Working | Devices where confirmed working | "SM-A125F (A12)" |
| Not Working | Devices where confirmed broken | "SM-S721B (A14)" |

---

## Naming Conventions

| Item | Convention | Example |
|------|------------|---------|
| Research files | lowercase-with-dashes.md | `samsung-intents.md` |
| Intent IDs | category_name | `samsung_galaxy_store` |
| Approach names | Title Case | "Battery Drain Method" |
| Device models | Official model code | "SM-S721B" |
| OS versions | "A" + version | "A14", "A13" |

---

## Git Strategy

- `research/` folder is **GITIGNORED** - never committed
- Only root files are tracked: `index.html`, `rules.md`, `CLAUDE.md`, `README.md`
- Production site deployed via GitHub Pages from root

---

## Agent Instructions

When working on this project:

1. **New research?** → Add to `research/intents-master.md` and `research/approaches.md`
2. **Testing results?** → Update the Working/Not Working columns in tables
3. **Updating production?** → Only add curated intents to `index.html`
4. **Cleaning up?** → Digest source files, then delete them

---

*Last updated: 2025-01-12*
