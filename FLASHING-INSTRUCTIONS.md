# Flashing Instructions for Omer's Custom JIANT Firmware

**Firmware File**: `release/jiant-v10.8.21-omer-features.fwsc`  
**SHA256**: `2ced83b091fa1b8a7f6efe5263581d56d0c3166aec54eeee32eba426dcf72a0b`  
**Size**: 596 KB  
**Version**: V10.8.21+omer

---

## ⚠️ IMPORTANT: BACK UP FIRST!

Before flashing custom firmware, **ALWAYS back up your projects**! You can lose all your music if something goes wrong.

---

## Method 1: Using JIANT Web Installer (EASIEST - RECOMMENDED)

### Prerequisites

- **Google Chrome** or **Microsoft Edge** browser (on Mac, Windows, or Linux)
- **USB data cable** (not just a charging cable!)
- **FM-1** powered on and connected

### Steps

1. **Download the firmware file**:
   - Get `jiant-v10.8.21-omer-features.fwsc` from this repository's `release/` folder
   - Or download from the GitHub release artifacts

2. **Open Chrome or Edge** on your computer

3. **Go to the JIANT web installer**:
   ```
   https://juanjiant-bit.github.io/JIANT/webapp/installer/
   ```
   (This is the official JIANT installer page)

4. **Back up your projects** (CRITICAL!):
   - The installer will prompt you to back up first
   - Follow the prompts to save your existing projects
   - Save the backup file somewhere safe!

5. **Return to Official Firmware First** (if coming from another custom firmware):
   - On the installer page, scroll down to **"Return to official"**
   - Click to expand this section
   - You'll see a file input that says **"Official FM-1.fwsc"**
   - **BUT**: You can use this same file input for custom firmware!
   
6. **Flash the custom firmware**:
   - In the **"Return to official"** section's file input
   - Click **"Choose File"** or the file input field
   - Select the downloaded `jiant-v10.8.21-omer-features.fwsc` file
   - **Note**: The installer will show a warning that it's not official firmware - this is expected and okay!
   - Click the **"Back up and return to official"** button (or the install button in that section)
   - The installer will begin flashing the custom firmware

7. **Wait for completion**:
   - Keep the FM-1 connected during the entire process
   - Do NOT disconnect USB or power off
   - Wait until you see "Done" or completion message
   - This usually takes 30-60 seconds

8. **Verify**:
   - The FM-1 will reboot automatically
   - You should see the JIANT boot screen
   - Version should show V10.8.21+omer (or similar)

---

## Method 2: Command Line (Advanced)

If you have Python and want to use the command-line installer:

```bash
# Install dependencies
pip3 install mido python-rtmidi

# Flash the firmware
python3 tools/fm1_install.py release/jiant-v10.8.21-omer-features.fwsc

# Check what's on the FM-1
python3 tools/fm1_install.py --info
```

---

## Verifying the Firmware File

Before flashing, you can verify the firmware file integrity:

```bash
# On Mac/Linux
sha256sum release/jiant-v10.8.21-omer-features.fwsc

# Should output:
# 2ced83b091fa1b8a7f6efe5263581d56d0c3166aec54eeee32eba426dcf72a0b

# On Windows (PowerShell)
Get-FileHash release\jiant-v10.8.21-omer-features.fwsc -Algorithm SHA256
```

---

## Troubleshooting

### "Cannot find FM-1" or "Device not detected"

1. **Check USB cable**: Must be a data cable, not charging-only
2. **Try different USB port**: Some ports have better power/data
3. **Check driver**: On Windows, make sure USB MIDI drivers are installed
4. **Restart browser**: Close and reopen Chrome/Edge
5. **Try another browser**: Chrome on another computer if possible

### "Install failed" or error during flashing

1. **Power cycle FM-1**: Turn off, wait 10 seconds, turn on
2. **Check cable connection**: Ensure it's firmly plugged in
3. **Close other apps**: Close DAWs, MIDI apps that might be using the FM-1
4. **Try again**: Flashing can sometimes fail - retry once

### FM-1 won't start after flashing (black screen)

1. **Don't panic!** This is recoverable
2. **Check if computer sees "WL80UBOOT"** (device ID 4C4A:8057)
3. **Reflash**: Try flashing again - the bootloader should still work
4. **Last resort**: Use [FM-1 Transporter](https://github.com/kurogedelic/FM-1-transporter) for recovery

### Features aren't showing up

1. **Check version**: Power on FM-1, it should show version at boot
2. **Check GEN**: Hold HOME + press SELECT, turn KNOB 1 - "LANE 8" should be in the list
3. **Check CHORD**: Go to SCL > CHORD page - KNOB 4 should be "MODE" with OFF/MEMORY options

---

## Testing the New Features

### Test LANE 8 MODE:

1. Hold **HOME** button
2. Press **SELECT** button once
3. Turn **KNOB 1** (GENRE) until you see **"LANE 8"**
4. Press **OCT+** button (orange button, top right)
5. Wait 2-3 seconds
6. You should hear: pad + arp + kick playing!

### Test CHORD MEMORY:

1. Press and hold **SCL** button
2. Navigate to **CHORD** page (use KNOB or buttons)
3. Set **CHORD** (KNOB 1) to: **TRIAD** or **7TH**
4. Set **MODE** (KNOB 4) to: **MEMORY**
5. Release SCL button
6. Play any white key on the keyboard
7. Each key should play a full chord!

**Example** (in C Major scale):
- Press C = C major chord (C-E-G)
- Press D = D minor chord (D-F-A)
- Press E = E minor chord (E-G-B)
- Press F = F major chord (F-A-C)
- etc.

---

## Reverting to Official Firmware

If you want to go back to M-VAVE's official firmware:

1. Download official firmware from [M-VAVE Downloads](https://www.m-vave.com/download)
   - Look for FM-1 firmware V16 (or V15)
   - Unzip the download
   - Find `FM-1.fwsc` inside (should be 718,196 bytes for V16)

2. Use the same web installer:
   - Go to https://juanjiant-bit.github.io/JIANT/webapp/installer/
   - Scroll to "Return to official"
   - Select the official `FM-1.fwsc`
   - Click the button to flash it

3. Your custom firmware will be replaced with official M-VAVE firmware

---

## Support

If you have issues:

1. **Check the docs**: Read `docs/OMER-FEATURES.md` for feature usage
2. **Check GitHub issues**: See if others had the same problem
3. **Create an issue**: On the GitHub repository with:
   - What you tried
   - What error you got
   - Your operating system
   - Browser and version
   - Photos/videos if helpful

---

## Safety Notes

- ⚠️ **Back up before flashing** - cannot be stressed enough!
- ⚠️ **Custom firmware is at your own risk** - M-VAVE does not support it
- ⚠️ **Keep the official firmware file** - in case you need to revert
- ⚠️ **Don't disconnect during flashing** - can brick the device
- ✅ **Flashing is usually safe** - thousands have done it successfully
- ✅ **Recovery is possible** - even from most failures

---

**Last Updated**: 2026-11-24  
**Firmware Version**: V10.8.21+omer  
**Base Version**: JIANT V10.8.21
