# Google Flow prompt · Serif Staircase
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Serif Staircase" caption style to it.

The look in one sentence: Untouched full-frame footage, a tilted white italic serif title rising in, captions building in a staircase of white serif words and yellow italic keywords, black-on-white label boxes on bright shots.

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
| Text white | #FFFFFF | Title, roman caption words |
| Keyword yellow | #F4F10E | Italic emphasis words |
| Label box | #FFFFFF at 95 % | Box behind caption text in box mode |
| Label text | #111111 | Caption text inside the box |
| Text shadow | #000000 at 40 % | Soft shadow under white and yellow text on footage |
| Box shadow | #000000 at 12 % | Faint edge shadow on the box |

Brand-swap rule: if the user gives a brand colour, replace Keyword yellow with it (keep it bright enough to read on footage). Never change the white or the black. No other colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, borders, masks, rounded corners, blur plates or colour overlays. |
| Label box (box mode only) | Sharp-cornered rectangle, white, fits the text: width = text width + 2 × 0.035W [38] padding; height 0.058H [112]; centred on x = 0.50W. Measured on the reference: x 0.089–0.898W, y 0.204–0.262H for a 23-character line. |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor = the speaker's face box (or the main subject). |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Title block | 0.13, 0.08, 0.86, 0.18 [140,156,929,346]; centre x = 0.49W, centre y = 0.13H [250] | Tilted title |
| Staircase lane | 0.18, 0.60, 0.82, 0.74 [194,1152,885,1421] | Caption mode "build" on a speaker or calm footage |
| Staircase line 1 | text centred on x = 0.50W; baseline ≈ 0.645H [1238] | First line |
| Staircase line 2 | line pitch 0.064H [123] below line 1; single emphasis word centred on x = 0.41W [443]; two or more words centred on x = 0.50W | Second line |
| Box lane (top) | box centre y = 0.233H [447] | Caption mode "box" (default) |
| Box lane (bottom) | box centre y = 0.80H [1536] | Box mode when the subject or a face sits in the top lane |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Italic serif with calligraphic shapes, semibold, mixed case (as the user wrote it), rotated −4.5° (rising to the right) | Newsreader Display SemiBold Italic | Lora SemiBold Italic, Source Serif 4 SemiBold Italic | Font size ≈ 0.20W [215]; width of the line ≈ 0.72W [780] for a 9-letter word; max width 0.80W |
| Caption roman word | Soft old-style serif, medium weight, mixed case as written, tight word spacing | Newsreader Medium | Lora Medium, Source Serif 4 | Font size ≈ 0.10W [108]; letter-spacing −0.02em |
| Caption keyword | Same family, italic, yellow | Newsreader Medium Italic | Lora Italic, Source Serif 4 Italic | same size as roman words |
| Box text | Same roman face, near-black | Newsreader Medium | Lora Medium | Font size ≈ 0.09W [97]; letter-spacing −0.02em |
| Solo keyword (C3) | Keyword style, enlarged | Newsreader Medium Italic | Lora Italic | 1.5× the caption size |

Font note: the family was identified by letterform only (soft calligraphic italic, ink-trap-free old-style roman). Check the render against the reference crops and fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Rules: text case exactly as the user wrote it (no forced uppercase). No outline-only text. Only the title is rotated; captions and boxes are never rotated.

Text on footage gets a soft shadow (0, +3 px, blur 6 px, #000000 at 40 %). The title shadow is stronger: (0, +6 px, blur 10 px, #000000 at 45 %).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Title entrance | ease-out (cubic: 1−(1−t)³), rise from below + alpha | 0.25 s (6 f) |
| Title exit | linear alpha fade, no movement | 0.38 s (9 f) |
| Caption word entrance | ease-out alpha ramp, no movement | 0.125 s (3 f) |
| Caption chunk exit | hard cut, replaced in the same frame | 1 f |
| Box caption entrance and exit | hard cut | 1 f |
| Cuts | hard cut (no transition effect), caption mode switches on the same frame | 0 f |

Never: bounce, overshoot, spring, slides, typewriter letter-by-letter, wipes, glitch, shake, scale pops on captions, flashes, transitions between shots, rotation of anything except the title.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Slow push-in about the face or subject anchor (M1) | Total scale ≤ 1.08 per shot; reset at the next cut |
| Text, shadow and label box overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; freezing; blur, glitch, warp, zoom-punch or colour grading of any kind; adding footage the user did not supply. The primary footage plays live, in sync with the audio, at all times. Footage is never hidden or darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by captions or the box. The title may overlap hair or background but never the forehead, eyes, nose or mouth. |
| Staircase lane | Default region 1.3. If the face box bottom edge is below 0.58H, move the whole lane down so line 1 sits ≥ 0.03H under the chin; if that pushes line 2 below 0.88H, switch the chunk to box mode in the bottom lane. |
| Title block | If the face box top is above 0.20H, shift the title up (min centre y 0.07H) or shrink it; if that fails, drop it to the bottom of the video's first calm shot or skip to T2 later. |
| Box lane | Pick the top or bottom lane with less subject overlap; never over a face. |
| Footage text (signs, UI) | If readable footage text sits in the chosen lane for more than 1 s, use the other lane. |
| Edges | Every glyph and the box stay ≥ 0.04W from the left and right edges. |

---

## 7. MOMENT LIBRARY
Family codes: **T** title · **C** caption · **X** cut treatment · **M** footage motion · **E** ending.

### MOMENT T1 · TILTED TITLE RISE
**What it is:** a one- or two-word white italic serif title, tilted slightly upwards to the right, fades in while rising a few pixels, holds, then fades out in place.
**Use when:** the opening line states the topic; the video starts on a speaker or a calm shot. **Avoid when:** the first 0.3 s contains a cut, or the face box cannot be cleared (use the 1.7 fallback).
**Text:** 1–2 words from the user's own words (or a title the user supplied), as written. Max 16 characters in total. If two words do not fit on one line at ≤ 0.80W, stack them in two lines (line pitch 0.9 em, both centred).
**Geometry / Graphics:** Title block, centre x = 0.49W, centre y = 0.13H, rotation −4.5° about its centre, white fill, title shadow. Font size scaled so the widest line ≈ 0.72W (9 letters ≈ 0.2W font size); cap at 0.22W.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.04–0.29 [1–7] | title | alpha | 0 → 1 | ease-out |
| 0.04–0.29 [1–7] | title | y offset | +0.03H [58] → 0 | ease-out (cubic) |
| 0.29–1.54 [7–37] | title | hold | final state | — |
| 1.54–1.92 [37–46] | title | alpha | 1 → 0 | linear |

Start: 0.04–0.3 s into the video (at the first spoken word at the latest). Hold: 1.1–1.5 s; the fade-out starts when the first caption chunk ends or 1.5 s after the start, whichever is later, and finishes ≥ 0.3 s before a cut.
**Footage / plate behaviour:** footage untouched.
**Captions during it:** C1 runs underneath in the staircase lane; the title never shares a region with it.
**Exit:** 0.38 s linear fade.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, written in a graceful white italic serif and tilted slightly upwards to the right, fades in near the top of the frame while rising a little, stays for about a second and a half, then fades away. It never covers the speaker's face."
**Still-image state:** final state.

### MOMENT C1 · STAIRCASE CAPTION
**What it is:** a phrase builds word by word in the lower middle of the frame. Plain words are white roman serif; keywords are yellow italic and each keyword drops to a new line, so the phrase steps down like a staircase. When the phrase is complete the whole block is replaced by the next one.
**Use when:** always on speaker shots and calm footage. **Avoid when:** the lane's background is bright or busy (use C2).
**Text:** the user's exact words, case as written. Chunk rules: 3–5 words per chunk; split at punctuation and natural phrases; never end a chunk on an article, preposition or conjunction ("a", "the", "of", "and", "to"); a chunk lasts 0.8–1.5 s; prefer chunk changes at cuts. Keywords: 1–2 per chunk, ≤ 3 per 5 s; choose the meaning-carrying nouns and verbs (the topic word, the person, the action); never an article or preposition. The first word of a chunk may be a keyword.
**Geometry / Graphics:** Staircase lane. The whole chunk is laid out before it starts so that no word ever moves: the first word of the chunk is always on line 1, centred on x = 0.50W at baseline 0.645H. Line break rule: a keyword that follows a roman word or another keyword starts a new line; roman words that follow a keyword join that keyword's line to its right; roman words that follow roman words stay on the same line. Max 3 lines. Line 2+ pitch 0.064H. A line with a single keyword is centred on x = 0.41W; any other line is centred on x = 0.50W. Words are separated by 0.25 em.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | new word | alpha | 0 → 1 (starts as a dim olive-grey ghost, reaches full colour) | ease-out, 3 f |
| word start | earlier words | — | unchanged (no colour change, no movement) | — |
| chunk end | all words of the chunk | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Word start = the word's spoken start time. Chunk end = the next chunk's first word start (no empty gap), or min(last word end + 0.4 s, next cut) for the last chunk of a shot.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system. At a cut, the chunk in progress is replaced in the same frame by the next chunk (in C1 or C2 mode, chosen for the new shot).
**Exit:** hard cut per the table.
**Flow prompt text:** "In the lower middle of the frame, captions appear word by word in a soft serif typeface. Ordinary words are white; important words, {{KEYWORDS}}, are yellow and slanted, and each one starts a new line slightly to the left, so the caption steps downwards. Each new word fades in softly in place. When a phrase is complete it is replaced at once by the next phrase. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### MOMENT C2 · LABEL BOX CAPTION
**What it is:** the whole phrase appears at once as black serif text on a plain white label box near the top of the frame.
**Use when:** the footage under the staircase lane is bright (mean luminance > 0.6) or detailed (flat objects, text, patterns); B-roll with a main subject in the middle; any shot where white and yellow text would not read. **Avoid when:** the shot is a calm speaker shot with a dark or mid-tone lane (use C1).
**Text:** the user's exact words, case as written; one line, 2–6 words, ≤ 28 characters (≤ 0.82W wide); same chunk rules as C1; no keyword colours (all text near-black).
**Geometry / Graphics:** Label box and Box text per 1.2 and 1.4. Box lane (top) by default; bottom lane per 1.7. The box fits the text exactly each time the phrase changes.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| phrase start | box + text | alpha | 0 → 1 | hard cut (1 f) |
| phrase end | box + text | alpha | 1 → 0, replaced in the same frame by the next phrase | hard cut (1 f) |

Phrase length: 1.0–2.5 s (the reference held phrases for 2.2 s and 1.0 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption. The whole phrase is visible at once, so the viewer reads while the speaker or narration continues; for speech, start the box at the phrase's first word.
**Exit:** hard cut.
**Build notes:** draw the box with `ImageDraw.rectangle` at 2× then downscale; add the faint box shadow as a blurred rectangle at 12 % alpha.
**Flow prompt text:** "At the top of the frame, a short line of text, {{PHRASE}}, appears all at once in black serif lettering on a plain white rectangular label that fits the text, and is replaced at once by the next line. The label never covers the main subject."
**Still-image state:** the phrase in the box.

### MOMENT X1 · CUT RESTYLE
**What it is:** the shot changes with a plain hard cut, and the caption mode switches in the same frame to suit the new shot. There is no transition effect.
**Use when:** every footage cut. **Avoid when:** never; do not add effects.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut (the footage's own cut time) | caption | mode and chunk | C1 chunk → C2 phrase (or the reverse), same frame as the cut | hard cut |

The caption in progress is not allowed to straddle a cut in a different mode: end the old chunk on the cut frame and start the new one on that frame. If the speech continues across the cut, the new chunk starts with the next word that is still unspoken at the cut.
**Footage / plate behaviour:** untouched; no flash, blur or zoom on the cut.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** compute the caption mode per shot from the scene table (luminance of the lane region, subject overlap); keep the mode constant within a shot.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the captions change their style in the same moment to suit the new shot: {{CAPTION_STYLE_BEFORE}} before the cut and {{CAPTION_STYLE_AFTER}} after it."
**Still-image state:** none.

### MOMENT T2 · SECTION TITLE
**What it is:** a second tilted title, smaller, for a new topic word later in the video.
**Use when:** the story moves to a new topic, step or name (≥ 3 s after T1 ended, ≥ 0.5 s after a cut). **Avoid when:** a caption chunk occupies the title block region (it never does by default) or the video is shorter than 6 s.
**Text:** 1–2 of the user's words, as written, max 16 characters.
**Geometry / Graphics:** same as T1 at 0.75× size; centre x = 0.50W (or 0.30W / 0.70W to avoid the face), centre y = 0.11H, rotation −4.5°.
**Motion:** same as T1 (0.25 s rise + fade-in, hold 1.0–1.3 s, 0.38 s fade-out).
**Footage / plate behaviour:** untouched.
**Captions during it:** unchanged.
**Exit:** 0.38 s linear fade, ≥ 0.3 s before a cut.
**Build notes:** reuse the T1 renderer.
**Flow prompt text:** "Later in the video, a smaller tilted title, {{TITLE}}, in the same white italic serif fades in near the top while rising a little, stays for about a second, and fades out."
**Still-image state:** final state.

### MOMENT C3 · SOLO KEYWORD
**What it is:** one payoff word alone at 1.5× size in yellow italic.
**Use when:** a strong turn or payoff word ("never", a number, a name) that deserves a beat. **Avoid when:** the word is longer than 12 characters; max 2 per video, ≥ 3 s apart.
**Text:** one user word, case as written.
**Geometry / Graphics:** Keyword style at 1.5× size, centred on x = 0.50W, baseline 0.66H (staircase lane), text shadow.
**Motion:** C1's word entrance (3 f alpha ramp); hold 0.4–0.8 s; hard cut to the next chunk.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the normal chunk for its duration.
**Exit:** hard cut.
**Build notes:** same renderer as C1; scale the font size, not the bitmap.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in the lower middle of the frame in large yellow slanted lettering, fading in softly, then is replaced by the next caption."
**Still-image state:** the word.

### MOMENT M1 · SLOW PUSH
**What it is:** a barely visible push-in on a long static shot so it never looks frozen.
**Use when:** a shot longer than 2 s with no cut and little motion. **Avoid when:** the footage already moves a lot.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:** scale ×1.00 → ×1.06 across the shot (linear), about the subject anchor (face box centre); reset to 1.00 at the next cut.
**Footage / plate behaviour:** live footage, scaled only; no blur.
**Captions during it:** unaffected (captions do not scale).
**Exit:** reset by the cut.
**Build notes:** `Image.resize(..., box=floats)` about the anchor; clamp the crop box inside the frame.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### MOMENT E1 · END HOLD
**What it is:** the last caption stays until just before the end, then the picture finishes clean.
**Use when:** every video. **Avoid when:** the last line is a payoff that needs C3.
**Text:** the last chunk's words.
**Geometry / Graphics:** C1 or C2 as chosen for the last shot.
**Motion:** the last chunk or phrase holds to min(last word end + 0.4 s, end − 0.25 s); the final 0.25 s [6 f] has no caption.
**Footage / plate behaviour:** untouched (M1 optional).
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1/C2.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 | X1 on every cut; C1 on speaker shots, C2 on bright or busy B-roll; M1 on a long B-roll shot | E1 |
| Single talking head, no cuts | T1 + C1 | C3 on one payoff word; T2 at a new topic; M1 on a shot > 2 s | E1 |
| B-roll only, no speech | T1 (user's own title words, if any) + C2 | X1 on every cut; C2 phrases of 1.0–2.5 s; M1 on long shots | E1 |
| Still image + text | T1 final state, C2 phrase in the settled state | — | — |

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
