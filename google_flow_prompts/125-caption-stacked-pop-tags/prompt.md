# Google Flow prompt · Stacked Pop Tags
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Stacked Pop Tags" caption style to it.

The look in one sentence: Tiny white helper words stacked around one huge slanted condensed keyword in a hot accent colour that slides in and hard-cuts to the next phrase.

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
| Keyword accent | #BBDD32 — a parameter; the public demo uses #FF2E93 | Big keywords |
| Helper text | #FFFFFF | Small words |
| Keyword shadow | #2A0016 at 90 % in the demo (dark tone of the accent; the reference used a dark green-black) | Hard drop shadow |
| Helper shadow | #000000 | Dark halo under small words |

Brand-swap rule: replace the accent with the user's colour (bright, saturated, readable on footage). White stays white.

### 1.2 Containers / shapes
Footage full frame, untouched. No boxes, plates, strokes or gradients. Text only, plus shadow.

### 1.3 Layouts / grid

| Lane | Region | Use |
|---|---|---|
| Top | stack top at 0.10H (reference: keyword at y 0.13–0.22 above the head) | Only when no face or subject occupies it (reference had headroom; the demo uses it on faceless B-roll) |
| Low | stack top at 0.60H, stack bottom ≤ 0.90H | Default on a talking head or when the face is high |
| Alignment | Left edge at 0.07W, right edge at 0.93W, or centred | Reference was left; vary per chunk |

Stack: lines top to bottom in reading order, line gap 0.012H. A key line is as tall as its cap height + 0.032H (descender room); a small line is its cap height + 0.25 × small size.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Very condensed heavy sans, mixed case as written, sheared right 0.2 (about 11°) | Anton | Bebas Neue, Barlow Condensed Bold | Cap height 0.09H (reference ≈ 0.10H); shrink until ink width ≤ 0.86W |
| Solo keyword | Same | Anton | same | Cap height 1.22 × 0.09H, same width cap |
| Helper word | Wide geometric sans, medium weight | Montserrat Medium (500) | Manrope, Poppins Medium | 0.066W (reference ≈ 0.042W; enlarged for legibility on bright footage) |

Helper rule: first word of a small line at full size on the baseline; each following word on the same line at 0.9 × size, dropped 0.25 × (0.9 size) below the baseline, word gap 0.3 em.

Shadows: keyword hard drop shadow offset (0.06 × font size) right and down, 1.2 px blur; helper words a dark halo (5 px max-filter of the glyph, +2 px down, 2 px blur, 95 %).

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Helper word entrance | ease-out cubic, alpha 0 → 1 with a rise of 0.012H | 0.125 s |
| Keyword entrance | ease-out cubic, alpha 0 → 1 with a slide of 0.04W toward its rest place from the side it is aligned to (reference: slid from the left edge) | 0.17 s |
| Phrase exit | hard cut in the next phrase's first frame (or at the phrase end) | 1 frame |
Never: bounce, overshoot, scale pops, typing, wipes, glitch, shake, rotation, flashes, effects on cuts, boxes.

### 1.6 What may happen to the user's footage
Full-frame display untouched; text with shadow on top. Forbidden: replacing, retiming, trimming, reordering, blurring, grading, cards, splits, backgrounds, B-roll frames. Footage is never darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Edges | Ink at rest ≥ 0.05W from left and right, ≥ 0.02H from top, ≤ 0.97H bottom; while sliding ≥ 0.02W |
| Text vs text | No overlap between any two words of a chunk |
| Footage text (UI, signs) | Helper words may cross it briefly; keyword may not hide a readable label for > 1 s: move lane |

---

## 7. MOMENT LIBRARY
Families: **C** caption · **K** keyword · **P** placement · **X** cut · **E** ending. Energy:  calm ·  medium ·  high.

### MOMENT C1 · STACKED PHRASE
**What it is:** a phrase builds word by word as a left-aligned (or right or centred) stack: tiny helper words above and below one big keyword.
**Use when:** always. **Avoid when:** the chunk is a single word (use C2).
**Text:** the user's exact words, case as written; 2–6 words, one keyword.
**Geometry:** lines per 1.3. Reading order = line order; keyword on its own line; helper words that follow each other share a line (staggered per 1.4). Whole layout fixed before the first word shows.
**Motion (reference: words every 0.3–0.5 s, phrase hold 1.5–2.8 s):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | helper word | alpha + rise | 0 → 1, 0.012H → 0 | ease-out, 0.125 s |
| word start | keyword | K1 | — | — |
| phrase end | whole stack | alpha | 1 → 0 | hard cut |

Phrase end = next phrase's first word or min(last word start + 0.7 s, next cut); at least 0.25 s after the last word.
**Footage:** untouched. **Exit:** hard cut.
**Flow prompt text:** "In the lower part of the frame, a short phrase builds word by word as a small stack. Tiny white words sit above and below one large slanted condensed word, {{KEYWORD}}, in {{ACCENT_COLOUR}}. The only words are {{CAPTION_WORDS}}. The phrase is replaced at once by the next phrase."
**Still-image state:** the full stack.

### MOMENT K1 · KEY SLIDE-IN
**What it is:** the keyword arrives with a short side slide and fade, the main hit of every phrase.
**Use when:** every chunk. **Avoid when:** never.
**Text:** one meaning-carrying word.
**Geometry:** Anton, cap 0.09H, shear 0.2, accent fill, hard shadow.
**Motion:** alpha 0 → 1 and x offset 0.04W (from the aligned side) → 0, ease-out cubic, 0.17 s.
**Footage:** untouched. **Exit:** with the phrase.
**Build notes:** shear the glyph mask with an affine about the baseline before downscaling.
**Flow prompt text:** "The key word {{KEYWORD}} slides in a short distance from the side while fading in, in large slanted condensed {{ACCENT_COLOUR}} lettering with a hard dark shadow."
**Still-image state:** keyword at rest.

### MOMENT C2 · SOLO KEY
**What it is:** a one-word chunk, the keyword alone, larger.
**Use when:** a short punchy word or sentence end ("left.", "now"). **Avoid when:** longer than 10 characters.
**Text:** one word. **Geometry:** key size 1.22×, lane and alignment.
**Motion:** as K1; hold 0.5–0.9 s; hard cut.
**Footage:** untouched. **Exit:** hard cut.
**Build notes:** same renderer, larger cap height.
**Flow prompt text:** "One word, {{WORD}}, appears alone in very large slanted condensed {{ACCENT_COLOUR}} lettering, then is replaced by the next caption."
**Still-image state:** the word.

### MOMENT C3 · DOUBLE KEY
**What it is:** two keywords in one stack separated by one small word, for a payoff line.
**Use when:** last line, a two-part contrast. **Avoid when:** more than once per video or on a face lane that cannot hold 0.35H.
**Text:** 2 keywords + helper words, ≤ 5 words.
**Geometry:** key / small / key stack in the low lane; the stack may rise to 0.54H.
**Motion:** each keyword K1 at its own word time.
**Footage:** untouched. **Exit:** hard cut or E1.
**Flow prompt text:** "Two important words, {{KEYWORD_1}} and {{KEYWORD_2}}, appear one after the other in large slanted condensed {{ACCENT_COLOUR}} lettering with one small white word between them."
**Still-image state:** full stack.

### MOMENT P1 · LANE PLACEMENT
**What it is:** where each stack sits: low lane by default; top lane where no face or subject is there; alignment alternates between chunks.
**Use when:** every chunk. **Text:** none.
**Spec (lane, alignment):** per 1.3 and 1.7. Check against the shot's face box. Never keep the same alignment for more than two chunks in a row.
**Motion:** none. **Footage:** untouched.
**Flow prompt text:** "The caption sits in the lower part of the frame, or near the top when the picture's subject is lower, never over a face."

### MOMENT X1 · CUT HAND-OFF
**What it is:** footage cuts plainly; the caption in progress hard-cuts to the next phrase on the same frame.
**Use when:** every cut. **Text:** none.
**Motion:** old phrase ends on the cut frame; the next phrase starts at the cut (or at its first word if later); lane may switch.
**Footage:** no effect. **Flow prompt text:** "At each cut the picture cuts plainly and the current caption is replaced at once."

### MOMENT E1 · END HOLD
**What it is:** last phrase holds to min(last word start + 0.6 s, end − 0.25 s), then clean.
**Spec:** per C1. **Flow prompt text:** "The last caption stays until just before the end, then disappears."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 (low) | X1 each cut, P1 top lane on faceless B-roll, C2 on a one-word sentence | C3 + E1 |
| Single talking head | C1 | C1 with alternating alignment, C2 on punchy words | E1 |
| B-roll only, no speech | C1 | P1 lanes by subject | C2 |
| Still image + text | C1 settled | — | — |

Each video gets its own selection. Never paste a row blindly.

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
