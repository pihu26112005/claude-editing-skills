# Google Flow prompt · Arc Crown Caps
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Arc Crown Caps" caption style to it.

The look in one sentence: The key word of each phrase curves over the head as a chunky accent arch with a small 3D edge while the small words pile up as tilted white caps on the chest.

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
| Accent | measured default #F9BC34 (amber, median of the keyword face; 10th–90th percentile 208,153,37 – 255,195,68). Demo uses hot pink #FF2E93 | Arch keyword face |
| Accent depth | accent darkened to about 50 % (demo #800A46) | 3D extrusion under every arch letter |
| Text white | #FFFFFF | Stack words, big solo word |
| Outline | #141418 at 92 % | 2 px stroke on white words |
| Shadow | #000000 at 45–50 % | Soft drop shadow under every text role |

Brand-swap rule: the accent is a parameter. Any saturated colour that reads on the footage is allowed; keep white, outline and shadow fixed. Exactly one accent per video.

### 1.2 Containers / shapes

No containers. The footage is always full frame, 100 % of W and H: no cards, boxes, bars, label plates, masks, borders, blur plates or colour overlays. Text is the only layer. Crop anchor only if the source is not 9:16 (cover-fit about the speaker's face).

### 1.3 Layouts / grid

| Layout | Region (fractions) | Use |
|---|---|---|
| Crown arch (default) | apex baseline y = 0.115H [221], centred x = 0.50W, widest span 0.74W [800] | C1, C4 |
| Low arch | apex baseline y = 0.46H [883]; same arch | K1: when a face sits in the top band |
| Chest lane | x0 = 0.105W [113], y0 = 0.50H [960], max line width 0.54W [583] | C2 on a speaker (face box ends at 0.40H) |
| Lower lane | x0 = 0.105W, y0 = 0.70H [1344] | C2 on B-roll / hands / screens |
| Upper-left lane | x0 = 0.105W, y0 = 0.14H [269], max width 0.36W [389] | C2 when the face sits right of centre |
| Solo centre | centre x = 0.50W, y = 0.52H [998] | C3 |

Safe frame for ALL text, including entrance scale: x 0.05W–0.95W, y 0.02H–0.98H. Face box (speaking face) is never touched by any glyph, shadow or extrusion.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Arch keyword | uppercase, ultra-heavy geometric sans, letters placed on a circle and each rotated to the tangent, small 3D extrusion downward, soft shadow | Poppins Black | Montserrat Black, Archivo Black | cap height ≈ 0.045–0.06H [86–115]; fit so chord width ≤ 0.74W; size 118 px at 720 W, shrinks for long words |
| Arch geometry | measured on an 8-letter word: chord 0.78W, sag ≈ 0.045H → circle radius ≈ 0.95W [1026]; tracking +0.015 em | — | — | — |
| Stack word | uppercase, extra-bold sans, tracking +0.02 em, outline + shadow | Poppins ExtraBold | Montserrat ExtraBold | 54 px at 720 W (cap ≈ 0.026H; reference ≈ 0.04H on a 640 px tall frame, so the demo is a touch smaller) |
| Solo word | uppercase, black weight | Poppins Black | Montserrat Black | 150 px at 720 W (≈ 2.8x stack size; reference "EK" ≈ 2.5x) |

Case: UPPERCASE for all text; the user's words and punctuation (commas, full stops) stay; case is a display transform only.

### 1.5 Motion language

- Keyword enter: blurred and slightly large, resolving to sharp while fading in; 0.26 s (6 frames), ease-out cubic; scale 1.12 → 1, blur radius 12 px → 0, alpha 0 → 1. Reference shows a motion-blur streak on arrival.
- Keyword exit: 0.14 s, alpha 1 → 0 with blur 0 → 6 px. Always finishes before the next keyword starts (the reference crossfades two keywords; this skill keeps them apart so captions never overlap).
- Stack word enter: 0.20 s, ease-out cubic, scale 1.1 → 1, blur 8 px → 0, alpha 0 → 1. Words appear one by one at their spoken time and stay.
- Stack exit: the whole group fades together 0.12 s, alpha 1 → 0, 0.5 s after its last word starts, and never later than 0.15 s before the next group or solo word starts.
- Holds: keyword stays 0.65–1.45 s (long enough to read, then clears; a keyword never outlives the shot it was placed for if the next shot has a face in the arch zone).
- Never: bounce, overshoot, letter-by-letter typing, slides, shake, flashes, colour changes, boxes.

### 1.6 What may happen to the user's footage

Nothing. Full frame, untouched, live and in sync with the audio. Forbidden: any zoom, crop, blur, grade, filter, mask, cut-out, background change, split, card, transition, speed change, trimming or reordering. Only text, outline and shadow layers are added.

### 1.7 Safe zones

- Face box of the speaking person (demo talking head: x 0.34–0.66W, y 0.15–0.40H; checkout shot: x 0.50–0.75W, y 0.10–0.37H) stays clear of every glyph, extrusion and shadow in every frame. Check by mask, not by bounding box: an arch's rectangular bbox is larger than its ink.
- Captions never overlap each other: keyword, stack and solo word never share a pixel region at the same time (same-group stack words are laid out on a grid).
- Keep arch ink at least 8 px above the face box top; if the head is high (face box top < 0.14H) use K1.
- Never start a new keyword within 3 frames after a cut when avoidable; small stack words may.

---

## 7. MOMENT LIBRARY
Families: **C** caption · **K** keyword placement variant · **T** title/headline · **E** end. Energy: low / mid / high. Signature moments (mandatory in every output): C1, C2, C3 (when the text has a natural solo word or phrase end) and C4.

### C1 · ARC CROWN KEYWORD — C high
**What it is:** the key word of each phrase as a bold accent arch above the head, extruded, resolving from a blur.
**Use when:** every phrase has one stand-out word: topic noun, verb of an instruction, number, time phrase, payoff word.
**Avoid when:** the word is an article or preposition; the same word would repeat within 1.5 s.
**Text:** one user word (with its own punctuation) per keyword, max 12 characters before shrinking; max 1 per phrase, 0.9–1.4 keywords per second at most (demo: 8 in 10 s).
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start (word's spoken time) → +0.26 s (6 f) | keyword | scale / blur / alpha | 1.12 / 12 px / 0 → 1 / 0 / 1 | ease-out cubic |
| hold | keyword | all | static | — |
| end − 0.14 s | keyword | alpha / blur | 1 → 0 / 0 → 6 px | linear |
**Footage:** untouched. **Captions during it:** stack words below (C2).
**Exit:** fade as above, ends at least 0.02 s before the next keyword starts.
**Flow prompt text:** "As the speaker says {{WORD}}, that word appears in big bold {{ACCENT COLOUR}} capital letters curved in an arch just above the head, with a small solid 3D edge and a soft shadow; it sharpens in from a blur and fades out smoothly after about a second."
**Still-image state:** arch word settled above the head, sharp.

### C2 · TILTED WHITE STACK — C mid
**What it is:** the small connecting words appear one by one as white heavy caps, set on a slight tilt, filling a tight block that grows to 2–3 lines.
**Use when:** every phrase; they carry the words around the keyword.
**Text:** the user's other words, in spoken order, each at its own spoken time; line max width per lane (1.3); tilt -6° … +6°, alternating between groups.
**Geometry / Graphics:** word spacing 0.32 em, line pitch 1.18 em, left-aligned from the lane origin, whole block rotated about the origin by the group tilt (positive = counter-clockwise). Outline 2 px, shadow as 1.1.
**Motion:** each word 0.20 s pop (1.5); group exits together (1.5).
**Footage:** untouched. **Captions during it:** keyword arch above (C1) never touches the stack: arch ends ≥ 0.2H above the chest lane.
**Exit:** group fade 0.12 s.
**Build notes:** lay out words unrotated, rotate centres about the lane origin by the tilt, rotate each word sprite by the same tilt (expand), paste at the rotated centre. Pick the lane by the shot the group starts in and keep it for the whole group (do not move a group across a cut).
**Flow prompt text:** "The words around it appear one by one in small white bold capital letters with a thin dark outline, stacked in a tilted block on the lower left of the frame, then fade away together."
**Still-image state:** a 2–3 line white stack on the chest lane at a small tilt.

### C3 · BIG SOLO WORD — C high
**What it is:** one word (or short phrase end) as a huge white word in the middle of the frame, tilted about 6°, with outline and shadow.
**Use when:** a sentence ends on a punchline word ("more.", "now.", a number) and the keyword slot is already taken or an interruption beat is wanted; max 1–2 per video.
**Text:** one user word with punctuation, ≤ 8 characters.
**Geometry:** centre (0.50W, 0.52H) on a speaker (below the face box); font 150 px at 720 W; tilt +6° (±6°); width ≤ 0.70W.
**Motion:** enter 0.26 s: scale 1.3 → 1, blur 12 → 0, alpha 0 → 1, ease-out cubic; hold 0.45 s; exit 0.14 s fade.
**Footage:** untouched; the word covers the chest, never the face.
**Build notes:** same sprite pipeline as C2 with Poppins Black, outline 3 px.
**Flow prompt text:** "On the word {{WORD}} a very large white capital word pops in the middle of the frame, slightly tilted, then fades; it never covers the face."
**Still-image state:** the word large and tilted below the face.

### C4 · KEYWORD HANDOVER — C mid (signature, timing rule)
**What it is:** the rule that only one arch is visible at a time: the old keyword blurs out in 0.14 s and the next one blurs in at its spoken time, in the same place.
**Use when:** always, between C1s.
**Motion:** old exit ends at the new start − 0.02 s; new enter starts exactly at the spoken time.
**Build notes:** compute each keyword's end = min(start + hold, next start − 0.02); then t1 = end − 0.14 s.
**Flow prompt text:** "Only one arched word is on screen at a time; each new word replaces the previous one in the same spot."

### K1 · LOW ARCH — K mid
**What it is:** the same arch moved below the face when the face sits in the top band (shot where the speaker is high or at the side).
**Use when:** a shot's face box top < 0.14H or the face box intersects the crown arch zone.
**Geometry:** apex baseline y = 0.46H; arch ink starts below the face box bottom (+ 0.015H). Keep C2 words in the upper-left or lower lane so they never touch it.
**Motion:** as C1. **Exit:** as C1; a keyword placed for this shot ends before the next cut if the next shot has no such face.
**Flow prompt text:** "The curved word appears below the speaker's face, across the chest."

### K2 · FLAT KEYWORD ON STACK — K mid
**What it is:** a keyword set straight (no arc) in the accent, directly above a white stack, used when the arch zone is occupied (reference: a flat accent word over a two-line white stack on the chest).
**Geometry:** flat accent word, same font and size as C1, left of centre; the white stack sits right under it with a 0.012H gap; no overlap.
**Flow prompt text:** "The word appears straight in big {{ACCENT COLOUR}} capitals with the smaller white words directly under it."

### T1 · ARCH OPENER — T high
**What it is:** the first spoken keyword is allowed 15 % larger and held 0.3 s longer to introduce the style.
**Use when:** the first phrase of a video. **Avoid when:** the video opens on a cut within 0.3 s.
**Geometry:** C1 with chord ≤ 0.78W and hold +0.3 s. **Flow prompt text:** "The first key word arrives slightly larger and stays a bit longer."

### C5 · BRIGHT-FOOTAGE CONTRAST MODE — C low
**What it is:** on pale or busy shots, white text keeps the dark outline and the shadow strengthens; the arch keeps its extrusion. On dark footage the outline may be dropped (reference had none).
**Rule:** judge by the median luminance of the lane region (> 0.55 → bright mode).
**Flow prompt text:** "On bright shots the white words get a thin dark outline so they stay readable."

### C6 · SIDE LANE — C low
**What it is:** the stack in the upper-left lane (1.3) when the face is right of centre and the chest is occupied.
**Use when:** face box left edge ≥ 0.45W. **Geometry:** lane x0 0.105W, y0 0.14H, max width 0.36W.
**Flow prompt text:** "The small white words stack in the upper left, away from the face."

### E1 · ARCHED WHITE SIGN-OFF — E mid
**What it is:** on the last two words, a white arched phrase (the reference ends with a two-word white arc, tilted, blurring out) instead of an accent keyword; exits last 0.3 s with a blur-out.
**Use when:** a quiet sign-off ("that's it") rather than a punchline.
**Geometry:** C1 pipeline with white face and no extrusion; apex 0.115H.
**Flow prompt text:** "The final two words curve over the head in white and blur away."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + C2 | C1/C4 per phrase, C3 on a punchline, K1 on shots with a high face | C1 on the payoff word |
| Single talking head | T1 + C2 | C1/C4 alternate, C3 once | E1 or C1 |
| B-roll only | C1 | C1/C4, C2 on the lower lane | C1 |
| Still image | C1 settled + C2 stack | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Demo values (shared 10 s clip, tuned) — word start times (s)
Stack: Saving.10, isn't.55, about.80 (clear ≈1.30) · MORE. solo 1.45–2.04 · Pay 2.10, first, 2.60 · automate 3.20, your 3.55 · and 4.95, only 5.45, what's 5.70 · Do 6.90, it 7.10, for 7.25, one 7.45 · and 8.45, watch 8.65, what 8.95.
Arch holds (s): money.70, earning 1.20, yourself.90, investments, 1.15 (clears before the 4.92 cut), spend.80 (low arch), left..65 (low arch), year 1.45, happens. 1.0 (runs to the end).
Lane per group: shot 1 chest, shots 2–3 lower, shot 4 upper-left, shot 5 y 0.58H, shot 6 y 0.52H. Tilts: -6, +4, -4, +5, -5, +4.

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
