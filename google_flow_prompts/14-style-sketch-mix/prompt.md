# Google Flow prompt · Sketch Mix
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Sketch Mix" motion style to it.

The look in one sentence: A fat white keyword in a pencil-scribbled ellipse, word-by-word handwritten captions, a round speaker bubble over B-roll and a cream sketch page with a hand-circled phrase.

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
| PAPER | `#FAF4ED` | the cream page (SK05) |
| PENCIL | `#E2DACD` at 88 % (second pass 70 %) | scribble ellipse over footage |
| INK | `#3A3935` | page ink: circle, handwriting, bold caption on paper |
| WHITE | `#FFFFFF` | keyword, captions over footage |
| SHADOW | `#000000` at 30–50 %, blur 0.007 W | soft shadow under white text |

No other colour is added. Brand variant: PAPER may become another warm neutral; ink stays near-black.

### 1.2 Containers / shapes
- **Full frame:** all footage plays full frame, untouched. There are no cards or borders.
- **Speaker bubble:** a circle, diameter **0.50 W** [540], centred at x = 0.75 W (or 0.25 W) and y = 0.235 H [450]; flush with the frame edge. No border, no shadow.
- **Scribble ellipse:** two loose hand-drawn passes (1.9 and 1.6 turns) with a wobble of ±1.2 %, rotated −4° (left end lower), stroke 0.0065 W [7] and 0.0045 W [5].
- **Paper page:** full-frame flat PAPER colour, no texture.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | ultra-heavy sans, UPPERCASE, white, tight | Archivo (wght 900, wdth 100) | Montserrat Black, Inter Black, Anton | widest allowed 0.52 W; start 0.075 H [144] and shrink |
| Hand caption | round handwriting, bold, white | Gaegu Bold | Patrick Hand, Caveat, Gochi Hand | 0.058 H [111] |
| Bold caption | geometric heavy sans, sentence case | Montserrat (wght 800) | Inter ExtraBold, Poppins Bold | 0.049 H [94] |
| Page phrase | handwriting, dark ink, 2–3 short lines | Gaegu Bold | same as hand caption | 0.080 H [154], line pitch 0.080 H |
| Page caption | as bold caption, INK colour, no shadow | Montserrat 800 | same | 0.049 H |

### 1.4 Motion language
- **Draw-on:** strokes are revealed along their path in 7 f (0.23 s), ease-out-cubic; a second pass follows 1 f later.
- **Wipe:** text appears or leaves by a left-to-right crop of its own width (6 f in, 5 f out), ease-out-cubic.
- **Word fade:** each caption word fades in over 4 f (0.17 s), ease-out-cubic, at its spoken time, in its final position. Words never move.
- **Bubble pop:** diameter 0.14 W to 0.50 W over 8 f with a tiny overshoot (ease-out-back, 1.2), starting 5 f after a cut.
- **Page fade:** the paper fades in over 5 f.
- Nothing bounces except the bubble pop, nothing rotates while moving, nothing slides.

### 1.5 What may happen to the user's footage
- Allowed: overlays (keyword, ellipse, captions); a **bubble** showing the speaker (live footage if the speaker is on screen in the current shot, otherwise a still of the speaker or a ≤ 1.5 s silent loop); a cream page that covers a **B-roll shot with no person** for at most 1.5 s (≤ 15 % of the video).
- The primary footage plays full frame, in sync with the audio, except under the page.
- Forbidden: colour grading, speed changes, trimming, reordering, replacing anything, blurring, cutting a face out, and covering any face that is speaking.

### 1.6 Safe zones
- Keyword + ellipse sit below the chin: centre y = the lower of 0.50 H and (face bottom + 0.09 H). Keep the ellipse top at least 0.02 H under the chin. Recheck on shots that zoom in.
- Hand and bold captions sit at y = 0.665 H and 0.675 H (baseline); when a face reaches below 0.55 H, move the caption to 0.775 H.
- The bubble sits in the top corner opposite any visible face (check the B-roll's face box).
- Never put the bubble over a speaking face.

---

## 7. MOMENT LIBRARY
Families: **K** keyword, **C** caption, **B** bubble, **P** page, **X** extension. Energy:  calm,  medium,  punchy.

### MOMENT SK01 · SCRIBBLE WORD
**What it is:** a fat white UPPERCASE word inside a hand-drawn double ellipse that draws on, then wipes away before the next cut.
**Use when:** a talking-head shot has a theme word or contrast word; the opener; the payoff. **Avoid when:** the word would sit on the face, or the shot is shorter than 1 s.
**Text:** one user word (the topic or payoff word), UPPERCASE, up to 7 letters at full size.
**Geometry / Graphics:** word centred at x = 0.50 W, y per safe zone (default 0.50 H). Ellipse centre x 0.47 W, half-width = min(0.47 W, (word width + 0.32 W) / 2), half-height 0.066 H, rotated −4°. Colours PENCIL; word WHITE with SHADOW 30 %.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 | ellipse pass 1 | drawn length | 0 → 100 % over 7 f | out-cubic |
| +1 f | ellipse pass 2 | drawn length | 0 → 100 % over 7 f | out-cubic |
| +2 f | word | left-to-right wipe | 0 → 100 % over 6 f | out-cubic |
| end − 5 f | ellipse + word | erase from the left | 0 → 100 % over 5 f | out-cubic |
**Footage:** untouched. **Captions during it:** hand captions below (SK02).
**Exit:** erased by the end of the shot (at least 0.2 s before a cut); on the last shot it stays to the end.
**Build notes:** draw polylines at 2x and downscale; wipe by cropping the text layer; erase by trimming the start of the path.
**Flow prompt text:** "A thick white capital word, {{WORD}}, is encircled by a loose pencil-style double ellipse that is drawn on in a quarter of a second while the word wipes in from left to right, sits below the speaker's chin for {{DURATION}} seconds, then is erased from left to right. The speaker is never covered."
**Still-image state:** word and both ellipse passes complete.

### MOMENT SK02 · HAND CAPTION
**What it is:** white handwritten words appear one at a time, laid out at their final place as a short centred chunk.
**Use when:** any shot where the speaker is the main footage. **Avoid when:** B-roll (use SK03).
**Text:** user words in their own case, 2–3 words, max 20 characters per chunk; split at punctuation and at cuts; never end a chunk on an article or preposition.
**Geometry:** centred at x = 0.50 W, baseline y 0.665 H (0.775 H if the face is low); word gap 1.1 spaces; WHITE with SHADOW 30 %.
**Motion:** each word fades in over 4 f at its spoken time (out-cubic). A chunk shows from its first word to min(next chunk start − 0.05 s, last word start + 0.6 s).
**Footage:** untouched. **Exit:** the whole chunk disappears when the next begins.
**Build notes:** lay out the full chunk first, draw only the words whose time has come.
**Flow prompt text:** "Handwritten white words appear one at a time near the lower middle of the frame, each fading in as it is spoken, in short groups of two or three words, then the group is replaced by the next. They stay clear of the face."

### MOMENT SK03 · BOLD CAPTION
**What it is:** the same word-by-word system in a heavy white sans with a soft shadow, for B-roll.
**Use when:** a shot without the speaker as main footage. **Avoid when:** a face sits at y 0.58–0.72 H.
**Text:** as SK02, max 18 characters per chunk.
**Geometry:** centred at x 0.50 W, baseline y 0.675 H; WHITE with SHADOW 50 %.
**Motion:** as SK02. **Footage:** untouched. **Exit:** replaced by the next chunk; hard cut with the shot.
**Flow prompt text:** "Bold white words with a soft shadow appear one at a time in the lower middle of the frame, each fading in as it is spoken, then are replaced by the next short group."

### MOMENT SK04 · SPEAKER BUBBLE
**What it is:** when the shot cuts to B-roll, the speaker shrinks into a round window in the top corner and keeps talking.
**Use when:** every cut from the speaker to B-roll and between B-roll shots while the speech goes on. **Avoid when:** a face or key subject sits in that corner (flip the side, SK08); the speaker never appears in the video (skip).
**Content:** the speaker from the nearest talking-head shot: cover-fit crop centred on the face, about 0.46 W wide. Live if the speaker is on screen; otherwise a still (a calm frame with the mouth nearly closed) or a ≤ 1.5 s silent loop.
**Geometry:** circle 0.50 W, centre y 0.235 H, centre x 0.75 W or 0.25 W (side). Anti-aliased edge, no border.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut + 5 f | bubble | diameter | 0.14 W → 0.50 W over 8 f | out-back 1.2 |
**Footage:** B-roll full frame, untouched. **Captions during it:** SK03 at the lower middle.
**Exit:** disappears with the shot at the next cut and pops again on the next B-roll if still needed.
**Build notes:** cache the circular crop per diameter; mask drawn at 3x.
**Flow prompt text:** "Right after the cut, a small round window of the speaker pops open in the {{SIDE}} top corner and grows to about half the frame width, then stays there while the full-frame shot plays."

### MOMENT SK05 · PAPER PAGE
**What it is:** a flat cream page with a hand-circled short phrase and a bold dark caption below it, written word by word.
**Use when:** a B-roll shot with no person near the end (a list, a number, a time phrase, a payoff). Hidden footage ≤ 1.5 s. **Avoid when:** a face is speaking on screen.
**Text:** the phrase (1–3 words, user's case) inside the circle; the spoken chunks as bold captions below.
**Geometry:** PAPER fill. Ellipse centre (0.50 W, 0.295 H), half-width 0.34 W, half-height 0.135 H, two INK passes (0.0065 W, 0.0045 W), rotated −3°. Phrase lines centred in it, pitch 0.080 H. Caption baseline y 0.655 H.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 | page | opacity | 0 → 100 % over 5 f | out-cubic |
| +5 f + 0.05 s | circle | drawn length | 0 → 100 % over 9 f | out-cubic |
| +3 f later | phrase lines | wipe | 0 → 100 % over 7 f | out-cubic |
**Footage:** covered; the audio goes on. **Exit:** hard cut on the next footage cut (the page must end on a cut).
**Flow prompt text:** "A plain warm cream page fades in over the shot. A loose dark pencil circle is drawn on, with {{PHRASE}} handwritten inside it, and bold dark words appear one at a time below it as they are spoken. On the next shot the page is gone."
**Still-image state:** page, circle, phrase and the full caption.

### MOMENT SK06 · PENCIL UNDERLINE
**What it is:** a hand-drawn PENCIL underline under one bold caption word over B-roll. **Use when:** an emphasis word on B-roll (a number, "first", "only"). **Avoid when:** more than 3 per video.
**Geometry:** one pass 0.004 W, 6° wobble, 0.01 H under the baseline, spanning the word + 4 %. **Motion:** draws on in 6 f, out-cubic, at the word's time; leaves with the chunk.
**Flow prompt text:** "A loose pencil underline is drawn under the word {{WORD}} as it is spoken."

### MOMENT SK07 · NUMBER CIRCLE
**What it is:** a numeral or amount in handwriting inside a small scribble circle (diameter 0.22 W) at the top corner, for lists and amounts. **Use when:** steps (1, 2, 3), amounts, durations. **Text:** the numeral from the user's words only.
**Motion:** circle draws on 7 f, numeral wipes 5 f; replaced by the next numeral with a 3 f erase. Opposite corner to the bubble.
**Flow prompt text:** "A small pencil circle with the handwritten {{NUMBER}} inside it is drawn on in the {{SIDE}} top corner."

### MOMENT SK08 · BUBBLE FLIP
**What it is:** the bubble pops on the other side (x 0.25 W) when a visible face or key subject occupies the usual corner. **Use when:** the B-roll has a person at the top right (or left). Same spec as SK04 with x mirrored. **Flow prompt text:** as SK04 with the other side.

### MOMENT SK09 · SCRIBBLE POSTER
**What it is:** the still state for images: SK01 word and ellipse over the photo, SK02 caption below. **Use when:** C4/C5. Everything settled, no animation. **Flow prompt text:** "A thick white capital word inside a loose pencil ellipse sits under the subject's chin, with handwritten white words below."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| talking head → B-roll → talking head | SK01 + SK02 | SK04 on each B-roll cut + SK03; SK05 on a person-free shot | SK01 on the payoff word + SK02 |
| single talking head | SK01 + SK02 | SK01 on a second theme word | SK01 payoff |
| B-roll only | SK03 + SK07 | SK06, SK05 | SK05 |
| still image | SK09 | – | – |

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
