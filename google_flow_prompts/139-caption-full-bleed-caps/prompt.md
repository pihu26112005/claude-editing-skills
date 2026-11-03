# Google Flow prompt · Full Bleed Caps
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Full Bleed Caps" caption style to it.

The look in one sentence: One giant ultra-heavy condensed capital keyword per phrase in a flat accent colour stretched edge to edge at the top and tucked behind the hair, plus a tiny word-by-word line with the keyword in bold.

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
| Keyword fill | #FCE813 | Giant keyword and the bold keyword inside the small line |
| Small words | #FFFFFF (design; reference uses a pale yellow-green) | Helper words |
| Shadow | #0A0A0E at 45 % blurred 7 px, offset 6 px (keyword); stacked soft dark halo on small words | Keeps text readable on bright footage |

Brand-swap rule: the accent is a parameter. One flat, fully saturated colour for the keyword and the small-line keyword; pick one that reads on the shot (warm or strongly saturated, not pastel). White and shadow never change. Demo uses vermilion #FF4B2B.

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, boxes, bars, borders, outlines, blur plates or colour overlays. Text only, plus soft shadow.

### 1.3 Layouts / lanes

| Lane | Keyword ink | Small line baseline | Use |
|---|---|---|---|
| Crest | ink bottom = head top + 0.006H (tucked behind the hair; reference tucks about 0.07H and loses about 15–25 % of the letters, the skill caps it lower, see 1.7) | 0.66H | Speaker shots with ≥ 0.15H free above the head |
| Free top | ink top at 0.02H, cap height 0.12H | 0.80H | B-roll with nothing important along the top edge |
| Low | ink top at 0.80H, bottom ≤ 0.92H | 0.755H (above the keyword) | B-roll or a person shot whose face is in the upper half and whose lower area is free |

All lanes centre on x = 0.50W. Side margin ≥ 0.05W on every text box.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Ultra-heavy condensed grotesque capitals, very tight letter fit, no outline, no italic, always uppercase | Anton Regular | Bebas Neue, League Gothic, Oswald Bold | cap height 0.12H [about 154 at 720x1280]; if the word is wider than 0.88W, shrink until it is exactly 0.88W |
| Small words | Clean medium sans, mixed case as written, light spacing; the keyword inside it in a black-weight sans in the accent colour | Barlow Medium + Barlow Black | Inter, Manrope | 46 px (keyword inside: 52 px) at 720 wide; line ≤ 0.90W |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Keyword | fade 0 → 100 % over 0.25 s, ease-out cubic, starting at the chunk start; non-crest lanes also rise 0.015H over 0.30 s |
| Small word | fade 0 → 100 % over 0.20 s, ease-out, at its spoken time; the whole line is laid out first so no word moves |
| Exit | whole chunk fades out over 0.14 s |
| Never | bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, boxes, outlines, gradients, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: text and shadow overlays; a person cut-out (segmentation mask smoothed with EMA 0.6 / 0.4, light blur on the edge) used only to draw the keyword behind the head in the Crest lane. Forbidden: any colour change, blur, zoom, crop change, background swap, retime, reorder. The footage plays live and in sync.

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head) never receives visible text. The Crest keyword hides only behind hair.
- All text boxes inside 0.05W side margins, keyword ink top ≥ 0.02H.
- A chunk never runs across a cut.

---

## 7. MOMENT LIBRARY
Family codes: T title, K keyword, C caption, E end. Energy: low / medium / high.

### T1 · OPENING CREST — T high
**What it is:** the first phrase of the video: one giant keyword fades in tucked behind the hair, small line below it on the chest.
**Use when:** the video opens on a speaker with head room. **Avoid when:** the head top is above 0.12H (use K2) or the opening shot is B-roll (use K2 / K3).
**Text:** 1 keyword (a noun or the topic word), 2–5 words in the small line including the keyword.
**Geometry:** lane Crest (1.3), keyword 1.4 at cap height 0.12H, small line 1.4.
**Motion:** keyword fade 0.25 s from chunk start (chunk start = first word, 0.10 s on the demo); small words 1.5; exit fade 0.14 s. Chunk visible 0.8–1.2 s.
**Footage behaviour:** untouched; mask only hides the keyword where hair covers it. Face box clear from frame 0.
**Captions during it:** this is the caption.
**Exit:** fade.
**Build notes:** fix the keyword lane from the highest head top (smallest y) over the chunk's frames; composite text, then re-paste the original frame where mask = 1.
**Flow prompt text:** "Across the very top of the frame, one huge, ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in, its lower edge just tucked behind the speaker's hair, and a small clean white line '{{LINE}}' fades in word by word on the chest with '{{KEYWORD}}' in bold {{ACCENT}}."
**Still-image state:** keyword fully in, small line complete.

### K1 · CREST KEYWORD — K medium
**What it is:** the T1 layout used for any later phrase on a speaker shot.
**Use when:** speaker shot with head room, phrase has one strong word. **Limit:** ≤ 3 per video, never three lane repeats in a row.
**Text:** 1 keyword, 2–5 words in the small line.
**Geometry / Motion / Exit:** as T1.
**Flow prompt text:** as T1.

### K2 · FREE-TOP KEYWORD — K medium
**What it is:** the keyword along the top edge with no head to tuck behind, small line low.
**Use when:** B-roll whose top edge is calm, or a speaker who leaves the frame top. **Avoid when:** a face or a key object sits at the top (use K3).
**Geometry:** lane Free top: ink top 0.02H, small line baseline 0.80H.
**Motion:** keyword fade 0.25 s plus rise 0.015H over 0.30 s; small words 1.5; exit 0.14 s.
**Flow prompt text:** "Along the top edge, one huge ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in with a small rise, and a small white line '{{LINE}}' fades in word by word near the bottom with '{{KEYWORD}}' in bold {{ACCENT}}."

### K3 · LOW KEYWORD — K medium
**What it is:** the keyword along the lower part of the frame with the small line just above it.
**Use when:** B-roll with a face or subject in the upper half (grocery shot, product on a shelf). **Avoid when:** hands or the key action sit at 0.75–0.92H.
**Geometry:** lane Low: ink top 0.80H, small line baseline 0.755H, gap ≥ 0.012H.
**Motion / Exit:** as K2.
**Flow prompt text:** "Along the lower part of the frame, one huge ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in with a small rise, with a small white line '{{LINE}}' just above it, the keyword in bold {{ACCENT}}."

### C1 · WHISPER LINE — C low
**What it is:** the small line alone, building word by word with its bold accent word, no giant keyword. **Use when:** a phrase has no strong word, or to rest between keywords.
**Geometry:** small line 1.4, lane baseline 0.66H on speakers, 0.80H on B-roll. Chunk 3–6 words.
**Flow prompt text:** "A small clean white line '{{LINE}}' fades in word by word near the bottom with '{{WORD}}' in bold {{ACCENT}}."

### C2 · SOLO KEYWORD — K high
**What it is:** only the giant keyword, no small line, for a punchline word or number. **Limit:** ≤ 1 per 6 s.
**Geometry:** any keyword lane. **Motion / Exit:** as K1, keyword at chunk start.
**Flow prompt text:** "One huge ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in and fades out."

### E1 · CLOSING CREST — E medium (extension in the same grammar)
**Flow prompt text:** "For the last line the huge capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in behind the top of the head and stays until the speech ends."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | K3 / K2 on B-roll, K1 on any speaker | E1 |
| Single talking head | T1 | K1, C1, K1 (keep the same lane, change the word) | E1 |
| B-roll only | K2 | K3, C2 | E1 (K2) |
| Still image | K2 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Keyword Anton, cap height 154 px, flat #FF4B2B, tuck 0.006H, shrink to 0.88W, small words Barlow Medium 46 px / Black 52 px, keyword fade 0.25 s, small word fade 0.20 s, exit 0.14 s. Chunks: 0.10–1.02 T1 (money), 1.10–1.78 K1 (earning), 2.10–3.17 K3 (yourself), 3.25–4.85 K2 (investments), 4.95–6.55 K3 (spend), 6.90–8.30 K2 (year), 8.45–9.50 E1 (watch). Keyword is shown in uppercase with trailing punctuation dropped; the small line carries the full text as written.

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
