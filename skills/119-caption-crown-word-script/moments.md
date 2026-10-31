# moments.md — Crown Word Script: Style Bible + Moment Library

This file is the single source of truth for the Crown Word Script caption style. Part 1 is the style bible, Part 2 the moment library, Part 3 starting combinations. Values come from a 360x640, 24 fps, 4.0 s reference (one talking head, no cuts) converted to fractions; items labelled "(design, not measured)" are designed in the same grammar.

**The look in one line:** the footage stays clean while one heavy condensed uppercase keyword with a thick black outline pops in above the speaker's head, and white flowing script captions with a thin black outline build word by word at the lower left.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎.
4. Final video → build from the spec. Flow master prompt → use each moment's Flow prompt text, filling {{…}}.

Units: W, H, seconds (s). The reference ran at 24 fps. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Crown fill (default, measured median) | #FCC73B warm yellow | Crown words. Parameter: the accent; any saturated colour works (the public demo uses #FF3E9A) |
| Outline | #000000 | Crown outline, script outline |
| Script fill | #FFFFFF | Script captions |
| Ghost word | grey ≈ #969696 at 35 % alpha | First frames of a new script word |
| Shadow | #000000 at 45 % | Soft shadow under crown and script |

Brand-swap rule: the user's colour replaces the crown fill only. White script and black outlines never change.

### 1.2 Containers / shapes

None. Footage is full frame, untouched. No plates, boxes or cards behind text.

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Crown band | y 0.134–0.223H [257–428] on the reference (sitting on the hair top); centre x 0.50W; max width 0.62W [670] (measured 0.24–0.50W for 5–9 letters) | T1 default. Demo2 adaptation: band y 0.035–0.115H, centre y 0.075H, because the head top was at 0.09–0.15H |
| Script lane | baseline 0.805H [1546]; x-height band 0.755–0.82H (measured 0.752–0.82H) | C1 |
| Script x anchors | left edge 0.08W [86] on even chunks, 0.14W [151] on odd chunks (measured 0.08–0.22W); right edge ≤ 0.94W | C1, C2 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Crown word | Heavy condensed grotesque, UPPERCASE, outline 0.008W each side, tight spacing | Anton | Bebas Neue, Archivo ExtraCondensed Black | Cap height ≈ 0.045H; font ≈ 88 px at W 720; shrink until the word ≤ 0.62W |
| Script caption | Flowing connected brush script, bold, mixed case as written, white, outline 3.2 px at W 720 | Dancing Script Bold (wght 700) | Pacifico, Kaushan Script, Sriracha | Font ≈ 70 px at W 720 (≈ 0.097W); shrink in 2 px steps until the chunk ≤ 0.84W |

Word space in script = 0.9 × the font's space width. Rule: crown words are UPPERCASE; script keeps the user's case.

Soft shadow under both: offset (0, +3 px at W 720), blur 4 px, #000000 at 45 %.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Crown pop-in (measured: full width within 2 frames) | ease-out cubic, scale 0.82 → 1.00, alpha 0 → 1 over 0.083 s | 0.125 s |
| Crown swap | hard cut to the next word after a 0.1–0.25 s gap (measured gap 4 f ≈ 0.17 s) | 0 f |
| Crown exit | linear alpha fade, no movement (measured: 4–5 f, the fill fades to a ghost with the outline last) | 0.21 s |
| Script word entrance | ghost (alpha 0.35, grey 150) → full white, ease-out | 0.17 s |
| Script chunk exit | hard cut | 1 f |

Never: slides, bounce, typing letter by letter, rotation, boxes, flashes, effects on cuts.

### 1.6 What may happen to the user's footage

Full-frame display only; text and shadow overlays. Forbidden: replacing, retiming, trimming, reordering, blur, glitch, zoom, colour grading. Footage is never hidden or darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Head and face | Crown band bottom edge ≥ 0.02H above the head top. If the head top is above 0.11H, drop the crown to a smaller size (cap height 0.035H) or use T4. Script never covers a speaking mouth: default lane 0.755–0.82H is below the chin on talking heads. |
| Script lane | If the face bottom edge is below 0.74H, raise the lane (baseline min 0.70H) or move to the side away from the mouth. |
| Edges | Every glyph ≥ 0.06W from left and right. |
| Footage text | If readable footage text sits in the lane for > 1 s, shift the lane up by 0.08H. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title (crown) · **C** caption · **K** keyword accent · **E** end. Energy: ● calm · ●● medium · ●●● high.

### T1 · CROWN WORD POP — T ●●● (signature)
**What it is:** one keyword in heavy condensed capitals with a thick black outline snaps in above the head, holds, then is replaced by the next keyword.
**Use when:** a theme, turn, step or payoff word is spoken. **Avoid when:** the head top is above 0.04H.
**Text (✎):** one user word, UPPERCASE, ≤ 12 characters. Start ✎ = the word's spoken start (reference: 0.46 s after speech start). Hold ✎ 0.7–1.6 s (reference holds 1.1 s, 1.1 s, 0.96 s).
**Geometry / Graphics:** Crown band, centre x ✎ (0.50W default), fill = accent, outline 0.008W, shadow per 1.4.
**Motion (measured, 24 fps):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start ✎ | crown | alpha / scale | 0 → 1 over 0.083 s; 0.82 → 1.00 over 0.125 s | ease-out cubic |
| start + 0.125 → end − 0.21 | crown | hold | final state | — |
| end ✎ − 0.21 → end | crown | alpha | 1 → 0 | linear |

**Footage behaviour:** untouched. **Captions during it:** C1 runs below. **Exit:** T2 fade or hard swap (T3).
**Build notes:** render the word once at 2× with Pillow (`stroke_width` 6 at 2×, then the shadow from a blurred alpha copy), resize by scale per frame, composite centred on (cx, 0.075H) in the demo2 adaptation.
**Flow prompt text:** "Above the speaker's head, the word {{WORD}} pops in written in thick bold condensed capital letters with a heavy black outline in {{ACCENT_COLOUR}}, stays for about a second, then fades away. It never covers the face."
**Still-image state:** the word at full scale above the head.

### C1 · SCRIPT BUILD CAPTION — C ●● (signature, the caption system)
**What it is:** a phrase builds word by word on one line at the lower left in white brush script with a thin black outline. Each word first shows as a faint grey ghost, then turns full white. Earlier words stay still.
**Use when:** always on spoken phrases. **Avoid when:** the lane covers a mouth (shift per 1.7).
**Text (✎):** the user's exact words, case as written; 3–5 words per chunk, one line, ≤ 0.84W; split at punctuation; never end on an article, preposition or conjunction. Chunk length 0.8–1.7 s.
**Geometry / Graphics:** Script lane, x anchor per 1.3 (C2 alternation), the whole chunk laid out before its first word so no word moves.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha, grey | 0.35 → 1, grey 150 → 255 | ease-out, 0.17 s |
| chunk end ✎ | whole chunk | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Reference words appeared every ~0.3 s; chunk end = next chunk's first word, or last word end + 0.4 s.
**Footage behaviour:** untouched.
**Build notes:** Dancing Script variable font, `set_variation_by_axes([700])`; draw each word with `stroke_width` 3.2 px and `anchor="ls"` at the shared baseline; shadow per 1.4.
**Flow prompt text:** "In the lower left of the frame, captions build word by word in flowing white handwritten-style lettering with a thin black outline. Each new word fades in from a faint grey to white in place. When a phrase is complete it is replaced at once by the next phrase. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### T2 · CROWN SOFT EXIT — T ● (signature)
**What it is:** the crown word fades out in place over about 0.2 s before the next word or at the end of the hold.
**Use when:** after every crown word that is not followed directly by another (and at the very end). **Avoid when:** a hard swap (T3) is wanted.
**Text (✎):** none. **Geometry:** as T1.
**Motion:** alpha 1 → 0, linear, 0.21 s, no movement; ends ≥ 0.1 s before the next crown pop.
**Exit:** gone. **Flow prompt text:** "The word fades away softly in place without moving."

### T3 · CROWN RELAY — T ●●● (design, not measured; extends the measured 0.17 s gap)
**What it is:** several crown words follow each other in the same spot with a 0.1–0.25 s empty gap, one per step of a list.
**Use when:** 3+ parallel phrases or a fast listing. **Avoid when:** words are shorter than 0.7 s apart.
**Text (✎):** one word per step. **Motion:** each word is a T1 + T2 with the gap; centre stays fixed.
**Flow prompt text:** "One after another, the words {{WORDS}} appear in the same spot above the head, each popping in, holding briefly and fading, with a tiny pause between them."

### T4 · SIDE CROWN — T ●● (design, not measured)
**What it is:** T1 shifted sideways, to 0.27W or 0.73W, when the head sits high or off centre.
**Use when:** the shot's head top is above 0.11H or the head is on one side. **Text (✎):** one word; centre x ✎ on the side away from the head. **Motion:** as T1. Keep ≥ 0.06W from the edge.
**Flow prompt text:** "The word {{WORD}} pops in above and to the {{SIDE}} of the head, away from the face."

### C2 · SCRIPT ANCHOR SHIFT — C ● (measured: chunks started at 0.08W, 0.14W, 0.22W)
**What it is:** the left edge of the script alternates between 0.08W and 0.14W from chunk to chunk so the caption does not look pinned.
**Use when:** always with C1. **Text (✎):** none. **Rule:** clamp so the right edge ≤ 0.94W.

### C3 · SOLO SCRIPT LINE — C ●●● (design, not measured)
**What it is:** a one- or two-word payoff shown alone at 1.3× the script size at the lane.
**Use when:** the last words or a strong turn. Max 2 per video, ≥ 3 s apart. **Text (✎):** the user's words, as written (not repeated in a crown word at the same time). **Motion:** C1 entrance, hold 0.6–1.0 s, hard cut.
**Flow prompt text:** "One short phrase, {{WORDS}}, appears alone and larger in the same white script lettering, then is replaced."

### K1 · ACCENT SCRIPT WORD — K ●● (design, not measured)
**What it is:** one word of a chunk coloured in the accent (with the same black outline) instead of white.
**Use when:** a chunk contains the key number or name and no crown word is up. Max 1 per chunk, ≤ 2 per video. **Text (✎):** one word.
**Flow prompt text:** "One word of the caption, {{WORD}}, is written in {{ACCENT_COLOUR}} instead of white."

### E1 · END HOLD — E ● (design, not measured)
**What it is:** the last chunk holds until min(last word end + 0.4 s, end − 0.25 s); the last crown word fades ≥ 0.1 s before the end; the picture ends clean.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 on the topic word + C1 | T3 on a list, T1 per phrase, T4 when the head moves | T1 on the payoff word + E1 |
| Single talking head | T1 + C1 | T1 per phrase, K1 on one number, C3 once | T1 + E1 |
| B-roll only, no speech | T4 or T1 on the first phrase's key word + C1 | T1 every 2 s, caption lane lifted on busy shots | E1 |
| Still image + text | T1 final state + C1 chunk | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (demo2 render, 720x1280, 24 fps)

- Head top 0.09–0.15H, so crown centre y 0.075H, cap height ≈ 0.045H; in the grocery shot (head at x 0.50–0.75W, top 0.09H) the crown centre x moved to 0.27W (T4).
- Crown words used: .35–1.70, 2.30–3.10, 3.30–4.85, 5.15–6.50, 7.60–8.40, 9.15–9.76 s; pop 0.125 s, fade 0.21 s.
- Script 70 px shrunk per chunk to fit 0.84W (about 58–70 px); stroke 3.2 px. Chunk ends: 0.80, 2.02, 3.15, 4.85, 6.50, 8.35, 9.76 s.
- Outline and shadow kept white script readable on the white phone screen, wood and plant shots; no lane shift needed.
