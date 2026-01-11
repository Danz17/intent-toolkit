# Intent Toolkit

A mobile-friendly web toolkit for Android intent URL research and testing. Designed for security researchers studying FRP (Factory Reset Protection) mechanisms on Samsung devices.

## Live Demo

Access the toolkit: **[Your GitHub Pages URL]**

## Features

- **Intent URL Generator** - Launch Android apps via Chrome intent:// URLs
- **QR Code Generator** - Create scannable QR codes for intent URLs
- **Samsung Secret Codes** - Collection of diagnostic dialer codes
- **Mobile-First Design** - Optimized for use directly on target devices
- **One-Tap Actions** - Fixed bottom bar for quick access

## Supported Intents

| Category | Examples |
|----------|----------|
| System Apps | Settings, Dialer, Contacts, File Manager |
| Samsung Apps | Galaxy Store, Samsung Members, SmartThings |
| Settings Activities | Developer Options, WiFi, Security, Accessibility |
| Dialer Codes | *#0808# (USB), *#0*# (Diagnostics), *#9900# (SysDump) |

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
