# How to Install Omer's Custom JIANT Firmware

**Firmware**: `release/jiant-v10.8.21-omer-features.fwsc`  
**Version**: V10.8.21+omer  
**SHA256**: `2ced83b091fa1b8a7f6efe5263581d56d0c3166aec54eeee32eba426dcf72a0b`

---

## ⚠️ BACKUP FIRST!

**ALWAYS back up your FM-1 projects before flashing custom firmware!**

Use the official JIANT web installer's backup feature or the command line:
```bash
python3 tools/fm1_backup.py backup.jiant
```

---

## Method 1: Web Installer (EASIEST - Mac/Windows/Linux)

### Step 1: Open the Custom Installer

**GitHub Pages URL** (once Pages is enabled):
```
https://omermishania.github.io/JIANT/webapp/installer/
```

Or open the installer locally:
```bash
# Clone this repository
git clone https://github.com/omermishania/JIANT
cd JIANT
git checkout cursor/omer-melodic-house-features-849d

# Build the local installer site
python3 web/make_site.py release/jiant-v10.8.21-omer-features.fwsc dev /tmp/omer-installer

# Serve it locally
cd /tmp/omer-installer
python3 -m http.server 8000

# Open in Chrome/Edge:
# http://localhost:8000/webapp/installer/
```

### Step 2: Connect FM-1

1. Connect FM-1 to computer via USB data cable
2. Power on the FM-1
3. Browser should detect it automatically

### Step 3: Back Up (Critical!)

The installer will prompt you to back up. **Do this!**

### Step 4: Install

Click the **Install** button and wait for completion (~30-60 seconds).

**Do NOT disconnect USB or power off during installation!**

### Step 5: Verify

- FM-1 reboots automatically
- Should show JIANT boot screen
- Version displays as V10.8.21+omer

---

## Method 2: Command Line via USB (Mac Terminal)

### Prerequisites

```bash
# Install Python dependencies
pip3 install mido python-rtmidi
```

### Steps

```bash
# 1. Download this repository
git clone https://github.com/omermishania/JIANT
cd JIANT
git checkout cursor/omer-melodic-house-features-849d

# 2. Connect FM-1 via USB and power on

# 3. Check connection (optional)
python3 tools/fm1_install.py --info

# 4. Back up (CRITICAL!)
python3 tools/fm1_backup.py ~/Desktop/fm1-backup-$(date +%Y%m%d).jiant

# 5. Flash the firmware
python3 tools/fm1_install.py release/jiant-v10.8.21-omer-features.fwsc

# 6. Wait for "Done" message
```

### On Mac: If Permission Denied

```bash
# Give Terminal permission to access USB MIDI:
# System Settings > Privacy & Security > Automation > Terminal
# Enable "MIDI devices"
```

---

## Verifying the Installation

### Check Version

Power on FM-1 - it should display version on boot screen.

### Test LANE 8 MODE

```
1. Hold HOME
2. Press SELECT  
3. Turn KNOB 1 to find "LANE 8"
4. Press OCT+ (top-right orange button)
→ Should generate melodic house track!
```

### Test CHORD MEMORY

```
1. Hold SCL
2. Navigate to CHORD page (white/black keys to move pages)
3. Set KNOB 1 (CHORD) to: TRIAD or 7TH
4. Set KNOB 4 (MODE) to: MEMORY
5. Play any white key
→ Each key should play a full chord!
```

---

## Troubleshooting

### "Cannot find FM-1" or "Device not detected"

1. **Check USB cable**: Must be a data cable, not charging-only
2. **Try different USB port**
3. **On Mac**: Check System Settings > Privacy & Security for USB/MIDI permissions
4. **Restart browser** (for web installer)
5. **Check if FM-1 appears in Audio MIDI Setup** (Mac) or Device Manager (Windows)

### "Install failed" or error during flashing

1. **Power cycle FM-1**: Turn off, wait 10 seconds, turn on
2. **Check cable connection**: Ensure firmly plugged in
3. **Close other apps**: Close DAWs, MIDI apps using the FM-1
4. **Try again**: Sometimes USB communication hiccups - retry once

### FM-1 won't start after flashing (black screen)

**Don't panic - this is recoverable!**

1. **Check if computer sees "WL80UBOOT"** when FM-1 is powered on
2. **Reflash**: Try flashing again - bootloader should still work
3. **Recovery tool**: Use [FM-1 Transporter](https://github.com/kurogedelic/FM-1-transporter) if needed

### Features not showing up

1. **Wrong branch**: Make sure you flashed `jiant-v10.8.21-omer-features.fwsc`
2. **Check SHA256**: Verify file integrity with `sha256sum` (see SHA256SUMS file)
3. **Reflash**: Try flashing again

---

## Reverting to Official Firmware

To go back to M-VAVE's official firmware:

1. Download from [M-VAVE Downloads](https://www.m-vave.com/download)
   - FM-1 firmware V16 or V15
   - Unzip and find `FM-1.fwsc`

2. Use same installation method:
   ```bash
   python3 tools/fm1_install.py ~/Downloads/FM-1.fwsc
   ```

Or use the official JIANT web installer at:
```
https://juanjiant-bit.github.io/JIANT/webapp/installer/
```

---

## Important Notes

- ⚠️ **Custom firmware voids warranty** - M-VAVE does not support it
- ⚠️ **Back up before flashing** - cannot be stressed enough!
- ⚠️ **Keep official firmware file** - in case you need to revert
- ⚠️ **Don't disconnect during flashing** - can brick the device
- ✅ **Flashing is usually safe** - thousands have done it successfully
- ✅ **Recovery is possible** - even from most failures with FM-1 Transporter

---

## Support

If you encounter issues:

1. **Check docs**: Read `docs/OMER-FEATURES.md` for feature usage
2. **GitHub Issues**: Search or create an issue
3. **Include details**:
   - What you tried
   - What error you got
   - Your operating system
   - Browser/terminal output
   - Photos/videos if helpful

---

**For detailed feature documentation**, see: `docs/OMER-FEATURES.md`

**Last Updated**: 2026-11-24  
**Repository**: https://github.com/omermishania/JIANT  
**Branch**: `cursor/omer-melodic-house-features-849d`
