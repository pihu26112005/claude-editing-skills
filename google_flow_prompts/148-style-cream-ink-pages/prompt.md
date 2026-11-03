# Google Flow prompt · Cream Ink Pages
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Cream Ink Pages" motion style to it.

The look in one sentence: Bold white word-by-word captions with an amber label keyword cutting to cream paper pages that hold the live footage in a rounded card beside plum ink captions and a rolling step counter, with a scalloped badge and drawn stickers.

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
| Paper cream | #EFE9E1 | Page background |
| Plum ink | #3A1456 | Page text, numerals, badge outline |
| Amber accent | #FFB62E | Label box, gradient start, underline, stickers (parameter: the user's brand colour) |
| Label text | #2B0F45 | Text inside the amber box |
| Caption white | #FFFFFF | Words on footage, with a soft black shadow (55 %, blur 4.5, offset 3) |
| Cream-white gradient end | #FFF4D6 | End of the gradient first word on footage |
| Bar track | #E6DCD2 | Empty progress track |

Brand-swap rule: replace Amber with the user's colour (keep it bright enough for dark label text); replace Plum with a very dark shade of the same colour family. Never change white or cream. The measured reference used a red/teal/blue set; the default here is the amber/plum set, and the accent is a parameter.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage on footage moments | Full frame, untouched. |
| Footage card (page) | 0.375W × 0.375H [270×480] (9:16), radius 28, x 40, y 590 (0.055W, 0.46H), soft plum drop shadow (30 %, blur 14, offset 10). Live footage, cover-fit; anchor = face or subject. |
| Page | Full frame cream, no border. |
| Label box | Amber, radius 0.16 × text size, padding 0.22 × size sides, 0.10 × size top/bottom; text dark plum. |
| Progress bar | x 72–648 (0.10–0.90W), y 408, track height 24, fully rounded, fill gradient amber→plum, white knob radius 18 with plum 6 px ring. |
| Scallop badge | 18 scallops, mean radius 250, amplitude 13, centre (0.5W, 0.55H), outline 6 px plum, fill cream 96 %. |
| Stickers | Hand-drawn flat icons (coin with star, price tag, sparkle), 104–118 px, soft shadow. No emoji. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Footage caption zone | 0.083, 0.547, 0.92, 0.72 | C1, K1 left-aligned stacks; anchor lower if the speaker's hands or face are low |
| Step page | numeral centre (0.5W, 0.195H); bar y 0.32H; card x 0.055–0.43W, y 0.46–0.84H; chip at x 0.49W, y 0.48H; caption column x 0.49–0.95W from y 0.58H | P1 |
| HUD | 0.055, 0.04, 0.46, 0.125 (top-left) | H1 |
| Sticker lane | right of the caption stack, y 0.52–0.66H | S1 |
| Badge | 0.15–0.85W, 0.35–0.74H | B1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Footage helper word | white, bold, mixed case as written | Montserrat Bold (700) | Poppins SemiBold, Inter Bold | 42 px (0.058W) |
| Footage key word | white, extra bold, large | Montserrat ExtraBold (800) | Poppins ExtraBold, Inter ExtraBold | up to 96 px (0.133W), auto-shrinks so the line fits 0.83W |
| First word of a chunk | same face, horizontal gradient amber→cream-white (flag g) | Montserrat | — | helper or key size |
| Label word | key size, dark plum on amber box | Montserrat ExtraBold | — | ≤ 96 px |
| Page helper / key | plum ink; key auto-fits the 0.46W column (max 60 px) | Montserrat Bold / ExtraBold | — | 36 / 60 px |
| Step numeral | plum, black weight | Montserrat Black (900) | Poppins Black | 190 px (0.26W) |
| Bar ticks | plum, bold | Montserrat Bold | — | 30 px |
| Badge text | plum, helper 50 px, key up to 118 px, centred | Montserrat | — | — |

Letter-spacing 0, word gap 0.25 × size, line pitch from baselines (0.22 × previous size + 0.74 × current size + 8 px).

### 1.5 Motion language

- Word reveal: fade 0→1 over 0.22 s with a blur of 7 px → 0 and a rise of 14 px, ease-out cubic; one word per spoken beat; the whole chunk's layout is fixed before its first word.
- Chunks hard-cut; never two chunks visible together; each ends at least 0.02 s before the next starts.
- Page in: hard cut on the footage cut, white flash 90 % → 0 over 8 f, content fade 0→1 over 6 f. Page out: dissolve over 4 f.
- Numerals roll: old slides up 46 px and fades while the new slides in from below, 0.22 s, ease in-out.
- Bar fill eases out; stickers pop 0 → 1.15 → 1 over 0.33 s with a slight wobble and a gentle bob.
- Never: footage blur, tilt, glitch, shake, bounce on text, letter-by-letter typing, colour grading of the footage.

### 1.6 What may happen to the user's footage

Full-frame display, untouched, with overlays. Live footage in the page card (scaled, cover-fit, rounded corners). Pages may cover the footage fully except the card, for at most 3 s at a time, and only on shots with no speaking face or while the card shows the speaker. No blur, grade, retime, reorder or replacement.

### 1.7 Safe zones

Face box never covered while speaking. Captions sit below the face box (y ≥ 0.54H on a speaker). All text and graphics keep ≥ 0.05W from the left and right edges. Captions never overlap each other or a sticker. HUD stays left of a face that sits at x ≥ 0.5W.

---

## 7. MOMENT LIBRARY
Families: C caption · K keyword · S sticker · P page · N counter · B badge · X transition · E end. Energy: low / mid / high.

### C1 · FOCUS-IN CAPTION — C mid (signature)
**What it is:** word-by-word caption stack on the footage: a small helper word above a large key word, left-aligned, the first word with an amber gradient.
**Use when:** any speech on full-frame footage. **Avoid when:** the lane is a bright wall and the shot has no face (use a page instead).
**Text:** the user's words, 2–3 per chunk, ≤ 0.83W per line.
**Geometry / Graphics:** zone 1.3, x 60, first baseline y ≈ 770 (top 700), fonts 1.4.
**Motion:** | t | Element | Property | From → To | Ease | each word at its spoken start: alpha 0→1, blur 7→0, y +14→0 over 0.22 s, ease-out |
**Footage:** untouched. **Captions during it:** itself. **Exit:** hard cut at chunk end.
**Build notes:** pre-render each word sprite at 2× then downscale; shadow baked into the sprite; blur applied per frame while p < 1.
**Flow prompt text:** "Words appear one at a time in the lower middle of the frame in bold white letters, a small word above a big word, the first word glowing from gold to cream, each word coming into focus as it is spoken: {{WORDS}}."
**Still-image state:** both lines fully shown.

### K1 · LABEL-BOX KEYWORD — K high (signature)
**What it is:** the last or most important word of a chunk set in an amber rounded box with dark text.
**Use when:** payoff word, contrast word, number, ≤ 1 per chunk and ≤ 3 per video. **Avoid when:** the word is long (> 9 characters at full size shrinks).
**Text:** one key word. **Geometry:** 1.2 label box; sits on the second line, 16 px extra gap above it.
**Motion:** same word reveal as C1. **Exit:** with the chunk.
**Flow prompt text:** "The word {{WORD}} sits inside a rounded golden label box with dark letters and comes into focus as it is spoken."

### U1 · UNDERLINE SWEEP — C low
**What it is:** a 6 px line under a key word, gradient amber→cream-white (footage) or amber→plum (page), drawn left to right in 0.3 s starting 0.12 s after the word, ease-out, 8 px below the text.
**Use when:** a key word is not boxed. ≤ 1 per chunk. **Exit:** with the chunk.
**Flow prompt text:** "A thin golden line draws itself under {{WORD}}."

### S1 · ICON STICKER — S mid
**What it is:** a flat hand-drawn icon (coin with a star, price tag, sparkle) that pops beside a caption stack.
**Use when:** money, price, result, celebration words. **Avoid when:** it would touch the caption or a face; never emoji.
**Text:** none; icon by meaning, centre in the sticker lane (right of the stack, ≥ 0.05W from the edge).
**Motion:** | 0–0.33 s | scale | 0 → 1.15 → 1 | ease-out then ease in-out | rotation +20° → wobble ±5°; bob ±5 px at 5 rad/s; soft shadow. **Exit:** hard end with the chunk.
**Flow prompt text:** "A small flat {{ICON}} sticker pops in beside the words with a little wobble."

### P1 · STEP PAGE WITH CARD — P high (signature)
**What it is:** a cream paper page; the live footage sits in a rounded card on the left, an icon chip and ink captions on the right, a step numeral and gradient bar above.
**Use when:** B-roll or a list item; each of 2–3 parallel steps. **Avoid when:** a speaker's face is large and speaking and the card would shrink it (use C1).
**Text:** step number, caption words. **Geometry:** 1.2 card, 1.3 step page.
**Motion:** enters through X1, stays for the whole step run (1.2–3.2 s); card plays the footage live, including across cuts inside the run.
**Exit:** X1 out. **Build notes:** build the page layer as a separate image, then blend; card shadow pre-rendered.
**Flow prompt text:** "The picture cuts to a warm cream paper page. The video plays live inside a rounded card on the left, and dark plum words appear on the right beside a small round icon."

### N1 · STEP COUNTER BAR — N high (signature)
**What it is:** a big plum numeral above a gradient bar with ticks 0 and the total; the bar fills as steps advance and the numeral rolls to the next number.
**Use when:** 2–4 parallel actions or a countdown. Numerals only for step counts.
**Text:** step numbers (1…total), total.
**Motion:** | page in +0.33 s, 0.5 s | fill | 0 → 1/total | ease-out |; | at next step's first word, 0.22 s | numeral roll | up 46 px / in from below | ease in-out |; | 0.4 s | fill | n/total → (n+1)/total | ease in-out |.
**Flow prompt text:** "A big dark number sits above a thin gradient bar that fills one step at a time; when the next step starts the number rolls up to the next one."

### H1 · HUD COUNTER — N mid
**What it is:** the counter shrunk onto the footage: white numeral 84 px and a 280 px bar at the top-left, bar fill 2/3 → 3/3 in 0.5 s.
**Use when:** the last step lands on a full-frame shot. **Avoid when:** a face sits at x < 0.46W, y < 0.13H. **Exit:** at the next cut.
**Flow prompt text:** "In the top left corner a small white number and thin gold bar show the last step filling up."

### B1 · SCALLOP BADGE — B high (signature)
**What it is:** a cream scalloped badge traced in plum ink over the footage, holding centred plum words.
**Use when:** a time phrase, a result, a slogan, the closing idea on B-roll. **Avoid when:** a face or subject sits behind the centre.
**Text:** 2–4 words, centred, key word up to 118 px.
**Motion:** | 0.10 s after the shot starts, 0.45 s | outline | traced 0 → 100 % | ease in-out | fill 0→96 % over 0.3 s | words from 0.15 s after | exit: 0.12 s before the next cut, scale 1 → 0.94 and fade.
**Flow prompt text:** "A cream badge with a wavy scalloped edge draws itself in dark plum ink over the picture and the words {{WORDS}} appear inside it."

### X1 · PAGE CUT — X high (signature)
**What it is:** the cut between footage and a page.
**Motion:** in = hard cut on a footage cut, white flash 90 % → 0 over 8 f, content fades in over 6 f; out = 4 f dissolve to the next footage. Never start a page within 3 f after a cut except on the cut itself.
**Flow prompt text:** "The picture cuts straight to a bright cream page that settles from near white; later it dissolves quickly back to the video."

### C2 · INK PAGE CAPTION — C mid
**What it is:** the caption stack on a page: plum ink, helper word small, key word large, left-aligned in the right column; gradient first word amber→plum.
**Geometry:** column x 352–684, first top y 745, key size auto-fits (≤ 60, 44 for long words). Same reveal as C1; no shadow.
**Flow prompt text:** "Dark plum words appear one by one in a stack beside the card, a small word above a bigger one."

### I1 · ICON CHIP — S low
**What it is:** an 84 px white circle with a plum ring and an amber star, above the page captions; appears with the page.
**Flow prompt text:** "A small round white icon with a gold star sits above the words."

### E1 · LABEL CLOSER — E high
**What it is:** the final chunk on a speaker: helper word + boxed key word + sparkle sticker, held until the last frame.
**Use when:** the last line. **Motion:** K1 + S1 sparkle at the box word's start + 0.15 s; hold to 0.04 s before the end.
**Flow prompt text:** "On the last words the key word lands in a golden label box and a gold sparkle pops beside it."

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 + K1 + S1 | P1 + N1 + C2 per list step, then H1, B1 on B-roll | E1 |
| Single talking head | C1 + U1 | K1 + S1 alternating, one P1 with the speaker in the card | E1 |
| B-roll only | B1 or P1 | P1 + N1 | B1 |
| Still image | C1 settled | — | K1 |

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
