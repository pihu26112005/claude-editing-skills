# moments.md — Whisper Blob: Style Bible + Moment Library

This file is the single source of truth for the Whisper Blob caption system. Part 1 is the style bible, Part 2 the moment library, Part 3 starting combinations. SKILL.md tells Claude how to pick and place moments. The look was measured on a 360x640, 32 fps, 7.25 s single-shot talking-head reference (no cuts); cut behaviour, the bottom-lane/top-lane switch and the second warp are design extensions, labelled "(design, not measured)".

**The look in one line:** the footage stays untouched while each phrase is split into a tiny hand-brushed white whisper line and one fat, rounded, saturated keyword that rises in under it, bent into an arch or a wave and sitting on a solid dark drop-slab, hopping between a top and a bottom lane so it never touches the face.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text**, filling its {{…}} placeholders.

Units: W, H, seconds (s). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Whisper white | #FFFFFF | Small script words, white keywords |
| Keyword accent A (parameter) | #A6F01E lime (measured, reference default); demo uses #FF8A1F orange | Keyword colour 1 |
| Keyword accent B (parameter) | #FF4FA0 pink (measured default); demo uses #2FD3FF cyan | Keyword colour 2 |
| Slab | #160E28 | Solid drop-slab under every glyph (design, not measured: the reference used a soft shadow) |
| Soft shadow | #000000 at 50 % | Blur 0.007W behind the slab |

Brand-swap rule: replace accents A and B with the user's colours (saturated, bright, readable on mid-tone footage). White and the slab never change. A keyword is one flat colour, never a gradient, never outline-only.

### 1.2 Containers / shapes

Footage is always full frame, 100 %, untouched. No cards, boxes, plates or tints. The only shape is the slab: each glyph is duplicated in #160E28 offset (+0.7 × s, +1 × s) with s = 0.045 × font size, drawn solid under the colour fill.

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Side margin | text edges ≥ 0.06W [65] left and right (never < 0.05W) | Always |
| Bottom lane | whisper line top y = 0.545H; keyword top = whisper bottom + 0.004H; keyword bottom ≤ ~0.70H | Shots with a face in the top 0.40H (default for speaker shots) |
| Top lane | whisper line top y = 0.062H; keyword below it, bottom ≤ 0.35H | Shots with no face, or face low in the frame (B-roll, hands, products) |
| Alignment | even chunks left-aligned at 0.06W, odd chunks right-aligned at 0.94W (design, not measured; the reference was left-aligned) | Whisper and keyword of one chunk share the same edge |

The reference placed the lane above the face for the first phrases (y 0.04–0.27H) and below it (y 0.55–0.72H) for later ones.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Fat rounded display, mixed case as written, tight, bent by a warp (1.5) | Paytone One | Lilita One, Baloo 2 ExtraBold | up to 0.19W [205]; shrink in 4 px steps until width ≤ 0.88W |
| Whisper | Hand-brushed script, white, sheared italic (−0.18), tilted +2° | Caveat Brush | Gochi Hand, Gaegu Bold | 0.085W [92] |
| Display keyword (white variant) | same as keyword, #FFFFFF fill | Paytone One | Lilita One | same |

Rules: case exactly as the user wrote it (the reference used capitals on keywords; this skill does not force them). No outline-only text. Keywords are at most 2 words per chunk and stay on one line.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Keyword entrance | rise from +0.035H to 0, ease-out cubic, alpha 0→1 over 0.6 of the time | 0.24 s |
| Whisper word entrance | rise from +0.008H to 0, alpha 0→1, ease-out cubic | 0.14 s |
| Chunk exit | hard cut, next chunk starts the same frame | 1 frame |
| Warp | static per chunk (arch or wave), baked into the glyph shapes | — |
| Tilt | keyword tilted +2.5° on left-aligned chunks, −2.5° on right-aligned | — |

Never: horizontal slides that leave the frame (the reference keyword slid in from the left edge; this skill rises instead so text never crosses the 0.05W margin), bounce, shake, outline-only text, letter-by-letter typing, glitch, colour changes on a word already shown.

### 1.6 What may happen to the user's footage

Full-frame display untouched. Text and shadows only. Forbidden: replacing, retiming, trimming, blurring, grading, zooming, cards, splits, background swaps, adding footage. Primary footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face box | No glyph or slab inside the speaking face. Bottom lane only when keyword top ≥ 0.43H and the face bottom is above that; top lane only when keyword bottom ≤ 0.35H and the face is below it. If both fail, use the lane with less overlap and shrink to 0.14W |
| Edges | Every glyph, slab and shadow ≥ 0.05W from the sides, assert in code |
| Overlap | Whisper line sits fully above its keyword; one chunk on screen at a time |
| Bright footage | The slab keeps white and cyan readable; do not drop it |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **T** title · **K** keyword · **E** end. Energy: ● calm · ●● medium · ●●● high.

### C1 · WHISPER LINE — C ● (signature)
**What it is:** the small connective words of a phrase appear one by one in a hand-brushed white script line above the keyword.
**Use when:** every phrase with connective words. **Avoid when:** the phrase is only keywords (skip the line).
**Text (✎):** the user's non-keyword words, in spoken order, as written.
**Geometry / Graphics:** Whisper font 0.085W, word gap 0.022W, line top per lane (1.3), edge per alignment (1.3), slab + soft shadow.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | whisper word | alpha, y | 0 → 1, +0.008H → 0 over 0.14 s | ease-out |
| chunk end ✎ | whole chunk | alpha | 1 → 0 | hard cut |

**Footage:** untouched. **Captions during it:** with C2. **Exit:** hard cut.
**Build notes:** render each word at 2× with Pillow, shear with an AFFINE transform, rotate 2°, downscale; lay the whole line out before the first word appears so no word moves.
**Flow prompt text:** "Small connective words, {{WHISPER_WORDS}}, appear one at a time in tiny white hand-brushed lettering above the big word, each rising slightly while it fades in."
**Still-image state:** the full line.

### C2 · BLOB KEYWORD — C ●● (signature)
**What it is:** one meaning-carrying word (or two) in a fat rounded saturated face rises in under the whisper line on a solid dark slab.
**Use when:** every chunk, 1 keyword per chunk (2 words for a pair like "what's left."). **Avoid when:** the word is an article or preposition.
**Text (✎):** 1–2 meaning words, ≤ 12 characters in total per line.
**Geometry / Graphics:** font up to 0.19W, auto-shrunk to ≤ 0.88W wide, colour accent A, accent B or white, slab 0.045 × size, tilt ±2.5°, warp per C3/C4. Colour order: accent A, white, accent B repeating; payoff in accent B.
**Motion:** rises +0.035H → 0 over 0.24 s ease-out, alpha ×1.6 ramp; starts at the keyword's spoken start; hard cut at chunk end.
**Footage:** untouched. **Captions during it:** C1 above it. **Exit:** hard cut.
**Flow prompt text:** "One important word, {{KEYWORD}}, appears in huge fat rounded {{COLOUR}} lettering with a dark solid shadow, bent slightly, rising up into place under the small white words."
**Still-image state:** the keyword.

### C3 · ARCH BEND — C ●● (signature, measured on the reference)
**What it is:** the keyword's baseline bulges upward in the middle like a rainbow.
**Geometry:** per-column vertical shift dy = −0.16 × size × (1 − (2u−1)²), u = 0..1 across the word. **Use when:** alternate chunks (even chunks in the demo). **Text (✎):** none. **Motion:** static. **Exit:** with its chunk.
**Flow prompt text:** "The big word is curved upward in the middle like an arch."

### C4 · WAVE BEND — C ●● (design, not measured)
**What it is:** the keyword ripples: one hump up, one down.
**Geometry:** dy = +0.06 × size × sin(2πu). **Use when:** odd chunks, for variety against C3. **Motion:** static.
**Flow prompt text:** "The big word waves gently, one hump up and one down."

### K1 · SOLO PAYOFF — K ●●● (signature)
**What it is:** the last or most important word alone, no whisper line, at the largest size.
**Use when:** the payoff or last line; at most 2 per video, ≥ 3 s apart. **Text (✎):** one word.
**Geometry:** font 0.19W, accent B, arch bend, lane per shot. **Motion:** as C2. **Hold:** 0.5–0.9 s, ends with the speech.
**Flow prompt text:** "The final word, {{WORD}}, appears alone in the largest size, arched, in bright {{COLOUR}} with a dark solid shadow."

### K2 · PAIR KEYWORD — K ●● (measured: a two-word stack)
**What it is:** two meaning words on one line, both in the same colour, shrunk to fit 0.88W.
**Use when:** a natural pair ("one year", "what's left."). **Text (✎):** 2 words.
**Motion:** both words appear together at the first word's start. (The reference stacked two lines; on a 9:16 face-safe lane one line is used.)
**Flow prompt text:** "Two important words appear together on one line in huge rounded lettering."

### C5 · LANE HOP — C ●● (design, not measured)
**What it is:** when the footage cuts to a shot where the current lane covers the subject, the caption jumps to the other lane on the cut frame, with no animation.
**Use when:** every cut; also at any change of face position. **Text (✎):** none. **Motion:** the chunk keeps its state (no re-entrance); position changes on the cut frame only.
**Flow prompt text:** "At each cut the captions jump to the top or the bottom of the frame, whichever keeps clear of the person, with no effect."

### T1 · BLOB TITLE — T ●● (design, not measured)
**What it is:** an opening topic title, 1–2 words, in the keyword style at 0.17W, arched, accent A, in the top lane with its whisper line replaced by nothing.
**Use when:** the opening line names the topic and the face box is below 0.30H or a bottom lane is available. **Avoid when:** the face is in the title lane (use the bottom lane).
**Text (✎):** 1–2 of the user's words. **Motion:** C2 entrance; hold 1.0–1.4 s; hard cut to the first chunk (never overlaps another chunk).
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, appears in fat rounded arched lettering."

### E1 · END HOLD — E ● (design, not measured)
**What it is:** the last chunk holds until the speech ends + 0.2 s, then the frame is clean for the last ≥ 0.2 s.
**Text (✎):** the last chunk. **Motion:** hard cut at the end. **Flow prompt text:** "The last caption stays until the speaker stops, then the picture finishes clean."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 + C2 from the first word | C3/C4 alternating, C5 on each cut, K2 for a pair | K1 + E1 |
| Single talking head | T1 + C1/C2 | alternate C3/C4, one K1 | K1 + E1 |
| B-roll only, no speech | C2 phrases (no whisper) | C5 per cut | E1 |
| Still image + text | one chunk settled (C1 + C2) | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Lanes used: bottom on shots 1, 4, 6 (faces), top on shots 2, 3, 5.
- 11 chunks; keyword colours orange / white / cyan repeating; payoff "happens." cyan.
- Keyword rise 0.24 s; whisper word 0.14 s; whisper 0.085W (the first 0.075W was too small to read); slide-in from the left was dropped because it crosses the side margin.
- Chunk "investments," was ended on the cut frame 4.917 s; "more." and "what's left." and the "Do it for one year" chunks cross a cut and hop lanes on the cut frame.
- Render asserts: all glyph bboxes inside 0.05W..0.95W; bottom-lane keyword top ≥ 0.43H; top-lane bottom ≤ 0.35H.
