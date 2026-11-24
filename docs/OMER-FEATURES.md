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

## Feature 3: BUILD/DROP (Using Existing JIANT Features)

**Status**: Not implemented as a dedicated feature, but achievable using JIANT's existing performance tools.

### Method 1: Using DJ FILTER + MACROS (Recommended)

JIANT already has powerful performance controls perfect for build/drop moments:

**Live Performance**:
1. **Hold FX** to enter FX layer
2. **Turn KNOB 4** (the rightmost macro knob) = **DJ FILTER**
   - Turn LEFT = Low-pass filter closes (darker, building tension)
   - Turn RIGHT = High-pass filter opens (brighter, rising energy)
   - CENTER = No filter (the drop!)
3. **For the build**:
   - Gradually turn KNOB 4 to the RIGHT over 8-16 bars
   - Watch the knob position to time it
4. **For the drop**:
   - Snap KNOB 4 back to CENTER on the downbeat!

**Pro Tips**:
- The filter macro has a quick-snap feature: turn past center quickly and it snaps to fully open
- Combine with KNOB 3 (MUTATE) for pattern variation during build
- Use KNOB 1 (STEPS) to gradually reduce loop windows for tension

### Method 2: Using SWEEP Effects

**THROW Sweep** (FX Layer):
1. Hold **FX**
2. Press and hold **F#5** (top-right black key) = **THROW**
3. While held, reverb and delay sends gradually increase over 2 bars
4. Release for instant drop back to dry

**CRUSH Sweep** (FX Layer):
1. Hold **FX**
2. Press and hold **D#5** (second from top-right black key) = **CRUSH**
3. While held, bit crushing gradually increases (lo-fi effect builds)
4. Release on downbeat for clean drop

### Method 3: Record Automation

For repeatable builds:
1. Go to **HOME > TIMELINE**
2. Turn on **REC**
3. Play and perform your DJ FILTER or MACRO movements
4. It records as automation
5. Playback repeats your exact performance!

### Why This Works Better

JIANT's existing tools are **more flexible** than a fixed BUILD/DROP button would be:
- **Tempo-independent**: Build over any length (1 bar to 32 bars)
- **Multiple effects**: Choose filter, crush, reverb, or combine them
- **Performance control**: React to the moment, not locked to timing
- **Recordable**: Capture your exact moves for later

**Lane 8-Style Builds**:
- Use DJ FILTER gradually opening HIGH-PASS
- Combine with increasing REVERB (adjust on GLO > FX page before playing)
- Add MUTATE for pattern variation
- Drop with everything snapping back = instant energy!

---

## Feature 4: FINISH-IT SONG MODE (Using Existing GEN FORM)

**Status**: Not implemented as a separate mode, but JIANT's GEN FORM does exactly this!

### Using GEN FORM = SONG (The Built-In "Finish It" Feature)

JIANT already has automatic song arrangement in the generator:

**How to Auto-Arrange Your Music**:

1. **Create your starting loop** (using LANE 8 MODE or manually):
   - 8-16 bar loop in one project slot (usually A)
   - Can be just drums + bass, or full arrangement

2. **Open GEN**:
   - Hold **HOME**
   - Press **SELECT**

3. **Configure the generator**:
   - **KNOB 1 (GENRE)**: Select **LANE 8** (or any genre)
   - **KNOB 2 (SEED)**: Any number (each gives different variations)
   - **KNOB 3 (ENERGY)**: 50-70 for melodic house
   - Navigate to **GEN 3** page
   - **KNOB 4 (FORM)**: Turn to **SONG**

4. **Generate the full arrangement**:
   - Press **OCT+**
   - Wait 3-5 seconds
   - GEN creates a complete song structure with:
     - Intro (without full drums)
     - Build section
     - Drop (full energy)
     - Break section
     - Final build
     - Drop again
     - Outro

5. **View the arrangement**:
   - Go to **HOME > TIMELINE**
   - See the generated song structure
   - Each row is a section
   - Shows bars per section

6. **Edit it**:
   - On TIMELINE page
   - **KNOB 1**: Select row
   - **KNOB 2**: Move row
   - **KNOB 3**: Change which part (A/B/C/D) plays
   - **KNOB 4**: Adjust length in bars
   - **OCT+**: Add new row
   - **OCT-**: Delete row

### Manual Song Arrangement (More Control)

If you want to arrange by hand:

1. **Create your parts**:
   - **SAVE > PARTS**: Save to slots A, B, C, D
   - **Part A**: Main groove/drop
   - **Part B**: Variation or build
   - **Part C**: Break/bridge
   - **Part D**: Climax or outro

2. **Build the timeline**:
   - Go to **HOME > TIMELINE**
   - **OCT+** = Add new row
   - **KNOB 2** = Pick which part (A/B/C/D) for this row
   - **KNOB 4** = How many bars
   - Create structure like:
     - Row 1: Part A, 16 bars (intro)
     - Row 2: Part B, 8 bars (build)
     - Row 3: Part A, 32 bars (drop)
     - Row 4: Part C, 16 bars (break)
     - Row 5: Part B, 8 bars (build)
     - Row 6: Part A, 32 bars (drop)
     - Row 7: Part A, 16 bars (outro)

3. **Adjust track mutes per row**:
   - **KNOB 1**: Select row
   - Black keys: Toggle track mutes for that row
   - Example: Intro = mute bass and kick

4. **Play the song**:
   - Press **PLAY**
   - It plays through your arrangement!
   - Sections transition automatically

### Pro Workflow: Combine Both Methods

**Best approach for beginners**:

1. **Use LANE 8 MODE** to generate initial loop
2. **Use GEN FORM = SONG** to generate full arrangement
3. **Go to TIMELINE** and tweak:
   - Adjust section lengths
   - Change which part plays where
   - Add/remove sections
   - Fine-tune the structure

This gives you:
- ✅ Starting point from generator (LANE 8)
- ✅ Full song structure from GEN FORM
- ✅ Manual control to perfect it

**Lane 8-Style Song Structure**:

```
Intro    (16 bars): Part A, kick only, no bass
Build 1  (8 bars):  Part A, add bass + pad
Drop 1   (32 bars): Part A, full energy
Break    (16 bars): Part C, no kick, pads + arp only
Build 2  (16 bars): Part B, add filter sweep + build drums
Drop 2   (32 bars): Part A, full energy with variations
Outro    (16 bars): Part A, gradually mute tracks
```

Create this in TIMELINE with the row controls described above!

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
