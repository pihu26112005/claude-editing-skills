# moments.md — Bauhaus Pop: Style Bible + Moment Library

This file is the single source of truth for the Bauhaus Pop style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, measured on a 1080x1920, 30 fps, 33.4 s reference reel and tuned on a 720x1280, 24 fps demo render. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** a flat poster palette (hot orange, cobalt, mustard, cream, ink black) wraps the footage: a condensed cream banner stamps in at the top, captions sit on cream label bars with the newest word in orange, footage drops into black-edged cards with a long extruded shadow that peels back, and a falling curtain of circles and bars wipes to a blue shape wall.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. Reference ran at 30 fps; the demo at 24 fps, so keep seconds when the fps differs. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Hot orange | #FD3B00 | Banner, split-card field, newest caption word, tag box, curtain panels |
| Cobalt | #0C4CE8 | Shape wall, curtain circles |
| Mustard | #F5B000 | Poster-card field, curtain bands |
| Cream | #E1D3BC | Caption bars, banner letters, floating words, wall shapes |
| Ink | #1B1A1C | Caption text, card edges, extruded shadow, tag text |

Brand-swap rule: a user brand colour replaces Hot orange (keep it saturated); the other four stay. Never add colours, gradients or photos to the graphics.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage default | Full frame, untouched. |
| Card | Straight-cornered rectangle, 2 px [4] ink border, extruded shadow down-right at 45°: rest length 0.008W [9], entry length 0.20W [216] shrinking to rest. Footage is cover-fit into it (crop anchor ✎). |
| Banner | Full-width orange bar, 2 px ink edge, height 0.14H [270] in the demo (reference 0.196H [376]; ≤ face top − 0.01H). |
| Caption bar | One cream rectangle per line, flush stacked, each as wide as its own text + 2 × 0.026W [28] padding, line height 0.073H [140]. |
| Curtain | A collage 1.6H tall: orange, mustard and cobalt bands with a cream disc, an ink disc, cobalt and cream ellipses, ink band at the leading edge. Solid, no gaps. |
| Wall | Full-frame cobalt with 12-point cream stars, cream hexagons, one small orange 5-point star, cream blob tops along the bottom edge. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Split top card | 0.095, 0.059, 0.905, 0.449 | Speaker or earlier shot |
| Split bottom card | 0.095, 0.554, 0.905, 0.944 | Current footage |
| Split caption | centre x 0.50, y 0.50 | Floating words between cards |
| Poster card | 0.098, 0.050, 0.915, 0.945 | Single portrait card |
| Bar lane | x0 0.044, top y 0.625 (grows down by line height) | Bar captions |
| Tag | centre x 0.50, y 0.70 | Single-word beats |
| Wall words | line k at y = 0.56H + 0.075H·k, x = 0.52W (even k) or 0.12W (odd k), left aligned | Wall captions |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Banner | Tall condensed caps, cream, tight | Anton | Bebas Neue, Barlow Condensed Bold | Font size so the line spans 0.94W; cap height ≈ 0.55 of banner height |
| Bar caption | Bold geometric sans, mixed case as written, ink; newest word orange | DM Sans Bold (wght 700) | Plus Jakarta Sans Bold, Manrope Bold | 0.093W [100] |
| Float and wall words | Same sans, cream, no box | DM Sans Bold | same | 0.085W [92] |
| Tag | Same sans ExtraBold, UPPERCASE, ink on orange box | DM Sans ExtraBold | Poppins Bold | 0.055W [60]; box pad 0.03W × 0.016H |

Rules: only banner and tag text is uppercase. Letter-spacing ≈ −0.02em on captions. No outlines, no shadows on text.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Banner wipe-in | ease-out cubic, width 0 → W | 0.40 s (reference 0.07–0.5 s) |
| Banner letters | alpha 0 → 1 per letter in random order, 0.125 s each, spread over 0.33 s | 0.45 s |
| Banner exit | slides up, ease-in cubic | 0.40 s |
| Caption word | hard appear (1 f), newest word orange, previous words turn ink | 1 f |
| Caption chunk change | hard cut | 1 f |
| Extrude peel | ease-out cubic: extrusion 0.20W → 0.008W, card scale 0.90 → 1 | 0.30 s |
| Curtain pass | ease-in-out cubic, y from −1.6H to +H | 0.70 s (reference 0.8–0.9 s) |
| Card grow | ease-in-out cubic to full frame, extrusion → 0 | 0.40 s |

Never: bounce, spring, tilt, text outlines, gradients, glow, shake, zoom punches, blur, footage colour changes.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Default |
| Cover-fit crop into a card | Primary shot stays live; speaker still in a secondary card ≤ 1.5 s |
| Curtain and wall covering a shot | Wall hold ≤ 1.0 s, total cover ≤ 1.7 s, never on a speaking face, only once per 8 s |
| Banner over the top strip | Never over the face box |

Forbidden: replacing, regenerating, retiming, trimming, reordering, recolouring, blurring or filtering footage; adding footage the user did not supply.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by banner, bar, tag, curtain or wall. Banner height shrinks to keep ≥ 0.01H above the face box top. |
| Bar lane | If the chin is below 0.60H, move the bar lane to start 0.03H under the chin; if it would pass 0.85H use tags. |
| Cards | A card must show the face of a speaker fully (crop anchor = face). |
| Edges | Text stays ≥ 0.04W from the edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **C** caption · **L** layout · **X** transition · **W** wall · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · BANNER STAMP — T ●● (signature opener)
**What it is:** an orange bar wipes in from the left at the top; cream condensed letters of the topic pop in one by one in random order; it holds, then slides up.
**Use when:** the opening line names the topic and the video starts on a speaker or calm shot. **Avoid when:** a cut falls in the first 0.4 s, or the face box top is above 0.06H.
**Text (✎):** 1–2 user words, uppercase, ≤ 14 characters; these words are removed from the first caption chunk (audit counts them).
**Geometry / Graphics:** 1.2 Banner, text centred, spans 0.94W.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.10–0.50 ✎ | bar | width | 0 → W | ease-out |
| 0.22–0.55 ✎ | letters | alpha | 0 → 1, random order | linear 0.125 s each |
| 0.55–1.42 ✎ | banner | hold | — | — |
| 1.42–1.83 ✎ | banner | y | 0 → −banner height | ease-in |

Hold ✎ 1.0–3.0 s (reference held 2.6 s). The exit must finish before or on the first cut.
**Footage / plate behaviour:** footage plays full frame, banner covers only the top strip.
**Captions during it:** C1 starts under the banner once the topic words are said.
**Exit:** slides up.
**Build notes:** draw bar on an RGB layer with a mask (mask width = wipe); letters as separate RGBA layers composited with alpha.
**Flow prompt text:** "A bright orange bar sweeps in from the left across the top of the frame and the word {{TOPIC WORD}} appears in tall cream capital letters, letter by letter in a scrambled order, holds, then slides upward off the frame."
**Still-image state:** orange bar at the top with the cream word spanning almost the full width.

### C1 · BAR CAPTIONS — C ●● (signature)
**What it is:** the main caption: words appear one at a time on cream label bars; the newest word is orange, older words ink.
**Use when:** any speech on full-frame footage or on a card. **Avoid when:** the bar lane would cover a face (use C3).
**Text (✎):** user words as written, 2–5 words per chunk, ≤ 2 lines, split at punctuation, never end on an article or preposition.
**Geometry / Graphics:** 1.3 Bar lane; text width limit 0.72W; wrap to a second flush bar.
**Motion:** word hard-appears at its spoken time; chunk replaced at the next chunk start; no easing. Chunk start ✎ = first word start (clamp to the cut when a shot changes).
**Footage / plate behaviour:** none.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** measure with `font.getlength`; one rectangle per line; orange only for index = last visible word.
**Flow prompt text:** "Captions appear word by word on cream label strips at the lower middle, dark bold letters, the newest word in orange."
**Still-image state:** two stacked cream bars with the last word orange.

### C2 · FLOAT CAPTIONS — C ●
**What it is:** plain cream words without a bar, centred between two cards on the orange field.
**Use when:** L1. **Avoid when:** no coloured field behind.
**Text (✎):** 2–4 words, one line, ≤ 0.82W wide.
**Geometry / Graphics:** centre (0.50W, 0.50H), size 0.085W.
**Motion:** words appear at their time, no easing; chunk hard cut.
**Footage / plate behaviour:** none. **Captions during it:** itself. **Exit:** hard cut with the split.
**Build notes:** `anchor="mm"`.
**Flow prompt text:** "Cream words sit in the gap between two photo cards on an orange background, appearing word by word."
**Still-image state:** line of cream text on orange between two cards.

### C3 · TAG BEAT — C ●●
**What it is:** one spoken word at a time in uppercase ink on a small orange box.
**Use when:** a quick list or payoff words, or a bar would cover a face. **Avoid when:** over 6 words in a row.
**Text (✎):** single user words, uppercase.
**Geometry / Graphics:** centre (0.50W, 0.70H), size 0.055W, box padding 0.03W × 0.016H.
**Motion:** each word hard-replaces the last at its start, 0.25–0.4 s each.
**Footage / plate behaviour:** none. **Captions during it:** itself. **Exit:** hard cut.
**Build notes:** box = text width + 2·pad.
**Flow prompt text:** "A small orange box with one capital word in black appears at the lower middle, the word changing with each spoken word."
**Still-image state:** orange tag with one word.

### C4 · WALL WORDS — C ●●
**What it is:** cream words stepping down a left/right staircase on the shape wall.
**Use when:** W1. **Avoid when:** no wall.
**Text (✎):** 1–4 user words.
**Geometry / Graphics:** 1.3 Wall words.
**Motion:** words appear at their time, hard.
**Footage / plate behaviour:** footage hidden by the wall. **Captions during it:** itself. **Exit:** with the wall.
**Build notes:** left aligned at x of the line.
**Flow prompt text:** "Cream words step down the blue wall one after another, alternating right and left."
**Still-image state:** two cream words on blue.

### L1 · SPLIT CARDS — L ●●● (signature)
**What it is:** orange field with two stacked black-edged cards: the speaker (still, ≤ 1.5 s, or live) above and the current shot live below, C2 caption in the gap.
**Use when:** person → B-roll cut, or a new step while the speaker is still relevant. **Avoid when:** a card would crop a face.
**Text (✎):** C2 words. **Geometry:** 1.3 Split cards. **Footage:** top = last speaker frame (still) or another crop; bottom = live.
**Motion:** hard cut in with X1 peel (0.30 s); on the next cut it ends.
**Captions during it:** C2. **Exit:** hard cut to the next scene.
**Build notes:** cover-crop each card (anchor ✎ face for the top card, subject for the bottom).
**Flow prompt text:** "On an orange background two framed photo cards are stacked, the person on top and {{SCENE}} below, with a long black shadow that pulls back."
**Still-image state:** two cards on orange.

### L2 · POSTER CARD — L ●●
**What it is:** one tall card on a mustard field, live footage inside.
**Use when:** a B-roll or phone shot with its own caption. **Avoid when:** the shot has important edge content.
**Text (✎):** C1 on the card. **Geometry:** 1.3 Poster card. **Footage:** live, cover-fit, anchor ✎.
**Motion:** X1 peel at the cut. **Captions during it:** C1 (bar hangs 0.054W outside the card edge). **Exit:** hard cut, curtain (X2) or E1.
**Build notes:** as L1.
**Flow prompt text:** "A tall framed photo card on a mustard yellow background with a long black shadow that pulls back as it lands."
**Still-image state:** card on yellow.

### X1 · EXTRUDE PEEL — X ●●● (signature, every card entry)
**What it is:** on a cut into a card scene, the card's black extruded shadow starts long and retracts while the card scales up.
**Use when:** every cut into L1 or L2. **Avoid when:** no cards.
**Geometry / Graphics:** extrusion at 45° down-right, hull of the card rect and the same rect shifted by e.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.30 | shadow | length | 0.20W → 0.008W | ease-out |
| 0–0.30 | card | scale | 0.90 → 1 | ease-out |

**Footage / plate behaviour:** live. **Exit:** none. **Build notes:** polygon at 2× then downscale as a mask. **Flow prompt text:** "The card lands with a long black diagonal shadow that retracts quickly to a thin edge."
**Still-image state:** card with thin shadow.

### X2 · SHAPE CURTAIN — X ●●● (signature)
**What it is:** a tall collage of circles and bars falls from the top to the bottom of the frame; behind it the scene swaps.
**Use when:** a section change or a hard cut worth marking, on B-roll or a non-speaking shot. **Avoid when:** a face is speaking.
**Motion:** collage y = −1.6H → +H, ease-in-out, 0.7 s; the underlay swaps at the midpoint (collage fully covers the frame). Use two passes (in, out) around W1, or a single pass over a cut.
**Footage / plate behaviour:** covered ≤ 0.35 s per pass. **Build notes:** collage pre-rendered 1.6H at 2×. **Exit:** itself.
**Flow prompt text:** "A tall wall of flat shapes, circles and rectangles in orange, mustard, blue, cream and black, sweeps down over the frame like a curtain."
**Still-image state:** collage mid-fall.

### W1 · SHAPE WALL — W ●●
**What it is:** the cobalt wall between two curtain passes, with C4 words.
**Use when:** a list item, a numbers phrase or a punch line on non-speaking footage. **Avoid when:** a speaker would be covered; only once.
**Motion:** hold 0.7–1.0 s between swap points (demo: swap 4.55 s and 5.55 s); a footage cut may happen under it.
**Footage:** hidden. **Build notes:** pre-render once. **Exit:** X2 out.
**Flow prompt text:** "A flat blue field with cream stars, hexagons and soft bumps along the bottom, words stepping across it."
**Still-image state:** blue wall with two words.

### E1 · CARD GROW — E ●●
**What it is:** the final speaker appears in a poster card, then grows to full frame as the field and shadow vanish.
**Use when:** the last shot returns to the speaker after a poster card. **Avoid when:** the last shot is B-roll with no speaker (use plain hold).
**Motion:** cut → X1 peel 0–0.30 s; grow 0.30–0.70 s ease-in-out: rect → full frame, extrusion → 0.
**Footage:** live; face anchor. **Captions:** C1 screen-fixed. **Build notes:** interpolate the rect, `resize(box=…)`.
**Flow prompt text:** "The framed card of the person grows smoothly until it fills the whole frame."
**Still-image state:** card nearly full on yellow.

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + C1 | L1 on first cut, L2 on later B-roll, X2/W1 once on a list | E1 |
| Single talking head | T1 + C1 | C3 on key words, C1 | C1 |
| B-roll only | L2 | L1 with two crops, X2/W1 | L2 |
| Still image | banner + L2 | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
