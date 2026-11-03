# Google Flow prompt · Doodle Board
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Doodle Board" motion style to it.

The look in one sentence: Boiling white pen outline with doodles around the speaker, tilted paper word tags, a pink chart growing behind you, handwritten captions with a pink marker key word.

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
| FOOTAGE | the user's own colours, never graded | everything underneath |
| LINE | `#FFFFFF` | all pen work: outline, frame, doodles, handwritten word, caption text |
| PINK | `#F4A7B9` | the one accent: marker swash behind the key word, bars, pink tags, the heart doodle |
| PAPER | `#FFF8EC` | cream paper tags |
| INK | `#2B2522` | text on paper tags and on the pink swash |
| SHADOW | `#1E1816` | thin outline and soft shadow under every white line so it reads on bright footage |

No other accent colour. Brand variant: PINK may become one brand colour.

### 1.2 Line work (the "boil")
- All hand-drawn lines are **stepped at 10 fps** and cycle through **3 jitter sets** (`set = floor(t × 10) mod 3`), so the line trembles like a real pen redrawn each frame; the footage itself keeps full frame rate.
- Pen: 5 px, round ends, white; every white stroke gets a SHADOW copy under it (blur 2 px, +2 px down, 50 %).
- Strokes **draw on** (0.4–0.45 s, ease-out-cubic along the path) and fade out in 0.1 s.
- Jitter: points shift ±1.4–2 px per step. Outline warp: low-frequency noise ±3 px.
- Doodles are **pictograms only** (heart, music notes, swirl, four-point sparkle, arrow). Never letters or fake words.

### 1.3 Paper and chart pieces
- **Tag:** rounded rectangle (radius 7 px), PAPER or PINK, faint ruled fibre lines, a translucent tape strip on top, soft shadow, tilt ±2.5–3° (alternate sides), padding 28 px × 17 px.
- **Bars:** rounded-top pink bars (PINK at 88 % with a soft white highlight strip), no outline, no axis, **no numbers or letters**.

### 1.4 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Caption | handwritten, white with dark outline, sentence case | Gaegu Bold | Gochi Hand, Patrick Hand | 0.066 H [84 px] |
| Caption key word | same font, INK on a PINK marker swash (a wobbly 4-point polygon, boiling) | same | same | same |
| Tag text | handwritten, INK | Gaegu Bold | same | 0.047 H [60 px] |
| Label tag | uppercase, letter-spaced 0.07 em, INK on PINK, optional drawn arrow | Inter ExtraBold | Arial Black | 0.031 H [40 px] |
| Handwritten word beside the speaker | brush-hand, white with dark outline, rotated 7° | Caveat Brush | Gochi Hand | 0.085 H [109 px] |

All words are the user's words, spelled as given. Headline tags use 1–3 user words, per line ≤ 14 characters, max 2 lines.

### 1.5 Motion language
- **Stick (tags):** scale 1.32 → 1.0, rotation +7° → resting tilt, fade in over the first half, 7 f at 24 fps (ease-out-cubic); shadow starts wide and tightens as it lands; three short white pop lines burst from the top-right corner for 0.3 s.
- **Grow (bars):** each bar rises over 0.55 s (ease-out-cubic), 0.09 s apart, left to right.
- **Draw-on:** pen strokes follow their path.
- **Leave:** tags fade over 0.12 s ending on the cut; the frame fades 0.08 s before it.
- Nothing rotates continuously, bounces or covers a face.

### 1.6 What may happen to the user's footage
- Default: footage stays full-frame, untouched, and everything is drawn on top.
- **Behind-person elements (D3 bars)** and the **matte-edge outline (D1)** need a clean person matte (MediaPipe selfie segmentation, threshold 0.4 to 0.65 ramp, EMA 0.6, reset at every cut). Use them only on a single clearly visible person; check the edge frames. If limbs drop out, hands blur into the wall, or the person leaves the frame, skip the moment (D1 falls back to doodles without the outline, D3 to a front chart that sits in a free zone away from the face).
- Limits: busy backgrounds, hair against similar colours, fast arm movement and several people all break the matte. Bars hidden behind a wide torso are partly out of sight; keep bar tops above the shoulders.

### 1.7 Safe zones
- Face box: never covered by tags, doodles, bars or captions.
- Tags and doodles live in the wall zone (above the shoulders, beside the head) or a free zone of B-roll; never over the main subject of a B-roll shot (hands, phone screen, object).
- Captions: bottom, baseline 0.835 H (0.62 H if the face is low). Label tag at 0.60–0.66 H on the side away from the face.

---

## 7. MOMENT LIBRARY
Family codes: **DRAW** (pen work), **PAPER** (tags, chart), **CAP** (captions), **CUT** (scene treatment). Energy:  low ·  medium ·  high.

### D1 · BOIL OUTLINE — DRAW  (signature)
**What it is:** A white pen outline traces the speaker's silhouette and boils, while line doodles pop up around them and one handwritten word is written beside the head.
**Use when:** the first talking-head line, or any person shot with a clean matte, 1–2 s.
**Text:** the handwritten word = 1 user word (the key noun of the line), no added punctuation. Doodles carry no text.
**Geometry:** outline gap 4 px outside the matte edge, 4–5 px thick, starts 0.3 s into the shot with a 0.25 s fade. Doodles side: heart (PINK, 0.13 W) top corner at 0.14 W / 0.125 H, notes (white, 0.11 W) opposite top corner, swirl (white, 0.10 W) mid-height on the face-free side; handwritten word at 0.80 W / 0.325 H on the side away from the face. Heart 0.5 s, notes 0.75 s, word 0.55 s, swirl 1.0 s after the shot starts. A speaker on one side swaps the sides.
**Motion:** outline boils (1.2); each doodle draws on over 0.45 s; the word is revealed left to right over 0.35 s; all end on the cut.
**Flow prompt text:** "A thin white hand-drawn outline wobbles around the person like a marker line redrawn each frame. Small white line doodles appear beside them: a soft pink heart, music notes and a swirl, and the handwritten word \"{{WORD}}\" is written in white next to their head. The face stays clear."

### D2 · PAPER TAGS — PAPER  (signature)
**What it is:** Small paper word tags stick onto the scene one at a time, slightly tilted, each as its words are spoken.
**Use when:** a list, steps, tips or key phrases, on a person shot (wall zone) or B-roll (free zone). One tag per phrase, max 1 visible tag at a time on B-roll, up to 3 on a wall shot.
**Text:** 1–3 user words per tag (≤ 14 characters per line, 2 lines max), tag colour alternating PINK, PAPER.
**Geometry:** tag centre in a free zone (default top band 0.095 H on B-roll without a face, 0.335 H beside a head); tilt −3° / +2.5° alternating; arrives 0.3 s after the first word is spoken, stays until the cut (fade over the last 0.12 s).
**Motion:** stick (1.5) with pop lines.
**Flow prompt text:** "A small paper tag with tape on top, handwritten words \"{{TAG}}\", is stuck onto the {{ZONE}} with a little pop, slightly tilted, with a soft shadow. It does not cover the face."

### D3 · CHART GROW — PAPER  (signature)
**What it is:** A soft pink bar chart grows **behind** the speaker, taller to the right, while a pink label tag with an arrow sits beside them.
**Use when:** the payoff, a result, growth, "over time", "watch what happens" (a person shot with a clean matte, last 1–2 s).
**Text:** the label tag = 1–3 user words in uppercase plus a drawn arrow (↗). Bars carry **no numbers or words**; numerals only if the user's own text contains them, then as a small tag, never on the bars.
**Geometry:** 7 bars x 0.07–0.93 W, baseline 0.49 H (at the shoulder line), bar width 0.075 W, heights 0.09, 0.13, 0.12, 0.19, 0.25, 0.30, 0.37 of H (a gently bumpy climb), PINK, radius 14 px; the person matte is composited over the bars. Label tag centre 0.30 W / 0.625 H (side away from the face). Bars start 0.3 s into the shot; label tag 0.35 s later; a sparkle doodle (white, 0.06 W) draws on above the tallest bar after growth (about 0.8 s later).
**Motion:** grow (1.5); D1's outline may run at the same time.
**Flow prompt text:** "Soft pink bars grow one after another behind the person, climbing to the right, with no numbers or letters. A small pink label \"{{LABEL}}\" with an arrow pointing up and right sits beside them. The person stays in front, face clear."

### D4 · DOODLE CAPTIONS — CAP (always on)
**What it is:** Big handwritten white captions near the bottom; the key word of each chunk sits on a pink marker swash.
**Text:** the user's words verbatim, chunks of 2–6 words over max 2 lines (≤ 18 characters per line), split at punctuation, never ending on an article or preposition; one key word per chunk, the payoff word always.
**Geometry:** centred; baseline of line 2 at 0.835 H; 4 px dark stroke plus soft shadow; swash is 4 jittered points, boiling at the 10 fps step.
**Motion:** each chunk scales 0.88 → 1.0 and fades in over 4 f (1/6 s); swaps on the next chunk.
**Flow prompt text:** "Big handwritten white captions in one or two short lines near the bottom, the key word written in dark ink on a pink marker stripe. The ONLY caption lines, in order, are: [a-b s] \"{{CHUNK_1}}\", …"

### D5 · DOODLE FRAME — CUT  (B-roll cut beat)
**What it is:** On B-roll (no person), a sketchy white pen frame draws itself around the edge of the shot.
**Use when:** every cut to a non-person shot, so the cut gets a beat.
**Geometry:** rounded rectangle inset 16 px, radius 36 px, pen 5 px, boiling (2 px jitter); draws on over 0.4 s from the cut; fades 0.08 s before the next cut. Not used on person shots that carry D1.
**Flow prompt text:** "A thin white hand-drawn frame wobbles around the edge of the shot like a marker line."

### D6 · SPARKLE SPRINKLE — DRAW  (extension)
**What it is:** 3–4 four-point sparkle doodles draw on in free corners of a B-roll shot, 0.15 s apart.
**Use when:** a calm B-roll (plant, object, view) that needs a beat, or the end of a chart.
**Geometry:** sizes 0.045–0.07 W, white, scattered in the free zones, never over the subject; starts 0.25 s after the cut.
**Flow prompt text:** "A few small white four-point sparkles are drawn in the corners of the shot, one after another."

### D7 · NUMBER STAMP — PAPER  (extension, numbers only)
**What it is:** A user numeral ("3", "2025", "10%") written in the handwritten word font inside a hand-drawn white circle that boils.
**Use when:** the user's text contains a number or step count.
**Text:** the numeral exactly as written; never an invented one.
**Geometry:** circle diameter 0.2 W, position as for D1's word; draws on 0.45 s.
**Flow prompt text:** "The number \"{{NUMBER}}\" is handwritten in white inside a wobbly hand-drawn circle."

### D8 · SLOW PUSH — CUT  (extension)
Footage scale 100 → 104 % linear over a shot longer than 1.5 s with no other arrival. Never while D3 or D1 run.
**Flow prompt text:** "The shot drifts in very slowly."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll list → talking head | D1 outline + doodles + handwritten word | D5 frame and D2 tag on each B-roll beat, D6 on a calm shot | D3 chart grow with outline |
| Single talking head | D1 | D2 tags on the wall, D7 for a number | D3 |
| B-roll / product only | D5 + D2 | D6, D8 | D2 label tag |
| Still image | D1 doodles (heart, notes) + D4 caption, D2 tag | — | — |

### Demo scene → moment table (demo2-original.mp4, 24 fps)

| Scene | Time | Moments |
|---|---|---|
| S1 talking head | 0–1.83 | D1 (outline 0.3, heart 0.5, word "money" 0.55, notes 0.75, swirl 1.0), D4 |
| S2 hands with cash | 1.83–3.25 | D5 frame, D2 tag "Pay yourself first" 2.15, D4 |
| S3 phone app | 3.25–4.92 | D5 frame, D2 tag "automate your / investments" 3.5, D4 |
| S4 grocery checkout | 4.92–6.63 | D2 tag "spend only / what's left" 5.2 (left, away from the face), D4 |
| S5 plant + clock | 6.63–8.38 | D5 frame, D6 sparkles 6.9 / 7.05 / 7.2, D2 tag "one year" 7.5, D4 |
| S6 talking head | 8.38–10 | D1 outline 8.5, D3 bars 8.65, label tag "what happens ↗" 9.0, sparkle 9.45, D4 |

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
