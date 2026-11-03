# Google Flow prompt · Punk Photocopy
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Punk Photocopy" motion style to it.

The look in one sentence: Black-and-acid-yellow cut-and-paste zine: yellow brush strokes and torn-paper wipes, a speech-bubble poster, deckle-edge photo cards, black caption bars with white slab-serif words and one big yellow word.

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
| Acid yellow | #F6F800 | Brush strokes, torn wipes, keyword text, bubble offset edge |
| Ink black | #000000 | Caption bars, labels, text on yellow paper |
| Plate black | #040404 with white dust specks (alpha 40–130 / 255, 1–2 px, ~260 per frame area) | Poster plate behind the bubble |
| Caption white | #FFFFFF | Plain caption words |
| Card paper | #F6F4EC | Deckle border of photo cards |
| Bubble edge | #D6D6D2 | Thin paper rim of the bubble window |
| Chrome ring | #CDCDCD | Ring round the small round window |
| Yellow paper dots | 6 % black dot grid every 5 px | Subtle halftone on yellow paper |

Brand-swap rule: a user's brand colour may replace Acid yellow if it is bright and saturated. Never change black or white. No other hues exist in the style (the footage supplies all other colour).

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Full frame, live, colour untouched, by default. Windows (bubble, card) show only the user's own footage. |
| Caption bar | Sharp-cornered black rectangle, fully opaque, sized to the WHOLE chunk before any word appears; width = text width + 2 × 0.42 × tallest font size; height = 1.34 × tallest font size; centred on x = 0.50W. Measured on the reference: 0.283W × 0.054H for a two-word chunk. |
| Tilt label | Black rectangle, text yellow, tilted +6° to +10° (rising to the right), width = text + 2 × 0.4 em, height 1.38 em. |
| Bubble window | Irregular speech-bubble polygon (9 points, fractions of W,H): (0,.10) (.15,.02) (1,.02) (1,.34) (.58,.38) (.47,.64) (.40,.37) (.14,.33) (0,.26); live footage inside at its normal position (not scaled); 7 px rim #D6D6D2; yellow copy of the polygon offset (−15, +13) px behind it; black plate everywhere else. |
| Round window | Circle at (0.45W, 0.745H), radius 0.12W, shows a 2.3× zoom of the live footage near its centre, 7 px chrome ring. |
| Photo card | 0.42W × 0.46H, deckle edge (white polygon with ±3 px jitter every 7 px), 11 px paper border, photo inside, soft shadow (+6, +9 px, blur 7 px, black 47 %), tilt ±3°. |
| Brush stroke | Yellow band of ~90 parallel bristle lines (3–10 px) with ragged ends, 0.10–0.16W thick. |
| Torn wipe | Yellow paper with a jagged leading edge (low-frequency noise ±0.045 of the sweep axis plus fine jitter). |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor = speaker face or main subject. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Caption lane (speaker) | bar centre y = 0.62H, below the chin | C1/C2 on a speaker shot |
| Caption lane (B-roll) | bar centre y = 0.66–0.70H | C1/C2 on B-roll |
| Reference lanes | the reference bar centre sat at y 0.55–0.70H depending on the layout | — |
| Card right | centre (0.745W, 0.28H) tilt +3° | K1 default |
| Card left | centre (0.255W, 0.27H) tilt −3° | K1 when the subject sits right |
| Bubble poster | polygon in 1.2, labels at (0.47W, 0.115H) tilt +9° and (0.60W, 0.25H) tilt +6° | P1 |
| Brush layout | right edge band x 0.84–0.96, y 0.06–0.78; bottom band y 0.78–0.92, x 0–0.65; open ring at (0.06W, 0.50H) r 0.15W | T1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption plain word | Sturdy slab serif, semibold (weight 650), white, mixed case as written | Roboto Slab | Zilla Slab Bold, Bitter SemiBold | 0.066W [71] |
| Caption keyword | Same slab, bold (700), yellow | Roboto Slab Bold | Zilla Slab Bold, Bitter Bold | 0.098W [106] |
| Tilt label text | Roboto Slab Bold, yellow on black | Roboto Slab | as above | 0.088W [95] |

Rules: case exactly as the user wrote it. Word gap 0.26 × plain size. Bar text baseline = bar centre + 0.34 × tallest size. Text on bars never gets a shadow; the bar is the contrast device. No outline text, no italics, no uppercase conversion.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Caption word | hard pop on the word's spoken start; bar is already there | 1 f |
| Caption chunk change | hard cut (bar replaced) | 1 f |
| Brush on / off | linear reveal along the stroke direction, hard edge; off wipes in the same direction | on 0.21 s, off 0.35 s |
| Echo stack | ease-out cubic 1−(1−t)³ | 0.78 s |
| Torn wipe in | ease-in cubic t³ | 0.22 s |
| Torn wipe out | ease-out cubic | 0.28 s |
| Bubble pop | ease-out cubic from 5 % size about the tail tip | 0.34 s |
| Bubble exit | ease-in cubic, polygon morphs to the frame | 0.30 s |
| Card slide in / out | ease-out in 0.35 s / ease-in out 0.30 s, with 8° extra tilt while off-screen | — |

Never: bounce, overshoot, spring, letter-by-letter typing, fades on captions, blur, glitch, camera shake, flashes, colour grading of footage, rounded caption bars, drop shadows on caption text.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame live display | Always, except during poster and wipe frames |
| Echo stack: the live frame scaled to 0.80 → 1.00 with three offset copies of the same live frame behind it, black margin | T1 only, ≤ 0.8 s, once |
| Windows (bubble, round window, card) showing user footage | Primary footage plays live and in sync inside the bubble; a card shows a still or ≤ 1.5 s loop of another of the user's shots |
| Yellow brush strokes and torn wipes over the picture | Per 1.7; a wipe fully covers the frame for ≤ 0.1 s and never over a speaking face |
| Black plate behind the bubble | P1 only, ≤ 1.6 s |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; recolouring or desaturating footage (the reference's black-and-white photo plates are NOT reproduced: the user's footage keeps its colour); blur, glitch or filters on footage; adding footage the user did not supply.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by strokes, wipes, cards, bars or the bubble body. Brush strokes stay on the edge bands of 1.3. A wipe may cover a face only when that shot has no speaking face; otherwise use W2 with its peak edge at 0.46H or lower, which keeps heads in the upper 0.4H visible. |
| Caption lane | Bar sits ≥ 0.03H below the chin. If the lane is occupied by a card, move the card (K1 side) rather than the bar. |
| Card | Never over a face on the primary shot. |
| Bubble poster | Pick it only on B-roll or a shot with no speaking face; the visible window part (top 0.64H) must still show the subject. |
| Footage text (signs, UI) | If readable footage text sits under the bar for more than 1 s, shift the lane up or down 0.06H. |
| Edges | Bars and labels stay ≥ 0.04W from the left and right edges (shrink the font until the bar ≤ 0.92W). |

---

## 7. MOMENT LIBRARY
Family codes: **T** opener · **C** caption · **P** poster · **L** label · **K** card · **W** wipe · **D** doodle · **M** footage motion · **E** ending.

### MOMENT T1 · BRUSH-STRIKE ECHO OPEN
**What it is:** the opening shot lands in a stack: the live frame jumps to 0.80 scale with three offset copies behind it that glide into one while yellow brush strokes and an open ring are painted on and wiped off, so the footage settles to full frame.
**Use when:** the video starts on a speaker or any shot. **Avoid when:** the first 0.2 s contains a cut (start 0.2 s after the cut) or the video is shorter than 3 s (shorten, never drop).
**Text:** none (captions run underneath).
**Geometry / Graphics:** stack: three ghost copies of the current live frame, each offset (−k·30, −k·34) px × (1−progress), k = 1..3, on black. Strokes per 1.3 Brush layout (three layers: right band revealed top to bottom, bottom band revealed left to right, ring revealed top to bottom).
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.17 [4] | live frame | scale | 1.00 → 0.80 | hard jump |
| 0.17–0.95 [4–23] | live frame | scale | 0.80 → 1.00 | ease-out cubic |
| 0.17–0.95 | ghost copies | offset | full → 0 | ease-out cubic |
| 0.17–0.38 (+0.05 per stroke) | strokes | reveal | 0 → 1 | linear |
| 0.55–0.90 (+0.06 per stroke) | strokes | wipe off | 0 → 1 | linear |

**Footage / plate behaviour:** the live frame plays in sync throughout; face stays in the central region, strokes never cross x 0.20–0.80 above y 0.78.
**Captions during it:** C1 runs on top from the first word.
**Exit:** strokes wiped off, ghosts merged, full frame by 0.98 s.
**Build notes:** draw strokes at 2×: ~90 lines with jittered ends, `MaxFilter(5)`, downscale; reveal with a per-pixel coordinate threshold along the stroke direction; resize the frame once per frame with BILINEAR.
**Flow prompt text:** "Right after the first moment, the picture steps back into a small stack of copies of itself that slide together into one full-frame picture while bright yellow brush strokes and a loose ring are painted over the edges of the frame and wiped away. The speaker's face stays clear."
**Still-image state:** full frame with the yellow strokes at the edges.

### MOMENT C1 · BLACK BAR CAPTION
**What it is:** every chunk sits on a hard black bar that is already as wide as the whole chunk; the words pop in one by one as they are spoken. Plain words are white, one keyword per chunk is bigger and yellow.
**Use when:** always. **Avoid when:** a poster (P1) is on screen and its labels carry the words.
**Text:** the user's exact words, case as written. 1–3 words per chunk, ≤ 20 characters; split at punctuation; never end on an article or preposition; chunk ends at the next chunk's first word (gap > 0.6 s: end 0.6 s after the last word start). Keyword: 1 per chunk at most, none in about 1 of 4 chunks, the meaning-carrying noun or verb or the payoff word; never an article or preposition.
**Geometry / Graphics:** Caption bar and Typography per 1.2 and 1.4; lane per 1.3 and 1.7. A chunk with a keyword has a taller bar (1.34 × keyword size).
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| chunk start | bar | alpha | 0 → 1 | hard cut |
| each word's spoken start | word | alpha | 0 → 1 | hard pop |
| chunk end | bar + words | alpha | 1 → 0, next bar in the same frame | hard cut |

**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system; it sits above every other layer including wipes.
**Exit:** hard cut.
**Build notes:** render each (chunk, words-shown) state once at 2× and cache it; lay the whole chunk out first so the bar never changes size; paste centred on x = 0.50W.
**Flow prompt text:** "Captions sit on a solid black rectangle near the middle of the lower half of the frame. The rectangle is already as wide as the whole phrase and the words appear one by one as they are spoken. Ordinary words are white in a sturdy slab-serif typeface; one important word, {{KEYWORD}}, is larger and bright yellow. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one complete chunk.

### MOMENT C2 · SOLO KEYWORD BAR
**What it is:** a chunk of one word, a big yellow word alone on its bar, for a payoff or turn.
**Use when:** a strong word ("never", a number, a name, the last word). **Avoid when:** more than 2 per video, or the word is longer than 12 characters.
**Text:** one user word.
**Geometry / Graphics:** C1 with only a keyword (size 0.098W; 1.15× at most 0.113W).
**Motion:** as C1; hold 0.5–1.0 s.
**Footage / plate behaviour:** untouched. **Captions during it:** replaces the chunk. **Exit:** hard cut.
**Build notes:** same renderer as C1.
**Flow prompt text:** "One important word, {{WORD}}, sits alone on a black rectangle in large bright yellow slab-serif lettering, then is replaced by the next caption."
**Still-image state:** the word on its bar.

### MOMENT P1 · BUBBLE POSTER
**What it is:** on a cut the picture becomes a poster: black plate with dust, a yellow-edged speech-bubble window showing the live footage, a small round chrome-ringed window, and one or two tilted black label strips carrying the caption words. At the end the bubble stretches out to the whole frame.
**Use when:** a B-roll shot or a topic-word beat (the reference used it for an adjective pair on a cut); a list item that deserves a poster. **Avoid when:** the shot has a speaking face, or within 3 f before a cut that already carries W1.
**Text:** 1–2 labels, the user's exact words, ≤ 16 characters each; they replace C1 for the duration.
**Geometry / Graphics:** Bubble window, Round window, Tilt label, Bubble poster layout per 1.2 and 1.3.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start (the cut) | plate | alpha | 0 → 1 | hard cut |
| start–start+0.34 | bubble polygon | scale about tail tip (0.47W, 0.64H) | 0.05 → 1.00 | ease-out cubic |
| start–start+0.30 | round window | radius | 0.04W → 0.12W | ease-out cubic |
| start | label 1 | alpha | 0 → 1 | hard pop |
| start+0.5 | label 2 | alpha | 0 → 1 | hard pop |
| end−0.30–end | bubble polygon | morph to full-frame rectangle; yellow edge and ring fade out | 0 → 1 | ease-in cubic |

Duration: 1.0–1.6 s.
**Footage / plate behaviour:** the live footage plays inside the bubble at its normal position and scale (only masked); the exit reveals the full frame again.
**Captions during it:** the labels are the captions; C1 resumes after the exit.
**Exit:** polygon morph, then the next shot or caption.
**Build notes:** polygon masks at 2×; `Image.paste(frame, mask=poly)` onto the plate; labels via `Image.rotate(angle, expand=True)`.
**Flow prompt text:** "The picture cuts to a black poster speckled with white dust. A speech-bubble shaped window with a bright yellow edge shows the same moving picture, a small round window with a silver ring shows a close-up of it, and one or two tilted black label strips carry the words {{LABEL_WORDS}} in yellow. At the end the bubble stretches until the picture fills the frame again."
**Still-image state:** the poster with both labels.

### MOMENT L1 · TILT LABEL
**What it is:** a single tilted black strip with a yellow word, placed on a card or poster for one beat word.
**Use when:** a keyword on K1 or P1 that needs more weight than a caption. **Avoid when:** it would cover a face; max 2 at once.
**Text:** 1–2 user words ≤ 16 characters.
**Geometry / Graphics:** Tilt label per 1.2; anchor on the card or poster.
**Motion:** hard pop, hold with the caption, hard cut.
**Footage / plate behaviour:** untouched. **Captions during it:** counts as the caption for those words (audit). **Exit:** hard cut.
**Build notes:** same renderer as the P1 labels.
**Flow prompt text:** "A tilted black label strip with the word {{WORD}} in yellow slab-serif lettering pops onto the card."
**Still-image state:** the strip in place.

### MOMENT K1 · TORN PHOTO CARD
**What it is:** a white deckle-edged photo card with a soft shadow slides in from the side, tilted slightly, and shows one of the user's other shots (a speaker still, the previous step) while the main footage keeps playing behind it.
**Use when:** a person ↔ B-roll cut, or a step that refers back to something already shown. **Avoid when:** the card would cover a face on the primary shot, or within 0.3 s after a cut. The reference used cards 4.46–6.2 s with a tall card sliding from the right edge.
**Text:** none (optionally L1 on it).
**Geometry / Graphics:** Photo card per 1.2; side and tilt per 1.3; photo content = a crop of one of the user's own frames, anchor on its subject.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| in (≥ 0.12 s after a cut) | card | x offset | ±0.55W → 0, extra tilt 8° → 0 | ease-out cubic, 0.35 s |
| hold | card | — | 0.9–1.2 s | — |
| out (finish ≥ 0.1 s before the next cut) | card | x offset | 0 → ±0.55W, extra tilt 0 → 8° | ease-in cubic, 0.30 s |

**Footage / plate behaviour:** the card shows a still or a ≤ 1.5 s loop; the primary footage stays live.
**Captions during it:** C1 stays in its lane; the card is placed away from it.
**Exit:** slides back out.
**Build notes:** build the card once at 2× (polygon jitter seeded), cache; per frame `rotate` + `alpha_composite`.
**Flow prompt text:** "A white paper photo card with torn, rough edges and a soft shadow slides in from the {{SIDE}} edge, slightly tilted, showing {{CARD_CONTENT}}, stays for about a second, and slides back out while the main picture keeps playing."
**Still-image state:** the card in place.

### MOMENT W1 · YELLOW TORN WIPE
**What it is:** a sheet of yellow torn paper sweeps diagonally across the frame, covers it for a couple of frames, the cut happens underneath, and the sheet sweeps off to reveal the new shot.
**Use when:** a cut into a new topic or step, especially into a shot without a speaking face. **Avoid when:** more than 3 per video, or a speaking face is on either side of the cut.
**Text:** none (captions stay on top).
**Geometry / Graphics:** yellow paper (1.1) with torn leading edge; sweep axis u = (0.8x/W + 0.35y/H) normalised.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut−0.22–cut | leading edge | u | −0.15 → 1.20 | ease-in cubic |
| cut | footage | cut under the sheet | hard cut | — |
| cut–cut+0.28 | trailing edge | u | −0.15 → 1.20 | ease-out cubic |

**Footage / plate behaviour:** only the footage's own cut happens under the sheet.
**Captions during it:** on top of the sheet.
**Exit:** the trailing edge clears the frame.
**Build notes:** noise profile (low-frequency control points, interpolated) added to u; mask threshold; light Gaussian blur 0.8 px on the mask.
**Flow prompt text:** "At the cut, a sheet of bright yellow torn paper sweeps diagonally across the frame, covers it for an instant, and sweeps away to reveal the next shot. The captions stay on top."
**Still-image state:** none.

### MOMENT W2 · YELLOW HILL RISE
**What it is:** a yellow torn-paper hill rises from the bottom of the frame to just under the face line at a cut and drops away again.
**Use when:** a cut back to a speaker, or a payoff line. **Avoid when:** more than 2 per video; the speaker's face is lower than 0.40H.
**Text:** none.
**Geometry / Graphics:** yellow paper filling below an arched torn edge: edge y = top + 0.16H × ((x − 0.5W)/0.5W)² + noise (±14 px on the left half). Peak top = 0.46H.
**Motion (reference: hill leaving the frame at 8.88 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut−0.22–cut | edge top | y | 1.05H → 0.46H | ease-in cubic |
| cut–cut+0.33 | edge top | y | 0.46H → 1.05H | ease-out cubic |

**Footage / plate behaviour:** the cut happens at the peak; the top 0.4H (heads) always stays visible.
**Captions during it:** on top.
**Exit:** the hill leaves through the bottom.
**Build notes:** analytic mask, no randomness per frame.
**Flow prompt text:** "At the cut, a bright yellow torn-paper hill rises from the bottom of the frame to about the middle, then drops away again, while the captions stay on top. The speaker's face stays clear."
**Still-image state:** none.

### MOMENT D1 · BRUSH RING
**What it is:** a loose hand-painted yellow ring or underline drawn around an empty area or a keyword's neighbourhood.
**Use when:** a long calm shot (> 1.5 s) needs a beat. **Avoid when:** it would touch a face; max 2.
**Text:** none.
**Geometry / Graphics:** ring radius 0.10–0.15W, 14 px stroke, open arc about 330°, on an edge band (1.3).
**Motion:** reveal 0.2 s linear, hold 0.4–0.8 s, wipe off 0.3 s.
**Footage / plate behaviour:** untouched. **Captions during it:** unchanged. **Exit:** wiped.
**Build notes:** same stroke renderer as T1.
**Flow prompt text:** "A loose bright yellow brush ring is painted near the edge of the frame, stays for a moment, and is wiped away."
**Still-image state:** the ring.

### MOMENT M1 · SLOW PUSH
**What it is:** a barely visible push-in on a long static shot.
**Use when:** a shot longer than 2 s with little motion. **Avoid when:** the footage moves a lot, or a card or poster is up.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:** scale 1.00 → 1.06 across the shot (linear), about the subject anchor; reset at the next cut.
**Footage / plate behaviour:** live, scaled only. **Captions during it:** unaffected. **Exit:** reset by the cut.
**Build notes:** `Image.resize(..., box=floats)`, clamp the box.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### MOMENT E1 · END HOLD
**What it is:** the last chunk stays until just before the end, then the picture finishes clean.
**Use when:** every video. **Avoid when:** never.
**Text:** the last chunk's words.
**Geometry / Graphics:** C1 or C2.
**Motion:** the chunk holds to min(last word start + 0.6 s, end − 0.25 s); final 0.25 s [6 f] has no caption; no wipes in the last 0.5 s.
**Footage / plate behaviour:** untouched. **Captions during it:** per above. **Exit:** video ends.
**Build notes:** none beyond C1.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 | K1 on person → B-roll cuts, P1 on a B-roll shot, W1 on a topic cut, L1 on a card | W2 into the last speaker shot, C2 on the last word, E1 |
| Single talking head, no cuts | T1 + C1 | C2 on a payoff word, D1 on a long calm line, M1 | E1 |
| B-roll only, no speech | T1 (strokes only) + C1 | P1 on the strongest shot, W1 on cuts, K1 with a still of another shot | E1 |
| Still image + text | settled T1 strokes, C1 chunk | — | — |

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
