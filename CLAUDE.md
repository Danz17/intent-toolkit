# Intent Toolkit - FRP Research Project

## Project Structure

```
FRP-Research/
├── index.html          # Main toolkit (SERVED via GitHub Pages)
├── README.md           # Documentation
├── CLAUDE.md           # This file - project rules
├── .gitignore          # Excludes research/
└── research/           # LOCAL ONLY - The "cookbook"
    ├── digest/         # Temp: downloaded source repos (delete after processing)
    ├── intent-database.json  # Source data for embedding
    ├── logo_source.png       # Favicon source
    └── research.md           # Notes and findings
```

## Development Rules

### Git Strategy
- `research/` folder is FULLY IGNORED in git
- Only root-level files are tracked and deployed
- GitHub Pages serves from root: https://danz17.github.io/intent-toolkit/

### Research Folder Workflow
1. **Download** sources to `research/digest/`
2. **Process** and extract data to `research/intent-database.json`
3. **Embed** processed data into `index.html`
4. **Delete** digest files after processing (they're temporary)
5. **Commit** only root files to git

### Database Updates
- Intent data is embedded directly in `index.html` for offline use
- Source JSON in `research/` is for development/reference only
- When adding new intents: update both source JSON and embedded JS

### Mobile-First Design
- All UI must work on FRP-locked devices (limited interaction)
- Large touch targets (min 44px)
- Fast loading, minimal dependencies
- Session-persistent state (not saved between page loads)

### Click Tracking Behavior
1. Click intent → Grey out, mark as "last tried"
2. Click another → Previous moves to end of category, gets fully greyed
3. Reset button → Clears all tried state, restores order

## Testing

### Local Testing
```bash
cd C:\Users\Kratos\Desktop\FRP-Research
python -m http.server 8000
# Open http://localhost:8000/
```

### Device Testing
1. Get device to Chrome browser (via keyboard settings or Assistant)
2. Navigate to toolkit URL
3. Switch to Database tab
4. Tap category to expand
5. Tap intents to test

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Complete toolkit - HTML, CSS, JS all-in-one |
| `research/intent-database.json` | Source database (120+ intents) |
| `research/digest/` | Downloaded repos for processing |

## Device Under Test
- **Model:** SM-S721B (Galaxy S24 FE)
- **Android:** 14
- **FRP Status:** TRIGGERED
- **Findings:** Chrome intent:// URLs blocked, Google Assistant voice commands WORK
