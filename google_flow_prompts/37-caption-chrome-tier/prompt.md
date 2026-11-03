# Google Flow prompt · Chrome Tier
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Chrome Tier" caption style to it.

The look in one sentence: Small thin white words plus huge heavy italic keywords with a glossy teal-silver chrome fill, stacking in a zigzag down the lower frame.

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
| Small word | #FFFFFF | Connecting words (tier 1) |
| Chrome dark | #2E4240 | Left and right ends of the keyword gradient, keyword edge ink #18262A |
| Chrome mid | #96B8C0 | Quarter points of the gradient |
| Chrome light | #EEF6F7 | Bright band at 55 % of the keyword width |
| Chrome low | #78A0AA | 80 % point, then back to Chrome dark |
| Shadow | #000000 | Soft shadow under every word |

Brand-swap rule: if the user gives a brand colour, tint the chrome mid and low stops towards it; keep the light band near white and the ends dark. Never change the white small words.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, untouched. No cards, boxes, plates, borders, masks, blur or dimming. |
| Text block | A stack of 1–3 lines, no background shape. Block width ≤ 0.86W. Left, right or centre aligned. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Lower lane | 0.07, 0.56, 0.93, 0.84; first baseline 0.655H | Default for every chunk |
| Top lane | 0.07, 0.03, 0.93, 0.15; baseline 0.115H | One-line chunks only (T1), when the face box top is ≥ 0.15H |
| Side margin | 0.07W each side | Left edge of a left stack, right edge of a right stack |
| Line indent | odd lines shift 0.05W towards the centre | The staggered "stair" |
| Line pitch | 0.20W if the next line holds a keyword; 0.17W after a line with a keyword; 0.105W for small-only lines | Between baselines |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Small word | Light-to-regular grotesk, mixed case as written, very tight spacing | Inter, weight 380 | Inter Tight Regular, Manrope Medium | 0.092W [99]; letter-spacing −0.035em; word gap 0.22 × size |
| Keyword | Black-weight italic grotesk, mixed case as written, chrome gradient fill, 3 px dark edge at 2× | Inter Tight Black Italic | Archivo ExtraBold Italic, Barlow ExtraBold Italic | 0.21W [227]; letter-spacing −0.02em; shrink ×0.94 steps down to 0.10W until the word fits ≤ 0.86W |
| Keyword gradient | Horizontal: 0 % #2E4240, 38 % #96B8C0, 55 % #EEF6F7, 80 % #78A0AA, 100 % #344A4C; plus a soft horizontal highlight band at 42 % of the height (+30 levels) | — | — | per word |
| Top-lane sizes | small 0.085 × and keyword 0.78 × the lower-lane sizes | — | — | — |

Font note: identified by letterform (tight neo-grotesk light for small words, heavy slanted grotesk with chrome shading for keywords). Check against the reference crops; fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Rules: text case exactly as the user wrote it. No outline-only text. Nothing rotated. Every word keeps the shadow (0, +6 px at 1×, Gaussian blur 7 px at 2×, #000000 at 100 % doubled for small words; keyword shadow 59 %, blur 10 px, offset +4 px).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Small word entrance | ease-out alpha ramp (cubic), no movement | 0.17 s (4 f) |
| Keyword entrance | ease-out alpha ramp + settle from 1.07× to 1.00× about its centre | 0.17 s (4 f) alpha, 0.25 s (6 f) settle |
| Chunk exit when the next chunk starts within 0.1 s | hard cut in the same frame | 1 f |
| Chunk exit otherwise | linear alpha fade | 0.125 s (3 f) |
| Cuts | footage cuts plainly; the caption carries on across the cut unchanged | 0 f |

Words never move once visible: the whole chunk is laid out before its first word appears. Never: bounce, overshoot, slides, typewriter letters, rotation, blur on the text, flashes, colour changes after appearing.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text and shadow overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; blur, dimming, grading or filters; cards, split screens, background swaps, blur pulls, graphic transitions; adding footage the user did not supply. The footage plays live in sync with the audio at all times.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Lower lane is used when the face box bottom edge is ≤ 0.56H. If the face sits lower, mirror to the top lane for one-line chunks, or shift the stack so the first baseline is ≥ 0.03H under the chin and the last baseline ≤ 0.88H. |
| Top lane | Allowed only if the glyph bottoms (including descenders) stay ≥ 0.02H above the face box top and the face box top ≥ 0.15H. |
| Footage text (signs, UI) | If readable footage text sits in the lane for more than 1 s, flip the stack to the other lane, or change the alignment side. |
| Edges | Every glyph ≥ 0.07W from the left and right edges. |
| Bright footage | White small words and a pale chrome fill lose contrast on bright, flat footage. Keep the shadow and the dark edge as written; if still weak, move the stack onto the darker half (C3). |

---

## 7. MOMENT LIBRARY
Family codes: **C** caption · **T** title/headline · **K** keyword · **X** cut treatment · **E** ending.

### MOMENT C1 · TIERED LINE
**What it is:** a phrase builds word by word in the lower lane. Small light white words and heavy chrome keywords share one baseline, each new word fading in where it will stay; the next phrase replaces the block.
**Use when:** always, on every kind of shot. **Avoid when:** never; use C3 to protect a face or footage text.
**Text:** the user's exact words, case as written. Chunks of 2–5 words; split at punctuation and natural phrases; never end a chunk on an article, preposition or conjunction where avoidable; 0.6–1.7 s per chunk. Keywords: exactly one per chunk (a second only in K3), the most meaning-carrying noun, verb or number; never an article or preposition.
**Geometry / Graphics:** Lower lane, first baseline 0.655H. Small words and the keyword share a baseline on a line while the line fits ≤ 0.86W; a small word that follows a keyword starts a new line; a keyword that does not fit starts a new line. Odd lines indent 0.05W. Pitches per 1.3. Alignment left or right (C2 alternates it).
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | small word | alpha | 0 → 1 | ease-out, 4 f |
| word start | keyword | alpha, scale | 0 → 1, 1.07 → 1.00 | ease-out, 4 f / 6 f |
| chunk end | all words | alpha | 1 → 0 | hard cut at the next chunk's first word, else 3 f fade |

Word start = the word's spoken start time. Chunk end = the next chunk's first word start, or min(last word end + 0.4 s, next cut + 0.2 s, video end − 0.25 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system.
**Exit:** per the table.
**Flow prompt text:** "In the lower part of the frame, captions build up word by word. Ordinary words are small, thin and white. The important word, {{KEYWORD}}, is large, heavy and slanted, filled with a glossy teal and silver metal shine, and sits on the same line or steps down onto its own line. Each word fades in softly in place and the phrase is replaced by the next. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### MOMENT K1 · CHROME KEYWORD
**What it is:** the keyword's material: black italic letters with a teal-silver chrome gradient, a dark edge and a soft shadow, settling in from slightly oversized.
**Use when:** inside every C1 chunk. **Avoid when:** the word is longer than 14 characters (it will shrink; if it falls under 0.10W, set it as a small word).
**Text:** one user word, case as written.
**Geometry / Graphics:** Keyword type per 1.4: gradient stops, 3 px edge in #18262A at 2× (alpha 90 %), shadow offset +8 px at 2×, blur 10 px.
**Motion:** per C1 keyword row.
**Footage / plate behaviour:** untouched.
**Captions during it:** part of the chunk.
**Exit:** with the chunk.
**Flow prompt text:** "The keyword {{KEYWORD}} is drawn in large heavy slanted letters with a glossy blue-grey and silver metallic gradient, a thin dark outline and a soft shadow."
**Still-image state:** the finished word.

### MOMENT T1 · OPENER HEADLINE
**What it is:** the first two words of the video as a single compact line in the top lane, small word plus chrome keyword, appearing as the speaker starts.
**Use when:** the video opens on a speaker or calm shot with the face box top ≥ 0.15H. **Avoid when:** the face box top is above 0.15H, or the first words need two lines (use C1 in the lower lane).
**Text:** the user's first 2–3 words, the last one the keyword. Max 16 characters.
**Geometry / Graphics:** Top lane, baseline 0.115H, left aligned at 0.07W; small word 0.085 × and keyword 0.78 × the lower-lane sizes; one line only.
**Motion:** per C1 (word starts at the spoken times, ≥ 0.25 s apart); holds until the next chunk starts.
**Footage / plate behaviour:** untouched.
**Captions during it:** none other.
**Exit:** hard cut to the C1 chunk.
**Build notes:** same renderer as C1 with the lane parameter set to top.
**Flow prompt text:** "At the very start, in the top-left of the frame, a short opening line appears: a small white word followed by {{KEYWORD}} in large glossy metallic slanted lettering. It stays clear of the face."
**Still-image state:** final state.

### MOMENT C2 · MIRROR STACK
**What it is:** consecutive chunks alternate between a left-hand stack and a right-hand stack so the block seems to zigzag down the frame.
**Use when:** two or more chunks in a row in the lower lane. **Avoid when:** a face or footage text sits on the chosen side (use the other side).
**Text:** as C1. **Side:** left or right per chunk, alternating by default.
**Geometry / Graphics:** C1 geometry; right alignment puts each line's right edge on 0.93W (minus the line indent).
**Motion:** as C1; the side flips on chunk boundaries only.
**Footage / plate behaviour:** untouched. **Captions during it:** this is the caption.
**Exit:** as C1.
**Build notes:** the alignment is a per-chunk parameter.
**Flow prompt text:** "Caption blocks alternate sides: one hugs the left side of the lower frame, the next hugs the right side, each built word by word."
**Still-image state:** one chunk.

### MOMENT K2 · SOLO CHROME WORD
**What it is:** one payoff word alone, chrome, at 1.3× keyword size.
**Use when:** a strong turn or payoff word, a number or a name. **Avoid when:** the word is longer than 9 characters; max 2 per video, ≥ 3 s apart.
**Text:** one user word, case as written.
**Geometry / Graphics:** Keyword style at 0.27W, left or right aligned per C2, baseline 0.66H, shrink to fit 0.86W.
**Motion:** keyword entrance; hold 0.5–0.9 s; hard cut to the next chunk.
**Footage / plate behaviour:** untouched. **Captions during it:** replaces the normal chunk.
**Exit:** hard cut.
**Build notes:** scale the font size, not the bitmap.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in the lower frame in very large glossy metallic slanted letters, then is replaced by the next caption."
**Still-image state:** the word.

### MOMENT K3 · KEYWORD PAIR
**What it is:** a chunk with two chrome keywords, each starting its own line, small words in between.
**Use when:** a contrast or a two-part idea ("more … less"). **Avoid when:** more than 2 per video.
**Text:** 4–6 user words, two of them keywords.
**Geometry / Graphics:** C1 geometry, up to 3 lines; the second line indents 0.05W.
**Motion:** as C1. **Footage / plate behaviour:** untouched. **Captions during it:** this is the caption.
**Exit:** as C1. **Build notes:** as C1.
**Flow prompt text:** "A caption with two heavy metallic slanted words, {{KEYWORD_1}} and {{KEYWORD_2}}, each on its own line, with small white words between them."
**Still-image state:** the chunk.

### MOMENT C3 · LANE GUARD
**What it is:** the placement rule that keeps captions off faces and footage text: lane, side and size are adapted per shot.
**Use when:** a face or readable footage text sits in the lower lane, or the footage is bright and flat. **Avoid when:** the default lane is clear.
**Text:** none.
**Geometry / Graphics:** options in order: switch side; move the stack so the first baseline is ≥ 0.03H under the chin; use the top lane for a one-line chunk; shrink keywords to ≥ 0.15W.
**Motion:** none; applied before the chunk starts.
**Footage / plate behaviour:** untouched. **Captions during it:** as chosen.
**Exit:** none. **Build notes:** compute from the scene table's face boxes.
**Flow prompt text:** "The captions sit in whichever part of the frame keeps the speaker's face and any readable text clear."
**Still-image state:** none.

### MOMENT X1 · CUT CARRY
**What it is:** the footage cuts plainly and the caption carries across the cut without moving, so the text becomes the thread between shots.
**Use when:** every footage cut. **Avoid when:** a chunk is wholly in a lane that the new shot's subject occupies (apply C3 on the cut frame).
**Text:** none. **Geometry / Graphics:** none.
**Motion:** no change at the cut; a chunk boundary within ±0.15 s of a cut is moved onto the cut frame.
**Footage / plate behaviour:** untouched; no flash, blur or zoom.
**Captions during it:** unchanged.
**Exit:** none. **Build notes:** snap chunk starts to cuts when within 0.15 s.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the caption words stay exactly where they are."
**Still-image state:** none.

### MOMENT T2 · SECTION HEADLINE
**What it is:** a later chunk set as a one-line headline in the top lane for a new topic.
**Use when:** a new topic word, ≥ 3 s after T1 and the face box top ≥ 0.15H. **Avoid when:** the video is shorter than 6 s.
**Text:** 2–3 user words, last one the keyword, max 16 characters.
**Geometry / Graphics:** as T1, side left or right.
**Motion:** as T1. **Footage / plate behaviour:** untouched. **Captions during it:** none other.
**Exit:** hard cut to the next chunk. **Build notes:** reuse T1.
**Flow prompt text:** "Later, a short headline appears at the top of the frame: a small white word and {{KEYWORD}} in large glossy metallic slanted letters."
**Still-image state:** final state.

### MOMENT E1 · END HOLD
**What it is:** the last chunk holds to just before the end and the picture finishes clean.
**Use when:** every video. **Avoid when:** never.
**Text:** the last chunk's words.
**Geometry / Graphics:** C1 lower lane.
**Motion:** holds to min(last word end + 0.4 s, end − 0.25 s), then a 3 f fade; the last 0.25 s has no caption.
**Footage / plate behaviour:** untouched. **Captions during it:** per above.
**Exit:** video ends. **Build notes:** none beyond C1.
**Flow prompt text:** "The last caption stays until just before the end, then fades and the picture finishes clean."
**Still-image state:** final chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 | C1 with C2 side flips, X1 on every cut, K3 on a contrast, C3 where a face or text blocks the lane | E1 |
| Single talking head, no cuts | T1 + C1 | C2 side flips, K2 on one payoff word, T2 at a new topic | E1 |
| B-roll only, no speech | C1 phrases of 1.0–2.5 s | X1, C2, C3 | E1 |
| Still image + text | C1 chunk in its settled state | — | — |

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
