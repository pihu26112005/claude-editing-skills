# Google Flow prompt · Ghost Underline
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Ghost Underline" caption style to it.

The look in one sentence: Mid-frame captions building word by word from ghost-grey to heavy white sans, each phrase with one slim serif-italic keyword carrying a gradient underline.

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

| Role | Measured default | Demo accent (parameter) | Used for |
|---|---|---|---|
| Sans word | #FFFFFF | #FFFFFF | Ordinary caption words |
| Keyword | #F3E7CE (warm cream) | #EADFFF (pale lilac) | Serif italic keyword |
| Underline start → end | #C8A840 → #FF9F4A → #E6734D (gold, amber, coral) | #FF4FA3 → #8A5CFF (magenta to violet) | 2-3 px gradient line under keywords |
| Ghost word | #444444 rising to its final colour | same | First frames of every word |
| Shadow | none on black plate; use #000000 at 90 % blurred 6 px on footage | same | Legibility over footage |

Accent rule: the keyword colour and the underline gradient are parameters. If the user gives a brand colour, use it as the gradient start and a lighter or shifted tint as the end; keep the keyword colour pale. White stays white.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, boxes, bars, tints or blur plates behind text. |
| Underline | Height 0.004W [4], full width of the keyword (glyph advance), sits 0.012W [13] under the baseline, horizontal linear gradient, appears with the word. Measured: 2 px at 720 wide, 8 px under the baseline. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions of the frame) | Use |
|---|---|---|
| Caption lane | centre y = 0.665H, block width ≤ 0.76W, centred on x = 0.50W | All C moments |
| Line pitch | 1.22 × sans size [≈ 0.107W] | Two-line chunks |
| Title lane | centre y = 0.075H, centred | T1, T2 |
| Edges | every glyph ≥ 0.05W from left and right | Always |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption word | Heavy geometric grotesque, bold 700, mixed case as written, tight natural spacing | Inter Bold | Inter Tight Bold, Manrope ExtraBold | 0.088W [95] |
| Keyword | Light calligraphic serif italic, medium 500–560 weight, same text colour treatment, underlined | Newsreader Italic | Lora Italic, Source Serif 4 Italic | 0.098W [106] |
| Solo word | Keyword style enlarged | Newsreader Italic | Lora Italic | 0.17W |
| Title | Keyword style enlarged | Newsreader Italic | Lora Italic | 0.125W |

Word gap = 0.28 × sans size. Baselines of sans and serif words on a line are aligned. Case exactly as the user wrote it. No outline-only text.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Word entrance | colour ramp ghost grey → final colour, linear, with alpha 0 → 1 ease-out cubic 1−(1−p)^3 at 1.7× speed | 0.21 s (5 f) |
| Chunk exit | hard cut, replaced in the same frame by the next chunk or by nothing | 1 f |
| Layout | the whole chunk is laid out before its first word shows; no word ever moves | — |
| Title | rise 0.02H + alpha, ease-out cubic, 0.25 s; fade out linear 0.3 s | — |

Never: bounce, overshoot, slides, letter-by-letter typing, scale pops, rotation, wipes, glitch, shake, flashes, effects on cuts.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text, soft shadow and underline overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed changes; blur, grading, filters, cards, splits, B-roll frames, background swaps, graphic transitions. The primary footage plays live, in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Default lane centre y = 0.665H keeps a two-line chunk (top ≈ 0.60H) under a face whose bottom is ≤ 0.50H. If the face bottom is lower, move the lane down (min block bottom ≤ 0.90H) or shorten to one line. |
| Title lane | Title bottom (with underline) ≤ 0.14H; skip or shrink if the face top is above 0.15H. |
| Footage text (signs, UI) | If readable footage text sits in the lane for > 1 s, shift the lane up or down by one line pitch. |

---

## 7. MOMENT LIBRARY
Family codes: **T** title · **C** caption · **K** keyword · **X** cut handling · **E** end. Energy legend:  calm ·  medium ·  high.

### MOMENT C1 · GHOST WORD BUILD
**What it is:** a phrase of 2–6 words is laid out in the caption lane; each word fades in at its spoken time, starting as a dark ghost grey and firming up to white. Earlier words stay put. At the end of the phrase the whole block cuts away.
**Use when:** always, on any footage. **Avoid when:** never.
**Text:** the user's exact words, case as written. Chunk rules: 2–6 words, ≤ 28 characters per line, split at punctuation and natural phrases, never end on an article, preposition or conjunction; chunk lasts 0.6–2.0 s; start = first word start; end = next chunk start − 0.05 s, or last word end + 0.4 s for the last chunk.
**Geometry / Graphics:** caption lane 1.3, sans size 0.088W. Wrap into two balanced lines only when the single line would exceed 0.76W; first word always on line 1. Line pitch 1.22 × size. Lines centred on x = 0.50W.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | word | colour | #444444 → white | linear, 0.21 s |
| word start | word | alpha | 0 → 1 | ease-out cubic, 0.12 s |
| chunk end | whole block | alpha | 1 → 0 | hard cut |

**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut; the next chunk starts on the next word, with no gap longer than the speech pause.
**Build notes:** pre-render each word as a glyph mask plus a blurred shadow mask at 2× then downscale; place by measured advance so a word's position never changes; tint per frame.
**Flow prompt text:** "In the middle-lower part of the frame, the caption builds word by word in heavy white sans-serif lettering. Each word first appears as a dim grey ghost and firms up to bright white within a fifth of a second. Nothing moves once placed. When the phrase is done it vanishes at once. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### MOMENT K1 · UNDERLINED ITALIC KEYWORD
**What it is:** one meaning-carrying word per phrase is set in a light serif italic in a pale tint and carries a thin gradient underline that appears with the word.
**Use when:** every chunk with a noun or verb that carries the idea; the topic word, the action, the number. **Avoid when:** more than 1 per chunk (2 only in a chunk of ≥ 5 words), or an article or preposition.
**Text:** the keyword, as written, including attached punctuation.
**Geometry / Graphics:** Keyword type 0.098W, baseline shared with the line, colour per 1.1; underline per 1.2 under the word's advance width.
**Motion:** same word entrance as C1; the underline fades in with the word (alpha only).
**Footage / plate behaviour:** untouched.
**Captions during it:** the keyword sits in the normal flow of the chunk.
**Exit:** with the chunk.
**Build notes:** align baselines by font ascent; draw the underline as a 3 px gradient strip per frame.
**Flow prompt text:** "One important word in the phrase, {{KEYWORD}}, is written in a slim slanted serif style in a pale tint with a thin colour-fading line under it, while the other words stay bold white."
**Still-image state:** the keyword with its underline.

### MOMENT C2 · SINGLE-LINE CHUNK
**What it is:** a short phrase (2–3 words) that fits one line, centred in the lane so that its single line sits on the lane's centre.
**Use when:** quick beats, short sentences. **Avoid when:** more than 28 characters.
**Text:** as C1.
**Geometry / Graphics:** as C1, one line centred vertically on y = 0.665H.
**Motion:** as C1.
**Footage / plate behaviour:** untouched. **Captions during it:** this is the caption. **Exit:** hard cut.
**Build notes:** same renderer.
**Flow prompt text:** "A short phrase builds word by word on one line in the lower middle of the frame, in bold white lettering, each word fading up from grey."
**Still-image state:** the phrase.

### MOMENT C3 · SOLO PAYOFF WORD
**What it is:** one payoff word alone in the keyword style at 0.17W with its underline.
**Use when:** the last word, a number, a turn. **Avoid when:** longer than 12 characters; max 2 per video, ≥ 3 s apart.
**Text:** one user word.
**Geometry / Graphics:** Solo word type, centred on x = 0.50W, baseline lane centre y = 0.66H.
**Motion:** C1 entrance; hold 0.4–0.8 s; hard cut or end.
**Footage / plate behaviour:** untouched. **Captions during it:** replaces the chunk. **Exit:** hard cut.
**Build notes:** same renderer, bigger size.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in large slanted pale lettering with a colour-fading line underneath, fading up softly."
**Still-image state:** the word.

### MOMENT T1 · ITALIC TITLE
**What it is:** a one- or two-word title in the keyword style at the top of the frame, rising 0.02H while fading in, with the gradient underline, then fading out.
**Use when:** the opening line names the topic. **Avoid when:** the face top is above 0.15H and the title would touch it; a cut within 0.3 s.
**Text:** 1–2 of the user's words, as written, max 16 characters; if moved into the title, remove them from the first caption chunk (caption audit counts them once).
**Geometry / Graphics:** keyword type 0.125W, centred x = 0.50W, centre y = 0.075H; underline per 1.2.
**Motion:** rise and fade-in 0.25 s ease-out cubic; hold 1.0–1.4 s; fade-out 0.3 s linear, finished ≥ 0.3 s before a cut.
**Footage / plate behaviour:** untouched. **Captions during it:** C1 runs lower; they never share a region. **Exit:** fade.
**Build notes:** reuse the keyword renderer.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, in slim slanted serif lettering with a thin colour-fading underline, fades in at the top of the frame while rising slightly, stays about a second, then fades away. It never covers the face."
**Still-image state:** title.

### MOMENT T2 · SECTION TITLE
**What it is:** a second title for a new topic, at 0.85× T1 size.
**Use when:** a real topic change, ≥ 3 s after T1 and ≥ 0.5 s after a cut. **Avoid when:** video shorter than 6 s.
**Text:** 1–2 user words. **Geometry / Graphics:** as T1, 0.85× size, centre x 0.50W (or 0.30W / 0.70W). **Motion:** as T1. **Footage:** untouched. **Exit:** fade.
**Build notes:** reuse T1.
**Flow prompt text:** "Later, a smaller title, {{TITLE}}, in the same slim slanted lettering fades in near the top, stays about a second, and fades out."
**Still-image state:** title.

### MOMENT X1 · CUT-SAFE SWAP
**What it is:** the footage cuts plainly; captions are not changed by the cut unless a chunk boundary falls within 0.3 s, in which case the boundary is moved to the cut frame.
**Use when:** every footage cut. **Avoid when:** never; add no effect.
**Text:** none. **Geometry:** none.
**Motion:** hard cut only. **Footage:** untouched. **Captions during it:** unchanged, or swapped on the cut frame. **Exit:** none.
**Build notes:** compute chunk boundaries against the scene cut list.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect; the caption keeps building and only changes between phrases."
**Still-image state:** none.

### MOMENT E1 · END HOLD
**What it is:** the last phrase or solo word holds until just before the end.
**Use when:** every video. **Avoid when:** never.
**Text:** the last chunk. **Motion:** holds to min(last word end + 0.4 s, end − 0.25 s); the last 0.25 s has no caption. **Footage:** untouched. **Exit:** end of video.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** the last chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 with K1 | C1 + K1 on every chunk; C2 on short beats; X1 on cuts | C3 + E1 |
| Single talking head | T1 + C1 with K1 | T2 at a topic change; C3 on one payoff word | E1 |
| B-roll only, no speech | C1 with K1 from the first caption | 1.0–2.0 s chunks across the shots | E1 |
| Still image + text | one C1 chunk with K1 in the settled state | — | — |

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
