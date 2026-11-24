# Omer's Melodic House Features - CORRECTED User Guide

**Version**: V10.8.25+omer  
**All button steps verified against firmware source code with file:line citations**

---

## Feature 1: LANE 8 MODE ✅

**Exact Button Steps**:
```
1. Hold HOME button
2. While holding HOME, press SELECT button
3. Turn KNOB 1 (GENRE) → "LANE 8" appears last in list (position 46/46)
4. Press OCT+
```

**Citations**:
- `firmware/src/ui_input.c:2215` - HOME + SELECT opens GEN
- `firmware/src/gen.c:2708` - KNOB 1 (k==0) controls genre
- `firmware/src/gen_tables.c:585` - LANE 8 at array index 43 (last genre)
- `firmware/src/gen_tables.c:597` - GEN_NPOS = NGENRE + 2 (46 total: EXPLORE, RANDOM, 44 genres)

**Position**: LANE 8 is the LAST genre (turn KNOB 1 all the way right from EXPLORE)

---

## Feature 2: CHORD MEMORY ✅

**Exact Button Steps**:
```
1. Hold SCL button
2. Navigate to CHORD page (white keys move between pages)
3. KNOB 1 (CHORD) → TRIAD or 7TH
4. KNOB 2 (VOICING) → MEMORY (5th option: after CLOSE, LEAD, OPEN, +BASS)
```

**Citations**:
- `firmware/src/params.c:601` - CHORD page definition: P_CHRD, P_CVOI, P_CSTR, 0xFF
- `firmware/src/params.c:246` - N_CVOI[] = {"CLOSE", "LEAD", "OPEN", "+BASS", "MEMORY", 0}
- `firmware/src/params.c:248` - VOICING max=4 (5 values: 0-4)
- `firmware/src/seq.c:247` - enum CV_CLOSE, CV_LEAD, CV_OPEN, CV_BASS, CV_MEMORY
- `firmware/src/seq.c:268` - if (vc == CV_MEMORY && mode >= CD_TRI...)

**KNOB 2 is VOICING**, not "MODE on KNOB 4"!

---

## Feature 3: BUILD/DROP (Using Existing DJ FILTER)

**Exact Button Steps**:
```
1. Hold GLO button
2. Navigate to MIXER page (white keys move between pages)
3. Turn KNOB 4 (DJ FILTER):
   - Turn RIGHT = High-pass opens (builds tension)
   - Turn LEFT = Low-pass closes (darker)
   - CENTER = No filter (neutral)
4. For BUILD: Turn KNOB 4 gradually RIGHT over 8-16 bars
5. For DROP: Snap KNOB 4 to CENTER on downbeat!
```

**Citations**:
- `firmware/src/params.c:663` - MIXER page: FAM_TRK, comment says "GLO button"
- `firmware/src/ui_input.c:547` - "KNOB 4 the master DJ FILTER (G_DJF...)"
- `firmware/src/ui_input.c:556` - case 3: controls song.g[G_DJF] (slot 3 = KNOB 4)
- `firmware/src/core.h:159` - G_DJF comment: "GLO > MIXER KNOB 4"

**Location**: GLO > MIXER, KNOB 4 (NOT "FX KNOB 4"!)

---

## Feature 4: FINISH-IT (Using GEN FORM)

**Exact Button Steps**:
```
1. Hold HOME
2. While holding HOME, press SELECT (opens GEN)
3. On GEN page 1 (default page):
   - KNOB 1 (GENRE) → LANE 8 or any genre
   - KNOB 2 (SEED) → any number
   - KNOB 3 (ENERGY) → 50-70
   - KNOB 4 (FORM) → SONG
4. Press OCT+
```

**Citations**:
- `firmware/src/ui_input.c:2215` - HOME + SELECT opens GEN
- `firmware/src/gen.c:2676-2684` - gen_knob() on page 0: k==0 is genre, k==1 is seed, k==2 is energy, k==3 is form
- `firmware/src/gen.c:2710` - if (k==3u) displays GEN_FORM[gp.form % 3u]
- `firmware/src/gen.c:2695` - gen_page() returns gp.page % 3u (pages 0, 1, 2 = "GEN 1, 2, 3")
- `firmware/src/gen.c:1801-1806` - chain_config.row[rows] written with parts and bars

**FORM is on GEN page 1 (the default/first page), KNOB 4** - NOT "GEN 3"!

---

## SUMMARY OF CORRECTIONS

| Was Wrong | Now Correct | Citation |
|-----------|-------------|----------|
| "Press SELECT for GEN" | "HOME + SELECT" | `ui_input.c:2215` |
| "FX KNOB 4 for DJ FILTER" | "GLO > MIXER KNOB 4" | `params.c:663`, `ui_input.c:547` |
| "KNOB 4 MODE parameter" | "KNOB 2 VOICING = MEMORY" | `params.c:248`, `seq.c:247` |
| "GEN 3 page FORM" | "GEN page 1 KNOB 4" | `gen.c:2684`, `gen.c:2710` |
| "LANE 8 halfway through list" | "LANE 8 is LAST (46/46)" | `gen_tables.c:585-597` |

---

**Version**: V10.8.25+omer  
**SHA256**: `28647c16b9846306565ccd471f499fe7e02c3672226a87fbfa94d5c85b120a6a`  
**File**: `release/jiant-v10.8.25-omer-features.fwsc`  
**Date**: 2026-11-24
