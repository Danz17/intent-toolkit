# Intent Toolkit - FRP Research Project

## Project Structure

```
FRP-Research/
├── index.html              # PRODUCTION - Curated intents (GitHub Pages)
├── rules.md                # PROJECT RULES - Data flow & curation criteria
├── CLAUDE.md               # This file - agent instructions
├── README.md               # Documentation
├── .gitignore              # Excludes research/
└── research/               # LOCAL ONLY - Complete research database
    ├── approaches.md       # Bypass methods table (step-by-step + KPIs)
    ├── intents-master.md   # ALL intents ever found (81+ entries)
    ├── journal.md          # Session notes & findings
    ├── samsung-intents.md  # Samsung-specific research
    └── digest/             # Temp: downloaded source repos
```

## Data Architecture

```
Research Sources → research/*.md (RAW) → index.html (CURATED)
```

| Location | Contains | Deployed? |
|----------|----------|-----------|
| `research/intents-master.md` | ALL intents (complete) | NO |
| `research/approaches.md` | ALL methods (with results) | NO |
| `index.html` | Curated intents only | YES |

**See `rules.md` for full data flow and curation criteria.**

## Research Tables

### 1. `research/approaches.md`
Table of bypass methods with:
- Step-by-step instructions
- KPI per step (✅/❌/❓)
- Working devices (model, OS)
- NOT working devices (model, OS)

### 2. `research/intents-master.md`
Complete intent database with:
- 81+ intents across all manufacturers
- Category, label, URL, purpose
- Source file reference
- Device compatibility tracking

## Digest Workflow

When new research arrives (e.g., from web search or agents):

1. **Save** raw findings to `research/*.md` (temp file)
2. **Extract** intents → add to `intents-master.md`
3. **Extract** approaches → add to `approaches.md`
4. **Delete** the source file after digesting
5. **Note** in `journal.md` what was digested

## Git Strategy

- `research/` folder is **GITIGNORED**
- Only root files tracked: `index.html`, `rules.md`, `CLAUDE.md`, `README.md`
- GitHub Pages: https://danz17.github.io/intent-toolkit/

## Production Curation

`index.html` contains ONLY:
- Confirmed working intents
- High-value theoretical intents (security, lock, account)
- Samsung-specific (target device)
- NOT confirmed broken on Android 14+

## Testing

### Local
```bash
cd C:\Users\Kratos\Desktop\FRP-Research
python -m http.server 8000
# Open http://localhost:8000/
```

### Device
1. Get to Chrome (keyboard settings or Assistant)
2. Navigate to toolkit URL
3. Test intents from categories

## Device Under Test

| Property | Value |
|----------|-------|
| Model | SM-S721B (Galaxy S24 FE) |
| Android | 14 |
| One UI | 6.0+ |
| FRP Status | TRIGGERED |
| Chrome intents | BLOCKED |
| Voice commands | WORKING |
| Auto Blocker | Blocks dial codes |

## Key Findings (S24 FE)

| What | Status |
|------|--------|
| `intent://` URLs in Chrome | ❌ Blocked |
| `*#0*#` test mode | ❌ Auto Blocker |
| `*#0808#` USB settings | ❌ Auto Blocker |
| Google Assistant | ✅ Works |
| "Open Settings" voice | ❓ Untested |
| Keyboard gear icon | ❓ Untested |
| Connection Settings | ❓ Exploring |
