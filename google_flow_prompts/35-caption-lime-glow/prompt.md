# Google Flow prompt · Lime Glow
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Lime Glow" caption style to it.

The look in one sentence: White semibold words over one heavy slanted lime keyword with a green glow, and a giant outlined slanted title with a red and cyan fringe sliding across the top.

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
| Caption white | #FFFFFF fading to #D8DCDE at the baseline | Plain caption words |
| Keyword lime | #CEFD38 | Keyword fill |
| Lime glow | #96FF00 at 75 % | Blurred halo behind each keyword |
| Title edge | #FFFFFF 95 %, #FF3C3C 90 % (shifted +5 px at 2x), #28C8FF 90 % (shifted −5 px at 2x) | Outline of the title: white ring with a red copy to the right and a cyan copy to the left |
| Title fill | #000000 at 34 % plus white halftone dots at 14 % | Inside the title letters (footage shows through) |
| Floor | #000000, 0 → 44 % | Vertical scrim from 0.50H to 0.92H, ease power 1.3 |
| Text shadow | #000000 at 80 % | Soft shadow under white words (0, +3 px, blur 5 px at 720 wide) |

Brand-swap rule: replace Keyword lime and Lime glow with the user's brand colour (a bright, saturated hue; keep glow = same hue, slightly deeper). White and the floor never change.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, borders, masks, splits or background changes. |
| Floor scrim | Legibility aid only: darkens the bottom half smoothly, maximum 44 % black at the bottom edge. Always on for the whole video. |
| Crop | Cover-fit only when the source is not 9:16; crop anchor = the speaker's face. |

### 1.3 Layouts / grid

| Layout | Region (fractions) | Use |
|---|---|---|
| Caption line 1 (white) | centred on x = 0.50W; baseline y = 0.636H [1221] | Plain words before the keyword, or a white-only chunk |
| Caption line 2 (keyword) | centred on x = 0.50W; baseline y = 0.743H [1427]; line pitch 0.107H | The keyword, plus any plain words that follow it on the same baseline |
| Title strip | top of frame, y from 0.015H to ≈ 0.125H [29–240]; centred on x = 0.50W | T1 and T2 |
| Edge margin | every glyph ≥ 0.04W from the left and right edges | All text |

Measured on the reference: white line 1 baseline 0.626–0.641H; lime line baseline 0.743H; a two-word keyword line spans up to 0.65W.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Plain caption word | Clean grotesque, semibold, mixed case as written, vertical white gradient | Inter SemiBold (opsz 28, wght 600) | SF-like: Manrope SemiBold, DM Sans SemiBold | 0.111W [120]; at 720 wide 80 px; word space 0.85 × normal |
| Keyword | Heavy slanted grotesque, mixed case, lime, green glow | Barlow Black Italic | Barlow ExtraBold Italic, Archivo Black Italic | 0.162W [175]; at 720 wide 117 px; word space 0.6 × normal |
| Title | Tall condensed heavy caps, sheared 0.22 to the right, outline only (ring ≈ 2 px at 720 wide), halftone-dotted dark fill | Anton, sheared | Bebas Neue, Barlow Condensed Black Italic | cap height 0.105H (T1) / 0.085H (T2); T1 of 6 letters ≈ 0.66W wide |

Rules: captions keep the user's case. Titles are UPPERCASE (the only forced case). Max one lime keyword group per chunk. No outline-only captions.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Caption word entrance | ease-out cubic alpha 0 → 1, scale 0.92 → 1 about the word centre, rise 8 px → 0 (720 wide) | 4 f (0.17 s) |
| Caption chunk exit | linear alpha fade, ends exactly when the next chunk starts | 3 f (0.125 s) |
| Title entrance | ease-out cubic slide in from the left (x offset −0.7W → 0) with alpha | 0.25 s |
| Title exit | ease-in cubic slide out to the right (+0.7W) fading to 20 % | 0.25 s |
| Echo stack entrance | each row ease-out cubic from 0.05H above, rows staggered 0.07 s | 0.30 s |
| Cuts | footage cuts untouched; captions continue across them | 0 f |

Never: bounce or overshoot beyond the 0.92 → 1 settle, letter-by-letter typing, wipes, shake, flashes, caption rotation, caption shadows in colours, extra colours, effects on the footage.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Bottom floor scrim | Per 1.2: max 44 % black, smooth, whole video |
| Text overlays, glow and title overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; cards, splits, B-roll frames, background swaps, graphic transitions; blur, glitch, warp, zoom, flashes, grading. The footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Captions sit below 0.55H; the title strip stays above the face box top. |
| Title strip | If the face box top is above 0.17H, shrink the title cap height until its bottom edge is ≥ 0.02H above the face box top, or skip titles on that shot. |
| Caption block | If the face box bottom is below 0.56H, move both caption baselines down by the overlap (max +0.06H); if still overlapping, drop line 1 to a white-only chunk below the chin. |
| Footage text (signs, UI) | If readable text sits in the caption block for > 1 s, shift the block up by 0.08H when no face is there. |
| Edges | Glyphs ≥ 0.04W from the edges. A keyword line wider than 0.92W: move the last word of the keyword group to line 1 as plain white. |

---

## 7. MOMENT LIBRARY
Family codes: **C** caption · **T** title · **K** keyword treatment · **X** cut handoff · **E** end.

### MOMENT C1 · SPLIT-LINE CAPTION
**What it is:** a phrase appears word by word. The plain words stand on line 1 in white; the keyword drops to line 2 in heavy lime italic with a green glow.
**Use when:** any speech or voice-over. **Avoid when:** the phrase has no keyword (use C2).
**Text:** the user's exact words. Chunk: 2–5 words, split at punctuation and natural phrases, never end on an article, preposition or conjunction. Keyword: 1 meaning-carrying noun or verb per chunk, ≤ 1 chunk in 3 may skip it.
**Geometry / Graphics:** Caption lines 1 and 2 (1.3). The whole chunk is laid out before it starts, so no word ever moves. Plain words before the keyword go on line 1; the keyword goes on line 2.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | each word | alpha, scale, rise | 0 → 1, 0.92 → 1, 8 px → 0 | ease-out, 4 f |
| word start | earlier words | — | unchanged | — |
| chunk end | all words | alpha | 1 → 0 | linear, 3 f; ends at the next chunk's first word start |

Word start = the word's spoken start time. Chunk end = min(last word start + 1.4 s, next chunk start); the last chunk ends at the end of speech + 0.1 s.
**Footage / plate behaviour:** untouched except the floor scrim.
**Captions during it:** this is the caption system; it continues across cuts without a break.
**Exit:** 3 f linear fade.
**Flow prompt text:** "In the lower part of the frame, captions appear word by word. Ordinary words are clean white; the important word, {{KEYWORD}}, sits on its own line below in heavy slanted lime green letters with a soft green glow. Each word pops in with a tiny rise, and the phrase fades quickly before the next one."
**Still-image state:** one full chunk.

### MOMENT C2 · WHITE-ONLY LINE
**What it is:** a chunk with no keyword: one centred white line on line 1.
**Use when:** connective phrases between keyword beats, lists of small words. **Avoid when:** two C2 in a row (add a keyword to the second).
**Text:** 2–4 plain words.
**Geometry / Graphics:** line 1 only (baseline 0.636H).
**Motion:** as C1 (same word entrance, 3 f exit).
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** same layer builder as C1.
**Flow prompt text:** "A short line of clean white words, {{WORDS}}, pops in word by word in the lower part of the frame, then fades."
**Still-image state:** the line.

### MOMENT C3 · SOLO KEYWORD
**What it is:** the keyword alone on line 2 with line 1 empty, for one-word beats.
**Use when:** a standalone key word or an exclamation. **Avoid when:** more than 2× in a video.
**Text:** 1 word.
**Geometry / Graphics:** line 2 only (baseline 0.743H), centred.
**Motion:** as C1; hold ≥ 0.5 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** same builder.
**Flow prompt text:** "One big word, {{WORD}}, pops in on its own in heavy slanted lime green letters with a green glow, then fades."
**Still-image state:** the word.

### MOMENT K1 · KEYWORD WITH TAIL
**What it is:** the keyword on line 2 followed on the same baseline by plain white words that continue the phrase.
**Use when:** the keyword sits mid-phrase ("… lime word, then a few plain words").
**Text:** keyword + 1–2 trailing plain words.
**Geometry / Graphics:** line 2 holds [keyword][plain words] centred as one run; the trailing words use the white style at 80 px (720 wide) on the lime baseline.
**Motion:** each word enters at its own start time (C1 motion).
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** layout the whole run once so the keyword does not shift when the tail arrives.
**Flow prompt text:** "The key word {{KEYWORD}} sits on the lower line in lime, and the plain white words {{TAIL}} pop in next to it on the same line."
**Still-image state:** the full run.

### MOMENT K2 · KEYWORD PAIR
**What it is:** two keywords share line 2 in lime, for a two-word idea.
**Use when:** a short noun phrase or number plus unit is the point. **Avoid when:** the pair is wider than 0.92W (keep one word lime).
**Text:** 2 words.
**Geometry / Graphics:** line 2, both words lime with glow, word space 0.6 × normal.
**Motion:** C1 motion for each word; second word at its own start time.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** same builder.
**Flow prompt text:** "Two key words, {{WORDS}}, pop in one after the other on the lower line in lime green with a glow."
**Still-image state:** the pair.

### MOMENT T1 · OUTLINE TITLE SLIDE
**What it is:** one giant outlined italic title slides in from the left along the top of the frame, holds, and slides out to the right.
**Use when:** the opening line names the topic, or at the first topic word. **Avoid when:** the face box top is above 0.17H and cannot be cleared (1.7).
**Text:** 1 word (≤ 8 letters) from the user's own words, UPPERCASE.
**Geometry / Graphics:** title strip; cap height 0.105H [201]; centred on x = 0.50W; top y = 0.015H. Outlined: white ring 2 px with red and cyan copies ±2.5 px (720 wide); fill black 34 % with halftone dots (9 px pitch at 2x, 3 px dots, 14 % white).
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start (0.2–0.6 s) | title | x offset, alpha | −0.7W → 0, 0 → 1 | ease-out cubic, 0.25 s |
| hold (1.5–2.5 s) | title | — | settled | — |
| end | title | x offset, alpha | 0 → +0.7W, 1 → 0.2 | ease-in cubic, 0.25 s |

The hold may run across a footage cut. It never starts within 3 f after a cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 runs below.
**Exit:** slide out to the right.
**Build notes:** draw text at 2x, shear with an affine (0.22), ring = MaxFilter(7) minus the mask, shift copies, paste.
**Flow prompt text:** "Near the start, a giant slanted outlined word, {{TITLE}}, with thin white edges and a faint red and blue fringe, slides across the top of the frame from the left, stays for a couple of seconds, then slides away to the right. It never covers the speaker's face."
**Still-image state:** settled.

### MOMENT T2 · ECHO STACK TITLE
**What it is:** the title appears as three stacked copies rising upward and fading, like an echo above the main row.
**Use when:** a payoff word near the end, or a topic repeat. **Avoid when:** T1 played < 3 s ago.
**Text:** 1 word from the user's words, UPPERCASE.
**Geometry / Graphics:** cap height 0.085H [163]; main row top y = 0.02H; echoes shifted up by 0.062H each (partly off the top edge), alpha 1.0 / 0.5 / 0.25; same outline and fill as T1.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start | row r (0, 1, 2) | y, alpha | −0.05H → 0, 0 → row alpha | ease-out cubic 0.30 s, delay 0.07 s × r |
| end | all rows | alpha | → 0 | linear 0.2 s |

**Footage / plate behaviour:** untouched; the stack stays above the face box top.
**Captions during it:** C1 below.
**Exit:** 0.2 s fade.
**Build notes:** one title layer pasted three times.
**Flow prompt text:** "A giant slanted outlined word, {{TITLE}}, repeats three times stacked at the top of the frame, each copy fainter than the one below, and rises in with a soft slide, then fades away."
**Still-image state:** the stack at rest.

### MOMENT X1 · CUT HANDOFF
**What it is:** at a footage cut the caption chunk in progress keeps playing; chunk boundaries are placed on cuts when the speech allows.
**Use when:** every cut. **Avoid when:** never.
**Text:** none.
**Geometry / Graphics:** captions stay in the same lines across the cut; the floor stays constant.
**Motion:** no effect on the cut; if a chunk boundary falls within 0.25 s of a cut, move it onto the cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** continue.
**Exit:** none.
**Build notes:** align chunk starts with scene-detect times when speech starts within 0.25 s of a cut.
**Flow prompt text:** "At every cut the captions simply carry on without any effect."
**Still-image state:** n/a.

### MOMENT E1 · CLOSER KEYWORD HOLD
**What it is:** the last chunk holds longer than the others, with its keyword on the lime line, and the video ends on it.
**Use when:** the last line is the payoff or call to action.
**Text:** the last phrase.
**Geometry / Graphics:** C1 layout; optional T2 above.
**Motion:** C1 entrances; chunk end = end of speech + 0.1 s with the 3 f fade.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade at the end of speech.
**Build notes:** extend the last chunk's end only; never past the video end.
**Flow prompt text:** "On the final line, the last key word {{KEYWORD}} lands in lime on the lower line and stays until the speaker finishes."
**Still-image state:** the final chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 on the topic word, C1 | C1 / C2 / K1 / X1 on every cut | T2 on the payoff word, E1 |
| Single talking head | T1, C1 | C1, C3 on one-word beats, K2 for a pair | E1 |
| B-roll only | C1 on the first line | C1 / K1, X1 on each cut | E1 |
| Still image | T1 settled + C1 chunk | n/a | n/a |

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
