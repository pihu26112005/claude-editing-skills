# Google Flow prompt · Crown Word Script
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Crown Word Script" caption style to it.

The look in one sentence: One heavy condensed uppercase keyword with a thick black outline pops in above the head while flowing white script captions with a thin outline build word by word at the lower left.

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
| Crown fill | #FCC73B warm yellow | Crown words. Parameter: the accent; any saturated colour works (the public demo uses #FF3E9A) |
| Outline | #000000 | Crown outline, script outline |
| Script fill | #FFFFFF | Script captions |
| Ghost word | grey ≈ #969696 at 35 % alpha | First frames of a new script word |
| Shadow | #000000 at 45 % | Soft shadow under crown and script |

Brand-swap rule: the user's colour replaces the crown fill only. White script and black outlines never change.

### 1.2 Containers / shapes

None. Footage is full frame, untouched. No plates, boxes or cards behind text.

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Crown band | y 0.134–0.223H [257–428] on the reference (sitting on the hair top); centre x 0.50W; max width 0.62W [670] | T1 default. Demo2 adaptation: band y 0.035–0.115H, centre y 0.075H, because the head top was at 0.09–0.15H |
| Script lane | baseline 0.805H [1546]; x-height band 0.755–0.82H | C1 |
| Script x anchors | left edge 0.08W [86] on even chunks, 0.14W [151] on odd chunks; right edge ≤ 0.94W | C1, C2 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Crown word | Heavy condensed grotesque, UPPERCASE, outline 0.008W each side, tight spacing | Anton | Bebas Neue, Archivo ExtraCondensed Black | Cap height ≈ 0.045H; font ≈ 88 px at W 720; shrink until the word ≤ 0.62W |
| Script caption | Flowing connected brush script, bold, mixed case as written, white, outline 3.2 px at W 720 | Dancing Script Bold (wght 700) | Pacifico, Kaushan Script, Sriracha | Font ≈ 70 px at W 720 (≈ 0.097W); shrink in 2 px steps until the chunk ≤ 0.84W |

Word space in script = 0.9 × the font's space width. Rule: crown words are UPPERCASE; script keeps the user's case.

Soft shadow under both: offset (0, +3 px at W 720), blur 4 px, #000000 at 45 %.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Crown pop-in | ease-out cubic, scale 0.82 → 1.00, alpha 0 → 1 over 0.083 s | 0.125 s |
| Crown swap | hard cut to the next word after a 0.1–0.25 s gap | 0 f |
| Crown exit | linear alpha fade, no movement | 0.21 s |
| Script word entrance | ghost (alpha 0.35, grey 150) → full white, ease-out | 0.17 s |
| Script chunk exit | hard cut | 1 f |

Never: slides, bounce, typing letter by letter, rotation, boxes, flashes, effects on cuts.

### 1.6 What may happen to the user's footage

Full-frame display only; text and shadow overlays. Forbidden: replacing, retiming, trimming, reordering, blur, glitch, zoom, colour grading. Footage is never hidden or darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Head and face | Crown band bottom edge ≥ 0.02H above the head top. If the head top is above 0.11H, drop the crown to a smaller size (cap height 0.035H) or use T4. Script never covers a speaking mouth: default lane 0.755–0.82H is below the chin on talking heads. |
| Script lane | If the face bottom edge is below 0.74H, raise the lane (baseline min 0.70H) or move to the side away from the mouth. |
| Edges | Every glyph ≥ 0.06W from left and right. |
| Footage text | If readable footage text sits in the lane for > 1 s, shift the lane up by 0.08H. |

---

## 7. MOMENT LIBRARY
Family codes: **T** title (crown) · **C** caption · **K** keyword accent · **E** end. Energy:  calm ·  medium ·  high.

### MOMENT T1 · CROWN WORD POP
**What it is:** one keyword in heavy condensed capitals with a thick black outline snaps in above the head, holds, then is replaced by the next keyword.
**Use when:** a theme, turn, step or payoff word is spoken. **Avoid when:** the head top is above 0.04H.
**Text:** one user word, UPPERCASE, ≤ 12 characters. Start = the word's spoken start (reference: 0.46 s after speech start). Hold 0.7–1.6 s (reference holds 1.1 s, 1.1 s, 0.96 s).
**Geometry / Graphics:** Crown band, centre x (0.50W default), fill = accent, outline 0.008W, shadow per 1.4.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start | crown | alpha / scale | 0 → 1 over 0.083 s; 0.82 → 1.00 over 0.125 s | ease-out cubic |
| start + 0.125 → end − 0.21 | crown | hold | final state | — |
| end − 0.21 → end | crown | alpha | 1 → 0 | linear |

**Footage behaviour:** untouched. **Captions during it:** C1 runs below. **Exit:** T2 fade or hard swap (T3).
**Flow prompt text:** "Above the speaker's head, the word {{WORD}} pops in written in thick bold condensed capital letters with a heavy black outline in {{ACCENT_COLOUR}}, stays for about a second, then fades away. It never covers the face."
**Still-image state:** the word at full scale above the head.

### MOMENT C1 · SCRIPT BUILD CAPTION
**What it is:** a phrase builds word by word on one line at the lower left in white brush script with a thin black outline. Each word first shows as a faint grey ghost, then turns full white. Earlier words stay still.
**Use when:** always on spoken phrases. **Avoid when:** the lane covers a mouth (shift per 1.7).
**Text:** the user's exact words, case as written; 3–5 words per chunk, one line, ≤ 0.84W; split at punctuation; never end on an article, preposition or conjunction. Chunk length 0.8–1.7 s.
**Geometry / Graphics:** Script lane, x anchor per 1.3 (C2 alternation), the whole chunk laid out before its first word so no word moves.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | new word | alpha, grey | 0.35 → 1, grey 150 → 255 | ease-out, 0.17 s |
| chunk end | whole chunk | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Reference words appeared every ~0.3 s; chunk end = next chunk's first word, or last word end + 0.4 s.
**Footage behaviour:** untouched.
**Build notes:** Dancing Script variable font, `set_variation_by_axes([700])`; draw each word with `stroke_width` 3.2 px and `anchor="ls"` at the shared baseline; shadow per 1.4.
**Flow prompt text:** "In the lower left of the frame, captions build word by word in flowing white handwritten-style lettering with a thin black outline. Each new word fades in from a faint grey to white in place. When a phrase is complete it is replaced at once by the next phrase. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### MOMENT T2 · CROWN SOFT EXIT
**What it is:** the crown word fades out in place over about 0.2 s before the next word or at the end of the hold.
**Use when:** after every crown word that is not followed directly by another (and at the very end). **Avoid when:** a hard swap (T3) is wanted.
**Text:** none. **Geometry:** as T1.
**Motion:** alpha 1 → 0, linear, 0.21 s, no movement; ends ≥ 0.1 s before the next crown pop.
**Exit:** gone. **Flow prompt text:** "The word fades away softly in place without moving."

### MOMENT T3 · CROWN RELAY
**What it is:** several crown words follow each other in the same spot with a 0.1–0.25 s empty gap, one per step of a list.
**Use when:** 3+ parallel phrases or a fast listing. **Avoid when:** words are shorter than 0.7 s apart.
**Text:** one word per step. **Motion:** each word is a T1 + T2 with the gap; centre stays fixed.
**Flow prompt text:** "One after another, the words {{WORDS}} appear in the same spot above the head, each popping in, holding briefly and fading, with a tiny pause between them."

### MOMENT T4 · SIDE CROWN
**What it is:** T1 shifted sideways, to 0.27W or 0.73W, when the head sits high or off centre.
**Use when:** the shot's head top is above 0.11H or the head is on one side. **Text:** one word; centre x on the side away from the head. **Motion:** as T1. Keep ≥ 0.06W from the edge.
**Flow prompt text:** "The word {{WORD}} pops in above and to the {{SIDE}} of the head, away from the face."

### MOMENT C2 · SCRIPT ANCHOR SHIFT
**What it is:** the left edge of the script alternates between 0.08W and 0.14W from chunk to chunk so the caption does not look pinned.
**Use when:** always with C1. **Text:** none. **Rule:** clamp so the right edge ≤ 0.94W.

### MOMENT C3 · SOLO SCRIPT LINE
**What it is:** a one- or two-word payoff shown alone at 1.3× the script size at the lane.
**Use when:** the last words or a strong turn. Max 2 per video, ≥ 3 s apart. **Text:** the user's words, as written (not repeated in a crown word at the same time). **Motion:** C1 entrance, hold 0.6–1.0 s, hard cut.
**Flow prompt text:** "One short phrase, {{WORDS}}, appears alone and larger in the same white script lettering, then is replaced."

### MOMENT K1 · ACCENT SCRIPT WORD
**What it is:** one word of a chunk coloured in the accent (with the same black outline) instead of white.
**Use when:** a chunk contains the key number or name and no crown word is up. Max 1 per chunk, ≤ 2 per video. **Text:** one word.
**Flow prompt text:** "One word of the caption, {{WORD}}, is written in {{ACCENT_COLOUR}} instead of white."

### MOMENT E1 · END HOLD
**What it is:** the last chunk holds until min(last word end + 0.4 s, end − 0.25 s); the last crown word fades ≥ 0.1 s before the end; the picture ends clean.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 on the topic word + C1 | T3 on a list, T1 per phrase, T4 when the head moves | T1 on the payoff word + E1 |
| Single talking head | T1 + C1 | T1 per phrase, K1 on one number, C3 once | T1 + E1 |
| B-roll only, no speech | T4 or T1 on the first phrase's key word + C1 | T1 every 2 s, caption lane lifted on busy shots | E1 |
| Still image + text | T1 final state + C1 chunk | — | — |

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
