# Google Flow prompt · Neon Echo
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Neon Echo" caption style to it.

The look in one sentence: Small bold white captions with glowing lime italic keywords, a giant scan-lined neon slab for the payoff word, and outline echo rows behind the speaker.

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
| Caption white | #FFFFFF | Plain caption words, stack outlines |
| Neon lime | #C6FA3B | Keyword fill, slab fill |
| Neon glow | #6EFF28 | Blurred halo under lime text |
| Title violet | #685CEB | Title outline, haze fill at 34 % of #504CAA |
| Split red / cyan | #FF465A / #46E6FF | Colour-split ghosts of the echo stack, 55 % |
| Shadow | #080C12 | Soft shadow and thin stroke under all text |

Brand-swap rule: a user brand colour replaces Neon lime and Neon glow (use a lighter tint as fill, the saturated colour as glow). White never changes.

### 1.2 Containers / shapes
No containers. Footage is always full frame, 100 % of W and H. No boxes, cards, borders, plates, dimming or colour overlays. Cover-fit only if the source is not 9:16.

### 1.3 Layouts / grid

| Layout | Region (fractions) | Use |
|---|---|---|
| Chest lane | first line centre y = 0.64H [1229] (ref 0.61–0.63H), x centred 0.50W | Default caption lane |
| Neck lane | first line centre y = 0.50H [960] (ref 0.47H) | Lane hop, and the caption lane when a slab is on screen |
| Slab lane | centre y = 0.715H [1373] (ref 0.69H) | K2 slab |
| Title lane | centre y = 0.073H [140]; cap height ≤ 0.09H | T1 |
| Stack field | rows from y = 0.012H, pitch 0.115H [221], 9 rows, 0.90W wide | T2 |
| Line pitch | 1.30 × caption font size | Lines inside a chunk |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption word | Bold grotesque, sentence case as written, tight | Inter Bold (wght 760) | Roboto Bold, Manrope Bold | 0.092W [99]; word gap 0.26 em |
| Keyword | Bold italic, lime, glow | Inter Tight ExtraBold Italic | Inter Bold Italic, Roboto Bold Italic | 1.18 × caption size |
| Slab (K2) | Heavy italic, UPPERCASE, lime, scan-line slits, glow | Barlow Black Italic | Archivo Black, Anton | em 0.27W, fit so width ≤ 0.74W |
| Title and stack | Extra-bold italic, UPPERCASE, outline only | Barlow ExtraBold Italic | Barlow Condensed Bold Italic, Roboto Condensed | T1 width 0.64W; T2 row cap height 0.098H, stretched to 0.90W |

Rules: captions keep the user's case and punctuation. Slab, title and stack words are uppercase copies of user words. No boxes behind text. Shadow on all text: blurred 7 px at 75 % plus a 1 px dark stroke at 55 %.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Caption word entrance | ease-out alpha ramp, no movement | 0.125 s [4 f @30] (ref 2 f @15) |
| Chunk exit / swap | hard cut | 1 f |
| Slab entrance | ease-out alpha + scale 1.07 → 1.00 | 0.15 s |
| Title pass | enter from the left ease-out, slow drift, exit to the right ease-in | 0.30 s in, 0.38 s out |
| Stack entrance | rows alpha ramp ease-out, 0.05 s stagger top to bottom | 0.125 s per row |

Never: letter-by-letter typing, bounce, spring, slides on captions, boxes behind captions, shake, flashes, caption rotation.

### 1.6 What may happen to the user's footage
Allowed: full-frame display untouched; text overlays; for T2 only, the stack drawn behind a person cut-out (the person is the live footage, the stack is only added behind). Forbidden: replacing, regenerating, retiming, trimming, reordering; blur, grading, background swaps, cards, splits, B-roll frames, graphic transitions. The primary footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by captions, slab or title. Lane y must be ≥ 0.03H under the chin; if the face bottom is below 0.46H use only the chest lane or lower. |
| Title lane | Needs the face top ≥ 0.12H; else shrink T1 or skip it. |
| Stack | Only on a shot with one clear person (mask from a person segmenter); the face is never covered because the person stays in front. Skip on shots with no person. |
| Edges | Glyphs ≥ 0.04W from left and right (chunks ≤ 0.88W wide). |
| Bright footage | Keep the shadow and stroke on; keep text off pure-white regions if a lane alternative exists. |

---

## 7. MOMENT LIBRARY
Family codes: **C** caption · **K** keyword · **T** title · **X** cut · **E** end.
Energy:  calm ·  medium ·  high.

### MOMENT C1 · POP CAPTION
**What it is:** a short chunk pops in word by word in white bold, laid out in full before the first word so nothing moves; the chunk is replaced by the next in one frame.
**Use when:** always. **Avoid when:** never.
**Text:** user's exact words. 2–5 words, 0.7–1.6 s, split at punctuation, never end on an article, preposition or conjunction, never straddle a cut. Lines break where the word type changes (white to keyword or back); white words stay together on one line.
**Geometry / Graphics:** Chest lane, centred on x = 0.50W, first line y per the lane, line pitch 1.30 em.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | new word | alpha | 0 → 1 | ease-out, 0.125 s |
| word start | earlier words | — | unchanged | — |
| chunk end | chunk | alpha | 1 → 0 | hard cut |

Ref words: One 0.80, bright 1.13, choice 1.60, can 2.07 (chunk gaps 0.05 s). Chunk end = next chunk start, or min(last word end + 0.4, next cut − 0.03).
**Footage:** untouched. **Exit:** hard cut.
**Build notes:** pre-render every word at 2× with shadow; one layout per chunk; alpha per word.
**Flow prompt text:** "Captions appear near the middle of the frame, word by word, in bold white lettering with a soft shadow. Each word fades in softly in place and the phrase is replaced at once by the next. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### MOMENT K1 · NEON KEYWORD
**What it is:** the meaning-carrying word of a chunk is lime bold italic with a green glow, on its own line.
**Use when:** a noun or verb carries the point. **Avoid when:** articles, prepositions; more than 1 per chunk or 4 per 5 s.
**Text:** one word per chunk as written, 1.18 × size.
**Geometry / Graphics:** inside the chunk per C1 line rules (keyword alone on its line; trailing white words go on the line below).
**Motion:** same entrance as C1.
**Footage:** untouched. **Exit:** with the chunk.
**Build notes:** glow = blurred mask (9 px) ×1.6 at 85 % in #6EFF28, under a lime fill.
**Flow prompt text:** "The important word, {{KEYWORD}}, is lime green, slanted and glowing, on its own line."
**Still-image state:** settled.

### MOMENT K2 · NEON SLAB
**What it is:** one payoff word blows up as a giant uppercase lime slab with horizontal scan-line slits and a green glow, while its chunk moves to the neck lane and the small lime keyword stays above it.
**Use when:** a turn, number, action or payoff word (max 2 per video, ≥ 3 s apart). **Avoid when:** word > 8 letters, or over a face.
**Text:** one user word, uppercase, without punctuation.
**Geometry / Graphics:** slab lane centre y = 0.715H, width ≤ 0.74W, em 0.27W (4 letters ≈ 0.55W); scan slits every 3 px at 35 %; its chunk uses the neck lane.
**Motion:** alpha 0 → 1 and scale 1.07 → 1.00 over 0.15 s ease-out at the keyword start; hold until the chunk ends, then hard cut (ref held 0.55 s).
**Footage:** untouched. **Exit:** hard cut with the chunk.
**Build notes:** fill alpha multiplied by (1 − 0.35) on odd 3 px bands.
**Flow prompt text:** "The word {{WORD}} appears huge in glowing lime green slanted capitals with thin horizontal slits cut through the letters, below the small caption, then disappears with it."
**Still-image state:** settled.

### MOMENT T1 · OUTLINE TITLE PASS
**What it is:** the topic word in uppercase outline letters (violet line, faint violet haze, lime ghost line) slides across the top in the same direction, holds and drifts, then leaves.
**Use when:** opening line or topic word, speaker below. **Avoid when:** face top < 0.12H, or a cut within 0.3 s.
**Text:** one user word, uppercase, width 0.64W.
**Geometry / Graphics:** title lane centre y = 0.073H; violet outline 2 px, haze 34 %, lime ghost outline offset (+4,+3) at 70 %.
**Motion:**

| t | Property | From → To | Ease |
|---|---|---|---|
| start (+0–0.30 s) | x offset | −0.95W → 0 | ease-out |
| hold | x drift | +0.03W per s | linear |
| end − 0.38 s | x offset | → +0.95W | ease-in |

Ref: in 0.67–0.83 s, out 1.5–1.9 s. Demo: 0.40–1.62 s. Finish ≥ 0.2 s before a cut.
**Footage:** untouched. **Exit:** slide right.
**Flow prompt text:** "Near the top, the word {{TITLE}} in large outlined capitals slides in from the left, drifts slowly and slides out to the right, never covering the face."
**Still-image state:** settled.

### MOMENT T2 · ECHO STACK
**What it is:** the topic word in uppercase outline repeated in 9 rows filling the frame behind the speaker, white lines with red and cyan splits, lower rows lime-tinted, rows appearing top to bottom.
**Use when:** a payoff or closing section on a shot with one clear person. **Avoid when:** no person, or the person fills the whole frame.
**Text:** one user word, uppercase.
**Geometry / Graphics:** Stack field; row alpha 1.0 at the top to 0.45 at the bottom; last 3 rows tinted #BEFF78; the stack is composited behind the person mask (EMA 0.6/0.4, 1.5 px blur).
**Motion:** each row alpha 0 → 1 over 0.125 s ease-out, row r starts at start + 0.05 r; then holds to the end of the video (ref: until the end).
**Footage:** live person in front; nothing else changed. **Exit:** none (video end).
**Build notes:** render one outline row, stretch to 0.90W, tile; mask from a segmenter in VIDEO mode.
**Flow prompt text:** "Behind the speaker, the word {{WORD}} repeats in rows of white outlined capitals with faint red and blue edges, filling the frame from top to bottom. The speaker stays in front, unchanged."
**Still-image state:** settled.

### MOMENT C2 · LANE HOP
**What it is:** a chunk sits in the neck lane instead of the chest lane to vary the rhythm or clear a hands area.
**Use when:** two chunks in a row would repeat the lane, or K2 is on. **Avoid when:** the neck lane is under the face (face bottom > 0.46H).
**Text:** as C1; lane. Everything else as C1.
**Flow prompt text:** "This caption sits a little higher, just under the speaker's chin."

### MOMENT C3 · BRIGHT-FOOTAGE GUARD
**What it is:** on bright or pale footage the shadow and 1 px stroke are kept at full strength and the lane moves to the darker half.
**Use when:** lane luminance > 0.6. **Flow prompt text:** "On bright shots the captions keep a soft dark shadow so they stay readable."

### MOMENT X1 · CUT RESET
**What it is:** on each footage cut the current chunk ends at cut − 0.03 s and the next chunk starts on the cut or its first spoken word, in the lane suited to the new shot. No effect on the cut.
**Use when:** every cut. **Flow prompt text:** "At each cut the picture simply cuts; the caption in progress ends just before and a new one starts at the cut."

### MOMENT E1 · END HOLD
**What it is:** the last chunk holds to min(last word end + 0.4 s, end − 0.25 s), then the picture finishes clean (T2 stays).
**Flow prompt text:** "The last caption stays until just before the end, then disappears."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1/K1 | K2 on one payoff word, C2 lane hops, X1 on cuts | T2 on the final speaker shot + E1 |
| Single talking head | T1 + C1/K1 | K2 on the turn word, C2 | T2 + E1 |
| B-roll only | C1/K1 (T1 if a title word exists) | K2 on a number or action, X1 | E1 (no T2) |
| Still image + text | T1 settled | one chunk with K1 | — |

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
