# moments.md — Chalk Talk: Style Bible + Moment Library

This file defines the **Chalk Talk** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*.

**The look in one line:** a classroom chalkboard come to life. White chalk circles draw themselves around the speaker's head, a yellow sketchy title is written then filled, handwritten captions light up word by word on little dark tags. Dry charcoal brush strokes slash across the screen to change scenes, B-roll sits in a card with a wobbly yellow chalk border on a charcoal board, and it ends on a cream paper page with a big sketchy-capitals quote, yellow quote marks, a yellow doodle and highlighter-marked captions. Everything feels hand-made: drawn on, written, brushed, never slid or bounced.

How to use it:
1. Pick moments by ID (SKILL.md, steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, text, which footage goes in the card, anchor, side). Everything else (sizes, colours, fonts, stroke widths, motion curves, durations, layer order) is the style and stays as written.
4. For a **final video**, build from the spec. For a **Google Flow master prompt**, use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W` = frame width, `H` = frame height, `f` = frames at 30 fps (at other frame rates keep the **seconds**). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette (sampled from the reference)

| Role | Hex | Used for |
|---|---|---|
| CHALK | `#F4F1E8` | chalk circles, caption words over footage |
| YELLOW | `#F3D10A` | titles over footage, card border, list numerals, quote marks, doodles, key caption words |
| BOARD | `#2F2F2D` | charcoal board and brush strokes (with fine horizontal grain) |
| PAPER | `#F7F2E8` | the cream end page and cream brush strokes (with faint horizontal fibres) |
| INK | `#312F2C` | quote text and captions on the paper page |
| TAG | `#221F1D` at 90 % | the dark rounded tag behind the word being spoken (over footage) |
| HIGHLIGHT | `#EDD860` | the highlighter box behind the word being spoken (on paper) |

Brand variant ✎: YELLOW may become one brand accent; BOARD and PAPER stay.

### 1.2 Materials
- **Chalk line:** solid CHALK or YELLOW stroke 0.007 W [8 px] wide, round caps, with a chalky texture (stroke opacity modulated by fine noise between 75 % and 100 %). Lines are slightly imperfect: radius or position wobble of ±0.002 W.
- **Charcoal board:** BOARD plus 3 % luminance noise and faint horizontal streaks (dry-brush grain).
- **Paper:** PAPER plus 2 % noise and faint horizontal fibres.
- **Dry-brush stroke (the transition material):** a horizontal band of BOARD or PAPER, 0.13–0.17 H tall, tilted −4° (rising to the right), whose leading edge is ragged: dozens of thin bristle streaks of random length (0–0.09 W) and thickness (1–4 px) poke ahead of the band, with gaps between them.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Titles, quotes, numerals | sketchy chalk capitals (double-stroke hatched letters) | Cabin Sketch Bold | Cabin Sketch Regular, Rubik Dirt, any chalk/sketch display | title: fit ≤ 0.80 W, cap height ≤ 0.07 H; quote lines: cap height 0.065 H [125 px] |
| Captions | rounded casual handwriting | Gochi Hand | Patrick Hand, Kalam, Comic Neue | 0.050 H [96 px] |

All words on screen are the user's words (or list numerals). Captions keep the user's casing; titles and quotes are UPPERCASE.

### 1.4 Motion language
- **Draw-on:** chalk lines and borders are drawn along their path (arcs grow from the top outward in both directions; rectangles trace around) over 0.3–0.8 s, ease-out-cubic.
- **Write-then-fill:** titles first appear as a chalk outline revealed left to right (0.3 s), then fill solid (0.2 s).
- **Brush wipe:** bands enter one after another (stagger 0.05 s) from alternating sides, each crossing the frame in 0.3 s with ease-in-quad, until the frame is covered. The same strokes run in reverse ("erase") to reveal what's underneath.
- **Words:** each caption word appears at its spoken time (fade 3 f). The active word sits in a TAG (over footage) or a HIGHLIGHT box (on paper) that jumps word to word.
- No sliding panels, no bounce, no zoom punches. The only camera move is a slow drift inside cards (100 → 104 %).

### 1.5 What may happen to the user's footage (style-specific rules)
- Allowed: full-frame footage with chalk drawn over it; footage inside a chalk card (cover fit, crop anchor ✎) on the board or paper; slow drift inside a card; covering the frame with brush strokes during a wipe.
- A brush wipe may fully cover the footage for **at most 0.25 s**, ideally around a footage cut (so it hides the cut). The paper page without footage (K08) is allowed only for the last ≤ 1.5 s or ≤ 15 % of the video; otherwise close with K09 (quote + live footage card).
- The **card always plays the current footage in real time**, in sync with the audio. Never put foreign imagery in a card.
- Never recolour, filter, blur or retime the footage.

### 1.6 Safe zones
- **Face box:** never covered by captions, titles or numerals. Chalk circles may pass around and behind-looking over hair and shoulders but never across the eyes or mouth.
- Captions sit in the chest band (0.58–0.80 H) or the top/bottom band of a card, wherever the shot is calm.

---

## PART 2 — MOMENT LIBRARY

Family codes: **CHALK** (drawn elements), **TYPE**, **CAP**, **WIPE**, **CARD**. Energy: ● low · ●● medium · ●●● high.

---

### K01 · CHALK HALO — CHALK ●●● (signature opener)

**What it is:** Three concentric white chalk circles draw themselves around the speaker's head, like a teacher circling the important thing on the board.

**Use when:** the opening line on a talking head (default opener); any key statement on a face.

**Geometry:** centre = the head's centre (face box centre, raised by 0.15 × face height, so the inner circle passes under the chin, not across the mouth) ✎. Radii **0.26 W, 0.35 W, 0.46 W** (measured on the reference). CHALK line, 0.007 W.

**Motion (measured):** each arc grows from the top (12 o'clock) in both directions: outer starts at 0.17 s, middle +2 f, inner +4 f; each reaches a full circle in 0.75 s (ease-out-cubic). Stays until a wipe covers it.

**Flow prompt text:** "Three white chalk circles draw themselves around the speaker's head, one inside the other, growing from the top in both directions until they are complete, with a dusty hand-drawn texture."

---

### K02 · CHALK TITLE — TYPE ●● (signature)

**What it is:** One big word in sketchy yellow chalk capitals at the top: first written as an outline left to right, then filled solid.

**Text (✎):** one user word: the key word of the opening line (or of a new section). UPPERCASE, ≤ 10 letters.

**Graphics:** YELLOW, sketch font, cap top 0.02 H, centred on the subject's x (or left-aligned at 0.05 W), largest size that fits 0.80 W with cap height ≤ 0.07 H. Over light backgrounds add a 0.004 W BOARD outline under it.

**Motion:** outline revealed left → right over 0.3 s (the reference shows the outline at 0.47 s), then fill fades in over 0.2 s. Stays until a wipe covers it.

**Flow prompt text:** "At the top, the word \"{{TITLE}}\" is written in sketchy yellow chalk capitals: first as an outline traced left to right, then filled in solid yellow."

---

### K03 · HAND CAPTIONS — CAP (always on)

**What it is:** Captions in casual handwriting. Over footage, words are chalk-white with a soft shadow; the word being spoken sits on a small dark rounded tag; the key word of a chunk is yellow. On paper, words are INK and the spoken word gets a yellow highlighter box.

**Text (✎):** the user's caption text **verbatim** (original casing), chunks of 1–4 words, ≤ 24 characters; at most one yellow key word per chunk (meaning words only; the payoff is always one).

**Graphics:** caption font 0.050 H. Over footage: CHALK words, shadow (0/+2 px, blur 4 px, black 45 %); TAG = rounded rectangle from baseline − 0.040 H to baseline + 0.012 H, 0.012 W wider than the word on each side, radius 0.012 W, behind the active word. On paper: INK words, HIGHLIGHT box (radius 0.008 W) behind the active word. Left-aligned at x 0.08 W (✎ inside a card: card x0 + 0.06 W). Baseline (✎): chest band 0.64 H on a talking head; card top band card y0 + 0.12 H or bottom band card y1 − 0.08 H; paper page 0.925 H.

**Motion:** words appear at their spoken time (fade 3 f, no reflow: the chunk is laid out in advance). The tag/highlight jumps to each new word (1 f). Chunk change: hard swap.

**Flow prompt text:** "Captions are in casual handwriting, white with a soft shadow, appearing word by word as spoken; the word being said sits on a small dark rounded tag, and the key word \"{{KEY}}\" is yellow. The ONLY caption lines, in order, are: [a-b s] \"{{CHUNK_1}}\", … No other text."

---

### K04 · CHARCOAL BRUSH WIPE — WIPE ●●● (signature transition)

**What it is:** Dry charcoal brush strokes slash across the screen in bands, one after another, until the whole frame is a chalkboard.

**Use when:** leaving the opening talking head; any big section change. Time it so the frame is fully covered **on a footage cut** (it hides the cut).

**Geometry:** 7 bands, each 0.15 H tall, overlapping by 0.01 H, tilted −4°; bands alternate entering from the left and the right; bristle edge per Part 1.2.

**Motion (measured on the reference: 2.53–3.20 s):** band k starts at k × 0.05 s, crosses in 0.3 s, ease-in-quad. Total ≈ 0.45–0.65 s. Elements under it (halo, title, captions) stay until covered.

**Flow prompt text:** "Thick dry charcoal brush strokes slash across the screen one after another, slightly tilted, with ragged bristle edges, until the whole frame becomes a dark chalkboard."

---

### K05 · CHALK CARD — CARD ●●● (signature middle)

**What it is:** On the charcoal board, the footage appears inside a tall card with a wobbly yellow chalk border, revealed by brush strokes erasing the charcoal.

**Use when:** right after K04 (B-roll, examples, lists); keep it through several cuts (the footage cuts inside the card).

**Geometry (measured):** card x 0.09–0.91 W, y 0.085–0.91 H (✎ shorten the bottom to 0.84 H when a caption needs the board below). Border: YELLOW chalk line 0.0065 W along the card edge with a small wave (amplitude 0.003 W, wavelength 0.02 W). Footage: cover fit, anchor ✎.

**Motion:** reveal = K04 bands running in erase mode, only inside the card, over 0.45 s; border traced around the card (clockwise from top-left) over 0.3 s, starting when the reveal is half done. Drift (K12) inside.

**Flow prompt text:** "On the dark chalkboard, the video appears inside a tall rectangle with a wobbly yellow chalk border, uncovered by brush strokes wiping away the charcoal."

---

### K06 · OUTLINE PRE-WRITE — TYPE ●

**What it is:** The closing quote is sketched as a thin dark outline over the card a moment before the paper page arrives, like a teacher pre-writing on the board.

**Text (✎):** the quote lines of K08/K09. **Graphics:** INK outline only (no fill), quote layout of K08. **Motion:** revealed left → right, line by line, 0.3 s, then stays until K07 covers it.

**Flow prompt text:** "Over the card, the closing words are sketched as thin dark outlines, ready to be filled in."

---

### K07 · PAPER WIPE — WIPE ●●●

**What it is:** Like K04, but the strokes are cream paper: the board is brushed over with cream until the paper page is revealed. The quote fills in solid as the paper passes behind it.

**Motion (measured: 4.07–5.0 s):** same band rules as K04, slower: each band 0.4 s, stagger 0.07 s. The frame is fully paper ≤ 0.3 s after a footage cut, or the strokes stop around the K09 card area.

**Flow prompt text:** "Cream paper brush strokes sweep across the dark board, band by band, revealing a clean cream page."

---

### K08 · QUOTE PAGE — TYPE ●●● (closer, footage hidden)

**What it is:** A cream paper page with a big quote in sketchy capitals, two yellow quote marks above it, a yellow doodle after the last line, and handwritten captions with a highlighter.

**Use only** for the last ≤ 1.5 s or ≤ 15 % of the video (Part 1.5). Otherwise use K09.

**Geometry (measured):** quote marks YELLOW (sketch font “ glyph at 0.22 H font size, or two drawn comma shapes) at x 0.04–0.14 W, y 0.02–0.10 H. Quote: INK, sketch font drawn with a 0.004 W same-colour stroke so the hatched letters read solid, cap height 0.065 H, line pitch 0.072 H, left-aligned at 0.05 W, first line top 0.16 H, ≤ 4 lines, ≤ 12 characters per line. Doodle: YELLOW chalk loop/squiggle (≈ 0.12 W × 0.10 H, line 0.0065 W) 0.07 W right of the last line. Captions K03 paper mode at 0.925 H.

**Motion:** quote fills as the paper wipe passes (or writes on line by line, 0.25 s each); quote marks draw on (0.2 s); doodle draws along its path (0.4 s), 0.3 s after the quote.

**Text (✎):** 2–6 user words: the final line or its payoff phrase, UPPERCASE, keeping its punctuation.

**Flow prompt text:** "A clean cream paper page. Two yellow chalk quote marks at the top left, then the words \"{{QUOTE}}\" in big sketchy dark capitals over a few lines, and a small yellow chalk squiggle after the last word."

---

### K09 · QUOTE CARD — TYPE + CARD ●●● (default closer, keeps the footage)

**What it is:** K08's quote, quote marks and doodle on the upper part of the cream page, and the live footage in a yellow-bordered chalk card below.

**Geometry:** quote block as K08 but lines start at 0.12 H (3 lines max); card x 0.09–0.91 W, y 0.40–0.87 H (✎ anchor on the face); captions paper mode at 0.935 H.

**Motion:** the paper wipe (K07) covers the frame around the cut; the card is then revealed by erase strokes (0.4 s) and its border traced (0.3 s); quote marks and doodle draw on.

**Flow prompt text:** "On a cream paper page, the words \"{{QUOTE}}\" are written in big sketchy dark capitals at the top with yellow chalk quote marks, and below them the speaker keeps talking inside a card with a wobbly yellow chalk border."

**Still-image state:** default poster.

---

### K10 · CHALK DOODLE — CHALK ●

**What it is:** A small yellow chalk loop/squiggle drawn next to a word or title to punctuate it.

**Motion:** drawn along its path in 0.4 s. **Use:** after a title or quote, max 2 per video. **Flow prompt text:** "A small yellow chalk squiggle draws itself next to the words."

---

### K11 · CHALK NUMERAL — TYPE ● (extension in the same grammar)

**What it is:** For lists and steps, a yellow sketchy numeral ("1", "2", "3") written in the board margin above the card's top-left corner as each item is spoken; the old numeral is smudged away (fade + 0.01 W horizontal smear, 0.15 s).

**Graphics:** YELLOW sketch font, cap height 0.055 H, left edge at the card's x0, baseline 0.01 H above the card. **Motion:** write-then-fill (0.2 s + 0.1 s).

**Flow prompt text:** "As each step is spoken, a yellow chalk number is written in the dark margin above the card, replacing the previous one."

---

### K12 · CARD DRIFT — CARD ●

**What it is:** Inside a card, the footage slowly pushes in (100 → 104 %, linear) over each shot. **Flow prompt text:** "Inside the card the shot drifts in very slowly."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll montage → talking head | K01 + K02 + K03 | K04 ending on the first cut → K05 card through the montage; K11 numerals for lists; K02 title inside the card for a new key phrase; K12 | K06 → K07 around the last cut → K09 (or K08 for the last ≤ 1.5 s) + K10 |
| Single talking-head shot | K01 + K02 + K03 | K04 → K05 with the same live shot in the card | K07 → K09 |
| B-roll only | K04 from the start (board) → K05 + K02 | K11; K12 | K07 → K09 |
| Still image (poster) | K09 settled (quote + image card + caption) | — | — |

Each video gets its own selection based on its own hook points (SKILL.md step 4). Never paste a row blindly.
