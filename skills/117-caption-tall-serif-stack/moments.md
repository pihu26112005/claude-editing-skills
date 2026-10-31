# moments.md — Tall Serif Stack: Style Bible + Moment Library

This file is the single source of truth for the Tall Serif Stack caption style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel (one continuous shot, no cuts); the rest are "(design, not measured)" and were proven on a 720x1280, 24 fps, 10 s demo. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while tall, narrow, high-contrast serif capitals in one saturated colour stack up in a block above the speaker's head (hard cut-in, hard cut-out, a soft light sheen across the letters), and a tiny bold white serif caption builds word by word right on the block's lower edge.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (keep seconds at other rates). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Title colour (default) ✎ | #CF3D3F | Title capitals. Measured median (207,60,63) over several frames. A parameter: replace it with the user's brand colour. |
| Title sheen | accent lightened 45–55 % toward white | A soft diagonal band inside the letters. Measured: a paler pink band sat roughly in the middle of the block (design, not measured: exact tint). |
| Caption white | #FFFFFF | Caption words |
| Caption ink | #14141E at 78 % | Thin 1.5 px outline round caption glyphs (design, for bright shots) |
| Shadow | #000000 | Caption shadow (0, +2 px, blur 5 px, 59 %); title shadow (0, +6 px, blur 7 px, 35 %) (design) |

Brand-swap rule: only the title colour (and its sheen) changes. Caption white never changes. Demo used cobalt #2B4DE8 with sheen #96B0FF so it differs from the reference hue.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, boxes, bars, blur plates, tints. |
| Title block | Centred on x = 0.50W; width of the longest line = 0.70W [756] (measured x 0.15–0.85W); lines stacked 1–3 high; every line centred; line pitch = 1.35 × cap height (measured ≈ 1.17–1.2; opened to 1.35 in the demo so lines never touch). |
| Caption | One centred line, no box. |

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Head lane (default) | Title block bottom edge ≈ 0.105H [202], above the speaker's hair line, top margin ≥ 0.02H, block height ≤ 0.084H; caption centre = block bottom + 24 px at 720 wide (0.019H), so the caption sits just under the block and never overlaps it | Speaker shots (measured: block bottom sat on the top of the head, 0.28–0.43H on a 0.31H hair line, with the title partly over hair; the demo lifts it clear of the face) |
| Top lane | Block top = 0.06H [115], block grows downward | Shots with no face in the upper third (design) |
| Low lane | Block bottom = 0.90H [1728], block grows upward | Shots whose top half holds a face or subject (design) |
| Caption lane | Centre on the last title line's lower edge: last-line top + 0.92 × cap height (on speaker shots: last-line top + 1.05 × cap height, so the caption sits just under the block) | All caption words |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Fat high-contrast Didone capitals squeezed narrow (x-scale 0.60) so the letters read tall; thick stems, hairline serifs; all caps | Bodoni Moda Black (wght 900, opsz 11), squeezed to 60 % width | Playfair Display Black squeezed, Abril Fatface squeezed | Cap height from width: cap = 0.70W / (longest line letters × 0.69); measured cap 0.066–0.083H (reference), demo 0.046–0.092H. Speaker shots: whole block ≤ 0.084H. |
| Caption | Small bold transitional serif, lowercase or as written, tight word spacing | Gelasio Bold (Georgia-like) | Newsreader Bold, Tinos Bold | 0.047W [51] (reference ≈ 0.04W) |

Rules: titles are uppercase (user's words, case changed only here). Captions keep the user's case and punctuation. No italics, no outlines on the title, no rotation.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Title in / out | Hard cut (measured: no fade, no slide) | 1 f |
| Title swap | Hard cut, new block replaces old in the same frame (measured) | 0 f |
| Title sheen | Slow linear drift left to right, band width 0.16 of block width, 0.30 of block width per s (design) | continuous, loops |
| Caption word in | Words appear one at a time (measured word build); alpha ramp ease-out cubic (design) | 2 f at 24 fps (0.083 s) |
| Caption chunk out | Hard cut | 1 f |
| Cuts | Plain hard cuts | 0 f |

Never: bounce, slides, typewriter letters, rotation, zoom, blur, glitch, flashes, extra colours, italics, outlined title.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text overlays and their soft shadows | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming, trimming, grading, blurring, zooming or masking footage; hiding it behind cards or bars. Primary footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Title block and caption stay above the hair line (face box top − 0.02H). If the face top is above 0.17H, shrink the block (budget 0.084H) or use a single line. |
| Non-face shots | Top lane; keep the block off hands, phone screens and text when a lane above 0.20H is free. |
| Face in the upper half of a non-speaker shot | Use the low lane. |
| Edges | Block and caption stay ≥ 0.04W from the left and right edges. |
| Overlap | The caption never overlaps the title block (the reference overlapped; the demo keeps them clear for legibility). |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **C** caption · **K** keyword · **X** cut treatment · **E** end.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · STACKED TITLE CUT-IN — T ●●● (signature)
**What it is:** one to three lines of tall narrow serif capitals in the accent colour appear in a single frame above the speaker, hold with a drifting sheen, and vanish in a single frame.
**Use when:** the opening line, a topic word, each new step. **Avoid when:** within 3 f after a cut with a different title still running; two titles at once.
**Text (✎):** 1–3 words taken from the user's own spoken words, uppercase, ≤ 3 lines, ≤ 12 letters per line. Words repeat from the captions (they are an emphasis layer).
**Geometry / Graphics:** 1.2, 1.4. Block width 0.70W for the longest line (cap = 0.70W/(letters × 0.69)); other lines share the same cap height and are centred.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 f | Title | alpha | 0 → 0.94 | hard cut (measured) |
| hold | Sheen | band x | −0.15 → 1.45 of block width at 0.30/s | linear (design) |
| end | Title | alpha | 0.94 → 0 | hard cut (measured) |

**Footage / plate behaviour:** untouched. **Captions during it:** C1 on the lane below.
**Exit:** hard cut, or hard swap to the next title (T3).
**Build notes:** render the line at 2× in the font, crop to glyph box, resize width × 0.60 × k and height × k; stack with pitch 1.2 × cap; paste into a full-frame mask once; per frame mix the accent and sheen colour by a Gaussian band over (x/w + 0.35·y/h), composite at 0.94 over a 35 % blurred shadow shifted +6 px.
**Flow prompt text:** "At {{TIME}} a block of {{LINE_COUNT}} line(s) of tall, narrow, high-contrast serif capitals in {{ACCENT_COLOUR}} reading {{WORDS}} appears instantly above the person's head, with a faint lighter sheen sliding slowly across the letters, then disappears instantly."
**Still-image state:** block above the head, full opacity, sheen mid-way.

### T2 · ONE-LINE TITLE — T ●● (extension in the same grammar)
**What it is:** the same title as a single wide line, used where the block budget is small (speaker shots with a high face).
**Use when:** 1–2 short words on a speaker shot, or a talking head with the face above 0.17H. **Avoid when:** more than 12 letters per line would push cap height below 0.040H.
**Text (✎):** ≤ 14 characters including the space.
**Geometry / Graphics:** one line, width 0.70W, bottom 0.105H; cap ≈ 0.042H for 12 letters.
**Motion:** as T1. **Footage:** untouched. **Captions:** C1 below the line.
**Exit:** hard cut. **Build notes:** as T1, n = 1.
**Flow prompt text:** "At {{TIME}} one line of tall, narrow serif capitals in {{ACCENT_COLOUR}} reading {{WORDS}} appears instantly high above the person's head and disappears instantly."
**Still-image state:** as T1.

### T3 · TITLE SWAP — T ●●● (signature rhythm)
**What it is:** one title is replaced by the next in the same frame, no gap (measured at 1.28 s, 2.78 s and 4.38 s on the reference, title blocks changed every 1.4–1.6 s).
**Use when:** a list, steps, or a run of topic words 1.1–1.8 s apart. **Avoid when:** the next word is under 1.0 s away (merge into one title).
**Text (✎):** next block, same layout rules. **Motion:** both hard cuts on the same frame; the new block restarts the sheen.
**Footage:** untouched. **Exit:** the last title ends on a cut or a pause.
**Build notes:** switch the active title index; never overlap two titles.
**Flow prompt text:** "At {{TIME}} the title instantly swaps to {{WORDS}} in the same place and style, without any transition."
**Still-image state:** n/a.

### T4 · LOW-LANE TITLE — T ●● (design, not measured)
**What it is:** the title block sits at the bottom, growing upward, when the upper half holds a face.
**Use when:** a shot has a face in the top 0.40H and the speaker is not the voice. **Avoid when:** the bottom lane has key footage text.
**Geometry:** block bottom 0.90H; max 3 lines. **Captions:** C1 on the last line's lower edge.
**Motion/Exit:** as T1. **Build notes:** top = 0.90H − block height.
**Flow prompt text:** "At {{TIME}} the title block of tall serif capitals reading {{WORDS}} appears instantly in the lower part of the frame and disappears instantly."
**Still-image state:** as T1, bottom lane.

### T5 · SHEEN DRIFT — T ● (design; the sheen itself is measured as a static pale band)
**What it is:** a soft diagonal pale band moving slowly across the title letters.
**Use when:** every title that holds > 0.8 s. **Avoid when:** never off (it is part of the look).
**Motion:** band centre from −0.15 to 1.45 × block width, 0.30 block widths per s, loops; band width 0.16, strength 0.65 toward the sheen colour.
**Build notes:** colour = accent × (1−b) + sheen × b, b = 0.65·exp(−((u−c)/0.16)²), u = x/w + 0.35·y/h.
**Flow prompt text:** "A faint lighter shimmer slowly sweeps across the title letters from left to right."
**Still-image state:** band near the middle.

### C1 · STRADDLE CAPTION BUILD — C ●● (signature)
**What it is:** a tiny bold white serif caption sits just under the title block and builds one word at a time (measured on the reference as word-by-word chunks of 1–3 words).
**Use when:** all speech. **Avoid when:** a chunk would run longer than 1.6 s or cross a cut.
**Text (✎):** the user's words exactly (case and punctuation as written); chunk 2–5 words; split at punctuation; never end on an article, preposition or conjunction; start = first word, end = min(last word end + 0.1, next start − 0.05) and before the next cut.
**Geometry / Graphics:** 1.4 caption; one line centred at x = 0.50W; centre on the last title line's lower edge (1.3). Each word is laid out in its final place before it appears; nothing moves.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | Word | alpha | 0 → 1 | ease-out cubic, 2 f (design) |
| chunk end | Whole chunk | alpha | 1 → 0 | hard cut |

**Footage:** untouched. **Exit:** hard cut.
**Build notes:** pre-render every word (shadow, 1.5 px ink outline, white fill) at 2×, downscale; keep the same lane for the whole shot even when no title is up.
**Flow prompt text:** "Small bold white serif captions appear one word at a time, centred just under the big title, with a thin dark outline and soft shadow; each caption line vanishes when the next begins. The caption words are: {{CAPTION_TEXT}}."
**Still-image state:** full chunk visible.

### C2 · BARE CAPTION — C ● (extension in the same grammar)
**What it is:** the C1 caption with no title above it, in the same lane.
**Use when:** between titles, or a shot where a title would hide the subject. **Avoid when:** it lasts more than 2.5 s with no title nearby.
**Text/Motion/Build:** as C1; lane = the shot's last title lane, or the head lane.
**Flow prompt text:** "Small bold white serif captions appear one word at a time in the same spot, with no title above them: {{CAPTION_TEXT}}."
**Still-image state:** as C1.

### K1 · SOLO KEYWORD TITLE — K ●●● (design, not measured)
**What it is:** one single word at the largest allowed size (cap = 0.70W / (letters × 0.69), single line) for the payoff or a number.
**Use when:** a one-word payoff, an amount, a year. **Avoid when:** more than 1× in 6 s.
**Text (✎):** one word ≤ 9 letters, uppercase. **Motion/Exit:** as T1. **Captions:** C1 beneath.
**Flow prompt text:** "At {{TIME}} one very large tall serif word {{WORD}} appears instantly above the person and disappears instantly."
**Still-image state:** as T2.

### X1 · CUT BEAT — X ●● (signature rule)
**What it is:** every footage cut gets a text beat: the title and caption chunk end on the cut frame (or just before), and the new shot's title starts 0.0–0.2 s after it with the new lane.
**Use when:** every cut. **Avoid when:** a title would start within 3 f after a cut while another is still running.
**Motion:** hard cuts only; lane switches on the cut frame. **Build notes:** assign a lane per shot; titles never cross a cut.
**Flow prompt text:** "At each shot change the on-screen words end and the next words begin, with plain hard cuts and no effects."
**Still-image state:** n/a.

### E1 · QUIET CLOSE — E ● (design, not measured; the reference also ended with only a caption)
**What it is:** the last 0.2–0.5 s keeps the final caption chunk only; the title ends first (measured: the last title ended 1.3 s before the end).
**Use when:** every ending. **Avoid when:** never.
**Motion:** hard cut off. **Flow prompt text:** "The big title disappears a moment before the end; only the small caption remains until the last word."
**Still-image state:** caption only.

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T2 or T1 + C1 | X1 + T1/T3 per step, T4 for a face shot | T1 + C1, E1 |
| Single talking head | T2 + C1 | T3 swaps every 1.4–1.8 s, C2 between | K1 + E1 |
| B-roll only | T1 + C1 | X1 per cut, T3 | E1 |
| Still image | T1 (settled) + C1 | n/a | n/a |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
