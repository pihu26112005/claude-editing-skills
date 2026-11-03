# Google Flow prompt · Sky Fill Sans
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Sky Fill Sans" caption style to it.

The look in one sentence: Small bold white sans words fading in around one giant extra-heavy keyword filled with a drifting cloud-and-sky texture, across the chest or in a top or low lane, clear of the face.

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
| Texture, measured default | sky blue #5FA3D6 through pale #EAF1F8 with white cloud wisps | Fill of the keyword |
| Texture, demo recolour | top #FFC454 amber, middle #FF4870 coral-pink, bottom #8C0A8C violet, white wisps #FFFAF5 in the upper half, 30 % violet wisps in the lower half | Fill of the keyword |
| Helper words | #FFFFFF | Small words |
| Shadow | #000000 at 85 % blurred 8 px (keyword); stacked 90 / 100 / 80 % (small words) | Keeps text readable on bright footage |

Brand-swap rule: the texture palette is a parameter. Any three-stop vertical gradient (light top, saturated middle, deep bottom) with white wisps works. Keep it saturated enough to read on the shot. White helper words and shadows never change.

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, boxes, bars, borders, blur plates or colour overlays. Text only, plus soft shadow.

### 1.3 Layouts / lanes

| Lane | Keyword baseline y | Small words | Use |
|---|---|---|---|
| Mid | 0.575H; helper top ≥ 0.41H so nothing touches the face | one line above (baseline = keyword cap top − 0.032H), optional line below at baseline + 0.062H | Speaker shots whose face ends above 0.40H |
| Top | 0.215H  | one line above | B-roll with a clear top fifth |
| Low | 0.80H  | one line above, optional line below | B-roll or shots with action in the middle |

All lanes centre on x = 0.50W. Side margin ≥ 0.05W on every text box. Text top ≥ 0.02H, bottom ≤ 0.97H. The reference puts the keyword over the mouth; this skill never does: the face box (x 0.34–0.66, y 0.15–0.40) stays clear.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Extra-heavy geometric sans, tight tracking, mixed case as written, letters filled with the sky texture | Poppins ExtraBold | Montserrat Black, Archivo Black | font size 150 px at 720 wide, shrunk so the word is ≤ 0.88W wide; Top lane ≤ 140 px (cap height ≈ 0.075H at 150) |
| Small words | Bold sans, mixed case, white, centred | Poppins Bold | Montserrat Bold, Inter Bold | 46 px at 720 wide (about 0.064W); line ≤ 0.90W |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Small word | fade 0 → 100 % over 0.20 s, ease-out cubic, at its spoken time; the whole line is laid out first so no word moves |
| Keyword | fade 0 → 100 % over 0.30 s plus rise from 0.02H below its rest position, ease-out cubic, at its spoken time |
| Texture | drifts 34 px/s sideways inside the letters, capped at 40 px total (reference: the sky pattern shifts slowly through the letters) |
| Exit | whole chunk fades out over 0.14 s |
| Never | bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, boxes, outlines, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: text and shadow overlays only. Forbidden: any colour change, blur, dimming, zoom, crop change, background swap, retime, reorder, person cut-out. The footage plays live and in sync. (The reference dims the footage under its opening title; this skill does not.)

### 1.7 Safe zones

- All text boxes inside 0.05W side margins.
- Helper line and keyword keep ≥ 0.012H between them.

---

## 7. MOMENT LIBRARY
Family codes: C caption, K keyword, T title, E end. Energy: low / medium / high.

### K1 · MID SKY KEYWORD — K medium
**What it is:** one giant sky-filled keyword across the chest with small white words above (and optionally below).
**Use when:** speaker shot whose face ends above 0.40H and the phrase has one strong word. **Avoid when:** hands or a phone sit at 0.45–0.70H and the text would hide the subject's action (use K2 or K3).
**Text:** 1 keyword (≤ 10 characters ideal, as written), 0–4 small words above, 0–2 below.
**Geometry:** lane Mid (1.3); keyword 1.4; texture 1.1.
**Motion:** small words per 1.5; keyword fade + rise 0.30 s at its spoken time; texture drift; exit fade 0.14 s. Chunk visible 0.7–1.6 s.
**Footage behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** fade.
**Build notes:** glyph mask drawn at 2x, downscaled; fill = texture crop × mask; shadow layer under it; fixed seed per chunk.
**Flow prompt text:** "Across the speaker's chest, one very large heavy sans word '{{KEYWORD}}' whose letters are filled with a soft {{TEXTURE}} cloud-and-sky pattern fades in, with small bold white words '{{HELPERS}}' fading in one by one around it."
**Still-image state:** keyword fully in, helper words complete.

### K2 · LOW SKY KEYWORD — K medium
**What it is:** the K1 layout in the lower lane. **Use when:** the middle holds action, or a speaker has a clear chest area below 0.70H. **Avoid when:** a face sits in the lower half.
**Geometry:** lane Low. **Motion/Exit:** as K1.
**Flow prompt text:** "In the lower part of the frame, small bold white words '{{ABOVE}}' fade in above one giant {{TEXTURE}} cloud-and-sky filled sans word '{{KEYWORD}}'."

### K3 · TOP SKY KEYWORD — K medium
**What it is:** the K1 layout near the top, on B-roll with a clear top fifth.
**Geometry:** lane Top. **Motion/Exit:** as K1. **Avoid when:** a face or the main subject is in the top fifth.
**Flow prompt text:** "Near the top of the frame, small bold white words '{{HELPERS}}' fade in above one large {{TEXTURE}} cloud-and-sky filled sans word '{{KEYWORD}}'."

### C1 · WHISPER LINE — C low
**What it is:** the small white line alone, building word by word, no keyword. **Use when:** a phrase has no strong word, or between keyword chunks.
**Geometry:** 1.4 small words, centred, at the Top lane or the Mid helper line. **Motion:** 1.5. Chunk 3–6 words.
**Flow prompt text:** "A small bold white line '{{LINE}}' fades in word by word near the top of the frame."

### C2 · SOLO KEYWORD — K high
**What it is:** only the giant keyword, no small words, for a punchline word. **Use when:** payoff or a number. **Limit:** ≤ 1 per 6 s.
**Geometry:** any keyword lane. **Motion/Exit:** as K1, keyword time = chunk start.
**Flow prompt text:** "One giant {{TEXTURE}} cloud-and-sky filled sans word '{{KEYWORD}}' fades in with a small rise and fades out."

### T1 · STACKED OPENER — T high
**What it is:** two short title lines in the sky-filled sans, stacked, in the Top lane above the face, as the first chunk. Footage is not dimmed.
**Use when:** the video opens on a speaker and the first words are a hook. **Avoid when:** the face box would be touched: lines must end above 0.15H or sit in the Low lane.
**Text:** 2 lines of 1–2 words each, ≤ 0.88W wide, font 120 px, line gap 0.012H. Counts as the first caption chunk.
**Motion/Exit:** as K1, second line starts at its spoken word.
**Flow prompt text:** "At the very top of the frame, two short lines '{{LINE1}}' and '{{LINE2}}' in large {{TEXTURE}} cloud-and-sky filled sans fade in one after the other."

### E1 · CLOSING KEYWORD — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 or K3, held 0.4 s past the last spoken word (never past the end of the shot).
**Flow prompt text:** "For the last line the keyword '{{KEYWORD}}' fades in large, filled with the {{TEXTURE}} cloud-and-sky pattern, and stays until the speech ends."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | K1 | K3 / K2 on B-roll, K1 on any speaker | E1 (K1) |
| Single talking head | T1 or K1 | K1, C1, K2 (alternate lanes) | E1 |
| B-roll only | K3 | K2, C2 | E1 (K3) |
| Still image | K3 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Keyword 150 px (Top lane 140, width-capped at 0.88W), small words 46 px, gap above 0.032H, below +0.062H, shadow 85 % blur 8 offset 6, texture drift 34 px/s cap 40 px, fade-out 0.14 s. Chunks: 0.10–1.02 K1 (money, Mid), 1.10–1.80 K2 (more., Low), 2.10–3.17 K3 (yourself, Top), 3.25–4.88 K2 (investments,, Low), 4.95–6.55 K1 (left., Mid), 6.90–8.30 K3 (year, Top), 8.45–9.55 E1/K1 (happens., Mid). Demo texture: amber #FFC454 → coral #FF4870 → violet #8C0A8C.

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
