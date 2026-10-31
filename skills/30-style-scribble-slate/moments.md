# moments.md — Scribble Slate: Style Bible + Moment Library

This file is the single source of truth for the Scribble Slate style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, measured on a 304x540, 24 fps, 10.0 s reference reel (one continuous speaker shot with graphic plates) and proven on the 720x1280 demo. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** a hand-doodled notebook look: chalky stacked block title hidden behind the speaker, a wobbly yellow marker outline around the person, tiny handwritten captions with dark label chips and yellow keywords, and a sliced glitch-wipe that drops a charcoal slate or cream paper board over the shot, where the footage sits in a wobbly yellow-framed card among squiggles and doodles.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference and demo ran at 24 fps, so "f" values are 24 fps frames; at another fps keep the seconds. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Marker yellow | #F8CE12 | Outline, card frames, squiggles, smiley, keyword text on dark, keyword chip on paper (measured 248,206,18 on paper; 239,201,14 on slate) |
| Slate | #373737 | Board plate, with faint grain and horizontal streaks (measured 55,55,55) |
| Paper | #F5ECD4 | Board plate, with faint grain (measured ≈ 246,236,208) |
| Chalk white | #F4F1E8 | Title fill and caption words on footage and slate |
| Ink | #1E1E1E | Caption words on paper, text inside yellow chips, cloud doodle, polaroid border (#2D2D2D) |
| Dark chip | #1E1E1E at 85 % | Rounded label behind the newest caption word |
| Word edge | #000000 at 55 % | Thin dark edge around white and yellow words on footage |

Brand-swap rule: if the user gives a brand colour, replace Marker yellow with it (bright enough to read on slate). Slate and paper may swap to the user's dark and light neutrals. No other colours exist.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage (full-frame shots) | 100 % of W and H, untouched. |
| Footage card | Wobbly-edged rectangle (edge jitter ±5.5 px at 720 wide, 14 points per side) rotated −2.5° to +1.6°, with a yellow marker frame (11 px stroke) plus a thin second stroke 4 px at 78 % alpha, 11 px outside the edge. Frame and edge re-jitter 8 times a second (3 variants cycled). Cover-fit of the live shot; crop anchor ✎. |
| Slate card | centre (0.51W, 0.70H), 0.90W × 0.46H, rotation −1.4° (second slate shot: centre 0.50W, rotation +1.6°). May bleed off the edges slightly. |
| Paper card | centre (0.50W, 0.80H), 0.94W × 0.40H, rotation −2.5°. |
| Polaroid | Tilted +8°, 0.56W × 0.34H, centre (0.40W, 0.215H), charcoal sketchy double border (9 px + 4 px). Shows a still or loop of the user's own footage. |
| Outline | 9 px yellow marker line plus a 4 px echo offset (+4, +3) px at 75 % alpha, drawn around the person mask dilated by 15 px, open at the frame edges. |
| Label chip | Rounded rectangle (radius 0.28 × font size), height of the text line + 0.16 em, padding 0.22 em left and right. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Title stack | 0.04, 0.03, 0.96, 0.40 | 3 lines of the title word, each line 0.93W wide, line pitch = 1.42 × cap height; first cap top at 0.03H |
| Footage caption lane | 0.14, 0.52, 0.86, 0.66 centre y 0.585H | C1 on full-frame shots |
| Slate caption lane | 0.11, 0.09, 0.80, 0.30; left aligned at 0.11W, each new line shifts right 0.04W | C2 |
| Paper caption lane | 0.10, 0.39, 0.90, 0.50 centre y 0.435H | C3 |
| Slate squiggles | y 0.40–0.41H, x 0.10–0.44W (first slate shot) or 0.62–0.88W (second) | D1 |
| Paper doodles | smiley centre (0.88W, 0.30H) radius 52 px; cloud centre (0.14W, 0.865H) radius 44 px | D1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Chalky hand-drawn block capitals with scratchy hatching, UPPERCASE | Cabin Sketch Bold (solid chalk fill underneath, hatch tone on top) | Gochi Hand, Anton with a texture | Fit the word to 0.93W; 3 identical lines |
| Caption words | Round handwriting, lowercase or as the user wrote, slightly tilted and bobbing | Gaegu Bold | Gochi Hand, Caveat Brush | 64 px on footage, 66 px on slate, 70 px on paper (≈ 0.09–0.10W); keyword × 1.28; solo keyword (K1) × 1.55 |
| Chip text | same face, yellow or white on dark, ink on yellow | Gaegu Bold | — | same as caption |

Rules: each word has its own random rotation (−4° to +4°, minus 2.5° on footage and paper) and baseline bob (±6 px), fixed per chunk. Word gap 0.32 em. Case as the user wrote it; the title is the only forced uppercase. Never a drop-shadow blur; words on footage get the thin dark edge instead.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Title reveal | ease-out left-to-right reveal, lines staggered 0.125 s | 0.28 s each |
| Title exit | linear alpha fade in place | 0.3 s |
| Outline draw-on | ease-out along the contour from one frame edge over the head to the other | 0.5 s |
| Caption word | ease-out alpha | 4 f (0.17 s) |
| Chunk exit | alpha 1 → 0 | 0.1 s (2–3 f), or hard at a cut |
| Chip | appears with its word, disappears 0.55 s later | — |
| Slice wipe | smoothstep sweep of the edge, top to bottom | 0.5 s (12 f) |
| Doodle draw-on | ease-out along the path | 0.5 s after the plate lands |
| Boil | frame and outline jitter re-seeded 8 times a second | continuous |

Never: bounce, overshoot, spring, 3D, blur, colour grading, drop-shadow blur, slides of text, letter-by-letter typing, zoom-punches.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always on speaker and full-frame shots |
| Person cut-out in front of the title (T1) and a marker outline (O1) | Mask smoothed (EMA 0.6/0.4, 1.5 px blur); the cut-out is the same pixels, nothing recoloured |
| Shot shown live inside a card on a plate (P1, P2) | Cover-fit crop only, in sync with the audio; plates last one shot or less; the speaking face is only shown this way when it is the polaroid or a card |
| Secondary window (polaroid) | Only the user's own footage: a still, a ≤ 1.5 s silent loop, or another crop |
| Slice wipe (X1) | 0.5 s, only on the frame of a footage cut |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; colour grading; blur; adding footage the user did not supply.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by captions, chips, outline or doodles. The title sits behind the person, so it can never cover the face. |
| Footage caption lane | Default centre 0.585H. If a face box bottom is below 0.52H, move the lane to 0.66H or to the bottom third. Avoid hands or key objects when possible. |
| Title | Needs a person cut-out. If none is possible, skip T1 and use K1 or a slate board. |
| Outline | Only around a person; skip on shots without one. |
| Edges | Every glyph stays ≥ 0.06W from the left and right edges; the card frame may bleed. |
| Footage text (UI, signs) | Anchor the card crop so readable UI stays inside the card. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **O** outline · **C** caption · **X** transition · **P** plate / board · **D** doodle · **K** keyword · **R** rhythm.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · CHALK TITLE STACK — T ●●● (signature opener)
**What it is:** the topic word appears three times, stacked, in chalky block capitals across the top, and the speaker stands in front of it.
**Use when:** the opening line states the topic and the first shot has a clear person. **Avoid when:** no person cut-out is possible, or the shot has a cut inside 1.5 s.
**Text (✎):** one word from the user's own text (a title word the user supplied is also fine), UPPERCASE, ≤ 8 letters. That word is counted in the caption audit and removed from the chunks.
**Geometry / Graphics:** Title stack. Font size so the word is 0.93W wide. Three lines, cap top of line 1 at 0.03H, pitch 1.42 × cap height. Fill chalk white with a faint hatch tone and a soft dark offset (+3, +5 px) behind. Person mask composited over the title.
**Motion (measured on the reference, 24 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.05–0.33 ✎ | line 1 | left-to-right reveal | 0 → 100 % | ease-out |
| 0.18–0.46 | line 2 | reveal | 0 → 100 % | ease-out |
| 0.30–0.58 | line 3 | reveal | 0 → 100 % | ease-out |
| 0.58–1.45 ✎ | stack | hold | final state | — |
| 1.45–1.75 ✎ | stack | alpha | 1 → 0 | linear |

**Footage / plate behaviour:** untouched; the person stays in front.
**Captions during it:** C1 below, from the first spoken word after the title word.
**Exit:** 0.3 s linear fade; must finish ≥ 0.1 s before a cut.
**Build notes:** MediaPipe selfie segmenter in VIDEO mode, EMA mask, Gaussian blur 1.5 px, then `out = title_composite * (1-m) + frame * m`. Render each of the 3 lines once.
**Flow prompt text:** "At the very start, the word {{TITLE}} is written three times, one under the other, across the top of the frame in chalky hand-drawn white block capitals. The speaker stands in front of the letters, so the letters are partly hidden behind their head and shoulders. After about a second and a half the letters fade away."
**Still-image state:** full stack visible, subject in front.

### O1 · SCRIBBLE OUTLINE — O ●●● (signature)
**What it is:** a wobbly yellow marker line draws itself around the person's head and shoulders and keeps boiling.
**Use when:** a speaker shot carries an emphasis line, the payoff, or a calm hold ≥ 1 s. **Avoid when:** no person is visible; another big move starts within 0.5 s.
**Text (✎):** none.
**Geometry / Graphics:** contour of the person mask, mask dilated by 15 px, off-frame-edge parts removed, resampled to 240 points, displaced by two sine waves (±5 px and ±3 px, 7 and 17 cycles around the arc), phase re-seeded 8 times a second. Stroke 9 px yellow + echo 4 px at +4,+3 px.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start ✎ | outline | arc length drawn | 0 → 100 % | ease-out, 0.5 s |
| after | outline | boil | continuous (8 fps) | — |
| shot end | outline | hard cut with the shot | — | — |

**Footage / plate behaviour:** untouched; outline sits outside the mask, never over the face.
**Captions during it:** C1 continues; the outline passes behind caption chips.
**Exit:** leaves with the shot (hard cut).
**Build notes:** `cv2.findContours` on the thresholded, blurred mask; roll the contour to start on a frame-edge point; take the longest off-edge run; draw with `cv2.polylines(..., LINE_AA)` twice.
**Flow prompt text:** "A wobbly hand-drawn yellow marker line draws itself around the speaker's head and shoulders, starting at one side and going over the top to the other side, and keeps trembling slightly like a doodle. It never covers the face."
**Still-image state:** fully drawn.

### C1 · DOODLE CAPTION — C ●● (signature, the caption system)
**What it is:** small handwritten words pop in one by one on a loose, slightly tilted line over the footage. The newest word sits on a dark rounded chip, one keyword per chunk is yellow and bigger.
**Use when:** always on full-frame shots (speaker or B-roll). **Avoid when:** the lane is covered by a plate (use C2 or C3).
**Text (✎):** the user's exact words, case as written. 2–5 words per chunk, ≤ 28 characters, split at punctuation, never end on an article, preposition or conjunction; prefer chunk changes at cuts. 1 keyword per chunk (≤ 1 in 2 chunks is fine), never an article.
**Geometry / Graphics:** Footage caption lane, centred, max width 0.72W, wrap to a second line at pitch 1.35 em. 64 px words, keyword 1.28×. White words with the thin dark edge, keyword yellow. Chip: dark, behind the newest word for 0.55 s.
**Motion (measured on the reference):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | word | alpha | 0 → 1 | ease-out, 4 f |
| word start | chip | on for 0.55 s then off | — | hard |
| chunk end ✎ | all words | alpha | 1 → 0 | 0.1 s, or hard at a cut |

Word start = the word's spoken start. Chunk end = next chunk's first word start, or min(last word start + 0.7 s, next cut).
**Footage / plate behaviour:** untouched.
**Exit:** 0.1 s fade or hard cut.
**Build notes:** lay out the whole chunk first (positions and rotations seeded by chunk index), render each word once at 2×, cache by (text, size, colour, rotation, chip).
**Flow prompt text:** "Near the middle of the lower half of the frame, small handwritten captions pop in one word at a time on a loose, slightly tilted line. Ordinary words are white; one important word, {{KEYWORD}}, is yellow and bigger. The newest word sits on a small dark rounded label. When a phrase is done it fades. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### C2 · SLATE CAPTION — C ●● (signature variant for plates)
**What it is:** the same handwriting, left-aligned in the upper left of a slate board, wrapping downwards with each line stepping slightly right.
**Use when:** a slate board (P1) is up. **Avoid when:** no board.
**Text (✎):** as C1.
**Geometry / Graphics:** Slate caption lane, 66 px words, chalk white with dark edge, keyword yellow with chip behind the newest word (chip #1E1E1E on slate reads as a subtle darker patch).
**Motion:** as C1.
**Exit:** 0.1 s fade; hard at the cut that ends the board.
**Flow prompt text:** "In the upper left of the dark board, handwritten white words appear one by one, the key word, {{KEYWORD}}, in yellow, and a second line steps a little to the right. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one chunk.

### C3 · PAPER CAPTION — C ●● (signature variant for paper)
**What it is:** dark handwriting centred on a cream board; the keyword sits on a bright yellow chip with dark text.
**Use when:** a paper board (P2) is up. **Avoid when:** no board.
**Text (✎):** as C1; the yellow keyword is the payoff word of the line.
**Geometry / Graphics:** Paper caption lane, 70 px ink words, no dark chips, keyword on a yellow chip tilted with its word. Lines split after 3 words.
**Motion:** as C1.
**Flow prompt text:** "On the cream paper, handwritten dark words appear one by one in the middle; the key word, {{KEYWORD}}, sits on a bright yellow highlighter patch. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one chunk.

### X1 · SLICE WIPE — X ●●● (signature transition)
**What it is:** a jagged, glitchy edge sweeps down the frame, replacing the footage with a board (or the board with footage).
**Use when:** every footage cut that enters or leaves a board; person → B-roll; B-roll → person. **Avoid when:** two wipes would be < 2 s apart.
**Text (✎):** none.
**Geometry / Graphics:** edge band 0.16H tall. Above the edge = the new layer, below = the old layer. Inside the band: horizontal strips 8–34 px high, each takes the old or new layer (old probability rises towards the bottom) and is shifted sideways by up to ±0.12W; 30 % of strips blend 50/50 with a counter-shifted copy.
**Motion (measured on the reference: slate arrives over 12–14 f, leaves over 10–12 f):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut ✎ → +0.5 s [12] | edge position | −0.16H → H | smoothstep |

Wipe-in: new = board with the live card; old = the shot full frame. Wipe-out: new = the next shot full frame (with its captions); old = the board.
**Footage / plate behaviour:** live footage keeps playing in both layers.
**Captions during it:** none start inside a wipe; end chunks on the cut.
**Exit:** the wipe finishes at the end of its 0.5 s.
**Build notes:** strips re-randomised every frame with `random.Random(frame)`; `np.roll` per strip.
**Flow prompt text:** "At the cut, a jagged glitchy edge sweeps from the top of the frame to the bottom, revealing {{NEW_LAYER}} while the old picture breaks into thin horizontal strips that slide sideways and vanish. The footage keeps playing smoothly."
**Still-image state:** not used.

### P1 · SLATE BOARD — P ●●● (signature)
**What it is:** a charcoal chalkboard plate. The current shot plays live inside a wobbly yellow-framed card in the lower half; captions and a yellow squiggle sit above.
**Use when:** a B-roll shot or a run of 1–2 B-roll shots; a topic or list line. **Avoid when:** a speaking face is in the shot (use a full-frame shot or P2), or the shot lasts < 0.8 s.
**Text (✎):** captions via C2.
**Geometry / Graphics:** slate plate with grain; slate card (1.2); D1 squiggle above the card; two yellow dots.
**Motion:** card and plate arrive with X1. On an inner footage cut the card hard-switches to the other slate card variant (R1).
**Footage / plate behaviour:** the card shows the live shot in sync; crop anchor ✎ (y of the subject, 0.55 default).
**Exit:** X1 wipe-out on the cut that leaves the board.
**Build notes:** card mask from a wobble polygon at 2×; composite footage × mask, then the frame stroke.
**Flow prompt text:** "The shot moves into a wobbly hand-drawn yellow frame on a dark chalkboard-grey background. Handwritten words and a yellow squiggle sit above it. The footage inside the frame keeps playing normally."
**Still-image state:** full board.

### P2 · PAPER BOARD — P ●●● (signature)
**What it is:** a cream notebook-paper plate with a tilted polaroid of the speaker (still), a smiley, a cloud doodle, a yellow-framed live card at the bottom and a centred handwritten line.
**Use when:** the closing step, a time or result phrase, or any B-roll shot after the speaker has been seen. **Avoid when:** no speaker footage exists for the polaroid (use a crop of the best shot).
**Text (✎):** captions via C3.
**Geometry / Graphics:** paper plate; polaroid; paper card (1.2); D1 smiley, cloud and squiggle.
**Motion:** arrives with X1; doodles draw on over 0.5 s.
**Footage / plate behaviour:** card live; polaroid is a still taken from the user's speaker shot (or a ≤ 1.5 s loop). Never a generated image.
**Exit:** X1 wipe-out.
**Flow prompt text:** "The shot moves into a wobbly yellow frame at the bottom of a cream notebook page. Above it a tilted photo of the speaker with a sketchy dark border, a small yellow smiley and a hand-drawn cloud. A short handwritten line sits in the middle, with the key word on a yellow highlighter patch."
**Still-image state:** full board.

### D1 · SQUIGGLE DOODLES — D ● (extension in the same grammar)
**What it is:** small yellow marker doodles that draw on and boil: a wavy line, dots, a smiley.
**Use when:** the board has empty space; a calm beat. **Avoid when:** it would cross a caption or face.
**Text (✎):** none.
**Geometry / Graphics:** squiggle = sine, amplitude 0.006–0.010H, 2.5–3 periods, length 0.26–0.44W, tilt −3° to +3°, stroke 8–9 px yellow; smiley = arc + 2 eye ticks, radius 52 px; cloud = 5 scallops, ink 8 px.
**Motion:** draw-on 0.5 s ease-out, then 1.2 px jitter at 8 fps.
**Flow prompt text:** "A few small hand-drawn yellow doodles, a wavy line and a tiny smiley, draw themselves on the empty space and wobble slightly."
**Still-image state:** drawn.

### K1 · SOLO CHIP KEYWORD — K ●● (extension in the same grammar)
**What it is:** the payoff word is shown 1.55× larger on a dark chip, yellow text, tilted.
**Use when:** the last line or a punch word. **Avoid when:** it would hide a face; at most once per video.
**Text (✎):** the last 1–2 words of the user's text.
**Geometry / Graphics:** as C1 with the keyword at 1.55× and a chip behind it that stays for the whole chunk.
**Motion:** as C1.
**Flow prompt text:** "The final word, {{WORD}}, appears large in yellow handwriting on a dark rounded label, slightly tilted."
**Still-image state:** word and chip.

### R1 · CARD JOLT — R ● (extension in the same grammar)
**What it is:** when the footage cuts inside a board, the card keeps its place but its tilt and wobble re-seed, so the cut reads as a flick of the page.
**Use when:** a second B-roll shot inside P1. **Avoid when:** the cut is the one that leaves the board (use X1).
**Text (✎):** none.
**Geometry / Graphics:** swap the card variant set (rotation −1.4° → +1.6°, centre 0.51W → 0.50W) on the cut frame; no easing.
**Flow prompt text:** "When the picture changes inside the frame, the frame gives a tiny flick to a new angle."
**Still-image state:** not used.

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + C1 | X1 into P1 (C2, D1, R1), X1 out to a full-frame shot with O1, X1 into P2 | X1 out to the speaker with C1, O1, K1 |
| Single talking head | T1 + C1 | O1 on the emphasis line, X1 into a P1 board built from a crop of the same shot for one list line | O1 + K1 |
| B-roll only | P1 with C2 | P2 with C3, X1 on every cut | K1 on a full-frame shot |
| Still image | T1 if a person exists, else P1 | C1 or C2 | K1 |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
