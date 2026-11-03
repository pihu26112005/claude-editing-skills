# Google Flow prompt · Sash Orbit Plate
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Sash Orbit Plate" caption style to it.

The look in one sentence: A glossy teal sash orbiting the speaker, back half behind the head and front half over the chest, carrying a tracked uppercase title, with every other line on a small dark rounded plate with an accent border.

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
| Sash light | #EBCE92 | Upper edge of the sash gradient |
| Sash deep | #C8A06E | Lower edge |
| Sash text | #2A1E0C | Title letters |
| Plate fill | #14110A at 88 % | Caption plate |
| Accent | measured: gold #DAA24D | Accent word, plate border, underline |
| Caption | #FFFFFF | Spoken words (unspoken words at 38 % opacity) |

Brand-swap rule: the accent is a parameter (one hue for sash, border and accent word; sash gradient light edge → deep edge of that hue). Demo uses teal: sash #96F2E6 → #1EA094, text #0A2826, accent #3FD6C6.

### 1.2 Containers / shapes

- **Sash:** a band half-width 0.04H (51 px at 720x1280, band 0.08H tall) following a tilted ellipse around the speaker; back half (top arc) drawn darker (×0.82), front half (bottom arc) with a soft shadow (offset 0.008H, blur 14 px, 45 %); two thin light pinstripes at ±0.78 of the half-width; 14-step gradient across the width, lightest at 0.35 of the width.
- **Plate:** rounded rectangle, radius 26 px, fill 88 % dark, 2 px accent border at 59 %, a 5 px solid accent line along the bottom edge inset 14 px from each corner. Width = text width + 2 × 0.055W; height = lines × 72 px + 52 px.
- Footage is always full frame and untouched.

### 1.3 Layouts

| Layout | Geometry | Use |
|---|---|---|
| Sash ring (design, tuned on demo) | ellipse centre (0.50W, 0.367H), rx 0.806W, ry 0.293H, tilted +5° clockwise; top arc centreline at about y 0.055H at the middle, bottom arc about 0.65H | Person shots; face box stays clear |
| Plate low lane | plate centre y = 0.795H, centred x, bottom ≤ 0.90H | Default for all plates |
| Plate top lane | centre y = 0.20H | When a face is low |

Text safe: every glyph and plate inside 0.05W side margins.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Sash title | Extra bold uppercase, tracking 0.16 em, placed glyph by glyph along the band centreline | Inter weight 800 | Roboto Bold, Archivo | 40 px at 720 wide, shrunk until the line is ≤ 0.74W |
| Plate caption | Bold sans, mixed case as written, centred, line pitch 72 px | Inter weight 700 | Roboto Bold, Plus Jakarta Sans | 58 px [87]; one or two lines, ≤ 0.62W for one line |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Sash band | wipes in left to right across the frame, 0.45 s, ease-out cubic, soft 40 px edge; top half first, bottom half 0.45 s later |
| Sash exit | wipes out left to right over 0.28 s, ending ≥ 0.05 s before a cut |
| Plate | fade-in 0.12 s; fade-out 0.10 s |
| Words | each word 38 % → 100 % over 0.20 s at its spoken time; layout fixed first |
| Never | bounce, overshoot, letter typing, scale pops, glitch, shake, flashes, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: overlays, and a person mask (confidence mask from a selfie segmenter, EMA 0.6 / 0.4, blur 1.5 px) that hides the sash's back half where the person is. Forbidden: any change to the footage itself.

### 1.7 Safe zones

- Face box (x 0.34–0.66, y 0.15–0.40) receives no sash pixels in front of the person and no text.
- Text and plates inside 0.05W side margins; plates never below 0.90H.

---

## 7. MOMENT LIBRARY
Family codes: T title, C caption, E end. Energy: low / medium / high.

### T1 · ORBIT SASH TITLE — T high
**What it is:** the sash wipes in around the speaker, top half behind the head with the first half of the line, then the bottom half across the chest with the rest, held, then wipes out.
**Use when:** a person shot opens (or closes) with a strong line. **Avoid when:** the shot has no person, the head top is above 0.10H, or a cut is within 1.7 s.
**Text:** 3–6 words from the user's line, uppercase, split in two (top ≤ 18 characters, bottom ≤ 19).
**Geometry:** ring 1.3; type 1.4; both halves keep text ≥ 0.05W from the edges.
**Motion:** top band in at chunk start (0.45 s); bottom band in 0.45–0.65 s later (at its first word); hold; exit 0.28 s.
**Footage behaviour:** untouched; face visible from frame 0; the top half passes behind hair and head.
**Captions during it:** none (the sash is the caption).
**Exit:** wipe out.
**Flow prompt text:** "A glossy {{ACCENT}} sash curves around the speaker like an orbit: its upper half passes behind the head and carries the tracked capital words '{{TOP}}', its lower half crosses in front of the chest with '{{BOTTOM}}'. It sweeps in from the left, holds, and sweeps out. The face stays clear."
**Still-image state:** both halves fully in.

### C1 · ACCENT PLATE — C medium
**What it is:** a small dark rounded plate in the low lane with one or two lines of bold white words that brighten as they are spoken, one word in the accent colour, an accent line along the plate's bottom edge.
**Use when:** any spoken line outside a title; always on bright or busy shots.
**Text:** 2–5 words (as written), 1 accent word (key noun or verb).
**Geometry:** plate 1.2; type 1.4; lane low.
**Motion:** 1.5. Chunk 0.9–1.7 s.
**Flow prompt text:** "A small dark rounded plate with a thin {{ACCENT}} border sits low in the frame; the words '{{LINE}}' brighten one by one as spoken, and '{{WORD}}' is {{ACCENT}}."
**Still-image state:** all words bright.

### C2 · BARE ACCENT LINE — C medium
**What it is:** the C1 text with no plate: white words with a soft shadow (black 90 / 100 / 80 % stack) and a short accent underline bar (0.125W × 4 px) 14 px below the last line.
**Use when:** dark or calm shots (lane luminance < 0.35) with room above 0.70H. **Avoid when:** bright footage (use C1).
**Geometry:** same positions as C1; underline centred.
**Flow prompt text:** "White bold words '{{LINE}}' brighten one by one low in the frame, '{{WORD}}' in {{ACCENT}}, with a short {{ACCENT}} line beneath."

### C3 · TOP PLATE — C medium (extension in the same grammar)
**What it is:** C1 at the top lane (centre y 0.20H), for shots where the lower half holds a face or the action. **Motion/Exit:** as C1.
**Flow prompt text:** "The same dark plate sits near the top of the frame with the words '{{LINE}}'."

### E1 · CLOSING SASH — E high (extension in the same grammar)
**What it is:** T1 used for the last line, held to 0.3 s before the end of the speech, exiting before the clip ends. Same spec as T1.
**Flow prompt text:** "For the last line the sash sweeps around the speaker again with '{{TOP}}' above and '{{BOTTOM}}' below, then sweeps out."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | C1 on every B-roll line | E1 |
| Single talking head | T1 | C2 / C1, C3 | E1 |
| B-roll only | C1 | C1, C3 | C1 |
| Still image | T1 settled or C1 | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Ring centre (360, 470) px, rx 580, ry 375, tilt 5°, half-width 51 px; sash text 40 px tracked 0.16 em; plate text 58 px, pitch 72, plate centre y 1018 px (0.795H). Chunks: T1 0.10–1.80 (top band in 0.10, bottom band in 0.75, exit 1.50–1.78); C1 2.10–3.15 (accent "first,"); 3.25–4.85 ("investments,"); 4.95–6.55 ("left."); 6.90–8.30 ("year"); E1 8.45–9.85 (top in 8.45, bottom in 8.90, exit 9.55–9.85). All B-roll shots were bright, so C1 plates were used throughout.

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
