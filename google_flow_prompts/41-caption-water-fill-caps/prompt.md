# Google Flow prompt · Water Fill Caps
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Water Fill Caps" caption style to it.

The look in one sentence: Small ultra-bold white lead-in words under the face that land on one giant keyword filled with a blue water texture.

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
| Lead white | #FFFFFF | Small lead-in words |
| Water deep | #163045 | Darkest patches inside the keyword fill |
| Water mid-dark | #376881 | Fill gradient stop (55,104,129) |
| Water mid | #7BA0BE | Fill gradient stop, median of the reference fill (123,160,190) |
| Water light | #BED5E8 | Fill gradient stop (190,213,232) |
| Water pale | #D5E9FA | Lightest streaks (213,233,250) |
| Text shadow | #000000 at 55 % | Soft shadow under every caption glyph |

Brand-swap rule: if the user gives a brand colour, rebuild the water fill as a 5-stop ramp from a very dark to a very light tint of that colour. White stays white. No other colours exist.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, boxes, plates, borders, masks, blur or colour overlays. |
| Caption block | Text only, centred on x = 0.50W. Lead-in lane and keyword lane per 1.3. |
| Water fill | A single texture, 4 soft cloud-like blobs of dark and light blue across the full frame (noise scales 0.22W, 0.10W, 0.04W; weights 0.5, 0.35, 0.15; contrast stretched ×1.8), mapped through the 5 palette stops. Fixed in screen space, never animated, so each keyword shows a different slice of it. Render it once. |

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Lead-in lane | last baseline 0.545H [1046]; line pitch 0.056H [108]; max 2 lines; max line width 0.84W | Small white words, stacked upward from the last baseline |
| Keyword lane | baseline 0.685H [1315]; x-height top ≈ 0.58H; width up to 0.92W; centred on x = 0.50W | Giant keyword |
| Reference values | lead-in last baseline ≈ 0.50–0.53H, keyword baseline ≈ 0.65H, keyword width 0.88–0.93W | Measured on the reference |

Both lanes sit in the lower middle, below the chin of a centred speaker.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Lead-in | Ultra-heavy grotesque, mixed case as written, tight spacing, white, soft shadow | Archivo (variable) weight 900, width 100 | Archivo Black, Montserrat Black, Inter ExtraBold | 0.095W [103]; line height 0.056H |
| Giant keyword | Same family, wider and heavier, filled with the water texture, soft shadow | Archivo weight 900, width 108 | Archivo Black, Montserrat Black | fit to 0.92W, capped at 0.34W [367]; shrink font until the word fits |
| Title (T1) | Giant keyword style, stacked | as above | as above | each line fit to 0.86W, cap 0.30W |

Rules: case exactly as the user wrote it (no forced uppercase). Punctuation stays attached to its word and is filled too. No outlines, no italics, no rotation.

Text shadow: (0, +3 px, blur 7 px, #000000 at 55 %), drawn at 2× then downscaled.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Lead-in word entrance | alpha ramp, ease-out (1−(1−t)³), no movement | 0.10 s |
| Keyword entrance | same ramp, 0.10 s, no movement | 0.10 s |
| Chunk exit | hard cut, whole chunk gone in one frame | 1 f |
| Cuts | hard cut; the new chunk starts on the cut | 0 f |
| Footage push (M1) | linear scale | across the shot |

Words appear one by one at their spoken time and never move once placed (the full chunk is laid out first). Never: bounce, overshoot, slides, typewriter letters, rotation, outlines, flashes, wipes, colour changes of a word after it appears.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Slow push-in about the face or subject (M1) | Total scale ≤ 1.15 per shot; reset at the next cut |
| Text and shadow overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; black or colour walls that hide the footage; text-shaped windows that replace the picture; speed ramps; freezing; blur, glitch, warp, colour grading; adding footage the user did not supply. The primary footage plays live, in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. The first lead-in line top (last baseline − (lines−1) × 0.056H − 0.07H) must sit ≥ 0.01H below the chin. If it does not, move both lanes down by up to 0.06H; if still blocked, drop the lead-in to one line. |
| Keyword lane | Keep the baseline ≤ 0.90H. If a face sits low (chin below 0.58H), put the lead-in above the face only if it clears the hair line; otherwise skip the lead-in and use K1 in the free lane. |
| Footage text (UI, signs) | If readable text sits in a lane for more than 1 s, shift both lanes by up to 0.10H. |
| Edges | Every glyph stays ≥ 0.04W from the left and right edges. |

---

## 7. MOMENT LIBRARY
Family codes: **C** caption · **K** keyword · **T** title · **X** cut treatment · **M** footage motion · **E** ending.

### MOMENT C1 · LEAD-IN + GIANT KEYWORD
**What it is:** a phrase builds in two layers. Small white heavy words pop in one by one under the face, then the last meaning word lands below them as a giant water-filled word. The whole chunk is replaced at once by the next.
**Use when:** always, on any shot with speech or phrases. **Avoid when:** the keyword is longer than 14 characters and would shrink under 0.12W (use C2).
**Text:** the user's exact words, case as written. Chunk = 1–4 lead-in words + 1 keyword (a keyword may carry trailing punctuation). Split at punctuation and natural phrases; never end the lead-in on an article, preposition or conjunction when the keyword could not follow it; the keyword is the strongest noun, verb or number of the chunk and is usually the last word. Chunk length 0.8–2.0 s.
**Geometry / Graphics:** lead-in lane and keyword lane (1.3). Lead-in wraps balanced into at most 2 lines if the single line exceeds 0.84W; lines are centred on x = 0.50W and stack upward from the last baseline. Keyword fits 0.92W, cap 0.34W.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | lead-in word | alpha | 0 → 1 | ease-out, 0.10 s |
| keyword start | keyword | alpha | 0 → 1 | ease-out, 0.10 s |
| chunk end | all words | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Word start = the word's spoken start time. Chunk end = the next chunk's start, or min(last word end + 0.4 s, next cut), or end − 0.25 s for the last chunk.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system.
**Exit:** hard cut.
**Flow prompt text:** "In the lower middle of the frame, captions build up in two layers. Small, very bold white words appear one by one under the speaker's chin, and then the key word, {{KEYWORD}}, appears below them very large in chunky lettering filled with a blue water texture of pale and deep blue, almost as wide as the frame. When the phrase is done it is replaced at once by the next one. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### MOMENT K1 · SOLO GIANT KEYWORD
**What it is:** one payoff word alone in the keyword lane, no lead-in.
**Use when:** a strong turn or payoff word, a number, or a one- or two-word sentence ("more.", "never", "free"); also when a chunk's lead-in was spoken before a cut and only the keyword remains. **Avoid when:** more than 2 per 5 s.
**Text:** one user word (with its punctuation), case as written.
**Geometry / Graphics:** keyword lane; font fit 0.92W, cap 0.34W; same fill and shadow.
**Motion:** C1 keyword entrance (0.10 s alpha ramp); hold 0.4–1.5 s; hard cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the normal chunk.
**Exit:** hard cut.
**Build notes:** C1 renderer with an empty lead-in.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in the lower middle of the frame, very large, in chunky lettering filled with a blue water texture, fading in quickly, then is replaced by the next caption."
**Still-image state:** the word.

### MOMENT C2 · PLAIN WHITE STACK
**What it is:** a chunk with only small white lead-in words, for phrases with no strong keyword or a keyword too long for the giant lane.
**Use when:** connective phrases, long words (> 14 characters), or when C1 would repeat more than 3 times in a row. **Avoid when:** it is the only mode used in a video.
**Text:** 2–6 user words, ≤ 2 lines.
**Geometry / Graphics:** lead-in lane (1.3), font 0.095W, last baseline 0.545H (shift per 1.7).
**Motion:** word-by-word ease-out ramps (0.10 s), hard cut out.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** C1 renderer with no keyword.
**Flow prompt text:** "In the lower middle of the frame, a short phrase, {{PHRASE}}, builds word by word in small, very bold white lettering, then is replaced at once by the next phrase."
**Still-image state:** the phrase.

### MOMENT T1 · STACKED WATER TITLE
**What it is:** a one- to three-word title stacked on separate lines, every word in the giant water-fill type, popping in line by line.
**Use when:** the opening line names the topic and the first 1.0 s has room (a speaker with the face high, or B-roll). **Avoid when:** the face box would be covered (use C1 instead), or within 0.3 s after a cut.
**Text:** 1–3 of the user's own words, as written, max 20 characters in total.
**Geometry / Graphics:** lines fit 0.86W (cap 0.30W), line pitch 0.14H, last baseline 0.685H, centred; water fill and shadow as 1.1/1.4. It replaces the C1 chunk for its duration.
**Motion:** each line alpha 0 → 1 over 0.10 s, lines 0.15–0.25 s apart; hold 0.8–1.4 s; hard cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** none; the title is the caption for those words (they are removed from the next chunk, caption audit counts them).
**Exit:** hard cut.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, appears in the lower middle of the frame with each word on its own line, in very large chunky lettering filled with a blue water texture, each line fading in quickly one after another, then it is replaced by the captions."
**Still-image state:** full title.

### MOMENT X1 · CUT RESET
**What it is:** the shot changes with a plain hard cut and the caption chunk changes on the same frame.
**Use when:** every footage cut. **Avoid when:** never; add no effect.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:** at the cut frame the running chunk ends and the next chunk starts; if speech continues over the cut, the new chunk starts with the next unspoken word. If only the keyword of the old chunk remains unspoken, use K1.

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut | caption chunk | old chunk → new chunk | same frame | hard cut |

**Footage / plate behaviour:** untouched; no flash, blur or zoom.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** split chunks at cut times and set the chunk start to max(first word start, cut time).
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the caption on screen is replaced in the same moment by the next caption."
**Still-image state:** none.

### MOMENT M1 · SLOW PUSH
**What it is:** a gentle push-in on a long static shot (the reference slowly zooms into the speaker during its last seconds).
**Use when:** a shot longer than 2 s with little motion, or the last shot. **Avoid when:** the footage already moves a lot.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:** scale ×1.00 → ×1.10 across the shot (linear, max 1.15), about the face box centre; reset at the next cut. Captions do not scale.
**Footage / plate behaviour:** live footage, scaled only.
**Captions during it:** unaffected.
**Exit:** reset by the cut.
**Build notes:** `Image.resize(..., box=floats)` about the anchor; clamp the crop box.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### MOMENT E1 · END HOLD
**What it is:** the last chunk stays until just before the end, then the picture finishes clean.
**Use when:** every video.
**Text:** the last chunk's words.
**Geometry / Graphics:** C1 or K1.
**Motion:** hold to min(last word end + 0.4 s, end − 0.25 s); the final 0.25 s has no caption.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 (or T1 if the face is high and the first line names the topic) | X1 on every cut; C1 per phrase; K1 on a payoff or one-word sentence; C2 for connective phrases | C1 + E1 |
| Single talking head, no cuts | C1 | K1 on one payoff word; C2 between; M1 on a shot > 2 s | E1 |
| B-roll only, no speech | T1 (user's own words) | X1 on every cut; C1 or K1 phrases of 1.0–2.0 s | E1 |
| Still image + text | C1 in its settled state | — | — |

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
