# moments.md — Podcast Headline: Style Bible + Moment Library

This file is the single source of truth for the Podcast Headline caption style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows. The headline stack was measured on a 720x1280, 30 fps, 3 s reference clip (a podcast reel; the app UI around its phone frame and the orange grade were ignored). The word captions, box captions and keyword box are not in the clip: they are designed in the same grammar and labelled "(design, not measured)". Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays full-frame and untouched while a 1–2 line bold sans headline sits at the top, white lettering over the footage on line 1 and black lettering on a sharp white box on line 2, with clean bold word-by-word captions low in the frame.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 30 fps and the demo at 24 fps; keep seconds at any other rate. Reference values in brackets are for 1080×1920 (measured values × 1.5).

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Headline white | #FFFFFF | Line 1 lettering, caption words (C1) |
| Box white | #FFFFFF (opaque; measured 255,255,255) | Highlight boxes behind line 2 and every box caption |
| Ink | #111111 | Lettering inside boxes (the reference reads as near-black; #111111 used) |
| Text shadow | #000000 at 45 % | Soft shadow under white lettering on footage |
| Box shadow | #000000 at 18 % | Faint edge shadow under boxes (design, not measured) |

No other colours exist in this style. There is no accent colour: emphasis is made by inverting a word into a white box with ink lettering (K1). Brand-swap rule: none for colours. If the user insists, only the box white may become the brand colour, and the ink must stay readable on it.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, untouched. No cards, borders, masks, blur plates, colour overlays or crops (cover-fit only if the source is not 9:16). |
| Headline box | Sharp-cornered white rectangle. Height = 1.34 × font size; padding left and right = 0.28 × font size; width fits the text. Measured: box x 0.176–0.822W, y 0.152–0.213H (195–273 px of 1280) for a 16-character line at font 58 px. |
| Box caption | Same box rule as the headline box, centred on x = 0.50W, one box per line, lines pitch 1.30 × font size. |
| Keyword box | Inline white box behind one caption word: height 1.20 × font size, padding 0.20 × font size each side. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Headline block | x 0.10–0.90, top edge 0.034H [65] (measured on the reference: 0.098H; moved up in the demo so the face stays clear), 2 lines, centred on x = 0.50W | H1, H2, H3 |
| Headline line 1 | cap-height centre at top + 0.5 × cap height | First line |
| Headline line 2 | pitch 1.50 × font size under line 1 (H1, measured 87 px at font 58) or 1.40 × font size (H2, boxes nearly touching, design) | Second line |
| Caption lane | centre of line 1 at 0.76H [1460]; lines pitch 1.30 × font size; block grows downward; max width 0.86W | C1, C2 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Headline | Heavy geometric grotesque, mixed case as the user wrote it, tight but not touching, no tracking (measured: "How I got Claude" = 7.95 em at weight 800, matches the reference width of 461 px at 58 px) | Inter ExtraBold (variable file, optical size 32, weight 800) | Inter Tight ExtraBold, Plus Jakarta Sans ExtraBold, Poppins ExtraBold | 0.08W [87] measured (58 px at W 720); use 0.07W [76] (50 px) when the face is in the top third; widest line ≤ 0.80W |
| Caption (C1, C2, K1) | Same face and weight, mixed case as written | Inter ExtraBold | same | 0.072W [78] (52 px at W 720) |
| Headline and caption case | As the user wrote it. Never forced uppercase | | | |

Rules: letter-spacing 0 (use the font's own kerning). Text on footage (white, no box) gets a shadow: (0, +3 px, blur 5 px, #000000 at 45 %) for the headline; captions use two stacked shadows (blur 4 px at 70 % and blur 12 px at 55 %) because they sit on busier footage. Lettering inside a box has no shadow. Cap height is vertically centred in every box.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Headline line entrance | ease-out cubic (1−(1−t)³): alpha 0 → 1 with a rise of 8 px | 0.17 s (measured: 5 f at 30 fps) |
| Headline line stagger | line 2 starts after line 1 | 0.20 s (measured: 6 f) |
| Headline exit | both lines fade together, linear, no movement (design, not measured) | 0.15 s |
| Caption word entrance (C1) | alpha ramp, no movement (design) | 0.125 s (3 f at 24 fps) |
| Caption chunk change | hard cut, same frame (design) | 1 f |
| Box caption (C2) | hard cut in and out (design) | 1 f |
| Cuts | hard cut, nothing added | 0 f |

Never: bounce, overshoot, spring, slides, tilt, typewriter letter-by-letter, wipes, glitch, shake, scale pops, flashes, colours other than white and ink, uppercase conversion, rounded boxes, outlines, effects on cuts.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text, shadow and box overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; freezing; zoom, push-in, blur, glitch, warp, colour grading or filters of any kind (the orange grade and phone frame in the reference are not part of the style); cards, splits, B-roll frames, background swaps, graphic transitions. The footage plays live in sync with the audio at all times and is never darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by the headline or a caption. If the face box top is above 0.20H, the headline block must end above the face top: bottom edge = top + 1.5 × size + 1.34 × size ≤ face top (use size 0.07W, top 0.034H, bottom ≈ 0.145H). If it cannot fit, shrink the size to 0.06W; if that fails, drop the headline for that shot and show it on the next shot without a face. |
| Headline on B-roll | Any size up to 0.08W; keep the block off the main subject; do not cover readable footage text. |
| Caption lane | Default centre of line 1 at 0.76H. If the face box bottom is below 0.62H, move the lane down so line 1 is ≥ 0.03H under the chin; if the lane would cross 0.90H, use 1 line. If the lane holds a face or the main subject, switch to the top region under the headline or the other lane. |
| Headline and caption together | The two never overlap: the headline lives in the top fifth, captions in the lower half. |
| Footage text (signs, UI) | If readable footage text sits in the lane for more than 1 s, use C2 boxes (they cover it fully) or move the lane. |
| Edges | Every glyph and box stays ≥ 0.04W from the left and right edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **H** headline · **C** caption · **K** keyword · **X** cut rule · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### H1 · HEADLINE STACK — H ●● (signature opener, measured)
**What it is:** a two-line headline at the top. Line 1 is white bold lettering straight on the footage; line 2 is black bold lettering on a white box. Line 1 fades up first, line 2 follows 0.2 s later.
**Role (important):** the headline is the clip's hook, one fixed headline for the whole video, not a caption. Default text: the opening sentence of the user's script (or a title the user gives). It enters at the first spoken word and holds near the top until 0.15 s before the end (it may swap once, at a real section change, with a 0.15 s fade between). The running words live in C1/C2 below. **Never show a headline line that duplicates the caption on screen at the same moment:** the headline words are the moved words, so captions start after the headline sentence (no captions during it) and the audit counts headline + chunks = user text.
**Use when:** the opening line states the topic or promise; the video starts on a speaker or a calm shot with a mid-tone top area. **Avoid when:** the top area is bright (white lettering will not read: use H2), or a cut falls within 0.3 s of the planned start.
**Text (✎):** 2–7 words from the user's own words (or a title the user supplied), as written, split in two lines at a natural break so that line 2 is the shorter or equal line and ≤ 22 characters per line. Never end line 1 on an article or preposition.
**Geometry / Graphics:** Headline block, headline type, line 1 white with headline shadow, line 2 black on box per 1.2. Both lines centred on x = 0.50W. Measured: line 1 x 0.181–0.821W, line 2 box x 0.176–0.822W.
**Motion (line 1 and 2 measured on the reference at 30 fps; hold and exit design):**

| t (s) [f at 30] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.17–0.33 [5–10] ✎ start | line 1 | alpha / y offset | 0 → 1 / +8 px → 0 | ease-out cubic |
| 0.37–0.53 [11–16] ✎ start + 0.2 s | line 2 box and text | alpha / y offset | 0 → 1 / +8 px → 0 | ease-out cubic |
| hold ✎ | both | final state | — | — |
| end − 0.15 s (design, not measured) | both | alpha | 1 → 0 | linear |

Start ✎: the first spoken word, at the latest. Hold ✎: the whole video (default), or until the swap; the final fade ends at video end − 0.15 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 or C2 run underneath in the caption lane.
**Exit:** 0.15 s linear fade.
**Build notes:** render each line once at 2×; draw the box with `ImageDraw.rectangle`, then the text with the cap height centred in the box; bake the shadow (Gaussian blur) into the layer; downscale with LANCZOS; composite per frame with alpha and y offset. Font: `ImageFont.truetype(Inter[opsz,wght].ttf)` then `set_variation_by_axes([32, 800])`.
**Flow prompt text:** "Near the start, a two-line headline, {{LINE_1}} over {{LINE_2}}, appears at the top of the frame in heavy sans lettering. The first line is white lettering straight on the picture; a moment later the second line appears as black lettering on a plain white rectangular box. It stays for about {{SECONDS}} seconds, then fades away. It never covers the speaker's face."
**Still-image state:** final state.

### H2 · BOXED HEADLINE — H ●● (extension in the same grammar, used on the demo)
**Usage rule:** H2 is the boxed variant of the same fixed headline (use it instead of H1 when the top area is bright, or as the single swap at a section change); it never repeats the caption on screen.
**What it is:** the same headline, but both lines are black lettering on white boxes, stacked with a hair gap. Reads on any footage, bright or dark.
**Use when:** the top area is bright or busy; the one swap at a new section. **Avoid when:** never; it is always safe.
**Text (✎):** 1–2 lines, user's own words, as written, ≤ 22 characters per line.
**Geometry / Graphics:** Headline block, both lines boxed, line pitch 1.40 × font size (box height 1.34 × font size, so 0.06 × font size of footage shows between boxes). Size 0.08W on B-roll, 0.07W with a face in the top third.
**Motion:** same as H1: line 1 rises and fades in over 0.17 s, line 2 follows 0.20 s later, hold 1.0–1.6 s, 0.15 s fade out.
**Footage / plate behaviour:** untouched.
**Captions during it:** per H1.
**Exit:** 0.15 s linear fade.
**Build notes:** reuse the H1 renderer with line 1 boxed.
**Flow prompt text:** "A short headline, {{LINE_1}} over {{LINE_2}}, appears at the top of the frame. Each line is black heavy sans lettering on its own plain white rectangular box, the second box appearing a moment after the first. It stays for about {{SECONDS}} seconds and fades away."
**Still-image state:** final state.

### H3 · ONE-LINE HEADLINE — H ●● (extension in the same grammar)
**What it is:** a single boxed line for a short topic word or phrase.
**Use when:** a new step or number appears and a two-line headline would be too heavy; videos under 6 s. **Avoid when:** the phrase is longer than 22 characters.
**Text (✎):** 1 line, user's words as written.
**Geometry / Graphics:** one box per 1.2, headline block top, same size rules as H2.
**Motion:** one line entrance (0.17 s), hold 0.8–1.4 s, 0.15 s fade out.
**Footage / plate behaviour:** untouched.
**Captions during it:** per H1.
**Exit:** 0.15 s linear fade.
**Build notes:** H2 renderer with one line.
**Flow prompt text:** "At the top of the frame, one short line, {{LINE}}, appears as black heavy sans lettering on a plain white rectangular box, stays for about a second, and fades away."
**Still-image state:** final state.

### C1 · WORD-BY-WORD CAPTION — C ●● (signature, the caption system; design, not measured)
**What it is:** white bold captions low in the frame that build word by word. Each new word fades in on the spot; the chunk is laid out in full first, so no word ever moves. The next chunk replaces the whole block in one frame.
**Use when:** speaker shots and calm footage with a mid or dark lane. **Avoid when:** the lane is bright or busy (use C2).
**Text (✎):** the user's exact words, case as written. Chunk rules: 3–5 words per chunk, at most 2 lines, ≤ 0.86W wide; split at punctuation and natural phrases; never end a chunk on an article, preposition or conjunction; prefer chunk changes at cuts.
**Geometry / Graphics:** caption lane, caption type, white, two stacked shadows (1.4). Lines centred on x = 0.50W; the layout of the full chunk is fixed before the first word shows.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ (spoken start) | new word | alpha | 0 → 1 | ease-out, 3 f at 24 fps (0.125 s) |
| word start ✎ | earlier words | — | unchanged | — |
| chunk end ✎ | whole chunk | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Chunk end = next chunk's first word start; at a cut, end on the cut frame when the next word starts after it; the last chunk holds to min(speech end + 0.4 s, video end − 0.25 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system.
**Exit:** hard cut.
**Build notes:** one RGBA layer per (chunk, alpha state), cached; quantise word alpha to 1/8 steps to limit the cache; measure with `font.getlength` before laying out.
**Flow prompt text:** "In the lower part of the frame, captions appear word by word in heavy white sans lettering with a soft dark shadow. Each new word fades in softly where it stands, and when a phrase is complete it is replaced at once by the next phrase."
**Still-image state:** one full chunk.

### C2 · BOX CAPTION — C ●● (signature for bright or busy shots; design, not measured)
**What it is:** the chunk appears at once as black bold lettering on white boxes, one box per line, the same box grammar as the headline.
**Use when:** B-roll with detail, flat objects, readable footage text, bright lanes, or when variety is needed after several C1 chunks. **Avoid when:** the shot is a calm speaker shot with a dark lane and you have used C2 three times in a row.
**Text (✎):** same chunk rules as C1; lines wrap at 0.86W minus the box padding.
**Geometry / Graphics:** caption lane, box caption per 1.2, caption type size 0.072W (shrink to 0.06W if a phrase does not fit in 2 lines).
**Motion:** whole chunk appears and disappears with a hard cut, at the chunk's first spoken word; chunk lasts 1.0–2.5 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** draw each box at 2×; add the faint box shadow as a blurred rectangle at 18 % alpha.
**Flow prompt text:** "In the lower part of the frame, the line {{PHRASE}} appears all at once as black heavy sans lettering, each line on its own plain white rectangular box, and is replaced at once by the next line."
**Still-image state:** the phrase in its boxes.

### K1 · KEYWORD BOX — K ●●● (extension in the same grammar, design, not measured)
**What it is:** one meaning-carrying word inside a C1 chunk is inverted: black lettering on an inline white box. It is the only emphasis the style has.
**Use when:** the topic word, a number or a turn word. **Avoid when:** in C2 chunks (already boxed); more than 1 per chunk, more than 3 per 5 s.
**Text (✎):** one word of the chunk, never an article or preposition.
**Geometry / Graphics:** keyword box per 1.2, inside the caption line at the word's place; layout of the line includes the box padding.
**Motion:** box and word alpha 0 → 1 on the word's start (same 0.125 s ramp), no movement.
**Footage / plate behaviour:** untouched.
**Captions during it:** part of C1.
**Exit:** leaves with its chunk.
**Build notes:** draw the box under the word in the same layer.
**Flow prompt text:** "One important word, {{WORD}}, in the caption is shown as black lettering on a small white box while the other words stay white."
**Still-image state:** the chunk with the boxed word.

### X1 · CUT RULE — X ● (signature treatment of every cut)
**What it is:** hard cuts only. Headline and captions never cross a cut mid-animation: an entrance never starts within 0.3 s after a cut, a headline fade finishes ≥ 0.2 s before a cut, and the caption mode (C1 or C2) may switch on the cut frame.
**Use when:** every footage cut. **Avoid when:** never; add no effects.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** at the cut, the chunk in progress ends on the cut frame (when the next word starts after the cut) or continues in the same mode across the cut (when a phrase of 1–3 words straddles it and its words are already shown).
**Footage / plate behaviour:** untouched; no flash, blur or zoom.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** compute the mode per shot from the scene table (lane luminance and detail).
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect; the headline and captions never wobble or slide at a cut."
**Still-image state:** none.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last caption chunk (or a closing H2 headline with a final line) holds until just before the end, then the picture finishes clean.
**Use when:** every video. **Avoid when:** never.
**Text (✎):** the last chunk's words.
**Geometry / Graphics:** C1 or C2 as chosen for the last shot.
**Motion:** the last chunk holds to min(speech end + 0.4 s, end − 0.25 s); the final 0.25 s has no caption; a closing headline fades 0.15 s before it ends.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1 or C2.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | H1 + C1 | X1 on every cut; C2 on bright or busy B-roll; H2 or H3 at a new step on a B-roll shot; K1 on topic words | H2 headline on the final speaker shot, E1 |
| Single talking head, no cuts | H1 + C1 | H2 at a new topic (≥ 3 s after the last headline); K1 on payoff words | E1 |
| B-roll only, no speech | H2 (user's title words) + C2 | X1 on every cut; C2 phrases of 1.0–2.5 s; H3 on a new step | E1 |
| Still image + text | H1 or H2 final state, one C2 phrase in the settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- One fixed H1 headline, "Saving money isn't / about earning more." (the opening sentence), 0.10–9.60 s at 50 px (0.07W), top edge 0.034H, block bottom 0.145H, just above the face box top (0.15H). Its words are moved words: captions start at "Pay" (2.10 s), so nothing is duplicated.
- Captions: type 52 px (0.072W), lane line 1 at 0.745H; C2 on the cash and phone shots, C1 elsewhere; K1 on "only" and "year". Stacked shadows were needed on the beige sweater.
- A C1 chunk is centred on its full layout, so while its first word shows alone it sits left of centre. That is the intended "no word moves" behaviour.
