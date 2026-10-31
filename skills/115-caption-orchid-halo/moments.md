# moments.md — Orchid Halo: Style Bible + Moment Library

This file is the single source of truth for the Orchid Halo caption style. Part 1 is the style bible (palette, type, layout, motion, footage rules, safe zones). Part 2 is the moment library. Part 3 gives starting combinations. Measurements come from a 720x640, 24 fps, 8.1 s caption-only reference on black; the placement, sizes for 9:16 and the footage rules are design decisions marked "(design)". SKILL.md tells Claude how to pick and place moments.

**The look in one line:** short word-by-word caption chunks in heavy white sans, with one glowing italic serif accent word per chunk that fades and settles in as it is spoken, sitting tucked against the sans line, low on untouched full-frame footage.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, accent word, lane height…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (24 in the reference and demo). Reference values in brackets are for 1080×1920. Measured reference widths were taken at W = 720, so the demo uses them 1:1 and enlarges the accent (design).

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Base word | #FFFFFF | Sans words (measured 248,251,246) |
| Accent top | #FFCDF8 (default, ✎ accent hue) | Top of the accent gradient (design) |
| Accent bottom | #E846DE (default, ✎ accent hue) | Bottom of the accent gradient (design) |
| Halo inner | #F434E2 at 0.9 × 0.9 | 11 px gaussian halo behind the accent (design) |
| Halo outer | #D618D6 at 0.85 × 0.9 | 26 px gaussian halo (design) |
| Shadow | #000000 | Base words: 6 px blur at 75 %; accent: 5 px blur at 50 % (design: the reference sat on black and needed none) |

The measured reference accent was a bright green gradient (about 39,240,61 at the core, darker toward the baseline) with a green halo. Accent hue is a parameter: keep the formula (very light tint at the top, saturated mid-tone at the bottom, halo two steps more saturated than the fill). The public demo uses orchid pink. Brand-swap rule: replace the three accent colours with the user's colour; never change white. No other colours exist.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, plates, boxes, bars, scrims or colour overlays. |
| Caption block | One chunk at a time; centred on x = 0.50W; the accent word's vertical centre sits on the lane line. |

### 1.3 Layouts / grid

| Item | Spec |
|---|---|
| Lane line (design) | accent centre y = 0.765H [1468]; allowed range 0.70–0.80H |
| Max width | 0.86W for the widest line (the accent shrinks to fit) |
| Lead line (words before the accent) | centre y = accent centre − (accent height/2 + base line height/2 − 6) |
| Tail line (words after the accent) | centre y = accent centre + (accent height/2 + base line height/2 − 6) |
| Tuck | base lines overlap the accent's ascender/descender band by 6 px at 720 wide (measured reference tuck ≈ 20 px at the 90 px accent) |

Layouts follow from where the accent word sits in its chunk: **A** accent first (tail line only), **B** accent last (lead line only), **C** accent in the middle (lead and tail lines), **S** accent alone.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Base word | Heavy geometric sans, mixed case as written, normal tracking | Plus Jakarta Sans ExtraBold (wght 800) | Nunito Sans ExtraBold, Archivo ExtraBold | 0.075W [81] (reference ≈ 0.042W at 720) |
| Accent word | High-contrast italic serif, bold, calligraphic, mixed case as written, punctuation kept | Newsreader Italic (wght 760, opsz 72) | Playfair Display Bold Italic, Gelasio Bold Italic | 0.194W [210] (reference ≈ 0.125W at 720, ratio accent:base ≈ 2.9 : 1; demo 2.6 : 1) |

Rules: text case exactly as written. Word spacing is one normal space in the base font. Only the accent word is serif and italic. No outlines, no uppercase conversion.

### 1.5 Motion language

| Item | Spec |
|---|---|
| Base word in | Fade 0 → 100 % over 0.20 s (5 f), rising 6 px to its place (rise is design; the reference was a pure fade through grey). Appears on its spoken start time. |
| Accent in | On its spoken time: scale 0.86 → 1.00 (measured 0.87 → 1.0 in 3 f) with ease-out cubic over 0.26 s, fade 0 → 100 % over 0.18 s; halo arrives with the fill. |
| Settled | Nothing moves after a word has landed. No drift, no pulse. |
| Chunk out | Whole chunk fades 100 → 0 over 0.12 s (3 f) at its end time, then the next chunk starts on its first word. |
| Never | Bounce, overshoot, letter-by-letter typing, slides, shake, flashes, rotation, colour cycling, uppercase, a second accent in the same chunk. |

### 1.6 What may happen to the user's footage
Allowed: nothing. Footage plays full frame, untouched, in sync with the audio. Only text, halo and shadow overlays. Forbidden: any effect on cuts, blurring, dimming, grading, zoom, speed changes, trimming, reordering, replacing.
On a black or empty plate (no footage, generate mode) the shadows are dropped.

### 1.7 Safe zones
- Face never covered while speaking: keep the block inside y 0.62–0.88H by default and shift the lane line (≥ 0.70H, ≤ 0.80H) when a face sits low. If the face bottom edge is below 0.62H, move the lane line to 0.30H only if the shot's top 0.38H is free; otherwise shrink to base-only (C2) at 0.86H.
- Keep text ≥ 0.07W from the left and right edges and ≥ 0.06H from the bottom.
- Do not place the block over existing footage text or UI labels when a free lane exists.

---

## PART 2 — MOMENT LIBRARY

Family codes: C caption · K keyword · T title · E end. Energy: ● calm, ●● medium, ●●● high.

### C1 · HALO STACK — C ●● (signature, the caption system)
**What it is:** A chunk of 2–5 words: base words fade in one by one on their spoken times while the one accent word lands, large and glowing, on its own spoken time. Lead words sit above, tail words below, tucked against the accent.
**Use when:** Any speech or script line. The default for every chunk.
**Avoid when:** The lane is a busy bright area and a second lane is free (move the lane line instead).
**Text (✎):** the user's words, case as written; 2–5 words, ≤ 30 characters in total; split at punctuation; never end a chunk on an article, preposition or conjunction; chunk change preferably on a footage cut; accent = the most meaningful noun or verb.
**Geometry / Graphics:** layout A, B or C from 1.3; accent text shrinks to fit 0.86W; base words in one line each.
**Motion:** | t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | base word | alpha, y | 0 → 1, +6 → 0 px | 0.20 s ease-out cubic |
| accent start | accent | scale, alpha | 0.86 → 1.00, 0 → 1 | 0.26 s / 0.18 s ease-out cubic |
| chunk end | whole chunk | alpha | 1 → 0 | 0.12 s linear |
**Footage behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** 3 f fade at the chunk's end; the next chunk's first word starts at its own spoken time (a gap of 0 to 0.4 s is fine).
**Build notes:** pre-render every word once (text at 2× then downscale, shadow blur layered under, accent gradient + two halo blurs). Lay out the whole chunk first so nothing moves after landing. Resize the accent layer about its centre for the scale-in.
**Flow prompt text:** "Short caption chunk {{CHUNK}} in heavy white sans-serif words that fade in one at a time as spoken, with the word {{ACCENT}} in a large glowing italic serif in {{COLOUR}} that fades and settles in as it is spoken, the sans words tucked just above or below it, low in the frame."
**Still-image state:** all words visible, accent settled.

### K1 · ACCENT SOLO — K ●●● (signature, for the payoff word)
**What it is:** A chunk that is the accent word alone, centred on the lane line, with the halo.
**Use when:** The last word, a number, a name or a punchline.
**Avoid when:** More than twice per video or twice within 3 s.
**Text (✎):** one word with its punctuation.
**Geometry / Graphics:** layout S; accent size as 1.4 (up to 1.15× for words ≤ 5 letters).
**Motion:** as C1 accent in; hold until its end time; 3 f fade.
**Footage behaviour:** untouched.
**Exit:** fade 0.12 s (or held to the last frame in E1).
**Build notes:** same layer as C1 accent.
**Flow prompt text:** "The single word {{WORD}} appears alone in a large glowing italic serif in {{COLOUR}}, fading and settling in at the moment it is spoken."
**Still-image state:** the word, settled.

### K2 · MIDDLE ACCENT — K ●● (signature layout C)
**What it is:** The accent sits between a lead word and tail words: a small sans word above, the glowing word, a small sans word below.
**Use when:** Verb or noun in the middle of a short phrase.
**Text (✎):** 3–5 words, accent in the middle.
**Geometry / Graphics:** layout C; lead line and tail line both tucked.
**Motion:** as C1; lead words land before the accent, tail words after.
**Footage behaviour:** untouched.
**Exit:** as C1.
**Build notes:** keep the block's total height inside the lane range of 1.3.
**Flow prompt text:** "A small white sans word above, the key word {{ACCENT}} in a large glowing italic serif in the middle, and a small white sans word below."
**Still-image state:** full stack.

### C2 · PLAIN RUN — C ● (extension in the same grammar)
**What it is:** A base-only chunk (no accent) of 1–4 sans words, for filler lines or fast speech.
**Use when:** Connecting words that carry no meaning; never in two chunks in a row.
**Text (✎):** 1–4 words.
**Geometry / Graphics:** one base line centred on the lane line.
**Motion:** as the base word in; fade out 0.12 s.
**Footage behaviour:** untouched.
**Exit:** as C1.
**Build notes:** same layers as C1 without the accent.
**Flow prompt text:** "Small white heavy sans words fade in one at a time as spoken, low in the frame."
**Still-image state:** the line.

### T1 · HEADLINE ACCENT — T ●● (extension in the same grammar)
**What it is:** An opener: the topic word as an accent, with a sans line above or below, held for 1.2–2 s starting at 0.10 s.
**Use when:** The first line names the topic.
**Text (✎):** user's topic word as accent plus up to 3 sans words.
**Geometry / Graphics:** C1 layout A or C.
**Motion:** as C1.
**Footage behaviour:** untouched; keep off the face box.
**Exit:** fade.
**Build notes:** identical to C1.
**Flow prompt text:** "At the start, the topic word {{TOPIC}} lands in a large glowing italic serif with a short white sans line beside it."
**Still-image state:** poster title block at the lane line.

### T2 · SECTION ACCENT — T ●● (extension in the same grammar)
**What it is:** A mid-video new-topic word as an accent with its lead word.
**Use when:** A real topic change without a cut.
**Text (✎):** user's words.
**Geometry / Graphics:** as C1 layout B.
**Motion:** as C1.
**Footage behaviour:** untouched.
**Exit:** fade.
**Build notes:** at most once per video.
**Flow prompt text:** "A new section word {{WORD}} appears in the glowing italic serif with a white sans lead word above it."
**Still-image state:** settled.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** The last chunk holds until 0.4 s before the end, then fades 0.3 s.
**Use when:** Always on the last chunk when the video ends on speech.
**Text (✎):** the last words.
**Geometry / Graphics:** K1 or C1.
**Motion:** hold; fade 0.3 s linear.
**Footage behaviour:** untouched.
**Exit:** fade.
**Build notes:** extend the end time, not the start.
**Flow prompt text:** "The last words stay on screen to the end, then fade out gently."
**Still-image state:** settled.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 on the topic word | C1 with one accent per chunk; K2 on lists; C2 on filler | K1 on the last word, E1 |
| Single talking head | C1 | C1, K2, C2 mixed | K1, E1 |
| B-roll only with a voice-over | C1 | C1, K1 on numbers | K1 |
| Still image | C1 (settled) | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

| Value | Used |
|---|---|
| Base font / accent font | 54 px / 140 px |
| Lane line | 0.765H (979 px) |
| Tuck | 6 px |
| Accent gradient | #FFCDF8 → #E846DE; halos #F434E2 (11 px), #D618D6 (26 px), factor 0.9 |
| Chunks used | 9: 3 × layout A, 3 × C, 2 × B, 1 × S |
| Accent words | Saving, earning, yourself, automate, spend, left., year, watch, happens. |
