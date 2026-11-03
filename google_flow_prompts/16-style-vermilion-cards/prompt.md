# Google Flow prompt · Vermilion Cards
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Vermilion Cards" motion style to it.

The look in one sentence: Hot orange-red and saffron pages with hard-shadow footage cards, giant condensed title bands, cream label captions with an orange newest word and a black wedge wipe.

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
| VERMILION | `#FE3B00` | page of the stack layout, title bands, newest-word colour |
| SAFFRON | `#F3AD01` | page of the single-card layout (V08) |
| CREAM | `#E0D1BC` | title letters, caption label boxes, plain captions |
| INK | `#1B1B1B` | card shadows, wedge, caption text |

No other colours; the footage carries everything else. Brand variant: VERMILION and SAFFRON may be swapped for two brand colours of similar strength; CREAM and INK stay.

### 1.2 Containers
- **Full-frame:** footage fills the frame. Two bands overlay it (V01), nothing else changes.
- **Card:** rectangle with 0.007 W radius, cover-fit crop (anchor), **hard offset shadow**: INK, no blur, extruded diagonally down-right by 0.014 W [15 px] at rest.
- **Stack card boxes:** top x 0.09–0.91 W, y 0.055–0.474 H; bottom x 0.09–0.91 W, y 0.551–0.957 H [0.12 W gap between them for a caption].
- **Single card box (V08):** x 0.087–0.92 W, y 0.049–0.963 H.
- Pages are flat colour; no texture, no gradient.

### 1.3 Layouts

| Layout | Page | Content |
|---|---|---|
| FULL + BANDS | footage | top band y 0–0.17 H, bottom band y 0.83–1 H, both VERMILION |
| STACK | VERMILION | two cards, plain captions between them |
| SINGLE | SAFFRON | one tall card, label captions |

### 1.4 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Title | ultra-condensed heavy grotesque, UPPERCASE, CREAM, left-aligned from x −0.004 W, repeated in both bands | Anton | Bebas Neue, League Gothic, Oswald Bold | cap height 0.12 H [230 px], shrunk so the word fits 0.96 W |
| Label caption | semibold sans, original case, INK on a CREAM box | Inter SemiBold (wght 600) | Plus Jakarta Sans 600, Manrope 600 | 0.039 H [75 px]; box height 0.052 H, side padding 0.014 W |
| Plain caption | medium sans, CREAM, no box, centred | Inter Medium (wght 500) | Plus Jakarta Sans 500 | 0.034 H [65 px], shrink to fit 0.84 W |

### 1.5 Motion language
- **Hard and punchy:** captions pop with no fade; layouts switch on footage cuts; the only soft curves are ease-out-cubic (arrivals) and ease-in-out-cubic (wedge).
- **Card arrival:** scale up from 62 % with a huge shadow that retracts (V04).
- **Pop:** 6 % overscale and a 0.04 W shadow settle back over 0.2 s (V05).
- No bounce, no rotation, no fades on cards. Letters of a title fade in individually.

### 1.6 What may happen to the user's footage
- Allowed: cover-fit crops into cards; full-frame footage with the two bands laid on top (bands never cover a face); uniform scale during pops and drops.
- The **primary footage always plays live, in sync with the audio**: full-frame, or the bottom card of a stack, or the single card. The top card of a stack shows the user's own previous shot as a **still** (≤ 1 shot old).
- Never recolour or filter footage. Never retime, reorder or trim.
- Exception: **footage is cropped** when it sits in a card (shape change only).

### 1.7 Safe zones
- Faces are never under a band, a label, a wedge or a shadow. In FULL + BANDS captions sit at y 0.64 H, under the chin of a normal talking head; if a face is lower than 0.55 H, move the label to y 0.80 H [].
- Cards: set the crop anchor so the face sits inside its card with ≥ 6 % margin.

---

## 7. MOMENT LIBRARY
Families: **BAND**, **CARD**, **CAP**, **CUT**. Energy:  low ·  medium ·  high.

---

### V01 · BAND OPEN — BAND  (signature opener)

**What it is:** Over full-frame footage, a vermilion block appears top-left and one bottom-right; both sweep across to become full-width bands.

**Use when:** the opening line; any talking-head stretch ≥ 1.5 s (also the closer, V09). **Avoid when:** a face sits in the top 17 % or bottom 17 % of the frame.

**Geometry:** top band x 0–W, y 0–0.17 H; bottom band x 0–W, y 0.83–1 H (height may shrink to 0.14 H for tight framing).

**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 3 | both blocks | width | pop to 0.12 W | hard |
| 3 → 9 | top block (anchored left), bottom block (anchored right) | width | 0.12 W → W | ease-out-cubic |

Starts 0.10 s into the video. Bands stay until the layout changes.

**Build notes:** draw plain rectangles on the live frame.

**Flow prompt text:** "Two bold orange-red bars sweep in across the top and the bottom of the frame, the top one from the left and the bottom one from the right, while the video keeps playing between them."

---

### V02 · TITLE REVEAL — BAND  (signature)

**What it is:** A giant condensed word fills both bands; its letters fade in one by one in a scrambled order.

**Text:** one user word (topic or verdict), UPPERCASE, ≤ 9 letters.

**Graphics:** CREAM, repeated identically in both bands, vertically centred in each band, left-aligned, size per 1.4.

**Motion:** after the bands finish (≈ 6 f after V01 starts), each letter goes 0 → 100 % over 5 f (0.17 s); letter start times are spread over 7 f in a scrambled order (not left to right).

**Exit:** leaves with the layout change (hard).

**Flow prompt text:** "The word \"{{TITLE}}\" appears in huge, tall, narrow cream capitals inside both bars, the letters fading in one at a time in a scattered order."

---

### V03 · LABEL CAPTIONS — CAP  (signature, always on in FULL and SINGLE layouts)

**What it is:** Small cream boxes with black text that grow word by word; the newest word is orange for 0.4 s, then black.

**Text:** the user's words verbatim, chunks of 2–4 words (≤ 26 characters), original case. Each word pops at its spoken time (no fade). A chunk wider than 0.66 W breaks onto a second box stacked under the first (gap 0.004 H).

**Graphics:** left edge x 0.15 W, top y 0.64 H; box CREAM, text INK, newest word VERMILION; sizes per 1.4.

**Exit:** the chunk disappears at its end (hard).

**Flow prompt text:** "Small cream label boxes with black text appear low on the frame and grow one word at a time; the newest word flashes orange for a moment, then turns black. The line is: \"{{LINE}}\"."

---

### V04 · CARD DROP — CARD  (signature)

**What it is:** On a cut, the page turns vermilion and two cards drop in: the new shot live in the lower card, the previous shot as a still in the upper card. Each card grows from small while its black shadow retracts.

**Use when:** person → B-roll cut, or any cut after FULL + BANDS. **Avoid when:** the new shot has a face that cannot fit a card.

**Content:** bottom = current footage (live); top = previous shot's calm still, or the person if the story needs the speaker.

**Motion:**

| t (f @30) | Property | From → To | Ease |
|---|---|---|---|
| 0 → 10 | card scale (about its centre) | 62 % → 100 % | ease-out-cubic |
| 0 → 10 | shadow offset | 0.17 W → 0.014 W | ease-out-cubic |
| 0 → 10 | cards' centre x | −0.08 W → 0 | ease-out-cubic |

Starts on the cut frame.

**Captions during it:** V06.

**Flow prompt text:** "On the cut, the screen turns bright orange-red and two framed pictures drop in, one above the other, each growing from small with a hard black block shadow that shrinks as it settles: {{TOP}} on top and {{BOTTOM}} below."

---

### V05 · CARD POP — CARD

**What it is:** A new shot in an existing layout arrives with a quick scale-and-shadow punch.

**Use when:** a cut that stays inside a stack or single card. **Motion:** 0 → 6 f: scale 106 % → 100 %, shadow 0.054 W → 0.014 W, ease-out-cubic; the content changes hard on the first frame. In a stack the top still updates to the previous shot.

**Flow prompt text:** "On the cut the framed picture lands with a small punch: it is slightly larger for an instant and its black block shadow settles back."

---

### V06 · PLAIN CAPTIONS — CAP

**What it is:** Cream text without a box, centred in the gap between the two cards; words pop in one by one.

**Text:** same chunks as V03. **Graphics:** centre x 0.5 W, y 0.5125 H, size per 1.4. **Exit:** hard at chunk end.

**Flow prompt text:** "Cream text with no box sits centred between the two pictures and grows one word at a time: \"{{LINE}}\"."

---

### V07 · WEDGE WIPE — CUT  (signature)

**What it is:** A black slanted band sweeps left to right across the whole frame; behind it the layout changes to the single saffron card.

**Use when:** a cut from a stack or bands to a calm hero shot; a section change. **Avoid when:** a face is expected to be on screen mid-sweep (the wedge crosses it for ~0.1 s; accept only on B-roll).

**Geometry:** band width 0.45 W, slant 0.30 W over the full height, INK.

**Motion:** 12 f @ 24 fps (0.5 s), ease-in-out-cubic; centre x from −0.37 W to 1.37 W. Left of the band: new layout; right: old layout (still updating live content).

**Flow prompt text:** "A black slanted band sweeps from left to right across the whole frame; behind it the orange-red page turns saffron yellow and the pictures become one tall framed picture."

---

### V08 · SAFFRON CARD — CARD

**What it is:** One tall card (box 1.2) on the saffron page with label captions (V03).

**Content:** current footage, live; anchor on the face. **Hold:** any length; use V05 on cuts.

**Flow prompt text:** "The video plays inside one tall framed picture with a hard black block shadow on a saffron yellow page."

---

### V09 · BAND CLOSE — BAND  (signature closer)

**What it is:** V01 + V02 again on the final section, with the payoff word as title.

**Text:** one user word from the last line. **Motion:** as V01/V02, starting 0.1 s after the layout cut.

**Flow prompt text:** "Two bold orange-red bars sweep in across the top and bottom again and the word \"{{TITLE}}\" fills them in huge cream capitals, letter by letter."

---

### V10 · SOLO CARD — CARD  (extension in the same grammar)

**What it is:** B-roll-only videos: one card on vermilion (box 1.2, same shadow) with V04's arrival, plain captions below the card.

**Use when:** no speaker anywhere. **Flow prompt text:** "A single framed picture with a hard black block shadow drops onto an orange-red page; cream text sits beneath it."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | V01 + V02, V03 | V04, V05, V06, V07 + V08 | V09 |
| Single talking head | V01 + V02, V03 | V07 + V08 half way | V09 |
| B-roll only | V10 | V04 / V05, V07 + V08 | V08 |
| Still image | V08 settled (saffron page) | — | — |

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
