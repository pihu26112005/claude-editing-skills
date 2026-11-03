# Google Flow prompt · Orchid Halo
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Orchid Halo" caption style to it.

The look in one sentence: Heavy white sans words fade in low as spoken and one large glowing orchid-pink italic serif accent word per phrase settles in, tucked against the sans line.

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
| Base word | #FFFFFF | Sans words |
| Accent top | #FFCDF8 (default, accent hue) | Top of the accent gradient  |
| Accent bottom | #E846DE (default, accent hue) | Bottom of the accent gradient  |
| Halo inner | #F434E2 at 0.9 × 0.9 | 11 px gaussian halo behind the accent  |
| Halo outer | #D618D6 at 0.85 × 0.9 | 26 px gaussian halo  |
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
| Lane line  | accent centre y = 0.765H [1468]; allowed range 0.70–0.80H |
| Max width | 0.86W for the widest line (the accent shrinks to fit) |
| Lead line (words before the accent) | centre y = accent centre − (accent height/2 + base line height/2 − 6) |
| Tail line (words after the accent) | centre y = accent centre + (accent height/2 + base line height/2 − 6) |
| Tuck | base lines overlap the accent's ascender/descender band by 6 px at 720 wide |

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
| Accent in | On its spoken time: scale 0.86 → 1.00 with ease-out cubic over 0.26 s, fade 0 → 100 % over 0.18 s; halo arrives with the fill. |
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

## 7. MOMENT LIBRARY
Family codes: C caption · K keyword · T title · E end. Energy:  calm,  medium,  high.

### MOMENT C1 · HALO STACK
**What it is:** A chunk of 2–5 words: base words fade in one by one on their spoken times while the one accent word lands, large and glowing, on its own spoken time. Lead words sit above, tail words below, tucked against the accent.
**Use when:** Any speech or script line. The default for every chunk.
**Avoid when:** The lane is a busy bright area and a second lane is free (move the lane line instead).
**Text:** the user's words, case as written; 2–5 words, ≤ 30 characters in total; split at punctuation; never end a chunk on an article, preposition or conjunction; chunk change preferably on a footage cut; accent = the most meaningful noun or verb.
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

### MOMENT K1 · ACCENT SOLO
**What it is:** A chunk that is the accent word alone, centred on the lane line, with the halo.
**Use when:** The last word, a number, a name or a punchline.
**Avoid when:** More than twice per video or twice within 3 s.
**Text:** one word with its punctuation.
**Geometry / Graphics:** layout S; accent size as 1.4 (up to 1.15× for words ≤ 5 letters).
**Motion:** as C1 accent in; hold until its end time; 3 f fade.
**Footage behaviour:** untouched.
**Exit:** fade 0.12 s (or held to the last frame in E1).
**Build notes:** same layer as C1 accent.
**Flow prompt text:** "The single word {{WORD}} appears alone in a large glowing italic serif in {{COLOUR}}, fading and settling in at the moment it is spoken."
**Still-image state:** the word, settled.

### MOMENT K2 · MIDDLE ACCENT
**What it is:** The accent sits between a lead word and tail words: a small sans word above, the glowing word, a small sans word below.
**Use when:** Verb or noun in the middle of a short phrase.
**Text:** 3–5 words, accent in the middle.
**Geometry / Graphics:** layout C; lead line and tail line both tucked.
**Motion:** as C1; lead words land before the accent, tail words after.
**Footage behaviour:** untouched.
**Exit:** as C1.
**Build notes:** keep the block's total height inside the lane range of 1.3.
**Flow prompt text:** "A small white sans word above, the key word {{ACCENT}} in a large glowing italic serif in the middle, and a small white sans word below."
**Still-image state:** full stack.

### MOMENT C2 · PLAIN RUN
**What it is:** A base-only chunk (no accent) of 1–4 sans words, for filler lines or fast speech.
**Use when:** Connecting words that carry no meaning; never in two chunks in a row.
**Text:** 1–4 words.
**Geometry / Graphics:** one base line centred on the lane line.
**Motion:** as the base word in; fade out 0.12 s.
**Footage behaviour:** untouched.
**Exit:** as C1.
**Build notes:** same layers as C1 without the accent.
**Flow prompt text:** "Small white heavy sans words fade in one at a time as spoken, low in the frame."
**Still-image state:** the line.

### MOMENT T1 · HEADLINE ACCENT
**What it is:** An opener: the topic word as an accent, with a sans line above or below, held for 1.2–2 s starting at 0.10 s.
**Use when:** The first line names the topic.
**Text:** user's topic word as accent plus up to 3 sans words.
**Geometry / Graphics:** C1 layout A or C.
**Motion:** as C1.
**Footage behaviour:** untouched; keep off the face box.
**Exit:** fade.
**Build notes:** identical to C1.
**Flow prompt text:** "At the start, the topic word {{TOPIC}} lands in a large glowing italic serif with a short white sans line beside it."
**Still-image state:** poster title block at the lane line.

### MOMENT T2 · SECTION ACCENT
**What it is:** A mid-video new-topic word as an accent with its lead word.
**Use when:** A real topic change without a cut.
**Text:** user's words.
**Geometry / Graphics:** as C1 layout B.
**Motion:** as C1.
**Footage behaviour:** untouched.
**Exit:** fade.
**Build notes:** at most once per video.
**Flow prompt text:** "A new section word {{WORD}} appears in the glowing italic serif with a white sans lead word above it."
**Still-image state:** settled.

### MOMENT E1 · END HOLD
**What it is:** The last chunk holds until 0.4 s before the end, then fades 0.3 s.
**Use when:** Always on the last chunk when the video ends on speech.
**Text:** the last words.
**Geometry / Graphics:** K1 or C1.
**Motion:** hold; fade 0.3 s linear.
**Footage behaviour:** untouched.
**Exit:** fade.
**Build notes:** extend the end time, not the start.
**Flow prompt text:** "The last words stay on screen to the end, then fade out gently."
**Still-image state:** settled.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 on the topic word | C1 with one accent per chunk; K2 on lists; C2 on filler | K1 on the last word, E1 |
| Single talking head | C1 | C1, K2, C2 mixed | K1, E1 |
| B-roll only with a voice-over | C1 | C1, K1 on numbers | K1 |
| Still image | C1 (settled) | | |

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
