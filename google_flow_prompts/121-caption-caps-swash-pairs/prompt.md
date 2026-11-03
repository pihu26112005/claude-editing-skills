# Google Flow prompt · Caps Swash Pairs
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Caps Swash Pairs" caption style to it.

The look in one sentence: Tiny wide-tracked white caps words orbiting one giant white italic serif keyword in the lower third, with an optional single accent-tinted payoff word.

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
| Caps ink | #FFFFFF | All small capitals |
| Keyword ink | #FFFFFF at 98 % (reference showed it slightly translucent while arriving) | Giant italic keyword |
| Soft shadow | #000000 at 42 %, offset (0, +3 px), blur 5 px (at 720 W) | Under every text element; the only thing that keeps it legible on bright footage |
| Accent (parameter) | measured default: none (reference is white only). Design default for demos: any single hue, e.g. #FF5CAA | Optional tint of ONE keyword (payoff word) per video; K1 |

Brand swap rule: the accent is a parameter. Use at most one accent colour per video; never tint the small capitals. No background plates, boxes or strokes anywhere.

### 1.2 Containers / shapes

None. The footage is full-frame and untouched. Text sits directly on the footage with a soft shadow. No cards, boxes, underlines, outlines or bars.

### 1.3 Layout (pair block, bottom third)

| Element | Position (fractions) | Notes |
|---|---|---|
| Pre-caps row | centre y = 0.745H [1430]; left edge = keyword's left edge | Measured: caps row sits just above the keyword's ascenders, left-aligned with the keyword |
| Keyword | baseline y = 0.855H [1642]; centred on x = 0.50W | Measured: keyword baseline ≈ 0.89–0.92H in the reference; moved up 0.04H here to clear platform UI |
| Post-caps row | centre y = 0.905H [1738]; right edge = keyword's right edge (side R) or left edge = keyword's left edge (side L) | Measured: trailing caps tuck under the keyword's end |
| Solo caps line (C2) | centre y = 0.84H [1613]; centred on x = 0.50W | Measured: caps-only lines sit lower-middle, larger |
| Horizontal clamp | every row stays inside 0.07W–0.93W | Rows slide inward, never get cut |
| Title zone (T1, T2) | y 0.035–0.115H, centred | above the face box, never touching it |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caps (pair block) | All caps, semibold, wide letter-spacing, white | Montserrat SemiBold (wght 600) | Josefin Sans SemiBold, Manrope SemiBold | 0.047W [51]; tracking +0.09em; word gap 0.033W [36] |
| Solo caps (C2) | same face, larger | Montserrat SemiBold | same | 0.069W [75]; tracking +0.10em; word gap 0.036W |
| Keyword | Lowercase high-contrast italic serif, medium weight, white | Playfair Display Italic (wght 500) | Bodoni Moda Italic, Instrument Serif Italic | 0.18W [195] (x-height about 0.09W); shrink in steps of 0.006W until width ≤ 0.84W; never below 0.083W |
| Title (T1) |  same italic serif, larger | Playfair Display Italic | same | 0.13W, one line ≤ 0.84W |
| Kicker (T2) |  same caps as pair block | Montserrat SemiBold | same | 0.040W; tracking +0.14em |

Case: caps rows are uppercased by the style (the user's words, converted); keywords keep the user's case (lowercase in practice). Punctuation stays (commas and full stops remain on whichever word carries them).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Keyword entrance | ease-out cubic (1−(1−t)³): alpha 0→1, rise 14 px → 0, scale 0.94 → 1 | 0.22 s |
| Caps word entrance | ease-out alpha ramp, 8 px rise (C2 only) | 0.10 s (C1 rows: alpha only) |
| Chunk exit | hard cut, whole block vanishes in one frame | 1 f |
| Block-to-block | hard cut; the next block starts on its first word's time | 0 f |

Words appear one by one on their spoken times and never move after appearing. Never: bounce, overshoot, slides, typing letter by letter, glow, outlines, boxes, scale pops, camera shake, flashes.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text overlay with soft shadow | Only the elements in this file |

Forbidden: crop, zoom, split, card, mask, blur, grade, speed change, retiming, reorder, background swap.

### 1.7 Safe zones

- Face box (x 0.34–0.66, y 0.15–0.40) always clear: pair block lives at y ≥ 0.70H; title zone at y ≤ 0.12H.
- Keep text inside 0.07W–0.93W. Keep the very bottom 0.05H free; keep the platform-watermark corner (x > 0.90W, y > 0.90H) free when the footage carries a sparkle or logo there: post-caps may stop short.
- Captions and titles never overlap: a title (T1/T2) must be gone, or end before the first pair block of the same time range begins, and never shares a frame with a pair block unless it is in the title zone (they are 0.6H apart).

## 7. MOMENT LIBRARY
Families: C caption, K keyword, T title, E end. Energy: low / medium / high.

### C1 · PAIR BLOCK — C medium (signature)
**What it is:** the core caption: 1–4 small caps words sit above a giant italic keyword, and 0–2 caps words trail under it. Words appear on their own spoken times.
**Use when:** every phrase with one meaning-carrying noun or verb. **Avoid when:** the phrase has no strong word (use C2), or the keyword would exceed the width limit at 0.083W.
**Text:** pre words (caps), keyword (as written), post words (caps), side L or R. Chunk 3–6 words in total, 0.9–2.0 s.
**Geometry / Graphics:** 1.3 and 1.4. Keyword width ≤ 0.84W; pre row left-aligned to the keyword's left edge; post row right-aligned (R) or left-aligned (L) to the keyword; clamp to 0.07–0.93W.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word time − 0 | each caps word | alpha | 0 → 1 over 0.10 s | ease-out |
| keyword time | keyword | alpha, y, scale | 0 → 1, +14 px → 0, 0.94 → 1 over 0.22 s | ease-out cubic |
| chunk end | whole block | alpha | 1 → 0 | hard cut |

**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption. Pre caps may wait alone (up to 1.0 s) before the keyword arrives; the keyword slot stays empty.
**Exit:** hard cut on the next chunk's first frame.
**Build notes:** draw caps and keyword at 2x, downscale, add the shadow (blur 5 px at 1x, 42 %). Lay the full row out before showing its first word so nothing moves. Measured on the demo: caps size 34 px, keyword 130 px (shrunk to fit), baseline y 1094, caps rows at y 954 and 1158 of 1280.
**Flow prompt text:** "A small row of white capital letters reading {{PRE WORDS}} appears word by word just above the lower chest, then the word {{KEYWORD}} fades in large in elegant white italic serif lettering right beneath it, and {{POST WORDS}} appears in small capitals tucked under the end of that word. The person and the scene are unchanged."
**Still-image state:** full block visible, keyword at full opacity.

### C2 · SOLO CAPS LINE — C medium (signature)
**What it is:** a phrase with no strong keyword shown as one larger caps line in the lower-middle area.
**Use when:** connective phrases, short sentences, rhythm resets between two C1 blocks. **Avoid when:** more than 24 characters (split it).
**Text:** 1–4 words, ≤ 24 characters.
**Geometry / Graphics:** Montserrat SemiBold 0.069W, tracking +0.10em, centred at x 0.50W, y 0.84H.
**Motion:** each word alpha 0 → 1 and rise 8 px → 0, 0.12 s ease-out, on its spoken time; hard cut out.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** reduce the size in steps if the line passes 0.86W.
**Flow prompt text:** "Large white wide-spaced capital letters reading {{PHRASE}} appear word by word in the lower middle of the frame, then disappear together."
**Still-image state:** line fully visible.

### C3 · HERO KEYWORD — C high
**What it is:** the keyword alone, with no caps rows, for a one-word beat.
**Use when:** a strong one-word payoff, a number, a name. Max 2 per video, ≥ 3 s apart. **Avoid when:** the word is already used in a neighbouring block.
**Text:** one word.
**Geometry / Graphics:** keyword at 1.25× the C1 size (shrink to ≤ 0.84W), baseline y 0.84H, centred.
**Motion:** as C1 keyword entrance, 0.26 s.
**Footage / plate behaviour:** untouched.
**Exit:** hard cut.
**Flow prompt text:** "One word, {{WORD}}, fades in very large in white italic serif lettering in the lower part of the frame."
**Still-image state:** word visible.

### C4 · LEAD-IN CAPS — C low
**What it is:** the pre-caps row alone during the first words of a C1 block, before its keyword arrives.
**Use when:** automatic: it is part of C1 whenever the keyword is not the first word. Listed so the plan keeps it deliberate.
**Geometry / Graphics:** identical to the C1 pre row. The keyword slot below stays empty; nothing shifts when the keyword lands.
**Motion:** as C1.
**Flow prompt text:** "Small white capital words build one by one in a row near the lower chest, leaving the space below them empty for one coming large word."

### K1 · ACCENT KEYWORD — K medium
**What it is:** the payoff keyword of the whole video drawn in the accent colour.
**Use when:** the last line or the single most important word. Once per video. **Avoid when:** no clear payoff.
**Text:** one keyword; accent colour (one hue, high saturation, never a hue already dominant in the footage's lower third).
**Geometry / Graphics:** C1 or C3 keyword with the fill replaced by the accent; the shadow stays black.
**Motion:** as C1.
**Flow prompt text:** "The final large italic word {{WORD}} appears in {{ACCENT COLOUR NAME}} instead of white."
**Still-image state:** word tinted.

### T1 · SWASH TITLE — T medium
**What it is:** an opening title in the keyword's italic serif at the top of the frame, with a small caps kicker above it.
**Use when:** the video has a clear topic phrase in the user's own words; the first 2 s. **Avoid when:** the title zone would touch a face above y 0.13H, or the topic words are used in caption chunks (then move them out of the chunks and include them in the audit).
**Text:** 1–3 words from the user's text (or the user's own title), lowercase.
**Geometry / Graphics:** italic serif 0.13W, centred x 0.50W, baseline y 0.105H; kicker (T2 style) at y 0.045H.
**Motion:** alpha 0 → 1 and rise 14 px → 0 over 0.25 s ease-out; hold ≥ 1.0 s; linear fade out 0.3 s. Never during a pair block's first 0.3 s.
**Footage / plate behaviour:** untouched.
**Exit:** fade, no movement.
**Flow prompt text:** "A short title, {{TITLE}}, fades in near the top of the frame in white italic serif lettering with a tiny caps line above it, then fades away."
**Still-image state:** title visible at the top.

### T2 · CAPS KICKER — T low
**What it is:** one small tracked caps line in the title zone, for a section label or the speaker's topic.
**Use when:** a new section without a cut; ≤ 3 words. **Avoid when:** a pair block is on screen within the same 0.6 s.
**Text:** 1–3 words.
**Geometry / Graphics:** Montserrat SemiBold 0.040W, tracking +0.14em, centred, y 0.06H.
**Motion:** alpha 0 → 1 over 0.15 s; hold 1.0–1.5 s; hard cut.
**Flow prompt text:** "A small row of white wide-spaced capital letters reading {{LABEL}} appears near the top centre, then disappears."

### E1 · CLOSING HOLD — E low
**What it is:** the last pair block is held to the final frame with no exit.
**Use when:** every video's last block. **Avoid when:** the video continues after the speech with a long silent tail (then hard cut at speech end + 0.3 s).
**Motion:** none; it stays until the last frame.
**Flow prompt text:** "The last words stay on screen until the end of the clip."

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 on the topic noun | C1 per list item, C2 between, C3 once | K1 on the payoff + E1 |
| Single talking head | T1 + C1 | C1, C2 | K1 + E1 |
| B-roll only | C2 | C1 per shot (side L/R alternating) | E1 |
| Still image | T1 | C1 in settled state | none |

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
