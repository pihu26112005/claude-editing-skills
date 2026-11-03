# Google Flow prompt · Mist Rise
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Mist Rise" motion style to it.

The look in one sentence: White serif captions fading in word by word with italic emphasis, long soft dissolves between shots, a feathered band of B-roll rising like mist while the speaker lifts upward.

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
| Caption ink | #FFFFFF | Every caption word, regular and italic. Measured: pure white on the reference. |
| Caption shadow | #000000 at 30–35 % | Soft shadow under all caption glyphs (blur σ 6 px [1080], offset 0 / +2 px). Measured: the ring 5–7 px outside a glyph is ~17 % darker than bright footage around it. |
| Caption halo | #FFFFFF at 35–45 % | Thin glow hugging the glyphs (blur σ 3 px [1080]). Measured: on dark footage the 3–4 px ring is lifted by ~30 levels. |
| Footage | untouched | No grade, no tint, no overlay colour, no vignette, no grain. |

Brand-swap rule: there is no accent colour in this style. If the user supplies an ink colour, change only "Caption ink" and keep the shadow so contrast stays readable. Never add a second colour, a box, a bar or a sticker.

### 1.2 Containers / Shapes

There are no cards, frames, borders, rounded corners or drop shadows on footage. Footage is always shown edge to edge (cover-fit, centred unless a crop anchor is given). Only two stack states exist.

| State | Primary shot | Plate (secondary) | Notes |
|---|---|---|---|
| L-FULL | full-frame, cover-fit, live | none | Default state. |
| L-SPLIT | full-frame, live, lifted up by U = 0.2125 H [408 px] | frozen still of the user's own footage, full-frame cover-fit at about 1.2x scale, crop anchor (default: centred horizontally, weighted toward the lower middle of the source frame), revealed through a vertical feather mask | Measured final state, held 2.8 s on the reference. |

Plate mask (L-SPLIT): alpha 0 above y = 0.47 H [900], alpha 1 below y = 0.57 H [1100], smoothstep between. Mask midpoint M = 0.52 H [1000]. The mask is vertical only: no left or right edge, no hard line, no outline.

Plate pixels do not move while the band is held: the plate is a still, and the mask edge is what travels.

### 1.3 Layouts / Grid

| Name | Region | x0, y0, x1, y1 (fractions) |
|---|---|---|
| Full frame | L-FULL shot | 0, 0, 1, 1 |
| Lifted primary zone | L-SPLIT upper area (visible primary) | 0, 0, 1, 0.52 |
| Plate zone | L-SPLIT lower area | 0, 0.52, 1, 1 |
| Caption zone (anchor A1) | all captions | 0.12, 0.64, 0.88, 0.78 (first-line baseline 0.6875 H) |
| Caption zone (anchor A2, fallback) | when A1 covers a face, mouth or key object | 0.12, 0.76, 0.88, 0.90 (first-line baseline 0.80 H [1536]) |
| Caption zone (anchor A3, last resort) | when A1 and A2 both collide | 0.12, 0.14, 0.88, 0.28 (first-line baseline 0.20 H [384]) |

A2 and A3 are design decisions consistent with the measured caption grammar (same size, same fade, same placement rules inside the zone).

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption (regular) | sentence case exactly as the user wrote it, white, soft shadow + halo | EB Garamond Regular | Cormorant Garamond Medium, Crimson Pro Regular, Lora Regular | 0.0926 W [100 px]; cap height 0.061 W [66 px] |
| Caption emphasis | same family, italic, same size, same ink | EB Garamond Italic | Cormorant Garamond Medium Italic, Crimson Pro Italic, Lora Italic | 0.0926 W [100 px] |
| Number beat (LST-1) | italic numeral, same ink and shadow | EB Garamond Italic | same as above | 0.074 W [80 px] |

Caption rules:

| Property | Value |
|---|---|
| Line pitch | 1.0 x font size [100 px] |
| Letter-spacing | 0 to +0.01 em |
| Alignment | lines of a block are centred on each other within ±0.1 W; the whole block is placed by its centre x |
| First-line baseline (A1) | 0.6875 H [1320 px]; ascender top 0.651 H [1250 px]. Identical in L-FULL and L-SPLIT. |
| Block centre x | any value in 0.38–0.68 W |
| Ink limits | all glyphs inside x 0.12–0.88 W [130–950 px] |
| Max line width | 0.67 W [725 px] |
| Chunk size | 1–5 words, at most 34 characters, at most 2 lines |
| Line break | after a comma or clause boundary when there is one; otherwise near 19 characters |
| Layout | the full chunk layout is fixed before the first word appears; words appear in place and nothing reflows or shifts |
| Case | never uppercase; never change the user's capitalisation or punctuation |

Horizontal stagger: consecutive chunks change block centre by 0.03–0.15 W. Choose the side away from the speaker's face, hands or the main object. The vertical position never changes.

Landscape and square sources: size = 0.052 x H, first-line baseline 0.78 H, block centre x 0.40–0.60 W, max line width 0.60 W, ink inside x 0.15–0.85 W. L-SPLIT is not used on landscape unless the user's subject is centred; then U = 0.17 H and M = 0.58 H.

### 1.5 Motion language

| Family | Easing | Typical duration | Used by |
|---|---|---|---|
| Word fade | ease-out, stepped (see CAP-1 table) | 4 f (0.13 s) | every caption word |
| Chunk exit | hard cut | 1 f | every caption chunk |
| Dissolve | ease-in-out, midpoint at 50–55 % of duration | 21–22 f (0.70–0.73 s) | DIS-1 |
| Lift (primary moves up) | ease-out quadratic | 45 f (1.5 s) | SPL-1 |
| Mist reveal (mask edge rises) | ease-out cubic | 32–34 f (1.1 s) | SPL-1, DIS-2 |
| Plate swap | ease-in-out | 12–15 f (0.4–0.5 s) | SPL-4 |

What never happens: no bounce, no overshoot, no scale pop, no text sliding or rotating, no tilt, no camera shake, no zoom punch, no flash, no whip, no hard-edged wipe, no coloured shape, no sticker, no box behind text, no uppercase, no per-letter animation, no outline-only text.

Density: the captions give a change every 0.2–0.5 s; structural moves (dissolve, rise) arrive every 2–4 s. Never two structural moves closer than 1.0 s. Never start a structural move within 3 f after a hard footage cut unless the move is the cut's own transition (DIS-1, DIS-2).

### 1.6 What may happen to the user's footage

Allowed:
- Cross-dissolving between the user's own shots at their existing cuts (DIS-1, DIS-2).
- Lifting the live primary shot straight up by at most U = 0.2125 H (SPL moments). Translation only: no scale change.
- Showing a frozen still of the user's own footage as a plate (SPL moments) or as a ghost (DIS-1, DIS-2, ≤ 0.7 s).
- A slow scale settle 1.000 → 1.03 on a long shot (DRF-1).
- Captions on top.

Forbidden: replacing or regenerating any shot, person, face or object; grading, filters or blur on shown footage; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio; moving the plate while it is held; a plate taken from anything except the user's own footage.

The primary window always plays the current footage live and in sync with the audio. Secondary content is only a still (plate or ghost). Footage is never fully hidden: in L-SPLIT the primary stays visible in the upper 0.47 H or more.

### 1.7 Safe zones

- Face rule: the face is never covered, cut or blurred while speaking. In L-SPLIT the eye line must end up at or below 0.08 H after the lift, and the chin must stay at least 0.04 H above the mask start (0.47 H). Lift limit: U_max = min(0.2125 H, eye_line_y − 0.08 H). If U_max < 0.10 H, do not use an SPL moment on that shot.
- Captions use anchor A1 unless a face, mouth, hands doing the main action or the key object sits in the band 0.62–0.80 H; then use A2, then A3.
- Footage text (signs, UI, product labels) that the story depends on must not sit inside the caption zone; if it does, move to the next anchor.
- Captions stay inside x 0.12–0.88 W and never cross the frame edge.
- In L-SPLIT the plate must not contain a face that competes with the speaker; choose a plate still without a face or with the face small.

---

## 7. MOMENT LIBRARY
Family codes: CAP = captions, DIS = shot-to-shot transitions, HLD = holds (quiet states), SPL = split states (mist rise), LST = list beats, DRF = drift.
Energy: E1 = quiet, E2 = medium, E3 = bold.

Signature moments (mandatory in every output): CAP-1, CAP-2, DIS-1 (or DIS-2) on at least one footage cut when the video has any cut, and SPL-1 (or SPL-3 when no B-roll exists) once. A signature move may be skipped only when physically impossible (e.g. DIS-1 on a video with no cuts; SPL on a shot with U_max < 0.10 H).

---

### CAP-1 · SERIF WORD-FADE CAPTIONS — CAP E1 (signature, the caption system)

**What it is:** Short phrases of white serif text sit in the lower third. Each word fades in from a soft blur at the moment it is spoken and then stays perfectly still. The whole phrase disappears in one frame and the next phrase begins after a tiny pause.

**Use when:** every video, from the first spoken word to the last. **Avoid when:** never skipped; only the anchor changes (A1 → A2 → A3).

**Text:** the user's exact words, split into chunks of 1–5 words and at most 34 characters, at most 2 lines, line break after a comma when there is one. Chunk start = first word start. Chunk end = min(last word end + 0.1 s, next chunk start − 0.05 s), minimum 0.4 s. Gap between chunks 2–4 f (0.07–0.13 s), nothing on screen.

**Geometry / Graphics:** font, size, ink, shadow and halo as in 1.1 and 1.4. First-line baseline 0.6875 H [1320]. Block centre x in 0.38–0.68 W, alternating sides from chunk to chunk. Full layout is computed first; words appear in their final positions.

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| w+0 | each word | opacity / blur σ | 0 / 8 px (not yet visible) | — |
| w+1 | each word | opacity / blur σ | 0.25 / 8 px | ease-out |
| w+2 | each word | opacity / blur σ | 0.55 / 5 px | ease-out |
| w+3 | each word | opacity / blur σ | 0.90 / 2 px | ease-out |
| w+4 | each word | opacity / blur σ | 1.00 / 0 px | ease-out |
| chunk end | whole chunk | opacity | 1 → 0 in 1 f | hard cut |
| chunk end → next start | screen | text | none for 2–4 f | — |

w = frame where the word is spoken. Measured on the reference: first word of a chunk reaches full opacity 3–4 f after its first visible frame; chunks were cleared in a single frame; gaps between chunks were 2, 3, 3, 4, 2, 3, 3, 3 f.

**Footage / plate behaviour:** none. Captions sit over L-FULL, dissolves and L-SPLIT with the same position and style.

**Captions during it:** this is the caption system.

**Exit:** hard cut on the chunk end frame.

**Flow prompt text:** "In the lower part of the picture, short phrases of elegant white serif lettering appear one word at a time. Each word fades in from a soft haze over about a tenth of a second and then stays perfectly still. The whole phrase vanishes at once just before the next phrase starts. The phrases sit slightly left or right of centre and change side from phrase to phrase. Only these exact words are ever written: {{CAPTION_PHRASES_IN_ORDER}}. Nothing else is written anywhere."

**Still-image state:** the last chunk fully visible at its anchor, white serif, soft shadow, no animation.

---

### CAP-2 · ITALIC EMPHASIS WORD — CAP E2 (signature, part of the caption system)

**What it is:** Inside a caption phrase, the one or two words that carry the meaning switch to the italic cut of the same font. Nothing else changes: same size, same ink, same fade.

**Use when:** the chunk contains a key action, concept, contrast word, number or payoff word. At least one chunk in two carries an emphasis. **Avoid when:** the candidate is an article, preposition or filler; two emphasis phrases in one chunk; more than two words in one emphasis.

**Text:** 1–2 consecutive words of the chunk. Keep the user's punctuation attached to the word.

**Geometry / Graphics:** italic cut at the same size as regular; italic words sit on the same baseline in the same line; the chunk layout is computed with the italic widths included.

**Motion:** identical to CAP-1 (4 f fade-in, same blur steps). No extra motion, no colour, no weight change, no scale.

**Footage / plate behaviour:** none.

**Captions during it:** part of the caption chunk.

**Exit:** with the chunk.

**Build notes:** build each chunk as a list of (word, style) pairs; measure with the matching font file so spacing is correct across the regular/italic boundary; add a normal space width between words.

**Flow prompt text:** "Inside each phrase, the one or two most important words are written in a slanted italic version of the same serif lettering, at the same size and in the same white. Important words in this video: {{EMPHASIS_WORDS_PER_PHRASE}}."

**Still-image state:** the key word in italic, the rest regular, same line.

---

### CAP-3 · CLOSING WORD — CAP E2

**What it is:** The final caption is a single italic word (or at most two) shown alone, held to the end of the video.

**Use when:** the last line has a payoff, call-to-action or one-word conclusion. **Avoid when:** the last line is a long sentence; then use CAP-1 with CAP-2 and let it hold.

**Text:** the last 1–2 words the user says, italic, exactly as written.

**Geometry / Graphics:** same size, ink and anchor as CAP-1; block centre x 0.40–0.55 W. Measured: closing word spanned x 0.25–0.58 W at the first-line baseline 0.6875 H.

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| w to w+4 | word | opacity / blur σ | 0 / 8 px → 1 / 0 px | as CAP-1 |
| w+4 to end | word | all | still | hold ≥ 0.3 s |

**Footage / plate behaviour:** usually inside L-SPLIT (SPL-1 or SPL-3 already on screen). The primary keeps playing live.

**Captions during it:** it is the caption.

**Exit:** none; the video ends on it. If the video continues, hard cut as CAP-1.

**Build notes:** same as CAP-1 with one italic word.

**Flow prompt text:** "For the last moment, one single word, {{CLOSING_WORD}}, fades in alone in slanted white serif lettering in the lower part of the picture and stays until the video ends."

**Still-image state:** one italic word at the caption anchor.

---

### DIS-1 · SOFT DISSOLVE SWAP — DIS E3 (signature)

**What it is:** At a footage cut the outgoing shot melts into the incoming shot with a long, calm cross-dissolve. No flash, no slide, no zoom.

**Use when:** person → B-roll, B-roll → person, B-roll → B-roll, scene or topic change, a turn word ("but", "instead", "next"). **Avoid when:** the video has no cut; within 1.0 s of another structural move.

**Text:** none.

**Geometry / Graphics:** full-frame blend. Build A: both shots are available around the cut. Build B (afterimage, default for a finished video that only has a hard cut): the incoming shot plays live at full opacity; a still of the outgoing shot's last frame lies on top as a ghost that fades away.

**Motion:**

| Dissolve | Duration | Alpha of incoming shot at f after start |
|---|---|---|
| person → B-roll | 22 f (0.73 s) | 0: 0.03, 2: 0.07, 4: 0.12, 6: 0.19, 8: 0.27, 10: 0.38, 12: 0.50, 14: 0.66, 16: 0.82, 18: 0.93, 20: 0.99, 21: 1.00 |
| B-roll → person | 22 f (0.73 s) | 0: 0.02, 2: 0.07, 4: 0.19, 6: 0.35, 8: 0.50, 10: 0.64, 12: 0.75, 14: 0.83, 16: 0.89, 18: 0.94, 20: 0.97, 22: 1.00 |

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–22 (Build A) | incoming shot | opacity | 0 → 1 (table) | ease-in-out |
| 0–15 (Build B) | ghost still of outgoing last frame | opacity | 0.85 → 0 | ease-out (cubic), duration 0.5 s, cap 0.7 s |

Build A: centre the dissolve so the 50 % point (f 12 of 22) lands on the footage cut ± 0.1 s. Build B: start at the cut frame.

**Footage / plate behaviour:** the incoming shot always plays live in sync with the audio. The ghost is a still, shown ≤ 0.7 s, never replacing live footage. No scale, no move during the dissolve.

**Captions during it:** unchanged; chunks may run across the dissolve. If a chunk gap (2–4 f) falls inside the dissolve, that is ideal but not required.

**Exit:** the dissolve ends fully on the incoming shot.

**Build notes:** pre-extract the last frame of the outgoing shot (frame before the cut) as the ghost; blend with `ghost*a + live*(1-a)` in float32 per frame; use the table for Build A alpha (linear interpolation between listed frames) or `smoothstep` shifted so 50 % lands at 55 % of the duration.

**Flow prompt text:** "At the moment the scene changes from {{OUTGOING_SHOT}} to {{INCOMING_SHOT}}, the two shots melt into each other with a long soft dissolve lasting about three quarters of a second. No flash, no sliding, no zooming. Everything in both shots stays exactly as filmed."

**Still-image state:** a half-way blend of two of the user's images, only when the user supplies two images; otherwise not applicable.

---

### DIS-2 · MIST WIPE SWAP — DIS E3 (extension in the same grammar)

**What it is:** The incoming shot rises into view from the bottom edge through a soft, feathered mask, like mist lifting, while the outgoing shot's last frame stays in the part not yet revealed.

**Use when:** B-roll → B-roll swaps, a topic change, a list step. Use instead of a second DIS-1 so the video does not repeat one transition more than twice. **Avoid when:** the incoming shot is a speaking face (use DIS-1); within 1.0 s of another structural move.

**Text:** none.

**Geometry / Graphics:** same mask as 1.2: feather ±0.05 H, vertical only, no hard edge. The mask edge midpoint travels from 1.05 H to −0.05 H.

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–24 | mask midpoint | y | 1.05 H [2016] → −0.05 H [−96] | ease-out cubic |
| 0–24 | incoming shot | revealed through the mask, live | — | — |
| 0–24 | outgoing last frame | still, visible where the mask has not reached | — | — |

**Footage / plate behaviour:** incoming plays live from f 0. Outgoing is a still, ≤ 0.8 s. Primary is not fully hidden for more than 0.4 s (the reveal covers 50 % of the frame by f 6).

**Captions during it:** unchanged position and style.

**Exit:** incoming full-frame, L-FULL.

**Build notes:** let `mid(t)` be the mask midpoint from the table and `r(y)` = smoothstep((y − (mid(t) − 0.05 H)) / (0.10 H)), which is 0 above the feather and 1 below it. The incoming shot has alpha `r(y)` at row y; the outgoing still shows through with `1 − r(y)`. Rows below the edge are therefore revealed first. Look at frames 3, 8 and 16 of the move to confirm the bottom shows the incoming shot first and no hard line appears.

**Flow prompt text:** "The next shot rises into the picture from the bottom edge like a soft mist lifting, with a gentle blurred edge and no hard line, taking about one second. The previous shot remains visible above it until the mist has passed. Both shots stay exactly as filmed."

**Still-image state:** not applicable.

---

### HLD-1 · QUIET TALK — HLD E1

**What it is:** The base state: one live shot in L-FULL with only captions on it. No other motion. This is where the style rests between moves.

**Use when:** opening line, the first 1–3 s, sections after a structural move. **Avoid when:** longer than 3.5 s without a structural move.

**Text:** captions per CAP-1/CAP-2.

**Geometry / Graphics:** L-FULL. Measured on the reference: 3.7 s of quiet talk at the start before the first dissolve.

**Motion:** none except captions.

**Footage / plate behaviour:** primary live, untouched.

**Captions during it:** anchor A1, staggered block centres.

**Exit:** into DIS-1, DIS-2, SPL-1, SPL-3 or DRF-1.

**Build notes:** nothing to draw except captions.

**Flow prompt text:** "For this part, the original shot plays exactly as filmed with nothing added except the white serif phrases in the lower part of the picture."

**Still-image state:** the photo untouched with the caption block.

---

### HLD-2 · FULL-FRAME B-ROLL HOLD — HLD E1

**What it is:** A B-roll shot plays alone and full-frame between two dissolves, with captions on it.

**Use when:** the story says what something looks like or does; after DIS-1 into B-roll. **Avoid when:** shorter than 1.0 s or longer than 3.5 s.

**Text:** captions per CAP-1/CAP-2.

**Geometry / Graphics:** L-FULL. Measured: 1.8 s of held B-roll between the end of one dissolve (4.43 s) and the start of the next (6.20 s).

**Motion:** none except captions. Optional DRF-1 on a hold longer than 2.5 s.

**Footage / plate behaviour:** live, in sync, untouched.

**Captions during it:** anchor A1. Check legibility on bright footage: raise shadow to 40 % if the background behind the text averages above 170 in luminance.

**Exit:** DIS-1 or DIS-2.

**Build notes:** nothing special.

**Flow prompt text:** "The shot of {{BROLL_SUBJECT}} plays full-frame exactly as filmed, with only the white serif phrases added in the lower part of the picture."

**Still-image state:** the image full-frame with the caption block.

---

### SPL-1 · MIST RISE SPLIT — SPL E3 (signature)

**What it is:** The live speaker slides straight up while a soft band of the user's own B-roll rises from the bottom edge and settles over the lower half. The frame becomes a calm two-layer stack: speaker above, still B-roll below, captions floating on the band.

**Use when:** a turn or step in the story ("next", "then", "here's the part"), the second half of a talking-head video, or any moment a visual example supports the line. **Avoid when:** U_max < 0.10 H; the primary is not a live shot with a face or clear subject in the upper area; within 1.0 s of another structural move.

**Text:** captions per CAP-1; keep the chunk at anchor A1 (it will sit on the plate).

**Geometry / Graphics:** L-SPLIT. Lift U = min(0.2125 H, U_max). Plate = a still of the user's own B-roll shot (or SPL-3 for self-stills). Mask: feather ±0.05 H, midpoint M = 0.52 H at rest.

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| T0 to T0+45 | primary shot | translateY | 0 → −U (−408 px at U = 0.2125 H) | ease-out quadratic. Measured offsets: f1 8, f4 40, f7 96, f10 152, f13 200, f16 248, f19 280, f23 328, f27 360, f31 376, f37 400, f45 408 px |
| T0+1 to T0+34 | mask midpoint | y | 1.05 H → 0.52 H | ease-out cubic. Measured midpoint: f4 0.92 H, f8 0.80 H, f12 0.66 H, f16 0.63 H, f20 0.60 H, f24 0.57 H, f28 0.54 H, f32 0.52 H |
| T0+1 to T0+34 | plate | position | fixed (still, never moves) | — |
| T0+45 onward | stack | all | hold | — |

**Footage / plate behaviour:** the primary keeps playing live and in sync; it only translates. The plate is a frozen frame of the user's footage, never a loop, never generated. The mask edge must stay above the primary's bottom edge at every frame (it does for these curves). Eye line stays at or below 0.08 H.

**Captions during it:** unchanged anchor and style; the chunk that is on screen at T0 stays in place and is not disturbed. Shadow 35–40 % on bright plates.

**Exit:** hold to the end of the video, or SPL-2 / SPL-4.

**Build notes:** pre-render the plate once: cover-fit the chosen still to W×H at about 1.2x with crop anchor, no filters. Per frame: shift the primary up by `U * ease_out_quad(t/45)` (fill revealed bottom rows with the plate, they are always covered by the mask); compute `m(y)` = smoothstep((y − (mid(t) − 0.05 H)) / (0.10 H)); out = primary*(1−m) + plate*m; then draw captions. Use sub-pixel translation via `Image.resize(..., box=floats)` or affine transform to avoid stepping.

**Flow prompt text:** "Over about one and a half seconds the speaker glides smoothly upward in the picture while a soft band of {{BROLL_SUBJECT}} rises from the bottom edge like mist, with a gently blurred top edge and no hard line. It settles over the lower half of the picture as a still image and stays there. The speaker keeps talking exactly as filmed, and the speaker's eyes and mouth stay clearly visible in the upper half. The white serif phrases stay in the lower part of the picture, now over the soft band."

**Still-image state:** upper part: the main image shifted up; lower part: a second crop of the user's image, joined by a soft mist edge; caption block on the band.

---

### SPL-2 · MIST FALL — SPL E2 (extension in the same grammar)

**What it is:** The reverse of SPL-1: the band sinks back below the bottom edge while the speaker glides down to full-frame.

**Use when:** returning to the speaker for a direct address, a section change, or the final line after a B-roll example. **Avoid when:** the video ends within 1.5 s; within 1.0 s of another structural move.

**Text:** captions per CAP-1.

**Geometry / Graphics:** L-SPLIT → L-FULL.

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–36 | mask midpoint | y | 0.52 H → 1.05 H | ease-in-out cubic |
| 0–36 | primary shot | translateY | −U → 0 | ease-in-out cubic |

**Footage / plate behaviour:** primary live; plate still until it leaves; both stay clear of the face.

**Captions during it:** unchanged.

**Exit:** L-FULL, HLD-1.

**Build notes:** same compositor as SPL-1 with the curves reversed and eased in-out.

**Flow prompt text:** "The soft band of {{BROLL_SUBJECT}} sinks smoothly back down out of the picture while the speaker glides back down to fill the whole frame, taking about one second. No hard edges. The speaker is exactly as filmed."

**Still-image state:** not applicable.

---

### SPL-3 · SELF-STILL RISE — SPL E3 (extension in the same grammar)

**What it is:** SPL-1 for videos that have no B-roll: the band shows a frozen frame from another moment of the user's own video.

**Use when:** a single continuous talking head, a product demo from one angle, any shot with no separate B-roll. **Avoid when:** U_max < 0.10 H; the video is shorter than 3 s.

**Text:** captions per CAP-1.

**Geometry / Graphics:** as SPL-1. The plate is a frame of the user's own video taken at least 1.0 s away from the live moment, sharp (highest Laplacian variance in the window), showing a different pose, gesture or object than the live frame. Cover-fit at about 1.2x, crop anchor on the most informative region (hands, object, gesture), not on the face.

**Motion:** same table as SPL-1.

**Footage / plate behaviour:** primary live; plate a still of the user's own footage; never a face crop that duplicates the speaker.

**Captions during it:** as SPL-1.

**Exit:** hold or SPL-2.

**Build notes:** extract 8–12 candidate stills, score by sharpness and difference from the live frame, pick the best, view it before building.

**Flow prompt text:** "Over about one and a half seconds the speaker glides smoothly upward while a soft band rises from the bottom edge showing a frozen moment from earlier in this same video: {{EARLIER_MOMENT_DESCRIPTION}}. The band has a gently blurred top edge and no hard line. The speaker keeps talking exactly as filmed."

**Still-image state:** the image shifted up with a second crop of the same image below, joined by a soft mist edge.

---

### SPL-4 · PLATE SWAP — SPL E2 (extension in the same grammar)

**What it is:** While L-SPLIT is held, the band's still melts into a different still of the user's footage, in the band area only. The speaker above is untouched.

**Use when:** the story moves to a new example or step while the speaker keeps talking; several B-roll shots are available. **Avoid when:** only one plate exists; within 1.0 s of another structural move; more than twice per video.

**Text:** captions per CAP-1.

**Geometry / Graphics:** L-SPLIT; new plate prepared like SPL-1's plate.

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–14 | plate zone | cross-fade old still → new still | 0 → 1 | ease-in-out |

**Footage / plate behaviour:** primary live and unmoved; both plates are stills of the user's own footage.

**Captions during it:** unchanged.

**Exit:** hold L-SPLIT.

**Build notes:** blend the two pre-rendered plates by `a(t)` before masking; the mask stays at M.

**Flow prompt text:** "The soft band at the bottom melts gently into a different still image of {{NEW_BROLL_SUBJECT}} over about half a second while the speaker above keeps talking, unchanged."

**Still-image state:** not applicable.

---

### LST-1 · NUMBER BEAT — LST E2 (extension in the same grammar)

**What it is:** For a list, a small italic numeral appears just above the first line of each step's caption chunk, in the same ink and style.

**Use when:** the user lists steps, tips or reasons ("first… second… third…", "three ways"). **Avoid when:** the list has more than 5 items; numerals are not in the user's words and the user did not give a list.

**Text:** the numeral 1, 2, 3… (numerals allowed only for list counters).

**Geometry / Graphics:** italic, 0.074 W [80 px], same ink, shadow and halo. Left edge aligned with the left edge of the chunk's first line; baseline 0.058 H [112 px] above the first-line baseline.

**Motion:** fades in with the chunk's first word using the CAP-1 4 f curve; leaves with the chunk in the same frame (hard cut).

**Footage / plate behaviour:** none.

**Captions during it:** the chunk is a normal CAP-1 chunk.

**Exit:** with the chunk.

**Build notes:** treat the numeral as a word in the chunk layout (its own layer, no reflow of the other words).

**Flow prompt text:** "Just above each step's phrase, a small slanted white numeral fades in together with the first word: {{LIST_NUMBERS_AND_TIMES}}. It disappears together with the phrase."

**Still-image state:** numeral above the caption block.

---

### DRF-1 · SLOW SETTLE — DRF E1 (extension in the same grammar)

**What it is:** On a long static shot with nothing else happening, the picture grows by at most 3 % over the shot, so it never feels frozen.

**Use when:** a shot lasts more than 2.5 s with no structural move. **Avoid when:** any other move is running; the shot already has camera motion; faces would leave the safe zone (never crop the face).

**Text:** captions per CAP-1.

**Geometry / Graphics:** scale about the subject's centre (default frame centre).

**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| shot start → shot end | shot | scale | 1.000 → 1.030 | linear |

**Footage / plate behaviour:** live, untouched apart from scale ≤ 1.03.

**Captions during it:** unchanged; captions do not scale.

**Exit:** the next moment resets scale to 1.000 at its own start only if it is a hard footage cut.

**Build notes:** apply with `Image.resize(..., box=floats)` for sub-pixel accuracy.

**Flow prompt text:** "During this long shot the picture very slowly grows closer, by a barely visible amount, with no shaking."

**Still-image state:** not applicable.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | CAP-1 + CAP-2 on HLD-1 | DIS-1 into B-roll, HLD-2 with captions, DIS-1 or DIS-2 back | SPL-1 (plate = still of the B-roll) with CAP-3 |
| Single talking head | CAP-1 + CAP-2 on HLD-1 | SPL-3 at a turn word, optional LST-1 for steps | CAP-3 inside L-SPLIT, or SPL-2 then CAP-3 |
| B-roll only | CAP-1 on HLD-2 | DIS-1 / DIS-2 alternating on cuts, DRF-1 on long shots | CAP-3 on the last shot |
| Product or landscape shots with a voice-over | CAP-1 on HLD-2 | DIS-2 on every other cut, DIS-1 on the rest | CAP-3 |
| Still image + text | CAP-1 settled on the image | optional split of two crops of the image (SPL still state) | CAP-3 |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

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
