# Google Flow prompt · Tall Serif Stack
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Tall Serif Stack" caption style to it.

The look in one sentence: Tall narrow high-contrast serif capitals in one bold colour cut in above the subject with a drifting sheen, tiny white serif captions building word by word along their lower edge.

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
| Title colour (default) | #CF3D3F | Title capitals. Measured median (207,60,63) over several frames. A parameter: replace it with the user's brand colour. |
| Title sheen | accent lightened 45–55 % toward white | A soft diagonal band inside the letters. Measured: a paler pink band sat roughly in the middle of the block. |
| Caption white | #FFFFFF | Caption words |
| Caption ink | #14141E at 78 % | Thin 1.5 px outline round caption glyphs (design, for bright shots) |
| Shadow | #000000 | Caption shadow (0, +2 px, blur 5 px, 59 %); title shadow (0, +6 px, blur 7 px, 35 %)  |

Brand-swap rule: only the title colour (and its sheen) changes. Caption white never changes. Demo used cobalt #2B4DE8 with sheen #96B0FF so it differs from the reference hue.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, boxes, bars, blur plates, tints. |
| Title block | Centred on x = 0.50W; width of the longest line = 0.70W [756]; lines stacked 1–3 high; every line centred; line pitch = 1.35 × cap height. |
| Caption | One centred line, no box. |

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Head lane (default) | Title block bottom edge ≈ 0.105H [202], above the speaker's hair line, top margin ≥ 0.02H, block height ≤ 0.084H; caption centre = block bottom + 24 px at 720 wide (0.019H), so the caption sits just under the block and never overlaps it | Speaker shots |
| Top lane | Block top = 0.06H [115], block grows downward | Shots with no face in the upper third  |
| Low lane | Block bottom = 0.90H [1728], block grows upward | Shots whose top half holds a face or subject  |
| Caption lane | Centre on the last title line's lower edge: last-line top + 0.92 × cap height (on speaker shots: last-line top + 1.05 × cap height, so the caption sits just under the block) | All caption words |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Fat high-contrast Didone capitals squeezed narrow (x-scale 0.60) so the letters read tall; thick stems, hairline serifs; all caps | Bodoni Moda Black (wght 900, opsz 11), squeezed to 60 % width | Playfair Display Black squeezed, Abril Fatface squeezed | Cap height from width: cap = 0.70W / (longest line letters × 0.69); measured cap 0.066–0.083H (reference), demo 0.046–0.092H. Speaker shots: whole block ≤ 0.084H. |
| Caption | Small bold transitional serif, lowercase or as written, tight word spacing | Gelasio Bold (Georgia-like) | Newsreader Bold, Tinos Bold | 0.047W [51] (reference ≈ 0.04W) |

Rules: titles are uppercase (user's words, case changed only here). Captions keep the user's case and punctuation. No italics, no outlines on the title, no rotation.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Title in / out | Hard cut | 1 f |
| Title swap | Hard cut, new block replaces old in the same frame | 0 f |
| Title sheen | Slow linear drift left to right, band width 0.16 of block width, 0.30 of block width per s  | continuous, loops |
| Caption word in | Words appear one at a time; alpha ramp ease-out cubic  | 2 f at 24 fps (0.083 s) |
| Caption chunk out | Hard cut | 1 f |
| Cuts | Plain hard cuts | 0 f |

Never: bounce, slides, typewriter letters, rotation, zoom, blur, glitch, flashes, extra colours, italics, outlined title.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text overlays and their soft shadows | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming, trimming, grading, blurring, zooming or masking footage; hiding it behind cards or bars. Primary footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Title block and caption stay above the hair line (face box top − 0.02H). If the face top is above 0.17H, shrink the block (budget 0.084H) or use a single line. |
| Non-face shots | Top lane; keep the block off hands, phone screens and text when a lane above 0.20H is free. |
| Face in the upper half of a non-speaker shot | Use the low lane. |
| Edges | Block and caption stay ≥ 0.04W from the left and right edges. |
| Overlap | The caption never overlaps the title block (the reference overlapped; the demo keeps them clear for legibility). |

---

## 7. MOMENT LIBRARY
Family codes: **T** title · **C** caption · **K** keyword · **X** cut treatment · **E** end.

### MOMENT T1 · STACKED TITLE CUT-IN
**What it is:** one to three lines of tall narrow serif capitals in the accent colour appear in a single frame above the speaker, hold with a drifting sheen, and vanish in a single frame.
**Use when:** the opening line, a topic word, each new step. **Avoid when:** within 3 f after a cut with a different title still running; two titles at once.
**Text:** 1–3 words taken from the user's own spoken words, uppercase, ≤ 3 lines, ≤ 12 letters per line. Words repeat from the captions (they are an emphasis layer).
**Geometry / Graphics:** 1.2, 1.4. Block width 0.70W for the longest line (cap = 0.70W/(letters × 0.69)); other lines share the same cap height and are centred.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 f | Title | alpha | 0 → 0.94 | hard cut |
| hold | Sheen | band x | −0.15 → 1.45 of block width at 0.30/s | linear  |
| end | Title | alpha | 0.94 → 0 | hard cut |

**Footage / plate behaviour:** untouched. **Captions during it:** C1 on the lane below.
**Exit:** hard cut, or hard swap to the next title (T3).
**Build notes:** render the line at 2× in the font, crop to glyph box, resize width × 0.60 × k and height × k; stack with pitch 1.2 × cap; paste into a full-frame mask once; per frame mix the accent and sheen colour by a Gaussian band over (x/w + 0.35·y/h), composite at 0.94 over a 35 % blurred shadow shifted +6 px.
**Flow prompt text:** "At {{TIME}} a block of {{LINE_COUNT}} line(s) of tall, narrow, high-contrast serif capitals in {{ACCENT_COLOUR}} reading {{WORDS}} appears instantly above the person's head, with a faint lighter sheen sliding slowly across the letters, then disappears instantly."
**Still-image state:** block above the head, full opacity, sheen mid-way.

### MOMENT T2 · ONE-LINE TITLE
**What it is:** the same title as a single wide line, used where the block budget is small (speaker shots with a high face).
**Use when:** 1–2 short words on a speaker shot, or a talking head with the face above 0.17H. **Avoid when:** more than 12 letters per line would push cap height below 0.040H.
**Text:** ≤ 14 characters including the space.
**Geometry / Graphics:** one line, width 0.70W, bottom 0.105H; cap ≈ 0.042H for 12 letters.
**Motion:** as T1. **Footage:** untouched. **Captions:** C1 below the line.
**Exit:** hard cut. **Build notes:** as T1, n = 1.
**Flow prompt text:** "At {{TIME}} one line of tall, narrow serif capitals in {{ACCENT_COLOUR}} reading {{WORDS}} appears instantly high above the person's head and disappears instantly."
**Still-image state:** as T1.

### MOMENT T3 · TITLE SWAP
**What it is:** one title is replaced by the next in the same frame, no gap.
**Use when:** a list, steps, or a run of topic words 1.1–1.8 s apart. **Avoid when:** the next word is under 1.0 s away (merge into one title).
**Text:** next block, same layout rules. **Motion:** both hard cuts on the same frame; the new block restarts the sheen.
**Footage:** untouched. **Exit:** the last title ends on a cut or a pause.
**Build notes:** switch the active title index; never overlap two titles.
**Flow prompt text:** "At {{TIME}} the title instantly swaps to {{WORDS}} in the same place and style, without any transition."
**Still-image state:** n/a.

### MOMENT T4 · LOW-LANE TITLE
**What it is:** the title block sits at the bottom, growing upward, when the upper half holds a face.
**Use when:** a shot has a face in the top 0.40H and the speaker is not the voice. **Avoid when:** the bottom lane has key footage text.
**Geometry:** block bottom 0.90H; max 3 lines. **Captions:** C1 on the last line's lower edge.
**Motion/Exit:** as T1. **Build notes:** top = 0.90H − block height.
**Flow prompt text:** "At {{TIME}} the title block of tall serif capitals reading {{WORDS}} appears instantly in the lower part of the frame and disappears instantly."
**Still-image state:** as T1, bottom lane.

### MOMENT T5 · SHEEN DRIFT
**What it is:** a soft diagonal pale band moving slowly across the title letters.
**Use when:** every title that holds > 0.8 s. **Avoid when:** never off (it is part of the look).
**Motion:** band centre from −0.15 to 1.45 × block width, 0.30 block widths per s, loops; band width 0.16, strength 0.65 toward the sheen colour.
**Build notes:** colour = accent × (1−b) + sheen × b, b = 0.65·exp(−((u−c)/0.16)²), u = x/w + 0.35·y/h.
**Flow prompt text:** "A faint lighter shimmer slowly sweeps across the title letters from left to right."
**Still-image state:** band near the middle.

### MOMENT C1 · STRADDLE CAPTION BUILD
**What it is:** a tiny bold white serif caption sits just under the title block and builds one word at a time.
**Use when:** all speech. **Avoid when:** a chunk would run longer than 1.6 s or cross a cut.
**Text:** the user's words exactly (case and punctuation as written); chunk 2–5 words; split at punctuation; never end on an article, preposition or conjunction; start = first word, end = min(last word end + 0.1, next start − 0.05) and before the next cut.
**Geometry / Graphics:** 1.4 caption; one line centred at x = 0.50W; centre on the last title line's lower edge (1.3). Each word is laid out in its final place before it appears; nothing moves.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | Word | alpha | 0 → 1 | ease-out cubic, 2 f  |
| chunk end | Whole chunk | alpha | 1 → 0 | hard cut |

**Footage:** untouched. **Exit:** hard cut.
**Build notes:** pre-render every word (shadow, 1.5 px ink outline, white fill) at 2×, downscale; keep the same lane for the whole shot even when no title is up.
**Flow prompt text:** "Small bold white serif captions appear one word at a time, centred just under the big title, with a thin dark outline and soft shadow; each caption line vanishes when the next begins. The caption words are: {{CAPTION_TEXT}}."
**Still-image state:** full chunk visible.

### MOMENT C2 · BARE CAPTION
**What it is:** the C1 caption with no title above it, in the same lane.
**Use when:** between titles, or a shot where a title would hide the subject. **Avoid when:** it lasts more than 2.5 s with no title nearby.
**Text/Motion/Build:** as C1; lane = the shot's last title lane, or the head lane.
**Flow prompt text:** "Small bold white serif captions appear one word at a time in the same spot, with no title above them: {{CAPTION_TEXT}}."
**Still-image state:** as C1.

### MOMENT K1 · SOLO KEYWORD TITLE
**What it is:** one single word at the largest allowed size (cap = 0.70W / (letters × 0.69), single line) for the payoff or a number.
**Use when:** a one-word payoff, an amount, a year. **Avoid when:** more than 1× in 6 s.
**Text:** one word ≤ 9 letters, uppercase. **Motion/Exit:** as T1. **Captions:** C1 beneath.
**Flow prompt text:** "At {{TIME}} one very large tall serif word {{WORD}} appears instantly above the person and disappears instantly."
**Still-image state:** as T2.

### MOMENT X1 · CUT BEAT
**What it is:** every footage cut gets a text beat: the title and caption chunk end on the cut frame (or just before), and the new shot's title starts 0.0–0.2 s after it with the new lane.
**Use when:** every cut. **Avoid when:** a title would start within 3 f after a cut while another is still running.
**Motion:** hard cuts only; lane switches on the cut frame. **Build notes:** assign a lane per shot; titles never cross a cut.
**Flow prompt text:** "At each shot change the on-screen words end and the next words begin, with plain hard cuts and no effects."
**Still-image state:** n/a.

### MOMENT E1 · QUIET CLOSE
**What it is:** the last 0.2–0.5 s keeps the final caption chunk only; the title ends first.
**Use when:** every ending. **Avoid when:** never.
**Motion:** hard cut off. **Flow prompt text:** "The big title disappears a moment before the end; only the small caption remains until the last word."
**Still-image state:** caption only.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T2 or T1 + C1 | X1 + T1/T3 per step, T4 for a face shot | T1 + C1, E1 |
| Single talking head | T2 + C1 | T3 swaps every 1.4–1.8 s, C2 between | K1 + E1 |
| B-roll only | T1 + C1 | X1 per cut, T3 | E1 |
| Still image | T1 (settled) + C1 | n/a | n/a |

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
