# Google Flow prompt · Mixed Face Stack
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Mixed Face Stack" caption style to it.

The look in one sentence: Two to four line word-by-word stacks mixing heavy white caps, one bright accent caps word, a big italic serif and tiny connector words, hard-cut away at each phrase end.

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
| Text white | #FFFFFF | Heavy capitals, serif italic words, connector words |
| Accent | #FFD400 | Accent capitals. **Parameter:** the user may pick any bright, saturated colour. The shipped demo uses hot magenta #FF2E88. |
| Shadow | #000000 at 82 %  | 3 px offset, 6 px blur drop shadow plus a 1 px near-black edge (2.5 px under the shadow) on every word (design: the reference sat on a dark plate and used a faint shadow; the edge keeps text readable on bright B-roll) |

Brand-swap rule: replace only the Accent. White stays white. No other colours, no boxes, no gradients.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, plates, blur, tint or masks. |
| Caption stack | No container. Words sit directly on the footage with the shadow only. |
| Crop | None (cover-fit only if the source is not 9:16; anchor = the speaker's face). |

### 1.3 Layouts / grid

Measured on the reference: stacks sat in the middle-lower third, left-biased, 0.44–0.66H [845–1267], x 0.00–0.78W; the block covered the speaker's chin. This skill moves the block below the face.

| Layout | Spec |
|---|---|
| Stack block (default) | Left margin 0.07W [76]; right margin 0.07W; first baseline at 0.535H + 1 line pitch (≈ 0.60H) [1152]; max 4 lines |
| Line pitch | 0.066H (84 px at 720x1280 [126]) |
| Line indents (cycle) | line 1: 0; line 2: +0.13W; line 3: +0.04W; line 4: 0. Cycle repeats. Indent is clamped so the line ends inside the right margin. |
| Word gap | 14 px at 720 wide [21] between words on the same line |
| Baseline rule | Words on one line share one baseline, so a small connector sits at the bottom edge of the big word beside it |
| Lane shift | If the face bottom is lower than 0.46H, move the block down so the first baseline is ≥ face bottom + 0.05H; if the block would pass 0.86H, anchor it above the face instead (first baseline 0.12H). |
| Mirror | If the subject sits in the left half, set line 1 flush right and indent lines leftward. |

### 1.4 Typography

Four roles. The mix IS the style: every stack uses at least three of the four.

| Role | Look | Preferred free font | Fallbacks | Size (720 wide [1080]) |
|---|---|---|---|---|
| BIG | Heavy geometric sans, UPPERCASE, tight | Poppins ExtraBold | Montserrat ExtraBold, Archivo Black | 78 px [117] |
| ACC | Bold geometric sans, UPPERCASE, in the accent colour | Josefin Sans Bold | Jost Bold, Poppins SemiBold | 96 px [144] (set larger than BIG: Josefin caps run short) |
| SERIF | High-contrast display serif, italic, lowercase (as written), white | Playfair Display Italic Medium | Newsreader Italic, Bodoni Moda Italic | 96 px [144] |
| SM | Plain humanist or geometric sans, lowercase, regular, white | Poppins Medium | Inter Medium, Open Sans | 46 px [69] (about 0.5 × BIG) |

Role assignment rules (the reference mixes by word weight):

| Word type | Role |
|---|---|
| Connectors: and, but, so, to, for, of, your, our, it, a, the, in, on, at, with, short pronouns | SM (never two stacked lines of only SM) |
| Main noun or verb of the phrase | BIG |
| The single payoff or meaning word of the chunk (≤ 1 per chunk, ≥ 60 % of chunks) | ACC |
| A turn, a feeling or a soft word (not, instead, maybe, adjectives of mood) | SERIF |

Case: BIG and ACC are uppercased by the renderer; SERIF and SM keep the user's case. Punctuation stays attached to its word.

### 1.5 Motion language

| Item | Spec |
|---|---|
| Word entrance | 0.25 s (6 f at 24 fps): rise 18 px [27] from below, scale 0.92 → 1.0, opacity 0 → 1 (reaches full at 60 % of the move). Ease-out cubic. |
| Word timing | Each word starts at its spoken start time. Measured: words of a chunk landed 0.19–0.2 s apart. |
| Hold | Stack stays still until the chunk ends. No drift, no breathing. |
| Exit | Hard cut of the whole stack. |
| Never | Overshoot, bounce, spin, tilt, typing letter by letter, karaoke recolouring, glow, outline-only text, boxes, wipes, transitions on cuts, uppercase on SERIF or SM. |

### 1.6 What may happen to the user's footage

Nothing. Footage plays untouched, full frame, in sync with the audio. Allowed: caption overlays and their shadows. Forbidden: zoom, push, blur, grade, speed change, trim, reorder, regenerate, card layouts, background swaps, graphic transitions. Footage cuts are left as plain cuts; captions may change on a cut.

### 1.7 Safe zones

- The speaking face is never covered: keep the whole stack outside the face box (add 0.03H of air).
- Stay ≥ 0.07W from left and right edges and ≤ 0.86H at the bottom (platform UI).
- Burnt-in footage text: if the block collides with it, use lane shift or mirror.
- Bright shots: the shadow and edge (1.1) already keep white readable; raise the shadow opacity to 95 % before changing any colour.

---

## 7. MOMENT LIBRARY
Family codes: **C** caption stack, **K** keyword treatment, **T** title/opening text, **E** end. Energy: low / medium / high.

### C1 · Triple Stack — C medium (signature)
**What it is:** the core caption. Three words to six words, three lines, every line a different face, each word popping on its spoken time, whole stack hard-cut at the chunk end.
**Use when:** any speech or phrase of 3–6 words. Default chunk. **Avoid when:** a one-word beat (use C3) or a number (use K3).
**Text:** 3–6 consecutive user words, 14–30 characters in total, split at punctuation, never ending on an article, preposition or conjunction.
**Geometry / Graphics:** 1.3 stack block; lines 2–3 words max, ≥ 3 roles used (e.g. SM + BIG, then SERIF, then ACC).
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | each word | y, scale, opacity | +18 px, 0.92, 0 → 0, 1.0, 1 over 0.25 s | ease-out cubic |
| chunk end | whole stack | visibility | 1 → 0 | hard cut (empty ≥ 0.05 s before the next stack) |

**Footage behaviour:** untouched. **Captions during it:** this is the caption. **Exit:** hard cut.
**Build notes:** pre-render each word as a 2x sprite with shadow, downscale with LANCZOS; lay out the complete chunk first so no word moves after landing; fit-shrink a line by 5 % steps until it fits inside the margins.
**Flow prompt text:** "A stack of three short lines of {{WORDS}} appears word by word on the lower middle of the frame, mixing heavy white capitals, one bright {{COLOUR}} capital word, an elegant italic serif word and a tiny plain word; the stack disappears instantly when the phrase ends."
**Still-image state:** full stack settled at the block position.

### C2 · Pair Stack — C medium
**What it is:** two-line version for short phrases (2–3 words): a BIG or SERIF line and an ACC or SERIF line, second line indented.
**Use when:** 2–3 word phrases, quick beats, list items. **Avoid when:** 5+ words.
**Text:** 2–3 user words. **Geometry:** lines 1–2 of 1.3. **Motion:** as C1.
**Footage / captions / exit:** as C1.
**Flow prompt text:** "Two lines of {{WORDS}} pop in one word at a time: the first in heavy white capitals, the second in a bright {{COLOUR}} colour, shifted to the right; both vanish together."
**Still-image state:** two lines settled.

### C3 · Solo Slam — C high
**What it is:** one word, centred on x = 0.50W, 1.35× the BIG size (or SERIF at 1.3×), single line, same entrance.
**Use when:** a one-word hook or a hard stop ("never", a name, a number word). **Avoid when:** more than 2× per video.
**Text:** one user word. **Geometry:** baseline at 0.62H. **Motion:** entrance 0.2 s, hold, hard cut.
**Flow prompt text:** "One large word {{WORD}} pops in at the lower middle of the frame in heavy white capitals, then vanishes."
**Still-image state:** the word centred at the lower middle.

### C4 · Flip Side Stack — C medium
**What it is:** C1 mirrored: line 1 flush right at 0.93W, later lines indented leftward. Used when the subject sits on the left.
**Use when:** the subject or a face is in the left half or burnt-in text sits on the left. **Avoid when:** it would hit the right-hand subject.
**Text:** as C1. **Motion:** as C1, rise stays vertical.
**Flow prompt text:** "The same word-by-word stack of {{WORDS}} is aligned to the right side of the frame."
**Still-image state:** stack on the right.

### K1 · Accent Capital — K medium (signature)
**What it is:** the chunk's meaning word in the accent colour, uppercase Josefin-style bold, one per chunk, set 1.23× BIG for visual parity.
**Use when:** payoff words, nouns that carry the topic, verbs of action. **Avoid when:** a connector; > 3 accent words in a row of chunks without a white-only chunk.
**Text:** one word per chunk. **Motion:** as C1 word entrance. **Exit:** with its stack.
**Flow prompt text:** "The key word {{WORD}} is written in bright {{COLOUR}} capitals while the other words stay white."
**Still-image state:** accent word on its own line.

### K2 · Serif Turn — K medium (signature)
**What it is:** a soft or contrasting word set in white italic serif, lowercase, larger than the sans words; it gives each stack its elegant counterpoint.
**Use when:** contrast words ("but", "not", "instead"), feelings, verbs of motion, the word after a pause. **Avoid when:** a number or an all-caps abbreviation.
**Text:** one word per chunk (two in a 4-line stack). **Motion:** as C1.
**Flow prompt text:** "The word {{WORD}} appears in a large, elegant white italic serif with lowercase letters."
**Still-image state:** serif word on its own line.

### K3 · Connector Whisper — K low (signature)
**What it is:** small plain lowercase words sitting on the baseline of the line's big word, about half its height, white.
**Use when:** every connector (1.4). **Avoid when:** it would be the only word on a line.
**Text:** the connector words. **Motion:** as C1 word entrance, shifted to arrive just before its neighbour (its own time).
**Flow prompt text:** "Tiny plain white words such as {{WORDS}} sit next to the big words, at their bottom edge."
**Still-image state:** a small word left of a big one.

### K4 · Number Stack — K high
**What it is:** a numeral or amount as BIG (or ACC when it is the payoff) with its unit or noun as SM on the same baseline.
**Use when:** numbers, prices, durations, percentages. **Avoid when:** the user wrote the number as a word (keep their writing).
**Text:** numeral + unit exactly as written. **Geometry:** BIG at 1.25×, SM at 1×, baseline shared.
**Flow prompt text:** "The figure {{NUMBER}} appears large in heavy capitals with the small word {{UNIT}} beside it."
**Still-image state:** figure + unit on one line.

### T1 · Opening Stack — T high (signature)
**What it is:** the first chunk of the video, starting with the first spoken word. Uses C1 or C2 with line 1 as BIG and line 2 as ACC.
**Use when:** always on the opening line. **Avoid when:** none (short videos: shorten the hold, never drop it).
**Text:** the first 2–4 user words. **Motion:** as C1, but the first word enters at the spoken time exactly.
**Flow prompt text:** "As the speaker begins, the opening words {{WORDS}} pop in stacked, the first in heavy white capitals and the next in a bright {{COLOUR}} colour."
**Still-image state:** opening stack.

### T2 · Topic Callout — T medium
**What it is:** a section or topic word held as a solo ACC line with an SM word above it, for list items or new topics.
**Use when:** a new step, a section change without a cut. **Avoid when:** within 0.5 s of a footage cut.
**Text:** the user's topic words. **Motion:** as C1. **Flow prompt text:** "A small word {{WORD}} sits above one bright {{COLOUR}} capital word {{TOPIC}} for the length of the section."
**Still-image state:** SM + ACC pair.

### E1 · Payoff Stack — E high (signature)
**What it is:** the last chunk, with the last word as ACC (or the strongest word), held until at most 0.1 s after the last spoken word, then cut away. Measured: the final stack was a short two-word SM + BIG pair that cut out when speech ended.
**Use when:** the last line, a call to action. **Avoid when:** none.
**Text:** last 2–4 user words. **Motion:** as C1. **Exit:** hard cut at speech end + 0.1 s (clamped to video end).
**Flow prompt text:** "The final words {{WORDS}} pop in stacked with the last word in bright {{COLOUR}} capitals and vanish when the speaker finishes."
**Still-image state:** closing stack.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 (BIG + ACC) | C1/C2 with K1 + K2 per chunk; C4 when the B-roll subject is on the left; chunk changes on the cuts | E1 |
| Single talking head | T1 | C1, C2 alternating, K3 on every connector, one C3 on a turn word | E1 |
| B-roll only (voice-over) | T1 on the first phrase | C2, C1 with lane shift per shot, K4 for numbers | E1 |
| Still image + text | C1 settled | none | none |

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
