# Google Flow prompt · Cutout Board
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Cutout Board" motion style to it.

The look in one sentence: Subject snapped out as a sticker with a boiling yellow outline onto a green cutting mat with grid and crop marks, captions mixing small serif words, a hot-pink highlighter tag and a giant ultra-wide black word on a white label strip.

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
| MAT | `#50705A` | cutting-mat base (sampled 76,107,81 → 82,113,87) |
| MAT-LINE | MAT + 6 % white | minor grid lines |
| MAT-MAJOR | MAT + 14 % white | major grid lines |
| MARK | `#C9D3C9` | crop marks |
| OUTLINE | `#E5BF06` | sticker outline and the small dots on the mat |
| PINK | `#E371A6` | highlighter tag |
| TAG-INK | `#1A1A1A` | text on the pink tag, giant word |
| PLATE | `#F2F0EA` | white label strip behind the giant word |
| SERIF | `#FFFFFF` | small serif words (soft shadow over footage) |

### 1.2 The cutting mat (board)
- Flat MAT colour, very slight lighter haze towards the top (+4 % luminance at the top edge, fading out by 0.3 H).
- Grid: 1-px lines every **0.05 W** [54 px] both ways (MAT-LINE); every 5th line is MAT-MAJOR (every 0.25 W).
- Crop marks: four L-shaped marks inset 0.02 W from the sides and 0.065 H from top/bottom, arms 0.03 W long, 0.002 W thick, MARK colour, opening towards the corner.
- 5–8 tiny OUTLINE-yellow dots (diameter 0.008 W) at random major/minor grid intersections near the edges, fixed for the whole video.

### 1.3 The sticker cutout
- The subject is separated from its background with a **person/object matte** (rembg u2netp / MediaPipe selfie segmentation / SAM). The **subject's pixels are the live footage**, unchanged; only the background is replaced by the mat.
- **Outline:** the matte dilated by **0.022 W** [24 px], filled OUTLINE yellow, edge slightly rough. It **boils**: the dilation edge is re-randomised (±0.004 W noise) every 0.2 s (6 times a second), like a hand-cut sticker on stop-motion.
- **Bottom edge:** the sticker is cut straight across at its bottom (the outline does not wrap the bottom); default bottom at 0.79 H.
- **Size:** sticker box x 0.20–0.78 W, y 0.30–0.79 H; the subject's head top sits ≈ 0.31 H. Scale ≈ 0.55–0.62 of the original frame for a waist-up talking head (0.62 when the speaker is framed wide), ≈ 0.64 for an object.
- If no matte tool is available or the matte is poor (hands, hair, objects lost), use the **card fallback**: a rectangle crop of the same footage with 0.015 W rounded corners and the same boiling yellow outline.

### 1.4 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Serif words | condensed display serif, regular, sentence case | Instrument Serif | Playfair Display, DejaVu Serif Condensed | 0.042 H [81 px] |
| Pink tag | bold geometric sans, lowercase as written | Inter Bold (wght 700) | Archivo Bold, Liberation Sans Bold | 0.036 H [69 px] |
| Giant word | ultra-wide black grotesk, UPPERCASE | Archivo Expanded Black (wdth 125, wght 900) | Unbounded Black, Dela Gothic One, Archivo Black | largest size that fits 0.90 W, cap height ≤ 0.040 H |

- **Pink tag:** PINK rounded rectangle (radius 0.008 W), padding 0.012 W horizontal, 0.004 H vertical, TAG-INK text.
- **Plate:** PLATE rounded rectangle (radius 0.01 W), 0.966 W wide (x 0.017–0.983 W), height 0.054 H; the giant word is centred, as large as fits.
- All words are the user's words.

### 1.5 The caption composition
Each caption chunk is a small stacked composition:
- **Line A:** 1–4 serif words with **at most one** word in a pink tag (the emphasis word), left-to-right in reading order.
- **Line B (optional):** one giant word on the plate (the key noun/verb of the chunk). Max one giant word per 2 s.
- **Line C (optional):** 1–3 trailing serif words (e.g. "beats", "when you're").
- Lines are centred on a common axis, 0.008 H apart. The whole block sits in a **placement zone**: TOP (block top at 0.075 H), HEAD-SIDE (right of the head, top 0.09 H, right-aligned at 0.94 W), CHEST (block top at 0.60 H), or LOW (block top at 0.80 H). Pick the zone that doesn't touch the face box.

### 1.6 Motion language
- **Hard and snappy.** Board pops and exits are cuts (1–2 frames). No slides, no long eases.
- Serif words fade in over 3 f (grey → white) at their spoken time.
- Pink tag pops in at its word: scale 90 → 100 % in 2 f, no overshoot.
- Giant word + plate "ghost in": opacity 0 → 100 % over 4 f with a slight blur (0.004 W) clearing; ghost out the same way when the chunk ends.
- Sticker outline boils at 6 fps (1.3).

### 1.7 What may happen to the user's footage (style-specific rules)
- Allowed: full-frame footage untouched; **board moments** (K01) where the subject is matted and placed as a sticker on the mat (subject pixels live and in sync, background replaced) for **≤ 2.5 s per use and ≤ 35 % of the video in total**; uniform scale of the subject for the sticker.
- The subject inside the sticker is always the current live footage, in sync with the audio. The board replaces only the background, never the person or object.
- Only use a board moment when the matte is clean (face, hair and hands intact); otherwise use the card fallback (1.3).
- Never recolour, filter, retime, reorder or trim the footage.

### 1.8 Safe zones
- Captions never touch the face box (use HEAD-SIDE only if there's 0.30 W of free space beside the head).
- The pink tag and plate never cover hands doing the action of the shot.
- On the board, the caption block goes in the TOP zone (above the sticker).

---

## 7. MOMENT LIBRARY
Family codes: **BOARD** (cutout/mat), **CAP** (caption compositions), **CUT**. Energy:  low ·  medium ·  high.

---

### K01 · BOARD POP — BOARD  (signature)

**What it is:** In one snap, the background vanishes: the subject is cut out and the frame becomes a green cutting mat. The cutout flashes at full size for one frame, then jumps to a small sticker with a thick boiling yellow outline in the middle of the mat. The caption composition sits above it.

**Use when:** the hook line or a key statement on a talking-head shot, or a hero object shot with a clean matte. Starts on a word (the first word of the statement). Max 2 per 10 s.

**Motion:**

| t (f @30) | State |
|---|---|
| 0 | mat replaces the background; the matted subject still at full size and position, no outline |
| 1 | sticker at its final size and position (x 0.20–0.78 W, y 0.30–0.79 H), yellow outline on |
| 1 → end | sticker live, outline boils every 6 f (0.2 s) |

**Anchor:** the subject's head-top and centre-x (or object centre) are mapped to (0.49 W, 0.31 H); bottom cut at 0.79 H.

**Flow prompt text:** "In one snap, the background disappears: the person is cut out like a sticker with a thick, slightly wobbly yellow outline and placed, smaller, in the middle of a green self-healing cutting mat with a fine grid, crop marks in the corners and a few tiny yellow dots. The person keeps talking normally inside the sticker."

**Still-image state:** sticker on the mat with a caption composition above it.

---

### K02 · BOARD EXIT — CUT

**What it is:** A hard cut back to the untouched full-frame footage. The sticker lingers on top for exactly one frame, then disappears, so the exit feels like peeling.

**Use when:** at the end of the board statement; preferably exactly on a footage cut (then the lingering frame is skipped).

**Motion:** f0: full-frame footage + sticker (same box); f1: footage only.

**Flow prompt text:** "The scene snaps back to the normal full-frame video; the sticker flickers once and is gone."

---

### K03 · SERIF LINE — CAP (always on)

**What it is:** The base caption: small white condensed serif words appearing one by one as spoken.

**Text:** the user's words **verbatim**, original case, 1–4 per line. **Graphics:** SERIF white, Part 1.4 size; over footage add a dark glow (text stroked 2 px in black at 65 %, offset +1 px, blurred 4 px) so thin serifs stay readable on light clothes and walls. On the mat no glow. **Motion:** each word fades in over 3 f at its start.

**Flow prompt text:** "Captions are small white elegant condensed serif words appearing one by one as spoken."

---

### K04 · PINK TAG — CAP

**What it is:** One emphasis word inside a hot-pink highlighter tag with bold dark sans text, inline with the serif words.

**Text:** the chunk's emphasis word (adjective, verb, number), as written. Max one per chunk. **Motion:** pops at its word, scale 90 → 100 % in 2 f.

**Flow prompt text:** "The word \"{{WORD}}\" appears in bold dark letters inside a hot-pink highlighter tag, inline with the serif words."

---

### K05 · GIANT WORD PLATE — CAP  (signature)

**What it is:** The key word of the line, set in huge ultra-wide black capitals on a long white label strip spanning almost the full width, directly under the serif line.

**Text:** one user word (noun/verb/payoff), UPPERCASE, punctuation kept ("DIRECTION."), ≤ 12 characters. **Graphics:** Part 1.4 plate + giant word. **Motion:** ghost in over 4 f at its spoken time (or with the first word of the chunk if it's the chunk's subject); stays until the chunk ends; ghost out 4 f.

**Flow prompt text:** "Under the serif words, the word \"{{WORD}}\" appears in huge, extremely wide, heavy black capitals on a long white label strip that spans almost the whole width."

---

### K06 · PLACEMENT JUMP — CAP  (keeps the eye moving)

**What it is:** Consecutive caption compositions jump between placement zones (TOP → CHEST → HEAD-SIDE → LOW…), chosen by the shot's empty space. No animation between them: the old block ghosts out, the new one builds in its new zone.

**Rule:** never the same zone three times in a row; never a zone touching the face or the action.

**Flow prompt text:** "Each new caption group appears in a different empty part of the frame (top, beside the head, chest height or low), never over the face."

---

### K07 · OBJECT STICKER — BOARD  (extension in the same grammar)

**What it is:** K01 applied to a B-roll object (plant, product, phone): the object is cut out with the boiling yellow outline and placed on the mat, bottom-cut at 0.79 H, slightly larger (object box ≈ 0.62 W wide).

**Use when:** a B-roll shot with a single clear object and a clean matte, on the line that names it or its meaning.

**Flow prompt text:** "The {{OBJECT}} is cut out like a sticker with a thick wobbly yellow outline and placed on the green cutting mat."

---

### K08 · CARD STICKER — BOARD  (fallback)

**What it is:** When no clean matte exists, the footage is shown as a rectangular card (0.015 W rounded corners) with the boiling yellow outline on the mat, same box as K01. Same timing and exit.

**Flow prompt text:** "The video shrinks to a rectangular card with a thick wobbly yellow border, placed on a green cutting mat with a grid."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | full frame + K03/K04 composition, then K01 board pop on the hook statement | K02 exit on the first cut; K03/K04/K05 compositions on B-roll with K06 placement jumps; K07 on one clean-object shot | final composition with K05 giant payoff word on the speaker (full frame), or a second K01 if the matte is clean |
| Single talking-head shot | K01 on the hook | K02, K06 jumps, one K05 per sentence | K05 payoff word |
| B-roll / product only | K07 (or K08) on the first shot | K06 jumps | K05 |
| Still image (poster) | K01 sticker on the mat + one full composition (serif + pink + giant) | — | — |

Never paste a row blindly.

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
