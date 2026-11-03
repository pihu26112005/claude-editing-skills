# Google Flow prompt · iOS Widgets
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "iOS Widgets" motion style to it.

The look in one sentence: Frosted home-screen widgets drop into the corners with a step counter, a cursor clicks blue check pills for each step, and a Follow card and glass capsule close the clip.

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

| Role | Value | Used for |
|---|---|---|
| System blue | #256BFD | Check pills, caption keyword pill |
| Glass | white 22 % tint over the blurred footage, backdrop darkened up to 20 % on bright footage, saturation ×1.4 | Widgets, closer capsule |
| Glass rim | white 45 %, 1.6 px | Edge of every glass panel |
| Glass sheen | white, 0 → 11 % over the top 55 % of the panel | Top highlight |
| Card white | white 80 % over the blurred footage | Follow card |
| Ink | #17171F | Dark text on white pills and the card |
| Follow button | #4F46E5 solid, white text (state "Follow") → #E4E4FF with #584EEE text (state "Following") | F1 |
| Closer tint | #FFD6B0 → #F0C0D0 left to right | Last word of the capsule |
| Cursor | near-black #0E0E12 arrow with a white 2 px outline | K1, F1 |
| Text white | #FFFFFF | Widget text, captions |

Brand-swap rule: replace System blue and Follow button with the user's brand colour (keep it saturated and dark enough for white text). Glass, white and ink never change.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, live and untouched. No cards around it, masks or colour overlays. Glass panels blur only the footage under themselves. |
| Counter widget | 208 × 236 [measured on the reference: 242 × 300 of 720×1280], corner radius 40, glass |
| Progress widget | 208 × 112–124, radius 34, glass |
| Follow card | 380 × 112 (600 with a user handle) [reference 624 × 116 with name], radius 40, white glass, centred on x = 0.50W |
| Closer capsule | text width + 76 × 88, fully round, glass |
| Check pill | height 62 [measured 58], fully round, width = text + 82 |
| Panel shadow | black 20 %, blur 11 px, offset 8 px down |
| Pill shadow | black 28 %, blur 7 px, offset 4 px down |
| Crop | Cover-fit only when the source is not 9:16. Anchor = the speaker's face box. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Widget left | 0.033, 0.084, 0.322, 0.268 [24,108,232,344] | Counter widget (default) |
| Widget right | 0.678, 0.084, 0.967, 0.172 (progress) or 0.268 (counter) | Progress widget (default), or counter widget on swap |
| Pill field | y 0.60–0.74, x 0.12–0.88 | Check pills, scattered: centres at (0.30, 0.615), (0.62, 0.668), (0.36, 0.722) |
| Caption lane | centre y = 0.83H [1062], max width 0.84W | C1 captions |
| Closer capsule | centre y = 0.745H | E1 |
| Follow card | centre y = 0.885H [1133] | F1 |

Face rule: widgets keep x ≤ 0.322W on the left and ≥ 0.678W on the right so they never reach a face box of x 0.34–0.66.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Progress header | semibold, white 94 %, auto-fit to width 146 | Inter 680 | Manrope, DM Sans | 21 down to 14 |
| Counter | bold, white, centred in the widget | Inter 760 | Manrope ExtraBold | 92 down to 40 |
| Check pill text | bold | Inter 700 | Manrope | 27 |
| Caption | bold, white, sentence case as written, soft shadow, centred | Inter 740 | Plus Jakarta Sans, Manrope | 54, line pitch 70, word gap 0.27em |
| Caption keyword | same, inside a blue pill, pill pad 15 left/right | Inter 740 | same | 54 |
| Capsule text | bold | Inter 740 | same | 44 |
| Card button | 720 | Inter | Manrope | 24 |

Rules: text case exactly as the user wrote it. Widget, pill and capsule text is a complete phrase copied as-is from the user's captions, or a counter numeral. UI labels "Follow" and "Following" are the only other words, and only inside F1. Never assemble a label from scattered words.

### 1.5 Motion language

- Entrances: overshoot ease (back, overshoot 1.2–1.8) with a scale from 0.55–0.90 to 1. Exits: ease-out cubic, scale 0.92–0.94 and a short upward drift.
- Idle: every glass panel and pill floats ±2.5–3 px on a sine of 2.4–2.6 s, each with its own phase (M1).
- Cursor: smooth ease-in-out path with a slight arc, click dip 0.86 scale for 0.16 s.
- Click: press dip 5 %, state change in ≤ 0.05 s, pop to 1.10 and back over 0.5 s, white ripple ring growing 8 → 38 px over 0.45 s.
- Never: slides across the whole frame, wipes, flashes, shake, glitch, rotation, extra colours, blur or zoom of the footage.

### 1.6 What may happen to the user's footage

Allowed: full-frame display; glass panels, pills, capsule, card and cursor drawn over it; the panels blur and tint the footage only inside their own shape. Forbidden: replacing or regenerating anything, grading, speed change, trimming, reordering, blur or zoom of the footage outside a panel. Avatar thumbnails inside widgets or the card are a still crop of the user's own speaker (never another person).

### 1.7 Safe zones

- Face box never covered while speaking. Corner widgets stay outside x 0.34–0.66.
- Pill field and captions sit in the lower half; on shots where the face is low (face bottom > 0.55H) move the pill field up to y 0.45–0.58 and keep the caption lane below the face.
- Footage text (a phone screen, a sign) may be covered by a pill for the length of one pill only.

---

## 7. MOMENT LIBRARY
Families: T title/tile, W widget, K check, F follow, E end, C caption, M motion. Energy: low / mid / high.

### T1 · WIDGET STACK DROP — T high (signature opener)
**What it is:** a step-counter glass widget on the left and a progress widget on the right drop in at the top corners and float.
**Use when:** the opening line, from 0.3 s. **Avoid when:** the face box reaches the top corners.
**Text:** big widget = a step counter "0/N" (N = number of list steps in the script; numerals allowed for counters), or a real number the user wrote, otherwise drop the big widget. No header, no sub. Progress widget header = one complete phrase copied as-is from the captions (e.g. a full noun phrase or step), never assembled from scattered words.
**Geometry / Graphics:** counter widget at Widget left (208×236, radius 40); progress widget at Widget right (208×112, radius 34); glass per 1.1; a small white dot icon (r 7) before each header.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.30 s (big), 0.40 s (progress) | panel | y offset, scale, alpha | −56 px, 0.88, 0 → 0, 1.0, 1 over 0.6 s (alpha over 0.2 s) | back 1.3 |
| after landing | panel | idle float | ±3 px, 2.4 s sine | M1 |
| 1.58–1.82 s (or before the next cut) | panel | exit | scale 0.94, −18 px, alpha 1 → 0 over 0.24 s | ease-out cubic |

**Footage:** untouched. **Captions during it:** C1 in the lane. **Exit:** before the next cut (never across a cut).
**Build notes:** blur the whole frame once per frame (Gaussian σ 14) and composite it inside each panel mask; draw masks at 3× and downscale.
**Flow prompt text:** "Two frosted glass home-screen widgets drop softly into the top corners of the frame, one with the step count {{COUNT}} in large bold white letters, one with the words {{PHRASE}} above a thin progress bar that fills while the speaker says them. They float gently and fade out before the next shot. The person is not covered."
**Still-image state:** both widgets settled, bar full.

### T2 · WIDGET SWAP — T mid (extension in the same grammar)
**What it is:** the counter widget returns later with a new word, on the side that is empty in the current shot.
**Use when:** a new topic or a B-roll shot with free corner space. **Avoid when:** within 0.3 s after a cut.
**Text:** counter as in T1, normally "N/N" (all steps done) or the next count; no header or sub.
**Geometry:** counter widget at Widget right (x 488, y 108). **Motion:** as T1 big widget, enter 0.32 s after the shot starts, exit 0.24 s before the next cut. **Footage:** untouched.
**Flow prompt text:** "A single frosted glass widget drops into the top {{SIDE}} corner showing the step count {{COUNT}} in large bold white letters, floats, then leaves before the next shot."

### W2 · PROGRESS FILL — W mid (signature detail of T1)
**What it is:** the progress widget's white bar fills while the user says its phrase.
**Motion:** bar 0 → 100 % over 0.9 s starting 0.25 s before the phrase, ease in-out; track white 31 %, fill white, height 14, round ends, 20 px side padding. No percentage text.
**Use when:** a phrase about growth, effort, time or "more". **Flow prompt text:** "A thin white progress bar inside a glass widget fills smoothly from empty to full."

### K1 · CHECK PILLS — K high (signature)
**What it is:** one blue pill per spoken step. It lands unchecked (white, empty ring), a mouse cursor glides in and clicks it, it turns blue with a tick and stays until the next cut.
**Use when:** lists, steps, 2–3 parallel phrases, "first / then / finally". Also single claims worth a tick. **Avoid when:** more than 3 pills in one shot.
**Text:** 2–4 user words per pill, taken in order.
**Geometry:** pill height 62 [measured 58], fully round; text Inter 700 27, left pad 26, gap 12, icon 22 (empty ring 20 px, 2.6 px grey; tick white 3.6 px stroke), right pad 22; unchecked fill white 92 %, ink text; checked fill System blue, white text. Positions: the pill field in 1.3. Cursor arrow 34×48 sprite, tip on the icon.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | pill | scale, alpha | 0.55, 0 → 1, 1 over 0.42 s | back 1.6 |
| −0.65 s before click | cursor | position | previous pill (first pill: just off the right edge at 0.52H) → this pill's icon over 0.65–0.75 s | in-out + 6 % arc |
| click | pill | scale | 0.95 for 0.08 s, then to 1.10 and back to 1.0 over 0.5 s | sine |
| click | pill | state | unchecked → checked, cross-fade 0.05 s | linear |
| click | ripple | radius, alpha | 8 → 38 px, 0.75 → 0 over 0.45 s | ease-out |
| shot end − 0.22 s | pills, cursor | exit | scale 0.92, alpha → 0 over 0.22 s | ease-out |

Click time = pill start + 0.7–1.1 s (tuned: 0.85, 1.10, 0.70). The cursor stays on the last pill until the exit.
**Footage:** untouched. **Captions during it:** C1 below the pill field.
**Flow prompt text:** "A small bright blue rounded pill with a white tick appears for each point the speaker makes, reading {{POINT_1}}, {{POINT_2}}, {{POINT_3}}. A mouse cursor glides to each one and clicks it, a soft ring spreads, and the pill turns from white to blue."
**Still-image state:** all pills blue and ticked, cursor on the last one.

### F1 · FOLLOW CARD — F high
**What it is:** a white profile card rises near the bottom with a round avatar, a name, a small line and a solid Follow button; the cursor clicks it and it becomes a pale Following button.
**Use when:** the payoff, call to action, a creator or product name, the last 1.5 s. **Avoid when:** the bottom is busy with footage text.
**Text:** none except the button labels "Follow" then "Following" (closed vocabulary). Only if the user gives their own handle or name, it may appear as a name line (complete, as given). Avatar = a still crop of the speaker (or the main subject) from the user's footage.
**Geometry:** 380×112 (600×112 when a user handle is shown), radius 40, white glass 80 %; avatar r 38 with a blue-to-violet ring (3 px) and a white 2 px gap at the left; button 150×56 round, right pad 22. Handle line (optional): Inter 760 31 ink.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| T0 | card | y offset, scale, alpha | +34 px, 0.90, 0 → 0, 1, 1 over 0.5 s | back 1.25 |
| T0 + 0.35 s | cursor | position | off the bottom-right corner → button over 0.55 s | in-out |
| T0 + 0.9 s | button | state | Follow → Following; card pops 1.025 over 0.35 s | sine |

**Footage:** untouched; keep the face clear (card is in the bottom 14 %). **Captions during it:** only E1 above the card.
**Flow prompt text:** "A white rounded profile card rises near the bottom with a round photo of the speaker and a blue Follow button. A mouse cursor clicks the blue Follow button and it changes to a pale Following button."
**Still-image state:** card visible with Following.

### E1 · GLASS CAPSULE CLOSER — E mid (signature)
**What it is:** the final line sits in a frosted capsule instead of plain captions, last word tinted peach.
**Use when:** the last sentence or call to action. **Avoid when:** shorter than 0.8 s.
**Text:** the last 2–4 user words. **Geometry:** capsule text width + 76 × 88, fully round, centre y 0.745H (above F1), glass tint 14 %; text Inter 740 44 white; last word gradient peach → pink.
**Motion:** from the first word: scale 0.90 → 1, alpha 0 → 1 over 0.35 s, back 1.2; float M1; stays to the end.
**Flow prompt text:** "The final words appear in a soft frosted glass capsule, white letters with the last word in a warm peach tint."

### C1 · CAPTION KEYWORD PILL — C mid (signature captions)
**What it is:** 3–5 word chunks of bold white sentence-case text, centred in the lower lane, one word turns into a blue pill when spoken.
**Rules:** chunk 3–5 words, split at punctuation, never end on an article, preposition or conjunction; max width 0.84W, ≤ 2 lines; ≤ 1 keyword per chunk, ≤ 3 per video; keywords are meaning words, never the last word of a list pill already shown. Chunk start = first word; end = min(next chunk start − 0.04 s, last word start + 1.0 s); min 0.4 s.
**Motion:** words fade in and rise 12 px over 0.16 s, staggered 0.035 s; the full chunk layout is fixed (nothing moves). The keyword shows as white text first; at its spoken time the blue pill pops in (scale 0.70 → 1, back 1.8, over 0.22 s). Chunk fades out over 0.08 s.
**Geometry:** lane in 1.3, text shadow black 38 %, blur 6, 3 px down. **Flow prompt text:** "Bold white captions in the lower part of the frame, two lines at most, one important word sitting in a bright blue rounded pill."

### C2 · CAPTION ON GLASS — C low (extension in the same grammar)
**What it is:** the same chunk inside a frosted capsule (E1 geometry, no tint on the last word) for bright or busy lanes. **Use when:** lane luminance > 0.7 or detail high. **Flow prompt text:** "The words sit inside a soft frosted glass capsule near the bottom."

### M1 · FLOAT — M low (idle motion, applies to every panel)
Sine drift ±2.5–3 px, period 2.4–2.6 s, phase offset per element, starts when the entrance finishes. Never on the captions or the cursor.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 (+W2) | K1 per list step on the B-roll, T2 on a new topic | E1 + F1 |
| Single talking head | T1 | K1 for 2–3 claims, T2 once | E1 + F1 |
| B-roll only | T1 in the emptiest corner | K1 per step, C2 if bright | E1 |
| Still image | T1 widgets only | K1 pills as a static tick list | F1 settled |

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
