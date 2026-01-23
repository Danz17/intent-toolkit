# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A mobile-first web toolkit for Android intent URL research and FRP (Factory Reset Protection) security testing. Single-page app with embedded intent database, QR code generation, and session tracking.

**Live Site:** https://danz17.github.io/intent-toolkit/

## Architecture

```
Production (Git tracked)     Local Research (Gitignored)
─────────────────────────    ─────────────────────────────
index.html (curated)    ◄─── research/intents-master.md (ALL)
rules.md                     research/approaches.md (methods)
CLAUDE.md                    research/journal.md (notes)
README.md                    research/digest/ (temp files)
```

**Key Principle:** `research/` contains ALL data. `index.html` contains only CURATED, TESTED intents.

## Development Commands

```bash
# Local development server
python -m http.server 8000
# Then open http://localhost:8000/

# Alternative (Node.js)
npx serve .
```

## Code Structure (index.html)

The entire application is a single HTML file with embedded JavaScript:

| Section | Lines | Purpose |
|---------|-------|---------|
| CSS Styles | 14-449 | Mobile-first dark theme, category UI |
| HTML Structure | 451-608 | Header, views (Intent/QR/WebADB/Admin), modals |
| `categories` object | 614-646 | Category definitions with icons and priority |
| `voiceCommands` array | 649-661 | Google Assistant commands |
| `secretCodes` array | 664-682 | Samsung dial codes |
| `intentDatabase` array | 685-887 | Main intent collection (150+ entries) |
| State variables | 893-896 | `currentView`, `triedIntents`, `lastTriedId` |
| View functions | 912-1005 | `switchView()`, `renderIntentView()`, `renderCategoryPills()` |
| Click handlers | 1042-1079 | `handleIntentClick()` - marks tried, opens intent |
| QR functions | 1085-1170 | `renderQrView()`, `showQrModal()` |
| Admin functions | 1214-1266 | Password gate (357357), stats, export |

## Data Flow for New Research

1. **Ingest:** Save raw findings to `research/*.md`
2. **Extract intents:** Add to `research/intents-master.md`
3. **Extract methods:** Add to `research/approaches.md`
4. **Curate:** Only add to `index.html` if meets criteria (see rules.md)
5. **Cleanup:** Delete source file, note in `research/journal.md`

## Curation Criteria for index.html

| Include | Exclude |
|---------|---------|
| ✅ Confirmed working on ANY device | ❌ Confirmed broken on Android 14+ |
| ✅ High-value (security, lock, account) | ❌ Obsolete/patched methods |
| ✅ Samsung-specific (target device) | ❌ Duplicates |
| ✅ Untested but reliable source | |

## Adding New Intents to index.html

Add to the `intentDatabase` array following this schema:

```javascript
{
  id: "category_001",           // Unique: category_number
  category: "samsung",          // Must match key in categories object
  label: "App Name",            // Human-readable
  intentUrl: "intent://...",    // Full intent URL
  purpose: "What it does"       // Brief description
}
```

## Research Table Schemas

**approaches.md:**
| Approach | Steps | KPI per Step | Working On | NOT Working On |

**intents-master.md:**
| ID | Category | Label | Intent URL | Purpose | Source | Working | Not Working |

## Target Device

| Property | Value |
|----------|-------|
| Model | SM-S721B (Galaxy S24 FE) |
| Android | 14 |
| One UI | 6.0+ |
| Chrome intents | ❌ Blocked |
| Dial codes | ❌ Auto Blocker |
| Google Assistant | ✅ Works |

## Key Findings

- `intent://` URLs blocked by Chrome on FRP-locked Samsung Android 14+
- Samsung Auto Blocker blocks `*#0808#`, `*#0*#` dial codes
- `*#9090#` service mode still works on S24 FE
- Google Assistant voice commands work during FRP lock
