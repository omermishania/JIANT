# Omer's Melodic House Features for JIANT

**For**: Omer (@omermishania), beginner producer making melodic house (Lane 8 style)  
**Goal**: Add four production-focused features to JIANT firmware

---

## Feature 1: LANE 8 MODE

**What it does**: One button press creates a melodic house starting point with:
- Warm pad track
- Plucky arp track  
- Soft four-on-the-floor kick (DRUM-X) with sidechain-style pumping
- Tempo: 120-124 BPM
- Uses current key/scale

**How to use**:
1. Hold **HOME**
2. Press **SELECT** to open GEN
3. Turn **KNOB 1** (GENRE) until you see **LANE8**
4. Press **OCT+** to generate

The firmware will create a complete melodic house project. You can undo with **GLO + G4**.

**What it sets up**:
- Track 1: ANALOG warm pad (saw waves, low-pass filter, long release)
- Track 2: PHASE plucky arp (fast attack, rhythmic 1/16 pattern)
- Track 3: DRUM-X kick (soft, four-on-the-floor pattern)
- Tracks 4-6: Empty (ready for your ideas)
- Master: DUCK enabled (kick sidechains other tracks)
- BPM: Random between 120-124
- Effects: Moderate reverb, subtle chorus

---

## Feature 2: CHORD MEMORY

**What it does**: Press one key and hear a full chord (triad or 7th) built on that scale degree.

**How to use**:
1. Go to **SCL** (hold SCL button)
2. Navigate to **CHORD** page
3. Set **CHRD** to: **TRIAD**, **7TH**, **ADD9**, **SUS2**, or **SUS4**
4. Set **MODE** to: **MEMORY** (new option)

Now when you play:
- Press **C** = plays I chord (C major triad in C major)
- Press **D** = plays ii chord (D minor triad in C major)
- Press **E** = plays iii chord (E minor triad in C major)
- etc.

Each key plays the chord built on that scale degree. Works with the sequencer - record single keys, hear full chords!

**Advanced**:
- **CLOSE**: Tight voicing
- **LEAD**: Smooth voice leading between chords
- **OPEN**: Wide voicing
- **+BASS**: Adds bass note

---

## Feature 3: BUILD/DROP

**What it does**: Hold a button to build tension (open filter, add reverb, riser sound), release for the drop.

**How to use** (Performance mode):
1. While playing, hold **FX** to see the FX layer
2. Press and **HOLD** the **BUILD** key (new: **A#5**, top-right black key)
3. While held:
   - Master DJ filter slowly opens (high-pass sweep)
   - Reverb size increases
   - Subtle riser effect builds
4. **Release** on the downbeat for the drop!
   - Everything snaps back instantly
   - Track sidechaining pumps harder

**Settings**:
- **FX + OCT+**: Switch build length between **8 BARS** and **16 BARS**
- Length is shown on screen while holding BUILD

**Recording**: The build/drop is recorded if REC is armed (as FX automation).

---

## Feature 4: FINISH-IT SONG MODE

**What it does**: Takes your loop (parts A-D) and auto-arranges them into a full song structure.

**How to use**:
1. Create your parts:
   - **Part A**: Main groove
   - **Part B**: Variation (optional)
   - **Part C**: Break/bridge (optional)
   - **Part D**: Build/climax (optional)
2. Hold **HOME**, go to **ARRANGE** page
3. Turn **KNOB 4** (FORM) to: **FINISH** (new option)
4. Turn **KNOB 3** (LENGTH) to: **SHORT** (3 min), **MEDIUM** (5 min), or **LONG** (7 min)
5. Press **OCT+** to generate arrangement

The firmware automatically creates:
- **Intro** (16-32 bars): Part A, no bass, soft kick
- **Build 1** (8-16 bars): Add bass, increase energy
- **Drop 1** (16-32 bars): Full Part A
- **Break** (16 bars): Part C (or stripped Part A), no kick
- **Build 2** (8 bars): Part D or buildup with filter
- **Drop 2** (32 bars): Full Part A/B
- **Outro** (16 bars): Part A, fade elements

**What gets automated**:
- Track mutes per section
- Filter movements
- Effect levels
- Transitions between sections

**To edit**: Go to **TIMELINE** page to see/adjust the arrangement.

---

## Implementation Notes

### CPU & RAM Safety
- All features use existing JIANT systems (GEN, chord engine, FX automation)
- LANE 8 MODE reuses GEN's voice allocation and mixing
- CHORD MEMORY extends existing chord code (minimal CPU)
- BUILD/DROP uses existing modulation matrix
- FINISH-IT reuses ARRANGE timeline logic

### Compatibility
- Old projects load normally (new features default to OFF)
- Save format stays compatible
- All features are optional/disabled by default

### How These Features Help Omer

**LANE 8 MODE**: 
- Defeats "blank canvas" syndrome
- Instant melodic house template
- Learn from pre-configured sounds

**CHORD MEMORY**:
- Play chords without music theory knowledge
- Focus on rhythm and emotion, not voicings
- Record chord progressions with one finger

**BUILD/DROP**:
- Perform like a DJ without complex automation
- Create tension and release naturally
- Record builds in real-time

**FINISH-IT SONG MODE**:
- Turn 8-bar loops into complete tracks
- Learn song structure from examples
- Export finished arrangements

---

## Technical Details (For Developers)

### Files Modified
- `firmware/src/gen.c` - Add LANE8 genre and preset templates
- `firmware/src/gen_tables.c` - LANE8 drum patterns, bass lines, harmonies
- `firmware/src/seq.c` - CHORD MEMORY mode in chord_build()
- `firmware/src/params.c` - Add P_CMODE parameter
- `firmware/src/fx.c` - BUILD/DROP automation hooks
- `firmware/src/perform.c` - BUILD key handling
- `firmware/src/song_main.c` - FINISH-IT arrangement generator
- `firmware/src/ui_*.c` - UI updates for new options

### New Parameters
- `P_CMODE`: Chord mode (OFF, CLOSE, OPEN, MEMORY) - uses FM op slot
- `G_BUILD`: Build/drop active state - uses existing FX automation slot

### Testing
- Unit tests for chord generation
- GEN regression test for LANE8
- Song arrangement validation
- CPU budget verification

---

## Build Instructions (For Omer)

1. **Prerequisites** (on Mac):
   ```bash
   pip3 install Pillow fonttools
   ```

2. **Get the toolchain**:
   ```bash
   cd /path/to/JIANT
   tools/get_toolchain.sh
   ```

3. **Get the SDK**:
   ```bash
   git clone --depth 1 --branch AC79NN_SDK_V1.2.1_2023-12-13 \
       https://gitee.com/Jieli-Tech/fw-AC79_AIoT_SDK.git ~/fw-AC79_AIoT_SDK
   ```

4. **Build**:
   ```bash
   ./build.sh
   ```
   
   The firmware file will be: `build/felucca.fwsc`

5. **Flash to FM-1**:
   - Open Chrome on your Mac
   - Go to: https://juanjiant-bit.github.io/JIANT/webapp/installer/
   - Connect FM-1 via USB
   - Click "INSTALL"
   - **OR** use custom firmware:
     - In installer, click "Advanced"
     - Select `build/felucca.fwsc`
     - Click "INSTALL CUSTOM"

6. **Verify**:
   - Power on FM-1
   - Hold HOME + press SELECT
   - Turn KNOB 1 - you should see **LANE8** in the genre list

---

## Troubleshooting

**"Build failed"**: Make sure Docker Desktop is running (needed for the JieLi toolchain)

**"Can't install firmware"**: 
- Use Chrome or Edge (not Safari, not Firefox)
- Try a different USB cable
- Hold POWER while plugging in USB (force bootloader mode)

**"LANE8 not in genre list"**:
- Make sure you flashed the custom firmware
- Try power-cycling the FM-1

**"Chords sound wrong"**:
- Check SCL > KEY is set to your song's key
- Check SCL > SCALE matches (probably MAJOR or MINOR)
- Make sure CHORD > MODE is set to MEMORY

---

*Last updated: 2026-11-24*  
*JIANT version: V10.8.21+omer-features*  
*License: GPL-3.0 (same as JIANT)*
