# moments.md — Caps Swash Pairs: Style Bible + Moment Library

This file is the single source of truth for the Caps Swash Pairs caption style. Part 1 is the style bible (palette, type, layout, motion, footage rules, safe zones). Part 2 is the moment library. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel (one talking head, no cuts); values labelled "(design, not measured)" are the same grammar extended for common inputs. Frame fractions are of W and H; reference values in brackets are for 1080x1920. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while small, wide-tracked sans capitals orbit one huge italic serif keyword in the lower third, so every phrase reads as a tiny typographic poster: quiet caps, one loud swash word.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, keyword, side, accent).
4. Final video: build from the spec. Google Flow master prompt: use each moment's **Flow prompt text** (plain words, no px, %, hex or font names), filling its {{…}} placeholders.

Units: W, H, seconds. Reference values in brackets are for 1080x1920.

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Caps ink | #FFFFFF | All small capitals |
| Keyword ink | #FFFFFF at 98 % (reference showed it slightly translucent while arriving) | Giant italic keyword |
| Soft shadow | #000000 at 42 %, offset (0, +3 px), blur 5 px (at 720 W) | Under every text element; the only thing that keeps it legible on bright footage |
| Accent ✎ (parameter) | measured default: none (reference is white only). Design default for demos: any single hue, e.g. #FF5CAA | Optional tint of ONE keyword (payoff word) per video; K1 |

Brand swap rule: the accent is a parameter. Use at most one accent colour per video; never tint the small capitals. No background plates, boxes or strokes anywhere.

### 1.2 Containers / shapes

None. The footage is full-frame and untouched. Text sits directly on the footage with a soft shadow. No cards, boxes, underlines, outlines or bars.

### 1.3 Layout (pair block, bottom third)

| Element | Position (fractions) | Notes |
|---|---|---|
| Pre-caps row | centre y = 0.745H [1430]; left edge = keyword's left edge | Measured: caps row sits just above the keyword's ascenders, left-aligned with the keyword |
| Keyword | baseline y = 0.855H [1642]; centred on x = 0.50W | Measured: keyword baseline ≈ 0.89–0.92H in the reference; moved up 0.04H here to clear platform UI |
| Post-caps row | centre y = 0.905H [1738]; right edge = keyword's right edge (side R) or left edge = keyword's left edge (side L) ✎ | Measured: trailing caps tuck under the keyword's end |
| Solo caps line (C2) | centre y = 0.84H [1613]; centred on x = 0.50W | Measured: caps-only lines sit lower-middle, larger |
| Horizontal clamp | every row stays inside 0.07W–0.93W | Rows slide inward, never get cut |
| Title zone (T1, T2) | y 0.035–0.115H, centred | (design, not measured) above the face box, never touching it |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caps (pair block) | All caps, semibold, wide letter-spacing, white | Montserrat SemiBold (wght 600) | Josefin Sans SemiBold, Manrope SemiBold | 0.047W [51]; tracking +0.09em; word gap 0.033W [36] |
| Solo caps (C2) | same face, larger | Montserrat SemiBold | same | 0.069W [75]; tracking +0.10em; word gap 0.036W |
| Keyword | Lowercase high-contrast italic serif, medium weight, white | Playfair Display Italic (wght 500) | Bodoni Moda Italic, Instrument Serif Italic | 0.18W [195] (x-height about 0.09W); shrink in steps of 0.006W until width ≤ 0.84W; never below 0.083W |
| Title (T1) | (design) same italic serif, larger | Playfair Display Italic | same | 0.13W, one line ≤ 0.84W |
| Kicker (T2) | (design) same caps as pair block | Montserrat SemiBold | same | 0.040W; tracking +0.14em |

Case: caps rows are uppercased by the style (the user's words, converted); keywords keep the user's case (lowercase in practice). Punctuation stays (commas and full stops remain on whichever word carries them).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Keyword entrance | ease-out cubic (1−(1−t)³): alpha 0→1, rise 14 px → 0, scale 0.94 → 1 | 0.22 s (measured: the reference keyword fades in ghosted over 4–6 frames at 32 fps) |
| Caps word entrance | ease-out alpha ramp, 8 px rise (C2 only) | 0.10 s (C1 rows: alpha only) |
| Chunk exit | hard cut, whole block vanishes in one frame | 1 f |
| Block-to-block | hard cut; the next block starts on its first word's time | 0 f |

Words appear one by one on their spoken times and never move after appearing. Never: bounce, overshoot, slides, typing letter by letter, glow, outlines, boxes, scale pops, camera shake, flashes.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text overlay with soft shadow | Only the elements in this file |

Forbidden: crop, zoom, split, card, mask, blur, grade, speed change, retiming, reorder, background swap.

### 1.7 Safe zones

- Face box (x 0.34–0.66, y 0.15–0.40) always clear: pair block lives at y ≥ 0.70H; title zone at y ≤ 0.12H.
- Keep text inside 0.07W–0.93W. Keep the very bottom 0.05H free; keep the platform-watermark corner (x > 0.90W, y > 0.90H) free when the footage carries a sparkle or logo there: post-caps may stop short.
- Captions and titles never overlap: a title (T1/T2) must be gone, or end before the first pair block of the same time range begins, and never shares a frame with a pair block unless it is in the title zone (they are 0.6H apart).

## PART 2 — MOMENT LIBRARY

Families: C caption, K keyword, T title, E end. Energy: low / medium / high.

### C1 · PAIR BLOCK — C medium (signature)
**What it is:** the core caption: 1–4 small caps words sit above a giant italic keyword, and 0–2 caps words trail under it. Words appear on their own spoken times.
**Use when:** every phrase with one meaning-carrying noun or verb. **Avoid when:** the phrase has no strong word (use C2), or the keyword would exceed the width limit at 0.083W.
**Text (✎):** pre words (caps), keyword (as written), post words (caps), side L or R. Chunk 3–6 words in total, 0.9–2.0 s.
**Geometry / Graphics:** 1.3 and 1.4. Keyword width ≤ 0.84W; pre row left-aligned to the keyword's left edge; post row right-aligned (R) or left-aligned (L) to the keyword; clamp to 0.07–0.93W.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word time − 0 | each caps word | alpha | 0 → 1 over 0.10 s | ease-out |
| keyword time | keyword | alpha, y, scale | 0 → 1, +14 px → 0, 0.94 → 1 over 0.22 s | ease-out cubic |
| chunk end | whole block | alpha | 1 → 0 | hard cut |

**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption. Pre caps may wait alone (up to 1.0 s) before the keyword arrives; the keyword slot stays empty.
**Exit:** hard cut on the next chunk's first frame.
**Build notes:** draw caps and keyword at 2x, downscale, add the shadow (blur 5 px at 1x, 42 %). Lay the full row out before showing its first word so nothing moves. Measured on the demo: caps size 34 px, keyword 130 px (shrunk to fit), baseline y 1094, caps rows at y 954 and 1158 of 1280.
**Flow prompt text:** "A small row of white capital letters reading {{PRE WORDS}} appears word by word just above the lower chest, then the word {{KEYWORD}} fades in large in elegant white italic serif lettering right beneath it, and {{POST WORDS}} appears in small capitals tucked under the end of that word. The person and the scene are unchanged."
**Still-image state:** full block visible, keyword at full opacity.

### C2 · SOLO CAPS LINE — C medium (signature)
**What it is:** a phrase with no strong keyword shown as one larger caps line in the lower-middle area.
**Use when:** connective phrases, short sentences, rhythm resets between two C1 blocks. **Avoid when:** more than 24 characters (split it).
**Text (✎):** 1–4 words, ≤ 24 characters.
**Geometry / Graphics:** Montserrat SemiBold 0.069W, tracking +0.10em, centred at x 0.50W, y 0.84H.
**Motion:** each word alpha 0 → 1 and rise 8 px → 0, 0.12 s ease-out, on its spoken time; hard cut out.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** reduce the size in steps if the line passes 0.86W.
**Flow prompt text:** "Large white wide-spaced capital letters reading {{PHRASE}} appear word by word in the lower middle of the frame, then disappear together."
**Still-image state:** line fully visible.

### C3 · HERO KEYWORD — C high (extension in the same grammar, design not measured)
**What it is:** the keyword alone, with no caps rows, for a one-word beat.
**Use when:** a strong one-word payoff, a number, a name. Max 2 per video, ≥ 3 s apart. **Avoid when:** the word is already used in a neighbouring block.
**Text (✎):** one word.
**Geometry / Graphics:** keyword at 1.25× the C1 size (shrink to ≤ 0.84W), baseline y 0.84H, centred.
**Motion:** as C1 keyword entrance, 0.26 s.
**Footage / plate behaviour:** untouched.
**Exit:** hard cut.
**Flow prompt text:** "One word, {{WORD}}, fades in very large in white italic serif lettering in the lower part of the frame."
**Still-image state:** word visible.

### C4 · LEAD-IN CAPS — C low (extension in the same grammar, design not measured)
**What it is:** the pre-caps row alone during the first words of a C1 block, before its keyword arrives.
**Use when:** automatic: it is part of C1 whenever the keyword is not the first word. Listed so the plan keeps it deliberate.
**Geometry / Graphics:** identical to the C1 pre row. The keyword slot below stays empty; nothing shifts when the keyword lands.
**Motion:** as C1.
**Flow prompt text:** "Small white capital words build one by one in a row near the lower chest, leaving the space below them empty for one coming large word."

### K1 · ACCENT KEYWORD — K medium (extension in the same grammar, design not measured)
**What it is:** the payoff keyword of the whole video drawn in the accent colour.
**Use when:** the last line or the single most important word. Once per video. **Avoid when:** no clear payoff.
**Text (✎):** one keyword; accent colour ✎ (one hue, high saturation, never a hue already dominant in the footage's lower third).
**Geometry / Graphics:** C1 or C3 keyword with the fill replaced by the accent; the shadow stays black.
**Motion:** as C1.
**Flow prompt text:** "The final large italic word {{WORD}} appears in {{ACCENT COLOUR NAME}} instead of white."
**Still-image state:** word tinted.

### T1 · SWASH TITLE — T medium (extension in the same grammar, design not measured)
**What it is:** an opening title in the keyword's italic serif at the top of the frame, with a small caps kicker above it.
**Use when:** the video has a clear topic phrase in the user's own words; the first 2 s. **Avoid when:** the title zone would touch a face above y 0.13H, or the topic words are used in caption chunks (then move them out of the chunks and include them in the audit).
**Text (✎):** 1–3 words from the user's text (or the user's own title), lowercase.
**Geometry / Graphics:** italic serif 0.13W, centred x 0.50W, baseline y 0.105H; kicker (T2 style) at y 0.045H.
**Motion:** alpha 0 → 1 and rise 14 px → 0 over 0.25 s ease-out; hold ≥ 1.0 s; linear fade out 0.3 s. Never during a pair block's first 0.3 s.
**Footage / plate behaviour:** untouched.
**Exit:** fade, no movement.
**Flow prompt text:** "A short title, {{TITLE}}, fades in near the top of the frame in white italic serif lettering with a tiny caps line above it, then fades away."
**Still-image state:** title visible at the top.

### T2 · CAPS KICKER — T low (extension in the same grammar, design not measured)
**What it is:** one small tracked caps line in the title zone, for a section label or the speaker's topic.
**Use when:** a new section without a cut; ≤ 3 words. **Avoid when:** a pair block is on screen within the same 0.6 s.
**Text (✎):** 1–3 words.
**Geometry / Graphics:** Montserrat SemiBold 0.040W, tracking +0.14em, centred, y 0.06H.
**Motion:** alpha 0 → 1 over 0.15 s; hold 1.0–1.5 s; hard cut.
**Flow prompt text:** "A small row of white wide-spaced capital letters reading {{LABEL}} appears near the top centre, then disappears."

### E1 · CLOSING HOLD — E low (extension in the same grammar, design not measured)
**What it is:** the last pair block is held to the final frame with no exit.
**Use when:** every video's last block. **Avoid when:** the video continues after the speech with a long silent tail (then hard cut at speech end + 0.3 s).
**Motion:** none; it stays until the last frame.
**Flow prompt text:** "The last words stay on screen until the end of the clip."

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 on the topic noun | C1 per list item, C2 between, C3 once | K1 on the payoff + E1 |
| Single talking head | T1 + C1 | C1, C2 | K1 + E1 |
| B-roll only | C2 | C1 per shot (side L/R alternating) | E1 |
| Still image | T1 | C1 in settled state | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
