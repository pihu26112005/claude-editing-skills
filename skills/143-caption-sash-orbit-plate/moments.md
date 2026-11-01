# moments.md — Sash Orbit Plate: Style Bible + Moment Library

This file is the single source of truth for the Sash Orbit Plate caption style. Part 1 is the style bible, Part 2 the moment library, Part 3 starting combinations. Values marked "measured" come from a 720x1280, 24 fps, 8.1 s reference reel of one talking head; everything marked "(design, not measured)" was tuned on a 720x1280, 24 fps, 10 s demo clip. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while a glossy curved sash orbits the speaker (back half tucked behind the head, front half crossing the chest) carrying a tracked uppercase title, and every other line sits on a small dark rounded plate with a thin accent border, white words that brighten as they are spoken and one accent-coloured word.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text**, filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Sash light | #EBCE92 (measured, champagne) | Upper edge of the sash gradient |
| Sash deep | #C8A06E (measured) | Lower edge |
| Sash text | #2A1E0C (measured, near black) | Title letters |
| Plate fill | #14110A at 88 % (measured) | Caption plate |
| Accent | measured: gold #DAA24D | Accent word, plate border, underline |
| Caption | #FFFFFF | Spoken words (unspoken words at 38 % opacity) |

Brand-swap rule: the accent is a parameter ✎ (one hue for sash, border and accent word; sash gradient light edge → deep edge of that hue). Demo uses teal: sash #96F2E6 → #1EA094, text #0A2826, accent #3FD6C6.

### 1.2 Containers / shapes

- **Sash:** a band half-width 0.04H (51 px at 720x1280, band 0.08H tall) following a tilted ellipse around the speaker; back half (top arc) drawn darker (×0.82), front half (bottom arc) with a soft shadow (offset 0.008H, blur 14 px, 45 %); two thin light pinstripes at ±0.78 of the half-width; 14-step gradient across the width, lightest at 0.35 of the width.
- **Plate:** rounded rectangle, radius 26 px, fill 88 % dark, 2 px accent border at 59 %, a 5 px solid accent line along the bottom edge inset 14 px from each corner. Width = text width + 2 × 0.055W; height = lines × 72 px + 52 px.
- Footage is always full frame and untouched.

### 1.3 Layouts

| Layout | Geometry | Use |
|---|---|---|
| Sash ring (design, tuned on demo) | ellipse centre (0.50W, 0.367H), rx 0.806W, ry 0.293H, tilted +5° clockwise; top arc centreline at about y 0.055H at the middle, bottom arc about 0.65H | Person shots; face box stays clear |
| Plate low lane | plate centre y = 0.795H, centred x, bottom ≤ 0.90H | Default for all plates |
| Plate top lane | centre y = 0.20H | When a face is low |

Text safe: every glyph and plate inside 0.05W side margins.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Sash title | Extra bold uppercase, tracking 0.16 em, placed glyph by glyph along the band centreline | Inter weight 800 | Roboto Bold, Archivo | 40 px at 720 wide, shrunk until the line is ≤ 0.74W |
| Plate caption | Bold sans, mixed case as written, centred, line pitch 72 px | Inter weight 700 | Roboto Bold, Plus Jakarta Sans | 58 px [87]; one or two lines, ≤ 0.62W for one line |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Sash band | wipes in left to right across the frame, 0.45 s, ease-out cubic, soft 40 px edge; top half first, bottom half 0.45 s later |
| Sash exit | wipes out left to right over 0.28 s, ending ≥ 0.05 s before a cut |
| Plate | fade-in 0.12 s; fade-out 0.10 s |
| Words | each word 38 % → 100 % over 0.20 s at its spoken time; layout fixed first |
| Never | bounce, overshoot, letter typing, scale pops, glitch, shake, flashes, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: overlays, and a person mask (confidence mask from a selfie segmenter, EMA 0.6 / 0.4, blur 1.5 px) that hides the sash's back half where the person is. Forbidden: any change to the footage itself.

### 1.7 Safe zones

- Face box (x 0.34–0.66, y 0.15–0.40) receives no sash pixels in front of the person and no text.
- Sash text on the back half keeps ≥ 85 % of its glyph pixels visible (assert; demo 100 %).
- Text and plates inside 0.05W side margins; plates never below 0.90H.
- Two chunks never visible on the same frame (assert).

---

## PART 2 — MOMENT LIBRARY

Family codes: T title, C caption, E end. Energy: low / medium / high.

### T1 · ORBIT SASH TITLE — T high (signature, measured look, design motion)
**What it is:** the sash wipes in around the speaker, top half behind the head with the first half of the line, then the bottom half across the chest with the rest, held, then wipes out.
**Use when:** a person shot opens (or closes) with a strong line. **Avoid when:** the shot has no person, the head top is above 0.10H, or a cut is within 1.7 s.
**Text (✎):** 3–6 words from the user's line, uppercase, split in two (top ≤ 18 characters, bottom ≤ 19).
**Geometry:** ring 1.3; type 1.4; both halves keep text ≥ 0.05W from the edges.
**Motion:** top band in at chunk start (0.45 s); bottom band in 0.45–0.65 s later (at its first word); hold; exit 0.28 s.
**Footage behaviour:** untouched; face visible from frame 0; the top half passes behind hair and head.
**Captions during it:** none (the sash is the caption).
**Exit:** wipe out.
**Build notes:** pre-render each half as RGBA at 2x (polygon stripes along the ellipse offsets, glyph tiles rotated to the tangent), shadow for the bottom half; per frame composite top half, re-paste the person by mask, then the bottom half.
**Flow prompt text:** "A glossy {{ACCENT}} sash curves around the speaker like an orbit: its upper half passes behind the head and carries the tracked capital words '{{TOP}}', its lower half crosses in front of the chest with '{{BOTTOM}}'. It sweeps in from the left, holds, and sweeps out. The face stays clear."
**Still-image state:** both halves fully in.

### C1 · ACCENT PLATE — C medium (signature, measured)
**What it is:** a small dark rounded plate in the low lane with one or two lines of bold white words that brighten as they are spoken, one word in the accent colour, an accent line along the plate's bottom edge.
**Use when:** any spoken line outside a title; always on bright or busy shots.
**Text (✎):** 2–5 words (as written), 1 accent word (key noun or verb).
**Geometry:** plate 1.2; type 1.4; lane low.
**Motion:** 1.5. Chunk 0.9–1.7 s.
**Flow prompt text:** "A small dark rounded plate with a thin {{ACCENT}} border sits low in the frame; the words '{{LINE}}' brighten one by one as spoken, and '{{WORD}}' is {{ACCENT}}."
**Still-image state:** all words bright.

### C2 · BARE ACCENT LINE — C medium (measured, not used in demo)
**What it is:** the C1 text with no plate: white words with a soft shadow (black 90 / 100 / 80 % stack) and a short accent underline bar (0.125W × 4 px) 14 px below the last line.
**Use when:** dark or calm shots (lane luminance < 0.35) with room above 0.70H. **Avoid when:** bright footage (use C1).
**Geometry:** same positions as C1; underline centred.
**Flow prompt text:** "White bold words '{{LINE}}' brighten one by one low in the frame, '{{WORD}}' in {{ACCENT}}, with a short {{ACCENT}} line beneath."

### C3 · TOP PLATE — C medium (extension in the same grammar)
**What it is:** C1 at the top lane (centre y 0.20H), for shots where the lower half holds a face or the action. **Motion/Exit:** as C1.
**Flow prompt text:** "The same dark plate sits near the top of the frame with the words '{{LINE}}'."

### E1 · CLOSING SASH — E high (extension in the same grammar)
**What it is:** T1 used for the last line, held to 0.3 s before the end of the speech, exiting before the clip ends. Same spec as T1.
**Flow prompt text:** "For the last line the sash sweeps around the speaker again with '{{TOP}}' above and '{{BOTTOM}}' below, then sweeps out."

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | C1 on every B-roll line | E1 |
| Single talking head | T1 | C2 / C1, C3 | E1 |
| B-roll only | C1 | C1, C3 | C1 |
| Still image | T1 settled or C1 | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Ring centre (360, 470) px, rx 580, ry 375, tilt 5°, half-width 51 px; sash text 40 px tracked 0.16 em; plate text 58 px, pitch 72, plate centre y 1018 px (0.795H). Chunks: T1 0.10–1.80 (top band in 0.10, bottom band in 0.75, exit 1.50–1.78); C1 2.10–3.15 (accent "first,"); 3.25–4.85 ("investments,"); 4.95–6.55 ("left."); 6.90–8.30 ("year"); E1 8.45–9.85 (top in 8.45, bottom in 8.90, exit 9.55–9.85). All B-roll shots were bright, so C1 plates were used throughout.
