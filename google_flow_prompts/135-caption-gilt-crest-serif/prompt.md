# Google Flow prompt · Gilt Crest Serif
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Gilt Crest Serif" caption style to it.

The look in one sentence: Tiny white serif helper lines fading in word by word beside one giant heavy gradient-serif keyword per phrase, tucked behind the top of the speaker's head or placed in a lower lane.

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
| Keyword gradient top | #EBCE92 | Top of the keyword, vertical gradient |
| Keyword gradient bottom | #C8A06E | Bottom of the keyword |
| Small line | #FFFFFF | Helper words |
| Shadow | #000000 at 40 % (keyword), stacked 90 / 100 / 80 % (small words) | Soft shadow, keeps text readable on bright footage |

Brand-swap rule: the accent is a parameter. Give the keyword any two-tone gradient (light top, deeper bottom, same hue). Keep it saturated enough to read on the shot. White and shadow never change. Demo uses a pink-to-magenta gradient (#FF96CD to #CD1E7D).

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, boxes, bars, borders, blur plates or colour overlays. Text only, plus one soft shadow.

### 1.3 Layouts / lanes

| Lane | Keyword baseline y | Small words | Use |
|---|---|---|---|
| Crest (signature) | head top + 0.02H | one line above, baseline = keyword top − 0.012H | Speaker shots with ≥ 0.17H of free space above the head |
| Free top | 0.19H  | one line above | B-roll or any shot with no person near the top |
| Chest | 0.60H (design; reference: 0.50H on a speaker) | one line above, one line below at baseline + 0.058H | Speaker shots with no room above the head; face stays above 0.40H |
| Low | 0.745H  | one line above, optional line below | B-roll and shots where the subject is high in frame |

All lanes centre on x = 0.50W. Side margin ≥ 0.05W on every text box. Keyword ascender top ≥ 0.02H.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Heavy, very high stroke contrast, sharp hairline serifs, tight tracking, mixed case as written | Playfair Display weight 800 | Bodoni Moda Bold, DM Serif Display | cap-to-descender ≈ 0.13H; font size ≈ 0.21W [150 at 720 wide], shrunk so the word is ≤ 0.78W wide; top lane ≤ 0.19W |
| Small words | Light condensed text serif, mixed case, centred | Instrument Serif Regular | Newsreader, EB Garamond | font size ≈ 0.08W [58 at 720 wide] (reference small cap height 0.03H); line ≤ 0.90W |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Small word | fade 0 → 100 % over 0.20 s, ease-out, at its spoken time; the whole line is laid out first so no word moves |
| Keyword | fade 0 → 100 % over 0.30 s plus rise from 0.02H below its rest position, ease-out cubic, starting at the keyword's spoken time |
| Exit | whole chunk fades out over 0.14 s (reference: about 3 frames at 32 fps) |
| Never | bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, boxes, outlines, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: text and shadow overlays; a person cut-out (segmentation mask smoothed with EMA 0.6 / 0.4) used only to draw the keyword behind the head in the Crest lane. Forbidden: any colour change, blur, zoom, crop change, background swap, retime, reorder. The footage plays live and in sync.

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head) never receives visible text. Crest keyword hides only behind hair; descenders end beside or behind the head.
- All text boxes inside 0.05W side margins.

---

## 7. MOMENT LIBRARY
Family codes: C caption, K keyword, E end. Energy: low / medium / high.

### K1 · CREST KEYWORD — K medium
**What it is:** one giant gradient serif keyword rises behind the top of the head, with a tiny line of helper words above it.
**Use when:** speaker shot with head room, and the phrase has one strong word. **Avoid when:** head top is above 0.12H or the head moves out of frame (use K3).
**Text:** 1 keyword (≤ 10 characters ideal, as written), 1–4 helper words above (never after the keyword; helper words that follow the keyword go to the next chunk).
**Geometry:** lane Crest (1.3); keyword 1.4; helper line centred above.
**Motion:** small words per 1.5; keyword fade + rise 0.30 s at its spoken time; exit fade 0.14 s. Chunk visible 0.7–1.6 s.
**Footage behaviour:** untouched; mask only hides the keyword where the head covers it.
**Captions during it:** this is the caption.
**Exit:** fade.
**Build notes:** fix the lane from the lowest head-top row (highest head) over the chunk's frames; composite text then re-paste the original frame where mask = 1.
**Flow prompt text:** "Just above the speaker's head, one very large heavy serif word '{{KEYWORD}}' in a soft {{ACCENT}} gradient fades in, its lower edge tucked behind the hair, with a tiny white serif line '{{HELPERS}}' above it."
**Still-image state:** keyword fully in, helper line complete.

### K2 · CHEST KEYWORD — K medium
**What it is:** helper words above, giant keyword, helper words below, centred on the chest.
**Use when:** speaker shot with no head room, or a phrase with words before and after its keyword. **Avoid when:** hands or a phone sit at 0.45–0.70H and the text would hide the subject's action.
**Text:** 1 keyword, 0–2 words above, 0–3 words below.
**Geometry:** lane Chest. **Motion/Exit:** as K1.
**Flow prompt text:** "Across the chest, tiny white serif words '{{ABOVE}}' fade in word by word over one giant {{ACCENT}} gradient serif word '{{KEYWORD}}', with '{{BELOW}}' underneath."

### K3 · FREE-TOP KEYWORD — K medium
**What it is:** the K1 layout with no occlusion, used on B-roll or when the head leaves the frame.
**Geometry:** lane Free top (keyword baseline 0.19H). **Motion/Exit:** as K1.
**Flow prompt text:** "Near the top of the frame, a tiny white serif line '{{HELPERS}}' fades in word by word above one large {{ACCENT}} gradient serif word '{{KEYWORD}}'."

### K4 · LOW KEYWORD — K medium
**What it is:** the keyword in the lower lane with helper words above (and below).
**Use when:** B-roll with a clear lower area; subject high in frame. **Avoid when:** a face sits in the lower half.
**Geometry:** lane Low. **Motion/Exit:** as K1.
**Flow prompt text:** "In the lower part of the frame, tiny white serif words '{{ABOVE}}' fade in above one giant {{ACCENT}} gradient serif word '{{KEYWORD}}'."

### C1 · WHISPER LINE — C low
**What it is:** the helper line alone, building word by word, no keyword. **Use when:** a phrase has no strong word, or between keyword chunks.
**Geometry:** 1.4 small words, centred, lane baseline at the Free top or Chest lane. **Motion:** 1.5. Chunk 3–6 words.
**Flow prompt text:** "A tiny white serif line '{{LINE}}' fades in word by word near the top of the frame."

### C2 · SOLO KEYWORD — K high
**What it is:** only the giant keyword, no helper line, for a punchline word. **Use when:** payoff or a number. **Limit:** ≤ 1 per 6 s.
**Geometry:** any keyword lane. **Motion/Exit:** as K1, keyword time = chunk start.
**Flow prompt text:** "One giant {{ACCENT}} gradient serif word '{{KEYWORD}}' fades in with a small rise and fades out."

### E1 · CLOSING CREST — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 or K3, held 0.4 s past the last spoken word (never past the end of the shot or the head leaving frame).
**Flow prompt text:** "For the last line the keyword '{{KEYWORD}}' fades in large in the soft {{ACCENT}} gradient and stays until the speech ends."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | K2 | K4 / K3 on B-roll, K1 on any speaker | E1 (K1) |
| Single talking head | K1 | K2, C1, K1 (alternate lanes) | E1 |
| B-roll only | K3 | K4, C2 | E1 (K3) |
| Still image | K3 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Keyword gradient #FF96CD → #CD1E7D, size 150 px (top lanes 138 px, width-capped at 0.78W), small words 58 px, shadows as 1.1, crest tuck 0.02H, chunk fade-out 0.14 s, keyword rise 0.02H over 0.30 s. Chunks: 0.10–1.02 K2 (money), 1.10–1.80 K1 (more.), 2.10–3.17 K4 (yourself), 3.25–4.88 K3 (investments,), 4.95–6.55 K4 (left.), 6.90–8.30 K3 (year), 8.45–9.55 E1/K1 (happens.; ended early because the speaker leans toward the camera at 9.6 s).

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
