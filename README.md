# Intent Toolkit

A mobile-friendly web toolkit for Android intent URL research and testing. Designed for security researchers studying FRP (Factory Reset Protection) mechanisms on Samsung devices.

## Live Demo

Access the toolkit: **[https://danz17.github.io/intent-toolkit/](https://danz17.github.io/intent-toolkit/)**

## Features

- **Google Assistant Commands** - Voice commands that work during FRP lock!
- **Intent URL Generator** - Launch Android apps via Chrome intent:// URLs
- **QR Code Generator** - Create scannable QR codes for intent URLs
- **Samsung Secret Codes** - Collection of diagnostic dialer codes
- **Device-Specific Visibility** - Greyed out items that don't work on tested devices
- **Mobile-First Design** - Optimized for use directly on target devices
- **One-Tap Actions** - Fixed bottom bar for quick access
- **Research Data** - Built-in device compatibility tracking

## Breakthrough: Google Assistant

On some devices (tested: SM-S721B), Chrome intent:// URLs are blocked during FRP, but **Google Assistant voice commands work!**

### Working Commands (SM-S721B)
- "Open Display Settings"
- "Open Accessibility"
- "Open Sound Settings"
- "Open Notifications"
- "Open Device Info"

## Supported Intents

| Category | Examples |
|----------|----------|
| System Apps | Settings, Dialer, Contacts, File Manager |
| Samsung Apps | Galaxy Store, Samsung Members, SmartThings |
| Settings Activities | Developer Options, WiFi, Security, Accessibility |
| Dialer Codes | *#0808# (USB), *#0*# (Diagnostics), *#9900# (SysDump) |

## Device Compatibility

| Device | Model | Chrome Intents | Secret Codes | Assistant |
|--------|-------|----------------|--------------|-----------|
| Galaxy S24 FE | SM-S721B | Blocked | No trigger | Works |

## Intent URL Format

```
intent://[package]/#Intent;scheme=android-app;end
```

### Examples

```
# Open Settings
intent://com.android.settings/#Intent;scheme=android-app;end

# Open Samsung My Files
intent://com.sec.android.app.myfiles/#Intent;scheme=android-app;end

# Open Developer Options (direct)
intent://com.android.settings/.DevelopmentSettings/#Intent;scheme=android-app;end
```

## Usage

### On a PC
1. Open `index.html` in your browser
2. Click any intent to generate a QR code
3. Scan QR with Google Lens on the target device

### On a Mobile Device
1. Navigate to the hosted URL in Chrome
2. Tap any intent link directly
3. The target app/activity should launch

## Disclaimer

This toolkit is intended for **educational and security research purposes only**. Use only on devices you own or have explicit permission to test. The author is not responsible for any misuse.

## Author

**Phenix** (Alaa Qweider)

## License

MIT License - Feel free to use, modify, and distribute.
