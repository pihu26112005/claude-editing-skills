# Google Flow prompt · Whisper Blob
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Whisper Blob" caption style to it.

The look in one sentence: Tiny hand-brushed white whisper words over one fat rounded keyword on a solid dark slab, bent into an arch or wave, hopping between top and bottom lane to stay off the face.

The footage stays FULL FRAME and UNTOUCHED: no cards, split screens, layouts, backgrounds, wipes or graphic transitions. This style only adds its caption system (and title/headline text if the style bible below lists it) on top of the original picture.

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
4. PLACE THE CAPTION MOMENTS: choose from the moment library below. Captions always follow the speech; title or headline moments go at the start or on the strongest words; keep the same grammar for the whole video.
5. CHECK THE SAFE ZONES (style bible): the speaking face is never covered; text stays inside the safe margins; if footage content (a sign, a screen) sits where the caption lane is, move the lane as the style bible says.
6. RENDER the video: every graphic and word appears and disappears exactly as the moments describe (timing, easing and entrance), cut to cut, and stays in sync with the audio.

## 6. STYLE BIBLE
### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Whisper white | #FFFFFF | Small script words, white keywords |
| Keyword accent A (parameter) | #A6F01E lime; demo uses #FF8A1F orange | Keyword colour 1 |
| Keyword accent B (parameter) | #FF4FA0 pink; demo uses #2FD3FF cyan | Keyword colour 2 |
| Slab | #160E28 | Solid drop-slab under every glyph |
| Soft shadow | #000000 at 50 % | Blur 0.007W behind the slab |

Brand-swap rule: replace accents A and B with the user's colours (saturated, bright, readable on mid-tone footage). White and the slab never change. A keyword is one flat colour, never a gradient, never outline-only.

### 1.2 Containers / shapes

Footage is always full frame, 100 %, untouched. No cards, boxes, plates or tints. The only shape is the slab: each glyph is duplicated in #160E28 offset (+0.7 × s, +1 × s) with s = 0.045 × font size, drawn solid under the colour fill.

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Side margin | text edges ≥ 0.06W [65] left and right (never < 0.05W) | Always |
| Bottom lane | whisper line top y = 0.545H; keyword top = whisper bottom + 0.004H; keyword bottom ≤ ~0.70H | Shots with a face in the top 0.40H (default for speaker shots) |
| Top lane | whisper line top y = 0.062H; keyword below it, bottom ≤ 0.35H | Shots with no face, or face low in the frame (B-roll, hands, products) |
| Alignment | even chunks left-aligned at 0.06W, odd chunks right-aligned at 0.94W | Whisper and keyword of one chunk share the same edge |

The reference placed the lane above the face for the first phrases (y 0.04–0.27H) and below it (y 0.55–0.72H) for later ones.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Fat rounded display, mixed case as written, tight, bent by a warp (1.5) | Paytone One | Lilita One, Baloo 2 ExtraBold | up to 0.19W [205]; shrink in 4 px steps until width ≤ 0.88W |
| Whisper | Hand-brushed script, white, sheared italic (−0.18), tilted +2° | Caveat Brush | Gochi Hand, Gaegu Bold | 0.085W [92] |
| Display keyword (white variant) | same as keyword, #FFFFFF fill | Paytone One | Lilita One | same |

Rules: case exactly as the user wrote it (the reference used capitals on keywords; this skill does not force them). No outline-only text. Keywords are at most 2 words per chunk and stay on one line.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Keyword entrance | rise from +0.035H to 0, ease-out cubic, alpha 0→1 over 0.6 of the time | 0.24 s |
| Whisper word entrance | rise from +0.008H to 0, alpha 0→1, ease-out cubic | 0.14 s |
| Chunk exit | hard cut, next chunk starts the same frame | 1 frame |
| Warp | static per chunk (arch or wave), baked into the glyph shapes | — |
| Tilt | keyword tilted +2.5° on left-aligned chunks, −2.5° on right-aligned | — |

Never: horizontal slides that leave the frame (the reference keyword slid in from the left edge; this skill rises instead so text never crosses the 0.05W margin), bounce, shake, outline-only text, letter-by-letter typing, glitch, colour changes on a word already shown.

### 1.6 What may happen to the user's footage

Full-frame display untouched. Text and shadows only. Forbidden: replacing, retiming, trimming, blurring, grading, zooming, cards, splits, background swaps, adding footage. Primary footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face box | No glyph or slab inside the speaking face. Bottom lane only when keyword top ≥ 0.43H and the face bottom is above that; top lane only when keyword bottom ≤ 0.35H and the face is below it. If both fail, use the lane with less overlap and shrink to 0.14W |
| Overlap | Whisper line sits fully above its keyword; one chunk on screen at a time |
| Bright footage | The slab keeps white and cyan readable; do not drop it |

---

## 7. MOMENT LIBRARY
Family codes: **C** caption · **T** title · **K** keyword · **E** end. Energy:  calm ·  medium ·  high.

### MOMENT C1 · WHISPER LINE
**What it is:** the small connective words of a phrase appear one by one in a hand-brushed white script line above the keyword.
**Use when:** every phrase with connective words. **Avoid when:** the phrase is only keywords (skip the line).
**Text:** the user's non-keyword words, in spoken order, as written.
**Geometry / Graphics:** Whisper font 0.085W, word gap 0.022W, line top per lane (1.3), edge per alignment (1.3), slab + soft shadow.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | whisper word | alpha, y | 0 → 1, +0.008H → 0 over 0.14 s | ease-out |
| chunk end | whole chunk | alpha | 1 → 0 | hard cut |

**Footage:** untouched. **Captions during it:** with C2. **Exit:** hard cut.
**Flow prompt text:** "Small connective words, {{WHISPER_WORDS}}, appear one at a time in tiny white hand-brushed lettering above the big word, each rising slightly while it fades in."
**Still-image state:** the full line.

### MOMENT C2 · BLOB KEYWORD
**What it is:** one meaning-carrying word (or two) in a fat rounded saturated face rises in under the whisper line on a solid dark slab.
**Use when:** every chunk, 1 keyword per chunk (2 words for a pair like "what's left."). **Avoid when:** the word is an article or preposition.
**Text:** 1–2 meaning words, ≤ 12 characters in total per line.
**Geometry / Graphics:** font up to 0.19W, auto-shrunk to ≤ 0.88W wide, colour accent A, accent B or white, slab 0.045 × size, tilt ±2.5°, warp per C3/C4. Colour order: accent A, white, accent B repeating; payoff in accent B.
**Motion:** rises +0.035H → 0 over 0.24 s ease-out, alpha ×1.6 ramp; starts at the keyword's spoken start; hard cut at chunk end.
**Footage:** untouched. **Captions during it:** C1 above it. **Exit:** hard cut.
**Flow prompt text:** "One important word, {{KEYWORD}}, appears in huge fat rounded {{COLOUR}} lettering with a dark solid shadow, bent slightly, rising up into place under the small white words."
**Still-image state:** the keyword.

### MOMENT C3 · ARCH BEND
**What it is:** the keyword's baseline bulges upward in the middle like a rainbow.
**Geometry:** per-column vertical shift dy = −0.16 × size × (1 − (2u−1)²), u = 0..1 across the word. **Use when:** alternate chunks (even chunks in the demo). **Text:** none. **Motion:** static. **Exit:** with its chunk.
**Flow prompt text:** "The big word is curved upward in the middle like an arch."

### MOMENT C4 · WAVE BEND
**What it is:** the keyword ripples: one hump up, one down.
**Geometry:** dy = +0.06 × size × sin(2πu). **Use when:** odd chunks, for variety against C3. **Motion:** static.
**Flow prompt text:** "The big word waves gently, one hump up and one down."

### MOMENT K1 · SOLO PAYOFF
**What it is:** the last or most important word alone, no whisper line, at the largest size.
**Use when:** the payoff or last line; at most 2 per video, ≥ 3 s apart. **Text:** one word.
**Geometry:** font 0.19W, accent B, arch bend, lane per shot. **Motion:** as C2. **Hold:** 0.5–0.9 s, ends with the speech.
**Flow prompt text:** "The final word, {{WORD}}, appears alone in the largest size, arched, in bright {{COLOUR}} with a dark solid shadow."

### MOMENT K2 · PAIR KEYWORD
**What it is:** two meaning words on one line, both in the same colour, shrunk to fit 0.88W.
**Use when:** a natural pair ("one year", "what's left."). **Text:** 2 words.
**Motion:** both words appear together at the first word's start. (The reference stacked two lines; on a 9:16 face-safe lane one line is used.)
**Flow prompt text:** "Two important words appear together on one line in huge rounded lettering."

### MOMENT C5 · LANE HOP
**What it is:** when the footage cuts to a shot where the current lane covers the subject, the caption jumps to the other lane on the cut frame, with no animation.
**Use when:** every cut; also at any change of face position. **Text:** none. **Motion:** the chunk keeps its state (no re-entrance); position changes on the cut frame only.
**Flow prompt text:** "At each cut the captions jump to the top or the bottom of the frame, whichever keeps clear of the person, with no effect."

### MOMENT T1 · BLOB TITLE
**What it is:** an opening topic title, 1–2 words, in the keyword style at 0.17W, arched, accent A, in the top lane with its whisper line replaced by nothing.
**Use when:** the opening line names the topic and the face box is below 0.30H or a bottom lane is available. **Avoid when:** the face is in the title lane (use the bottom lane).
**Text:** 1–2 of the user's words. **Motion:** C2 entrance; hold 1.0–1.4 s; hard cut to the first chunk (never overlaps another chunk).
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, appears in fat rounded arched lettering."

### MOMENT E1 · END HOLD
**What it is:** the last chunk holds until the speech ends + 0.2 s, then the frame is clean for the last ≥ 0.2 s.
**Text:** the last chunk. **Motion:** hard cut at the end. **Flow prompt text:** "The last caption stays until the speaker stops, then the picture finishes clean."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 + C2 from the first word | C3/C4 alternating, C5 on each cut, K2 for a pair | K1 + E1 |
| Single talking head | T1 + C1/C2 | alternate C3/C4, one K1 | K1 + E1 |
| B-roll only, no speech | C2 phrases (no whisper) | C5 per cut | E1 |
| Still image + text | one chunk settled (C1 + C2) | — | — |

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
