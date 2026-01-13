# Intent Toolkit

A mobile-friendly web toolkit for Android intent URL research and testing. Designed for security researchers studying FRP (Factory Reset Protection) mechanisms.

## Live Demo

Access the toolkit: **[https://danz17.github.io/intent-toolkit/](https://danz17.github.io/intent-toolkit/)**

## Features

- **Intent Database** - 80+ curated intent URLs across manufacturers
- **QR Code View** - Scannable QR codes for each intent
- **Google Assistant Commands** - Voice commands that work during FRP lock
- **Samsung Secret Codes** - Diagnostic dialer codes collection
- **Mobile-First Design** - Optimized for use on target devices
- **Session Tracking** - Track which intents you've tried
- **Admin Panel** - Stats, export, and device info

## Project Structure

```
FRP-Research/
├── index.html              # Production site (curated intents)
├── rules.md                # Project rules & data flow
├── CLAUDE.md               # Agent instructions
├── README.md               # This file
├── .gitignore              # Excludes research/
└── research/               # LOCAL ONLY - Complete research
    ├── approaches.md       # 15 bypass methods with step-by-step KPIs
    ├── intents-master.md   # 81+ intents (complete database)
    ├── journal.md          # Session notes & findings
    └── samsung-intents.md  # Samsung-specific research
```

## Data Architecture

| Location | Contents | Purpose |
|----------|----------|---------|
| `research/intents-master.md` | ALL intents ever found | Historical archive |
| `research/approaches.md` | ALL bypass methods | Track what works/doesn't |
| `index.html` | Curated intents only | Production use |

**Key Principle:** Research folder contains everything. Production site contains only tested/valuable intents.

## Device Compatibility

| Device | Model | Chrome Intents | Dial Codes | Assistant |
|--------|-------|----------------|------------|-----------|
| Galaxy S24 FE | SM-S721B | ❌ Blocked | ❌ Auto Blocker | ✅ Works |

## Intent URL Format

```
intent://[package]/#Intent;scheme=android-app;end
```

### Examples

```bash
# Open Settings
intent://com.android.settings/#Intent;scheme=android-app;end

# Open Galaxy Store
intent://com.sec.android.app.samsungapps/#Intent;scheme=android-app;end

# Open Smart Switch
intent://com.sec.android.easyMover/#Intent;scheme=android-app;end
```

## Research Database Stats

| Category | Intents |
|----------|---------|
| General Android | 9 |
| Security & Lock | 7 |
| Samsung Apps | 28 |
| Samsung Codes | 8 |
| Xiaomi | 6 |
| ColorOS (OnePlus/OPPO/Realme) | 5 |
| Google Pixel | 3 |
| Third-Party Tools | 7 |
| Google Apps | 8 |
| **Total** | **81+** |

## Bypass Approaches Documented

| # | Approach | Best For |
|---|----------|----------|
| 1 | Keyboard Gear Method | Samsung A11-A12 |
| 2 | Google Go Share | Moto, TCL |
| 3 | Battery Drain Trick | Android 11-12 |
| 4 | *#0808# ADB Enable | Samsung A10-A12 |
| 5 | *#0*# Test Mode | Samsung A9-A12 |
| 6 | Smart Switch Transfer | Samsung to Samsung |
| 7 | Galaxy Store → Alliance Shield | Samsung with store access |
| 8 | Force Stop Play Services | Any with Settings access |
| ... | + 7 more | Various |

## Usage

### On PC
1. Open `index.html` in browser
2. Switch to QR tab
3. Scan QR with Google Lens on target device

### On Mobile Device
1. Navigate to hosted URL in Chrome
2. Tap any intent link
3. Target app/activity launches (if not blocked)

### Voice Commands (if Assistant works)
- "Open Settings"
- "Open Chrome"
- "Open YouTube"
- "Open [app name]"

## Key Findings (SM-S721B / Galaxy S24 FE)

| Feature | Status |
|---------|--------|
| Chrome intent:// URLs | ❌ Blocked by FRP |
| Samsung dial codes | ❌ Blocked by Auto Blocker |
| Google Assistant | ✅ WORKING |
| TalkBack exploits | ❌ Patched in Android 14 |
| Keyboard gear icon | ❓ Needs testing |

## Disclaimer

This toolkit is intended for **educational and security research purposes only**. Use only on devices you own or have explicit permission to test. The author is not responsible for any misuse.

## Author

**Phenix** (Alaa Qweider)

## License

MIT License - Feel free to use, modify, and distribute.
