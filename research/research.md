# FRP Bypass Research Documentation

**Researcher:** Phenix (Alaa Qweider)
**Email:** Alaa@nulled.ai
**Last Updated:** 2026-01-12

---

## Device Under Test

| Property | Value |
|----------|-------|
| Model | SM-S721B |
| Name | Galaxy S24 FE |
| Android | 14 |
| Firmware | S721BXXS3AYB3 |
| FRP Status | TRIGGERED |
| Bootloader | LOCKED |
| Test Date | 2026-01-12 |

---

## Research Summary

### Breakthrough Finding
**Google Assistant voice commands work during FRP lock!** This is a significant finding as most other methods are blocked on this device/firmware combination.

---

## Detailed Test Results

### Working Methods

| Method | Command/Action | Result | Notes |
|--------|---------------|--------|-------|
| Google Assistant | Hold home / "Hey Google" | Works | Can invoke voice commands |
| Assistant | "Open Display Settings" | Works | Full access to display settings |
| Assistant | "Open Accessibility" | Works | Full access to accessibility |
| Assistant | "Open Sound Settings" | Works | Full access to sound settings |
| Assistant | "Open Notifications" | Works | Full access to notification settings |
| Assistant | "Open Device Info" | Works | Opens About Phone - but 7x tap doesn't enable Dev Options |

### Partial Success (Opens then Closes)

| Method | Command/Action | Result | Notes |
|--------|---------------|--------|-------|
| Assistant | "Open Play Store" | Partial | Opens, shows update prompt, then closes |
| Assistant | "Open YouTube" | Partial | Opens, shows update prompt, then closes |

**Note:** After allowing these apps to update, they no longer respond to Assistant commands.

### Failed Methods

| Method | Action Taken | Result | Notes |
|--------|-------------|--------|-------|
| Chrome intent:// URLs | Tapped all intent links | Blocked | Chrome blocks all intent:// URLs during FRP |
| Samsung secret codes | tel:*#0808#, *#0*#, *#9900# | No trigger | Codes don't activate from tel: links |
| SamFW Tool MTP→ADB | Used MTP mode exploit | Not compatible | Doesn't work on SM-S721B |
| USB Driver Switch | Tried COM14→ADB driver | Failed | No compatible ADB drivers found |
| Developer Options toggle | 7x tap on Build Number | Doesn't enable | Toggle is disabled during FRP |
| Direct Dev Options intent | intent://...DevelopmentSettings/... | Blocked | Like all Chrome intents |

---

## Interesting Behaviors

### IntentResolver Crash
- **Finding:** Some share requests cause the IntentResolver app to crash
- **Potential:** This crash might be exploitable for navigation bypass
- **Status:** Needs further investigation

### App Update Behavior
- Apps like Play Store and YouTube initially open via Assistant
- They prompt for updates
- After update, they become unresponsive to Assistant commands
- **Recommendation:** Don't update apps during bypass attempt

---

## USB Connection Analysis

### Detected COM Ports

| Port | Device | Driver Status |
|------|--------|---------------|
| COM12 | SAMSUNG Mobile USB Modem #2 | MTP mode - working |
| COM14 | SAMSUNG Mobile USB Serial Port | Serial driver - no ADB option |

### Driver Installation Attempts

1. **Google USB Driver** (`usb_driver_r13-windows`)
   - Downloaded and extracted
   - Location: `research/usb_driver/android_winusb.inf`
   - Result: "No compatible drivers"

2. **Samsung Android Driver** (from SamFW Tool)
   - Location: `research/SamFwTool/data/drivers/SAMSUNG_Android.inf`
   - Result: "No compatible drivers"

---

## Tools Used

| Tool | Location | Purpose | Result |
|------|----------|---------|--------|
| SamFW Tool | `research/SamFwTool/` | MTP→ADB exploit, device info | Device detected, exploit failed |
| Google USB Driver | `research/usb_driver/` | ADB driver installation | No compatible drivers |
| Intent Toolkit | `index.html` | Chrome intent testing | All intents blocked |
| ADB | System PATH | Device communication | No device detected |

---

## Next Steps to Investigate

1. **IntentResolver Crash Exploit**
   - Find reliable way to trigger crash
   - See if crash leads to navigation options

2. **Download Mode Approach**
   - Volume Up + Volume Down + USB connection
   - Flash older vulnerable firmware via Odin
   - Perform bypass on older firmware
   - Update back to current

3. **Emergency Download Mode**
   - Research test point access
   - Deep flash capabilities

4. **Accessibility Exploitation**
   - Since Accessibility settings are accessible via Assistant
   - Look for services that can be enabled for further access

5. **Notification Settings Exploitation**
   - Check if any apps have notification actions that can lead to settings

---

## Device Compatibility Matrix

This section tracks what works on different devices for future reference.

| Device | Model | Android | Chrome Intents | Secret Codes | Assistant | Notes |
|--------|-------|---------|----------------|--------------|-----------|-------|
| Galaxy S24 FE | SM-S721B | 14 | Blocked | No trigger | Works | See detailed results above |

---

## Appendix: Intent URL Format

### Correct Format
```
intent://[package]/#Intent;scheme=android-app;end
```

### Examples
```
# Open Settings
intent://com.android.settings/#Intent;scheme=android-app;end

# Open Samsung My Files
intent://com.sec.android.app.myfiles/#Intent;scheme=android-app;end

# Open Developer Options (if accessible)
intent://com.android.settings/.DevelopmentSettings/#Intent;scheme=android-app;end
```

### Wrong Format (doesn't work)
```
intent:#Intent;action=android.intent.action.VIEW;...;end
```

---

## Changelog

### 2026-01-12
- Initial testing on SM-S721B
- Discovered Google Assistant breakthrough
- Documented all working/failed methods
- Created Intent Toolkit HTML page
- Deployed to GitHub Pages

---

## License

This research is for educational and security research purposes only. Use only on devices you own or have explicit permission to test.
