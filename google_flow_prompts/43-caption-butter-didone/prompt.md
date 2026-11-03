# Google Flow prompt · Butter Didone
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Butter Didone" caption style to it.

The look in one sentence: Pale butter-yellow Didone captions pop in word by word with one capital keyword, while a giant edge-to-edge capital of the key word slams in across the top.

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
| Butter yellow | #FEF08F | Every glyph: giant words, caption words, caps keywords |
| Text shadow | #000000 | Soft drop shadow under all text so the pale yellow reads on bright footage |

Brand-swap rule: if the user gives a brand colour, replace Butter yellow with it (keep it light and warm enough to read on footage). There is one text colour; never add a second, no outlines, no boxes, no highlights.

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, borders, masks, label boxes, blur plates, tints or darkening overlays. Crop only when the source is not 9:16 (cover-fit, anchor = the speaker's face).

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Giant band, free | x 0.04–0.97, centre y 0.20H [384]; cap height 0.13–0.17H [250–326] | Giant word where no face sits in the top 0.30H |
| Giant band, face-safe | x 0.04–0.97, y 0.025–0.14H (cap height ≤ 0.115H) | Giant word over a speaker whose face top is below 0.15H (used on demo2) |
| Giant band, low face | x 0.04–0.97, y 0.025–0.095H (cap height ≤ 0.07H) | Face top near 0.10H (a person standing close to the top edge) |
| Caption lane | centred on x = 0.50W, lines 0.095H [182] apart; the last line baseline ≈ 0.79H [1517] for one line, 0.79H + 0.043H per extra line | Caption block, 1–3 lines (reference: baselines 0.79H for 1 line; 0.74/0.84H for 2; 0.69/0.78/0.875H for 3) |
| Max line width | 0.80W [864] | Wrap point |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Giant word | High-contrast Didone capitals, heavy stems, hairline serifs, letters nearly touching, uppercase always | Bodoni Moda, weight 900, optical size 14 (low), plus a 1.5 px same-colour stroke | Playfair Display Black, Libre Bodoni Bold | Fit the word to 0.93W wide; cap height capped by the band (1.3). Letter-spacing −0.02em |
| Caption word | Same family, bold, lowercase as written; first letter capital only if the user wrote it so | Bodoni Moda, weight 800, optical size 14 (low), plus a 0.6 px same-colour stroke | Playfair Display Bold, Libre Bodoni Bold | ≈ 0.143W [154] so that two words "xxxxx xxxxxx" of 12 characters span ≈ 0.79W; letter-spacing −0.005em; word space 0.22em |
| Caps keyword | Caption face, converted to UPPERCASE, same size and colour | Bodoni Moda 800 / opsz 14 + 0.6 px stroke | as above | same as caption words |

**Hairline rule:** every stroke must stay visible on bright and mid-tone footage. Never use a high optical size (it thins the hairlines of H, W, M, A until words read broken, e.g. "H APPENS"). Use the LOW optical-size axis (≈14, the sturdy text cut), weight ≥ 800, a same-colour stroke (giant 1.5 px, caption 0.6 px at W = 720, drawn at 2×) and the soft shadow below. Check a full-size crop of one giant word before delivering. Punctuation on caption words is exactly the user's ("first," stays "FIRST,").

Rules: one family, one colour. Giant words are always uppercase and drop trailing punctuation. Caption words keep the user's case and punctuation; only the keyword is uppercased. Draw letter by letter with the font's own advances (tracking via an offset). Font note: identified by letterform only (ball-terminal Didone with extreme stroke contrast); check against a reference crop, then fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Shadow: caption (0, +3 px, blur 6 px, #000000 at 60 %) plus a tight edge shadow (0, +1 px, blur 1.5 px, 55 %); giant (0, +5 px, blur 12 px, 55 %) plus the same tight edge shadow. Values at W = 720. Without them the yellow disappears on cream walls and wood.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Caption word entrance | hard pop, 1 f, no fade, no movement, at the word's spoken start | 0 s |
| Caption chunk exit | hard cut; all words of the chunk vanish in one frame | 0 s |
| Giant word entrance | hard pop at the word's spoken start, full size, no scale | 0 s |
| Giant word exit | hard cut, on the same frame as the chunk end or later by ≤ 0.15 s | 0 s |
| Gaps | between chunks nothing is on screen (the reference had a 1.3 s clean gap) | — |

Never: fades, slides, bounce, scale pops, typewriter letter-by-letter, rotation, wipes, glitch, shake, flashes, or any effect on cuts. The style is all hard pops.

### 1.6 What may happen to the user's footage

Nothing. Allowed: full-frame display, untouched, with text and shadow overlays on top. Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed changes; blur, tint, darken, colour grading or filters; cards, splits, zooms, graphic transitions, B-roll frames, background swaps; adding footage the user did not supply. The primary footage plays live, in sync with the audio, at all times.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by a giant word or a caption. Pick the giant band (1.3) from the face top: face top ≥ 0.15H → face-safe band; ≈ 0.10H → low-face band; face top < 0.09H or a face fills the top → no giant on that shot (use a caption-only moment, or place the giant only on a face-free shot) |
| Giant over hair | The reference giant overlapped the top of the hair; allowed only when the face top is below 0.25H |
| Caption lane | Default 1.3. If the face bottom edge is below 0.62H, move the block down so the first line sits ≥ 0.03H under the chin; if that pushes the last baseline below 0.93H, use a 1–2 line chunk |
| Footage text (signs, UI) | If readable footage text sits in the lane for more than 1 s, shift the lane up by 0.08H |
| Edges | Every glyph stays ≥ 0.03W from the left and right edges (giants ≥ 0.03W; captions ≥ 0.07W) |

---

## 7. MOMENT LIBRARY
Family codes: **T** title (giant word) · **C** caption · **K** keyword · **E** end.

### MOMENT T1 · GIANT KEYWORD SLAM
**What it is:** the most important spoken word of a phrase appears in giant capitals across the top of the frame at the moment it is spoken, holds under the speaker's face, and disappears with its caption chunk. The word is removed from the small caption so it is not shown twice.
**Use when:** a topic, verb or contrast word carries the sentence (reference: one verb or noun per phrase); 1 per phrase, every 2–3 s. **Avoid when:** two giants would be < 1.5 s apart, or the face leaves no band (1.7).
**Text:** 1 word from the user's own text, uppercase, no trailing punctuation, 3–9 letters ideal (longer words still fit by shrinking), ≤ 1 per chunk.
**Geometry / Graphics:** giant band per 1.3 (free, face-safe or low-face). Word centred on x = 0.505W, width 0.93W unless the cap-height limit binds first (then narrower, still centred). Butter yellow, giant shadow. Cap height measured on the reference: 0.173H BEST, 0.13H FORCE, 0.146H THEY, 0.14H MAKE.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start (1.43 s [43]) | giant | alpha | 0 → 1, full size | hard pop |
| hold | giant | — | final state; 0.77–0.97 s | — |
| end (2.20 s [66]) | giant | alpha | 1 → 0 | hard cut |

Start = the word's spoken start (within ±0.05 s). Hold: 0.7–1.0 s; end at or just after the chunk end, never across a footage cut (end on the cut frame).
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 keeps building in the lane; the giant word is skipped in the caption line.
**Exit:** hard cut.
**Flow prompt text:** "As the word {{WORD}} is spoken, it appears all at once in huge pale yellow capital letters in an elegant high-contrast serif face, stretched almost edge to edge across the top of the frame above the speaker's head. It stays for under a second and then disappears at once. It never covers the speaker's face."
**Still-image state:** the giant word at the top, full size.

### MOMENT T2 · GIANT STACK
**What it is:** two short words stacked on two lines as one giant block, for a two-word idea.
**Use when:** a two-word phrase is the whole point (a name, "never again"); the shot has no face in the top 0.45H (B-roll, product, landscape). **Avoid when:** a face is in the top half.
**Text:** two consecutive user words, uppercase, ≤ 14 letters total, no punctuation.
**Geometry / Graphics:** T1 styling; each line fits 0.93W; line pitch 0.95 em; block centred on y = 0.22H; total cap height ≤ 0.32H.
**Motion:** both words pop together at the first word's start, hold 1.0–1.3 s, hard cut. Same table as T1.
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 continues in the lane; both words skipped in the caption.
**Exit:** hard cut.
**Build notes:** draw each line like T1; stack with 0.95 em pitch.
**Flow prompt text:** "As {{WORD_1}} {{WORD_2}} is spoken, both words appear at once, stacked on two lines, in huge pale yellow capital letters in an elegant high-contrast serif face across the upper part of the frame. They stay about a second and disappear at once."
**Still-image state:** stack at the top.

### MOMENT T3 · GIANT ON BROLL
**What it is:** T1 at full reference size on a shot with no face in the top 0.30H.
**Use when:** B-roll, product, hands, plants, landscapes: a face-free shot with a strong spoken word. **Avoid when:** any face or head sits in y 0.10–0.35H.
**Text:** as T1.
**Geometry / Graphics:** free band: centre y 0.20H, cap height up to 0.17H [326], width 0.93W (demo2: YEAR at cap 0.14H, AUTOMATE cap 0.07H because the long word was width-limited).
**Motion:** as T1; end ≥ 1 f before a footage cut (on the cut frame).
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 lane as normal.
**Exit:** hard cut.
**Build notes:** as T1.
**Flow prompt text:** "As the word {{WORD}} is spoken, it appears all at once in huge pale yellow capital letters in an elegant high-contrast serif face across the top of the frame, over the scene, stays under a second and disappears at once."
**Still-image state:** the giant word in the free band.

### MOMENT C1 · BUTTER CAPTION BLOCK
**What it is:** a phrase of 2–5 words pops in word by word near the bottom, centred, in small bold lowercase Didone. Words stay put once they appear. The whole block is cut at the end of the phrase. Nothing is on screen between phrases.
**Use when:** always on speech. **Avoid when:** no speech and no on-screen need (use C2 or skip).
**Text:** the user's exact words, case as written; 2–5 words per chunk (reference: 2, 5, 2, 3); split at punctuation and natural phrases; never end on an article, preposition or conjunction; ≤ 1 keyword per chunk (K1); a giant word (T1) is skipped inside the chunk.
**Geometry / Graphics:** caption lane (1.3). Lay the whole chunk out first so no word moves: greedy wrap at 0.80W, lines centred on x = 0.50W, line pitch 0.095H, word space 0.22em. If one word is wider than 0.86W, shrink the whole chunk's font until it fits (demo2: INVESTMENTS, at 0.86 of base).
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | new word | alpha | 0 → 1 at its fixed position | hard pop (1 f) |
| chunk end | all words | alpha | 1 → 0 | hard cut |

Word start = spoken start. Chunk end = last word start + 0.45–0.7 s hold, or the next chunk's first word, or the footage cut, whichever is first (reference holds: 0.47, 0.40, 0.27 and 0.73 s after the last word). Gaps of 0.5–1.3 s with no caption are allowed in pauses.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system. At a cut, end the chunk on the cut frame if the speech continues; start the next chunk on the next word.
**Exit:** hard cut.
**Flow prompt text:** "In the lower middle of the frame, short captions appear word by word in small bold lowercase letters in pale yellow, in an elegant high-contrast serif face. Each word pops into place at the moment it is spoken and never moves. When the phrase is finished, all its words disappear at once. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk in the lane.

### MOMENT K1 · CAPS KEYWORD
**What it is:** one word per chunk is written in capitals at the same size, as a second beat of emphasis inside the small caption.
**Use when:** a chunk has a meaning-carrying noun or verb (the object, the action, the number word). **Avoid when:** the chunk is only fillers; never two caps words in one chunk; never on a word already used as a giant.
**Text:** 1 word per chunk, ≤ 1 per 2.5 s on average, uppercase conversion only (the word stays the user's word). Keep its punctuation.
**Geometry / Graphics:** same face, size, colour and shadow as caption words; it is simply uppercase, so it is wider (a 6-letter caps word ≈ 0.50W).
**Motion:** pops in on its own spoken start like any word (C1 table).
**Footage / plate behaviour:** untouched.
**Captions during it:** inside C1. It may sit anywhere in the chunk (reference: last, first, last).
**Exit:** with the chunk.
**Build notes:** call `.upper` on the display text only; the audit uses the original word.
**Flow prompt text:** "Inside the small caption, the word {{KEYWORD}} is written in capital letters while the other words stay lowercase, all in the same pale yellow."
**Still-image state:** chunk with the capital word.

### MOMENT C2 · SOLO WORD CAPTION
**What it is:** a one-word chunk (a punchy single word or an interjection) sits alone on one line in the lane.
**Use when:** a single emphatic word sits between pauses, or a shot has a one-word beat. **Avoid when:** it would be the giant's own word.
**Text:** 1 user word, case as written (uppercase if it is the chunk's keyword).
**Geometry / Graphics:** C1 lane, one line, baseline 0.79H, centred.
**Motion:** pop at the spoken start; hold ≥ 0.4 s after; hard cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** it is the caption.
**Exit:** hard cut.
**Build notes:** same as C1 with one word.
**Flow prompt text:** "Near the bottom of the frame, the single word {{WORD}} pops in by itself in small pale yellow lettering in an elegant serif face and disappears at once."
**Still-image state:** one word in the lane.

### MOMENT C3 · LANE SHIFT
**What it is:** the caption block sits higher or lower so it clears a face, a hand or readable footage text, without any animation.
**Use when:** the face bottom is below 0.62H, a subject stands in the lane, or footage text sits there. **Avoid when:** the default lane is clear.
**Text:** none.
**Geometry / Graphics:** shift the block up by 0.08H (to put the last baseline near 0.71H) or down to a last baseline of 0.90H; never inside the giant band; keep the chunk's line count ≤ 2 when shifted up.
**Motion:** none; the position is fixed for the whole chunk; at a cut it may change on the cut frame.
**Footage / plate behaviour:** untouched.
**Captions during it:** inside C1.
**Exit:** with the chunk.
**Build notes:** add a y offset to the lane baseline per chunk.
**Flow prompt text:** "The captions sit slightly {{higher_or_lower}} than usual so they stay clear of the {{SUBJECT}}."
**Still-image state:** chunk at the shifted lane.

### MOMENT E1 · CLEAN CLOSE
**What it is:** the last chunk (and last giant) hard-cut away just before the clip ends, so the final frames are clean footage.
**Use when:** always at the end of a speech video. **Avoid when:** the audio ends in the last 0.2 s.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:** the last caption and giant end at the clip end minus 0.05–0.3 s (reference: last text left 0.07 s before the end; demo2: 0.05 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** none after the cut.
**Exit:** hard cut.
**Build notes:** set the last chunk end and giant end ≤ duration − 0.05 s.
**Flow prompt text:** "The last words disappear at once just before the video ends and the picture finishes clean."
**Still-image state:** footage only.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 + T1 on the first topic word | T3 on face-free B-roll words, T1 on speaker words, K1 per chunk | C1 + T1 on the payoff word, E1 |
| Single talking head, no cuts | C1 + T1 | T1 every 2–3 s, K1 per chunk, C3 if the face is low | T1 on the last word, E1 |
| B-roll only, no speech | C2 phrases timed to the shots + T3 on the title word | T2 on a two-word idea | E1 |
| Still image + text | giant word in the band + C1 chunk in the lane | — | — |

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
