# moments.md — Swiss Poster: Style Bible + Moment Library

This file is the single source of truth for the Swiss Poster style. Part 1 is the style bible (palette, grid, type, motion, footage rules, safe zones). Part 2 is the moment library. Colour, type and grid come from two reference posters (a red Swiss-grid poster with a huge flush-left grotesk headline, grid lines with dots at the crossings and tiny metadata labels; a pale minimalist poster with one red shape and small type). The motion, timing and layouts are designed in the same grammar and are labelled "(design, not measured)". Everything was proven on a 720x1280, 24 fps, 10 s render. Part 3 gives starting combinations.

**The look in one line:** a strict six-column grid with hairlines and dot crossings drawn over everything, footage locked into grid modules on a Swiss-red or warm-paper field, huge tight flush-left grotesk captions, one giant step numeral per list item, one red circle, and a column-wipe that re-lays the grid on every cut.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (24 in the proof render; at another fps keep the seconds). All px values are for the 720×1280 proof frame; scale by W/720.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Swiss red | #CE2B25 | Field of red layouts (measured on the red poster: 204,45,38) |
| Paper | #DDD3C1 | Field of paper layouts (measured on the pale poster: 215–223, 206–213, 188–195) |
| Signal red | #EC3B38 | Circle, step numeral on paper, keyword on paper (measured on the pale poster's red shapes: 236,59,56) |
| Ink | #141414 | Caption text on paper, keyword on red, hairlines on paper, the swap edge |
| White | #FFFFFF | Caption text on red, numeral on red, grid on red/footage, hairlines on red |
| Grid on red or footage | white at 26 % lines, dots at 62 % | Grid overlay (design) |
| Grid on paper | ink at 16 % lines, dots at 38 % | Grid overlay (design) |

Brand-swap rule: replace Swiss red and Signal red with the user's brand colour (one hue; derive the signal red 10 % lighter). Never add a second accent colour, gradients or shadows.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage module | Sharp-cornered rectangle snapped to the grid, no border, no shadow, no rounding. Cover-fit from the full source frame; crop anchor ✎ (face or subject, fraction of source height). |
| Fields | Flat Swiss red or paper, full frame behind the module. |
| Circle | Diameter 0.128W [92 px at 720], flat Signal red, no outline. Always overlaps a module corner or edge. |
| Hairline | 1 px (2 px at 2×), full text width, alpha 47 %; progress fill 3 px, solid. |
| Swap edge | 5 px ink bar, full height, travelling left to right during X1. |

### 1.3 Layouts / grid

Grid: 6 columns × 10 rows (cell 120 × 128 px at 720×1280). Outer text margin 0.067W [48]. Modules snap to grid lines.

| Layout | Field | Footage module (x0,y0,x1,y1 px) | Caption block | Furniture |
|---|---|---|---|---|
| P1 Poster Split | red | 0,0,720,768 (top 60 %, full width) | flush-left at x 48, bottom of block on y 1176, size 92 | circle centre (624,672); rail at y 1224 |
| P2 Paper Offset | paper | 120,128,720,640 (bleeds off the right edge) | flush-left at x 288, top y 676, width 400, size 60 | numeral at x 30, top y 672; circle centre (120,128); rail at y 64 |
| P3 Red Tower | red | 240,0,720,640 (tall, bleeds top and right) | flush-left at x 48, bottom on y 1176, size 84 | white numeral at x 24, bottom on y 634; circle centre (600,560); rail at y 1224 |
| E1 Giant Closer | red | 0,0,720,640 | flush-left at x 48, bottom on y 1176, size 118, width 630 | circle centre (624,552); rail at y 1224 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption | Bold neo-grotesk, mixed case as the user wrote it, flush left, tracking −0.035em, leading 0.98, word space 0.24em | Inter (variable, weight 800, optical size 32) | Archivo ExtraBold, Instrument Sans Bold, Helvetica Neue Bold | 92 / 84 / 60 / 118 px per layout (see 1.3) |
| Step numeral | Single digit, Inter weight 900, tracking −0.05em | Inter Black | Archivo Black, Anton | font size 352 px, cap height ≈ 0.2H |
| Rail label | Tiny, weight 700, tracking +0.04em, shot counter "01 / 06" | Inter Bold | IBM Plex Mono Medium | 16 px |

Rules: no uppercase conversion, no italics, no outline text, no rotation. The headline is the biggest thing on the poster and fills its column. Keyword: ink on red, Signal red on paper; max 1 per chunk, max 5 per 10 s.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Grid draw (T1) | linear stagger, vertical lines 0.05 s apart, horizontals 0.03 s apart after 0.1 s, each line takes 0.44 s; dots grow from r 0 to 3.5 px at 0.75–1.0 of the build | 0.8 s |
| Field rise (T1) | expo ease-out (1−2^(−10u)) | 0.5 s, starts 0.05 s |
| Caption word | hard cut in, no movement, no fade; chunk layout is computed in full first so no word moves | 0 f |
| Caption chunk exit | hard cut | 0 f |
| Numeral | reveal from its baseline upward (clip rises), expo ease-out | 0.34 s, starts 0.10 s after the layout starts |
| Circle | scale from 0 to full, expo ease-out | 0.30 s, starts 0.12 s after the layout starts (0.7 s in T1) |
| Swap (X1) | edge travels 0→W with expo ease-out | 0.33 s (8 f) |
| Rail progress | linear over the whole clip | whole clip |

Never: bounce, overshoot, spring, rotation, shadows, blur, glow, flashes, shake, letter-by-letter typing, zoom punches, gradients, second accent colour.

### 1.6 What may happen to the user's footage

Allowed: cover-fit crop into a grid module, with the crop anchor on the subject; a hairline grid and dots drawn over the footage; the circle over a module corner; the field rising over the lower part of the frame (T1). Forbidden: speed change, retiming, grading, filters, blur, replacing, trimming, reordering, generated people, changing audio. The primary module always plays the current shot live and in sync. No secondary footage windows exist in this style. In X1 the old layout keeps showing the new shot until the edge passes, so every pixel of footage is always the current shot.

### 1.7 Safe zones

Face box of the speaker must lie inside the module crop with ≥ 0.02H margin; choose the layout whose module contains it (P1 and E1 keep the top 60 % and 50 %, so a face in y 0.10–0.45 is safe; P2 keeps 0.10–0.50 of the module). Circle never over a face (it sits in the right third). Captions live only in the field, never over the module. Keep caption text ≥ 48 px from the left edge and ≥ 48 px from the right edge.

---

## PART 2 — MOMENT LIBRARY

Families: **T** title/opener, **P** layout, **C** caption, **N** numeral, **K** accent, **X** cut transition, **M** metadata, **E** end. Energy: low, mid, high.

### T1 · GRID BUILD-IN — T high (signature, design, not measured)
**What it is:** the opener. The footage starts full frame; hairline grid lines draw across it, dots appear at the crossings, and the red field rises from the bottom edge to lock the footage into the top module while the first caption words appear.
**Use when:** every video, first 0.9 s. **Avoid when:** never; for a video under 3 s shorten the grid draw to 0.5 s.
**Text (✎):** none (first caption chunk starts at the first word).
**Geometry / Graphics:** grid 6×10 in white (26 % lines, 62 % dots); field top goes from H to 768 [P1]; module crop stays fixed, the field only covers it.

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.00–0.80 | grid lines | length | 0 → full, staggered | linear |
| 0.60–0.80 | dots | radius | 0 → 3.5 px | linear |
| 0.05–0.55 | red field | top edge | H → 768 | expo out |
| 0.70–1.00 | circle | scale | 0 → 1 | expo out |

**Footage / plate behaviour:** full frame, then top module; the face box (y 0.15–0.40) is never covered.
**Captions during it:** clipped to the field, so they never sit on footage.
**Exit:** none; it settles into P1.
**Build notes:** draw the grid overlay at 2× and downscale; the module is cover(W,H) during the build, cropped to the field top.
**Flow prompt text:** "The person's video starts untouched. Thin white grid lines draw across the picture and tiny white dots appear where they cross, then a flat bold red block slides up from the bottom edge and settles under the picture, leaving the speaker's face fully clear. The speaker's first words appear in huge white bold letters on the red block."
**Still-image state:** footage on top 60 %, red block below with the headline, grid over everything.

### P1 · POSTER SPLIT — P mid (signature, design, not measured)
**What it is:** footage on the top 60 % of the frame, a red field below carrying the caption stack.
**Use when:** talking heads, opening and closing lines, any calm shot. **Avoid when:** the subject sits in the bottom 40 % of the shot.
**Geometry / Graphics:** see 1.3. **Motion:** static; entered by T1 or X1.
**Footage / plate behaviour:** cover-fit into 720×768; anchor ✎ (face centre ≈ 0.30H for a talking head, 0.62H for a low subject).
**Captions during it:** C1 at size 92.
**Exit:** X1.
**Flow prompt text:** "The picture fills the top of the frame; below it is a flat bold red block with a few huge white words, thin white grid lines and dots over everything, and a small red circle over the picture's lower right corner."
**Still-image state:** as described.

### P2 · PAPER OFFSET — P mid (design, not measured)
**What it is:** a warm paper page; the footage sits in a module that bleeds off the right edge, a huge red step numeral at the lower left and the caption to its right in black.
**Use when:** list steps, B-roll, product shots. **Avoid when:** the subject needs more than 0.83 of the frame width.
**Geometry / Graphics:** see 1.3; ink grid at 16 %.
**Motion:** numeral N1, circle K1, rail at the top.
**Footage / plate behaviour:** cover-fit into 600×512; anchor ✎.
**Captions during it:** C1 at size 60, ink with Signal red keyword.
**Exit:** X1.
**Flow prompt text:** "A warm off-white page with faint grid lines. The picture sits in a rectangle that runs off the right edge. A giant red number stands at the lower left and the words appear to its right in bold black, with a small red circle on the picture's top left corner."
**Still-image state:** as described.

### P3 · RED TOWER — P mid (design, not measured)
**What it is:** red field, tall footage module on the right bleeding off the top and right edge, a giant white numeral on the left, caption below.
**Use when:** list steps, phone or product shots, portrait B-roll. **Avoid when:** the subject is wide (a landscape source loses its sides).
**Geometry / Graphics:** see 1.3.
**Footage / plate behaviour:** cover-fit into 480×640; anchor ✎.
**Captions during it:** C1 at size 84.
**Exit:** X1.
**Flow prompt text:** "A flat bold red page with thin white grid lines. A tall picture fills the upper right; a giant white number stands to its left; a few huge white words sit below, with a small red circle over the picture's lower part."
**Still-image state:** as described.

### C1 · FLUSH-LEFT STACK — C high (signature caption; chunking and look from the red poster, motion design)
**What it is:** the caption system. Chunks of 3–5 words are set flush left in a tight bold stack. Words appear one by one at their spoken time and never move.
**Use when:** all captions. **Avoid when:** none.
**Text (✎):** the user's own words, exact case and punctuation, 3–5 words per chunk, ≤ 3 lines, split at punctuation, never end a chunk on an article, preposition or conjunction (an unavoidable exception is allowed when a chunk must break at a cut). One keyword per chunk at most: ink on red, Signal red on paper.
**Geometry / Graphics:** font size, x and block anchor per layout (1.3); tracking −0.035em; leading 0.98; line breaks greedy by measured width; block bottom-anchored on red layouts (y 1176), top-anchored on paper (y 676).
**Motion:** word hard-cut in at its start time; chunk hard-cut out at max(last word end + 0.1, …) but ≥ 0.05 s before the next chunk; minimum 0.4 s.
**Footage / plate behaviour:** none; captions never touch footage.
**Exit:** hard cut.
**Build notes:** lay out the whole chunk first, draw only words with start ≤ t at their final positions. A chunk crossing a cut is re-laid in the new layout on the cut frame.
**Flow prompt text:** "The speaker's words appear one at a time in very large, tight, bold letters stacked at the left edge, white on red or black on paper, with one word per phrase in a contrasting colour. Words pop in with no movement and the whole phrase disappears at once."
**Still-image state:** the whole headline stack shown.

### N1 · STEP NUMERAL — N high (signature, design, not measured)
**What it is:** one huge digit marks each list step, rising from its baseline.
**Use when:** 2–5 parallel steps ("first", "second", three actions). **Avoid when:** no list; never for a single idea.
**Text (✎):** the step number as a single digit, the only numerals in the style.
**Geometry / Graphics:** Inter Black 352 px; red on paper at x 30, top y 672; white on red at x 24, bottom on y 634.
**Motion:** clip rises from the baseline in 0.34 s, expo out, starting 0.10 s after the layout starts.
**Exit:** leaves with the layout in X1.
**Flow prompt text:** "A single giant bold number {{STEP}} rises from the bottom of its space like a printed poster numeral, large enough to be read at a glance, and stays still."
**Still-image state:** digit fully shown.

### K1 · RED DOT — K high (signature, design, not measured)
**What it is:** one flat circle in Signal red that grows from nothing and sits over a module corner.
**Use when:** every layout (one per layout). **Avoid when:** it would cover a face; move it to another module corner.
**Geometry / Graphics:** diameter 92 px; centres per layout in 1.3.
**Motion:** scale 0 → 1, 0.30 s expo out, 0.12 s after the layout starts.
**Flow prompt text:** "A small flat red circle grows from a point and rests over one corner of the picture."

### X1 · MODULE SWAP — X high (signature, design, not measured)
**What it is:** the cut beat. A 5 px ink edge sweeps left to right; left of it the new layout, right of it the old layout (still playing the new shot) until the edge passes.
**Use when:** every footage cut (change layout and field colour each time; never two cuts in a row with the same layout). **Avoid when:** no cuts exist; use P-layout changes at sentence boundaries instead.
**Motion:** edge x = W × (1−2^(−10u)), u = 0→1 over 0.33 s from the cut frame.
**Footage / plate behaviour:** both sides show the live current shot.
**Captions during it:** each side shows its own layout's caption.
**Exit:** edge leaves at the right.
**Build notes:** render the old and new layout for the same frame and paste the new layout's columns 0..edge over the old layout.
**Flow prompt text:** "On every cut, a thin black line sweeps quickly across the frame from left to right and the layout behind it changes to a new arrangement of the same picture, with a new flat colour page."

### M1 · META RAIL — M low (design, not measured)
**What it is:** a hairline across the text width with a solid progress fill and a tiny "01 / 06" shot counter.
**Use when:** every layout (bottom on red, top on paper). **Text (✎):** counter digits only.
**Geometry / Graphics:** 1 px hairline at 47 % alpha, 3 px fill growing linearly with time; label 16 px weight 700.
**Flow prompt text:** "A thin line across the page shows the progress of the video, with a tiny counter of the current shot beside it."

### E1 · GIANT CLOSER — E high (signature, design, not measured)
**What it is:** the last line at 118 px, bigger than any other caption, over the red field; footage keeps playing in the top 50 %.
**Use when:** the payoff or call to action, last 1–2.5 s. **Avoid when:** the final line is longer than 5 words (use P1).
**Text (✎):** last line, 2–4 words.
**Geometry / Graphics:** module 0,0,720,640; field below; caption block bottom-anchored on 1176.
**Motion:** entered by X1; C1 word cuts.
**Exit:** holds to the end.
**Flow prompt text:** "For the final line the picture shrinks to the top half and the last words fill the red page in enormous white letters, with the speaker still talking and visible above."

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + P1 | X1 alternating P2 and P3 with N1 per list step, K1, M1 | X1 into E1 |
| Single talking head | T1 + P1 | P2/P3 re-laid at sentence boundaries, N1 per point | E1 |
| B-roll only | P3 (T1 grid) | alternate P2/P3/P1 on every cut | E1 |
| Still image | P1 | none | headline stack from C1 |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
