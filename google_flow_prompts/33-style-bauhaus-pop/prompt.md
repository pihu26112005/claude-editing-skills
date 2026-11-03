# Google Flow prompt · Bauhaus Pop
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Bauhaus Pop" motion style to it.

The look in one sentence: Flat orange, cobalt, mustard and cream poster blocks with a stamped condensed banner, cream label-bar captions with the newest word orange, black-edged cards with a retracting extruded shadow, a falling shape curtain to a blue wall.

Re-edit the uploaded video in this style: it may use the layouts, containers, graphics, transitions and captions of the style bible below, but the footage itself (people, scenes, voices, sound, order and timing of shots) is never replaced, recoloured, retimed or reordered.

## 2. INPUTS (fill in before pasting)
VIDEO: the short video uploaded in Flow. This is the only footage you may use; never generate new footage, people or scenes.
SCRIPT (optional): <paste the exact words you want shown as captions, or write NONE>
EXTRA NOTES (optional): <words to emphasise, parts to skip, an accent colour as a hex value, or NONE>

## 3. HOW TO USE THE INPUTS
3.1 SCRIPT is provided (anything other than NONE)
- Use exactly those words, in exactly that order, as the on-screen words. Do not paraphrase, correct, translate, add or drop words (apart from splitting them into caption chunks as the style bible says).
- Ignore all text that is already in the video as a source of words (old captions, subtitles, titles): the script wins.
- Time the words to the speech you hear in the video: each caption chunk appears when its first word is spoken and leaves when its last word ends. If the script and the speech differ, follow the speech's timing and keep the script's words.

3.2 SCRIPT is NONE
- Listen to the audio of the uploaded video and transcribe the speech word for word (same language, same spelling style, keep the speaker's own words, numbers and names). That transcript is the script.
- If the video already shows captions you may read them only as a spelling aid for names and unusual words; never copy their look or position.
- Mark pauses and sentence ends from the audio; they decide where chunks break.

3.3 Existing captions and text from another style (do this BEFORE adding anything)
- Scan the whole uploaded video for burned-in captions, subtitles, karaoke words, titles, lower thirds, emoji or word stickers, progress bars, watermarks and any other text or graphics that a previous edit added on top of the footage.
- Remove all of them completely in every frame where they appear: reconstruct the footage behind them cleanly (no ghost outlines, no smeared or blurred patches, no colour shifts). Original footage must look as if the old text had never been there.
- Keep text that belongs to the scene itself (street signs, shop names, product labels, phone or laptop screens, book covers, clothing prints), unless it is clearly an old caption.
- The reason: this style brings its own captions and graphics. If the old ones stay, the same words appear twice on screen, one in the old look and one in the new look. That must never happen.
- Only after the video is clean, add this style's text and graphics from the script.

3.4 EXTRA NOTES
- Apply them if given (emphasis words, parts to skip, accent colour as a hex value). They never override the hard rules in section 4. If an accent colour is given, swap this style's accent colour for it everywhere; keep neutral colours as they are.

3.5 Audio
- The soundtrack of the uploaded video stays exactly as it is, in sync. Do not generate or add any voice, music or sound of your own.

3.6 Language
- Captions are written in the language that is spoken (or that the script is written in). Keep punctuation as written in the script; for a transcript, add natural punctuation.

## 4. HARD RULES (never break these)
- Footage fidelity: same people, same scenes, same shot order, same timing, same sound. Output length equals input length (within one frame).
- The speaking face is never covered, blurred or distorted while the person speaks.
- Every word on screen comes from the script (or the transcript). Spell it exactly. No extra words, no filler, no lorem ipsum.
- Captions are in sync with the speech: a chunk starts when its first word is spoken.
- Only one caption system is ever visible: old captions are removed first (3.3), then this style's captions are added.
- Use only the fonts, colours, shapes and motion described in the style bible below. Do not mix in other looks.
- Keep everything inside the frame with the style's safe margins.

## 5. HOW TO BUILD THE EDIT (work in this order, silently)
1. WATCH the whole video: list its shots with start and end times (every cut), note who speaks, where the face is in each shot and where the quiet or busy areas of the frame are.
2. PREPARE THE WORDS (section 3): remove old captions, then get the script (given or transcribed) and split it into caption chunks the way the style bible's caption section says (chunk size, line breaks, emphasis words).
3. TIME THE WORDS to the audio: for every chunk, its start and end second.
4. PLACE THE MOMENTS: choose from the moment library below. Use each signature moment where the video gives it a reason (openers on the first words, cut moments on real shot cuts, closers after the last spoken word); use the recommended combinations as starting points, not as a fixed template. Do not use more variety than a short video can carry.
5. CHECK THE SAFE ZONES (style bible): the speaking face is never covered; text stays inside the safe margins; if footage content (a sign, a screen) sits where the caption lane is, move the lane as the style bible says.
6. RENDER the video: every graphic and word appears and disappears exactly as the moments describe (timing, easing and entrance), cut to cut, and stays in sync with the audio.

## 6. STYLE BIBLE
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
| Card | Straight-cornered rectangle, 2 px [4] ink border, extruded shadow down-right at 45°: rest length 0.008W [9], entry length 0.20W [216] shrinking to rest. Footage is cover-fit into it (crop anchor). |
| Banner | Full-width orange bar, 2 px ink edge, height 0.14H [270] in the demo. |
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
| Banner wipe-in | ease-out cubic, width 0 → W | 0.40 s |
| Banner letters | alpha 0 → 1 per letter in random order, 0.125 s each, spread over 0.33 s | 0.45 s |
| Banner exit | slides up, ease-in cubic | 0.40 s |
| Caption word | hard appear (1 f), newest word orange, previous words turn ink | 1 f |
| Caption chunk change | hard cut | 1 f |
| Extrude peel | ease-out cubic: extrusion 0.20W → 0.008W, card scale 0.90 → 1 | 0.30 s |
| Curtain pass | ease-in-out cubic, y from −1.6H to +H | 0.70 s |
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

## 7. MOMENT LIBRARY
Family codes: **T** title · **C** caption · **L** layout · **X** transition · **W** wall · **E** ending.

### MOMENT T1 · BANNER STAMP
**What it is:** an orange bar wipes in from the left at the top; cream condensed letters of the topic pop in one by one in random order; it holds, then slides up.
**Use when:** the opening line names the topic and the video starts on a speaker or calm shot. **Avoid when:** a cut falls in the first 0.4 s, or the face box top is above 0.06H.
**Text:** 1–2 user words, uppercase, ≤ 14 characters; these words are removed from the first caption chunk (audit counts them).
**Geometry / Graphics:** 1.2 Banner, text centred, spans 0.94W.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.10–0.50 | bar | width | 0 → W | ease-out |
| 0.22–0.55 | letters | alpha | 0 → 1, random order | linear 0.125 s each |
| 0.55–1.42 | banner | hold | — | — |
| 1.42–1.83 | banner | y | 0 → −banner height | ease-in |

Hold 1.0–3.0 s (reference held 2.6 s). The exit must finish before or on the first cut.
**Footage / plate behaviour:** footage plays full frame, banner covers only the top strip.
**Captions during it:** C1 starts under the banner once the topic words are said.
**Exit:** slides up.
**Flow prompt text:** "A bright orange bar sweeps in from the left across the top of the frame and the word {{TOPIC WORD}} appears in tall cream capital letters, letter by letter in a scrambled order, holds, then slides upward off the frame."
**Still-image state:** orange bar at the top with the cream word spanning almost the full width.

### MOMENT C1 · BAR CAPTIONS
**What it is:** the main caption: words appear one at a time on cream label bars; the newest word is orange, older words ink.
**Use when:** any speech on full-frame footage or on a card. **Avoid when:** the bar lane would cover a face (use C3).
**Text:** user words as written, 2–5 words per chunk, ≤ 2 lines, split at punctuation, never end on an article or preposition.
**Geometry / Graphics:** 1.3 Bar lane; text width limit 0.72W; wrap to a second flush bar.
**Motion:** word hard-appears at its spoken time; chunk replaced at the next chunk start; no easing. Chunk start = first word start (clamp to the cut when a shot changes).
**Footage / plate behaviour:** none.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** measure with `font.getlength`; one rectangle per line; orange only for index = last visible word.
**Flow prompt text:** "Captions appear word by word on cream label strips at the lower middle, dark bold letters, the newest word in orange."
**Still-image state:** two stacked cream bars with the last word orange.

### MOMENT C2 · FLOAT CAPTIONS
**What it is:** plain cream words without a bar, centred between two cards on the orange field.
**Use when:** L1. **Avoid when:** no coloured field behind.
**Text:** 2–4 words, one line, ≤ 0.82W wide.
**Geometry / Graphics:** centre (0.50W, 0.50H), size 0.085W.
**Motion:** words appear at their time, no easing; chunk hard cut.
**Footage / plate behaviour:** none. **Captions during it:** itself. **Exit:** hard cut with the split.
**Build notes:** `anchor="mm"`.
**Flow prompt text:** "Cream words sit in the gap between two photo cards on an orange background, appearing word by word."
**Still-image state:** line of cream text on orange between two cards.

### MOMENT C3 · TAG BEAT
**What it is:** one spoken word at a time in uppercase ink on a small orange box.
**Use when:** a quick list or payoff words, or a bar would cover a face. **Avoid when:** over 6 words in a row.
**Text:** single user words, uppercase.
**Geometry / Graphics:** centre (0.50W, 0.70H), size 0.055W, box padding 0.03W × 0.016H.
**Motion:** each word hard-replaces the last at its start, 0.25–0.4 s each.
**Footage / plate behaviour:** none. **Captions during it:** itself. **Exit:** hard cut.
**Build notes:** box = text width + 2·pad.
**Flow prompt text:** "A small orange box with one capital word in black appears at the lower middle, the word changing with each spoken word."
**Still-image state:** orange tag with one word.

### MOMENT C4 · WALL WORDS
**What it is:** cream words stepping down a left/right staircase on the shape wall.
**Use when:** W1. **Avoid when:** no wall.
**Text:** 1–4 user words.
**Geometry / Graphics:** 1.3 Wall words.
**Motion:** words appear at their time, hard.
**Footage / plate behaviour:** footage hidden by the wall. **Captions during it:** itself. **Exit:** with the wall.
**Build notes:** left aligned at x of the line.
**Flow prompt text:** "Cream words step down the blue wall one after another, alternating right and left."
**Still-image state:** two cream words on blue.

### MOMENT L1 · SPLIT CARDS
**What it is:** orange field with two stacked black-edged cards: the speaker (still, ≤ 1.5 s, or live) above and the current shot live below, C2 caption in the gap.
**Use when:** person → B-roll cut, or a new step while the speaker is still relevant. **Avoid when:** a card would crop a face.
**Text:** C2 words. **Geometry:** 1.3 Split cards. **Footage:** top = last speaker frame (still) or another crop; bottom = live.
**Motion:** hard cut in with X1 peel (0.30 s); on the next cut it ends.
**Captions during it:** C2. **Exit:** hard cut to the next scene.
**Build notes:** cover-crop each card (anchor face for the top card, subject for the bottom).
**Flow prompt text:** "On an orange background two framed photo cards are stacked, the person on top and {{SCENE}} below, with a long black shadow that pulls back."
**Still-image state:** two cards on orange.

### MOMENT L2 · POSTER CARD
**What it is:** one tall card on a mustard field, live footage inside.
**Use when:** a B-roll or phone shot with its own caption. **Avoid when:** the shot has important edge content.
**Text:** C1 on the card. **Geometry:** 1.3 Poster card. **Footage:** live, cover-fit, anchor.
**Motion:** X1 peel at the cut. **Captions during it:** C1 (bar hangs 0.054W outside the card edge). **Exit:** hard cut, curtain (X2) or E1.
**Build notes:** as L1.
**Flow prompt text:** "A tall framed photo card on a mustard yellow background with a long black shadow that pulls back as it lands."
**Still-image state:** card on yellow.

### MOMENT X1 · EXTRUDE PEEL
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

### MOMENT X2 · SHAPE CURTAIN
**What it is:** a tall collage of circles and bars falls from the top to the bottom of the frame; behind it the scene swaps.
**Use when:** a section change or a hard cut worth marking, on B-roll or a non-speaking shot. **Avoid when:** a face is speaking.
**Motion:** collage y = −1.6H → +H, ease-in-out, 0.7 s; the underlay swaps at the midpoint (collage fully covers the frame). Use two passes (in, out) around W1, or a single pass over a cut.
**Footage / plate behaviour:** covered ≤ 0.35 s per pass. **Build notes:** collage pre-rendered 1.6H at 2×. **Exit:** itself.
**Flow prompt text:** "A tall wall of flat shapes, circles and rectangles in orange, mustard, blue, cream and black, sweeps down over the frame like a curtain."
**Still-image state:** collage mid-fall.

### MOMENT W1 · SHAPE WALL
**What it is:** the cobalt wall between two curtain passes, with C4 words.
**Use when:** a list item, a numbers phrase or a punch line on non-speaking footage. **Avoid when:** a speaker would be covered; only once.
**Motion:** hold 0.7–1.0 s between swap points (demo: swap 4.55 s and 5.55 s); a footage cut may happen under it.
**Footage:** hidden. **Build notes:** pre-render once. **Exit:** X2 out.
**Flow prompt text:** "A flat blue field with cream stars, hexagons and soft bumps along the bottom, words stepping across it."
**Still-image state:** blue wall with two words.

### MOMENT E1 · CARD GROW
**What it is:** the final speaker appears in a poster card, then grows to full frame as the field and shadow vanish.
**Use when:** the last shot returns to the speaker after a poster card. **Avoid when:** the last shot is B-roll with no speaker (use plain hold).
**Motion:** cut → X1 peel 0–0.30 s; grow 0.30–0.70 s ease-in-out: rect → full frame, extrusion → 0.
**Footage:** live; face anchor. **Captions:** C1 screen-fixed. **Build notes:** interpolate the rect, `resize(box=…)`.
**Flow prompt text:** "The framed card of the person grows smoothly until it fills the whole frame."
**Still-image state:** card nearly full on yellow.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + C1 | L1 on first cut, L2 on later B-roll, X2/W1 once on a list | E1 |
| Single talking head | T1 + C1 | C3 on key words, C1 | C1 |
| B-roll only | L2 | L1 with two crops, X2/W1 | L2 |
| Still image | banner + L2 | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

## 9. OUTPUT
- One video, vertical 9:16, same duration, frame rate and resolution as the upload (at least 720 x 1280), original audio track unchanged.
- No watermark, no end card, no title card that is not part of the style.

## 10. NEGATIVE PROMPT (avoid all of these)
- Do not change, replace, recolour, retime or reorder the uploaded footage; do not alter anyone's face, body, outfit or voice.
- Do not add any word that is not in the script / transcript; no misspellings, no random gibberish text, no watermarks, no logos, no stock overlays.
- Never show the same words twice (one copy in an old style and one in the new style); never leave remnants, ghosts or blur patches of removed captions.
- Do not cover the speaker's face while they are speaking; do not let any text run outside the frame or sit on the very edge.
- No black bars, no letterboxing, no extra intro or outro, no end card, no added music or voice-over, no sound effects the style does not ask for.
- No glitches, flicker or warping outside what the style bible describes; no 3D lens flares, no cartoon filters, no beauty filters.

## 11. FINAL CHECK (verify before you finish)
- [ ] Old captions and old on-screen text are gone; nothing is ever shown twice.
- [ ] Every word matches the script or transcript, spelled correctly, and starts with the speech.
- [ ] The face is clear while speaking; no text is cut off or outside the margins.
- [ ] The look matches the style bible (colours, type, shapes, motion), and each moment appears the way its description says.
- [ ] Footage, order, timing and audio are unchanged; length matches the upload.
