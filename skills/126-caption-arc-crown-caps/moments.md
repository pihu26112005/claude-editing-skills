# moments.md — Arc Crown Caps: Style Bible + Moment Library

This file is the single source of truth for the Arc Crown Caps caption system. Part 1 is the style bible (palette, type, geometry, motion, footage rules, safe zones). Part 2 is the moment library: every caption move the style knows. Values marked "measured" come from a 9:16 reference of a speaker on a dark night background (360x640, 32 fps, 7.25 s, one continuous shot); values marked "(design, not measured)" were tuned on the shared 720x1280, 24 fps demo clip. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays full-frame and untouched while the one key word of each phrase sits in a bold accent-colour arch like a crown above the speaker's head, and the small words around it pile up as tilted white heavy caps on the chest.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, lane, tilt, accent colour). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s). Frame counts are at the source fps (24 on the demo; keep seconds at other rates). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Accent ✎ | measured default #F9BC34 (amber, median of the keyword face; 10th–90th percentile 208,153,37 – 255,195,68). Demo uses hot pink #FF2E93 | Arch keyword face |
| Accent depth | accent darkened to about 50 % (demo #800A46) | 3D extrusion under every arch letter |
| Text white | #FFFFFF | Stack words, big solo word |
| Outline | #141418 at 92 % | 2 px stroke on white words (design, not measured: the reference sat on a dark plate and needed none; added so white reads on bright footage) |
| Shadow | #000000 at 45–50 % | Soft drop shadow under every text role |

Brand-swap rule: the accent is a parameter. Any saturated colour that reads on the footage is allowed; keep white, outline and shadow fixed. Exactly one accent per video.

### 1.2 Containers / shapes

No containers. The footage is always full frame, 100 % of W and H: no cards, boxes, bars, label plates, masks, borders, blur plates or colour overlays. Text is the only layer. Crop anchor ✎ only if the source is not 9:16 (cover-fit about the speaker's face).

### 1.3 Layouts / grid

| Layout | Region (fractions) | Use |
|---|---|---|
| Crown arch (default) | apex baseline y = 0.115H [221] (measured band 0.24–0.37H of the reference where the head top was 0.30H; demo head top is 0.14H so the arch sits just above), centred x = 0.50W, widest span 0.74W [800] | C1, C4 |
| Low arch | apex baseline y = 0.46H [883]; same arch | K1: when a face sits in the top band |
| Chest lane | x0 = 0.105W [113], y0 = 0.50H [960], max line width 0.54W [583] | C2 on a speaker (face box ends at 0.40H) |
| Lower lane | x0 = 0.105W, y0 = 0.70H [1344] | C2 on B-roll / hands / screens |
| Upper-left lane | x0 = 0.105W, y0 = 0.14H [269], max width 0.36W [389] | C2 when the face sits right of centre |
| Solo centre | centre x = 0.50W, y = 0.52H [998] | C3 |

Safe frame for ALL text, including entrance scale: x 0.05W–0.95W, y 0.02H–0.98H. Face box (speaking face) is never touched by any glyph, shadow or extrusion.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Arch keyword | uppercase, ultra-heavy geometric sans, letters placed on a circle and each rotated to the tangent, small 3D extrusion downward, soft shadow | Poppins Black | Montserrat Black, Archivo Black | cap height ≈ 0.045–0.06H [86–115] (measured 0.06H); fit so chord width ≤ 0.74W; size 118 px at 720 W, shrinks for long words |
| Arch geometry | measured on an 8-letter word: chord 0.78W, sag ≈ 0.045H → circle radius ≈ 0.95W [1026]; tracking +0.015 em | — | — | — |
| Stack word | uppercase, extra-bold sans, tracking +0.02 em, outline + shadow | Poppins ExtraBold | Montserrat ExtraBold | 54 px at 720 W (cap ≈ 0.026H; reference ≈ 0.04H on a 640 px tall frame, so the demo is a touch smaller) |
| Solo word | uppercase, black weight | Poppins Black | Montserrat Black | 150 px at 720 W (≈ 2.8x stack size; reference "EK" ≈ 2.5x) |

Case: UPPERCASE for all text; the user's words and punctuation (commas, full stops) stay; case is a display transform only.

### 1.5 Motion language

- Keyword enter (measured shape, timing tuned): blurred and slightly large, resolving to sharp while fading in; 0.26 s (6 frames), ease-out cubic; scale 1.12 → 1, blur radius 12 px → 0, alpha 0 → 1. Reference shows a motion-blur streak on arrival.
- Keyword exit: 0.14 s, alpha 1 → 0 with blur 0 → 6 px. Always finishes before the next keyword starts (the reference crossfades two keywords; this skill keeps them apart so captions never overlap).
- Stack word enter: 0.20 s, ease-out cubic, scale 1.1 → 1, blur 8 px → 0, alpha 0 → 1. Words appear one by one at their spoken time and stay.
- Stack exit: the whole group fades together 0.12 s, alpha 1 → 0, 0.5 s after its last word starts, and never later than 0.15 s before the next group or solo word starts.
- Holds: keyword stays 0.65–1.45 s (long enough to read, then clears; a keyword never outlives the shot it was placed for if the next shot has a face in the arch zone).
- Never: bounce, overshoot, letter-by-letter typing, slides, shake, flashes, colour changes, boxes.

### 1.6 What may happen to the user's footage

Nothing. Full frame, untouched, live and in sync with the audio. Forbidden: any zoom, crop, blur, grade, filter, mask, cut-out, background change, split, card, transition, speed change, trimming or reordering. Only text, outline and shadow layers are added.

### 1.7 Safe zones

- Face box of the speaking person (demo talking head: x 0.34–0.66W, y 0.15–0.40H; checkout shot: x 0.50–0.75W, y 0.10–0.37H) stays clear of every glyph, extrusion and shadow in every frame. Check by mask, not by bounding box: an arch's rectangular bbox is larger than its ink.
- Captions never overlap each other: keyword, stack and solo word never share a pixel region at the same time (same-group stack words are laid out on a grid).
- Keep arch ink at least 8 px above the face box top; if the head is high (face box top < 0.14H) use K1.
- Never start a new keyword within 3 frames after a cut when avoidable; small stack words may.

---

## PART 2 — MOMENT LIBRARY

Families: **C** caption · **K** keyword placement variant · **T** title/headline · **E** end. Energy: low / mid / high. Signature moments (mandatory in every output): C1, C2, C3 (when the text has a natural solo word or phrase end) and C4.

### C1 · ARC CROWN KEYWORD — C high (signature, measured)
**What it is:** the key word of each phrase as a bold accent arch above the head, extruded, resolving from a blur.
**Use when:** every phrase has one stand-out word: topic noun, verb of an instruction, number, time phrase, payoff word.
**Avoid when:** the word is an article or preposition; the same word would repeat within 1.5 s.
**Text (✎):** one user word (with its own punctuation) per keyword, max 12 characters before shrinking; max 1 per phrase, 0.9–1.4 keywords per second at most (demo: 8 in 10 s).
**Geometry / Graphics:** circle radius 0.95W; letters centred on the arc, each rotated to the tangent (right letters clockwise); extrusion 8 px at 2x supersample (4 px final) downward in accent depth; shadow blur 7 px offset +5 px at 50 %. Apex baseline y 0.115H.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start (word's spoken time) → +0.26 s (6 f) | keyword | scale / blur / alpha | 1.12 / 12 px / 0 → 1 / 0 / 1 | ease-out cubic |
| hold | keyword | all | static | — |
| end − 0.14 s | keyword | alpha / blur | 1 → 0 / 0 → 6 px | linear |
**Footage:** untouched. **Captions during it:** stack words below (C2).
**Exit:** fade as above, ends at least 0.02 s before the next keyword starts.
**Build notes:** build the arch once per word at 2x: render each glyph on its own RGBA, rotate by the tangent angle about its baseline centre, paste at the circle point; derive extrusion from the alpha silhouette stacked 1–8 px; downscale with Lanczos; animate by resizing/blurring the sprite per frame about the apex.
**Flow prompt text:** "As the speaker says {{WORD}}, that word appears in big bold {{ACCENT COLOUR}} capital letters curved in an arch just above the head, with a small solid 3D edge and a soft shadow; it sharpens in from a blur and fades out smoothly after about a second."
**Still-image state:** arch word settled above the head, sharp.

### C2 · TILTED WHITE STACK — C mid (signature, measured)
**What it is:** the small connecting words appear one by one as white heavy caps, set on a slight tilt, filling a tight block that grows to 2–3 lines.
**Use when:** every phrase; they carry the words around the keyword.
**Text (✎):** the user's other words, in spoken order, each at its own spoken time; line max width per lane (1.3); tilt ✎ -6° … +6°, alternating between groups.
**Geometry / Graphics:** word spacing 0.32 em, line pitch 1.18 em, left-aligned from the lane origin, whole block rotated about the origin by the group tilt (positive = counter-clockwise). Outline 2 px, shadow as 1.1.
**Motion:** each word 0.20 s pop (1.5); group exits together (1.5).
**Footage:** untouched. **Captions during it:** keyword arch above (C1) never touches the stack: arch ends ≥ 0.2H above the chest lane.
**Exit:** group fade 0.12 s.
**Build notes:** lay out words unrotated, rotate centres about the lane origin by the tilt, rotate each word sprite by the same tilt (expand), paste at the rotated centre. Pick the lane by the shot the group starts in and keep it for the whole group (do not move a group across a cut).
**Flow prompt text:** "The words around it appear one by one in small white bold capital letters with a thin dark outline, stacked in a tilted block on the lower left of the frame, then fade away together."
**Still-image state:** a 2–3 line white stack on the chest lane at a small tilt.

### C3 · BIG SOLO WORD — C high (signature, measured as "EK" about 2.5x stack size, design for placement)
**What it is:** one word (or short phrase end) as a huge white word in the middle of the frame, tilted about 6°, with outline and shadow.
**Use when:** a sentence ends on a punchline word ("more.", "now.", a number) and the keyword slot is already taken or an interruption beat is wanted; max 1–2 per video.
**Text (✎):** one user word with punctuation, ≤ 8 characters.
**Geometry:** centre (0.50W, 0.52H) on a speaker (below the face box); font 150 px at 720 W; tilt +6° (✎ ±6°); width ≤ 0.70W.
**Motion:** enter 0.26 s: scale 1.3 → 1, blur 12 → 0, alpha 0 → 1, ease-out cubic; hold 0.45 s; exit 0.14 s fade.
**Footage:** untouched; the word covers the chest, never the face.
**Build notes:** same sprite pipeline as C2 with Poppins Black, outline 3 px.
**Flow prompt text:** "On the word {{WORD}} a very large white capital word pops in the middle of the frame, slightly tilted, then fades; it never covers the face."
**Still-image state:** the word large and tilted below the face.

### C4 · KEYWORD HANDOVER — C mid (signature, timing rule)
**What it is:** the rule that only one arch is visible at a time: the old keyword blurs out in 0.14 s and the next one blurs in at its spoken time, in the same place.
**Use when:** always, between C1s.
**Motion:** old exit ends at the new start − 0.02 s; new enter starts exactly at the spoken time. (Measured: reference keywords hold 1.4–2.5 s and swap in place within about 0.25 s.)
**Build notes:** compute each keyword's end = min(start + hold, next start − 0.02); then t1 = end − 0.14 s.
**Flow prompt text:** "Only one arched word is on screen at a time; each new word replaces the previous one in the same spot."

### K1 · LOW ARCH — K mid (design, not measured)
**What it is:** the same arch moved below the face when the face sits in the top band (shot where the speaker is high or at the side).
**Use when:** a shot's face box top < 0.14H or the face box intersects the crown arch zone.
**Geometry:** apex baseline y = 0.46H; arch ink starts below the face box bottom (+ 0.015H). Keep C2 words in the upper-left or lower lane so they never touch it.
**Motion:** as C1. **Exit:** as C1; a keyword placed for this shot ends before the next cut if the next shot has no such face.
**Flow prompt text:** "The curved word appears below the speaker's face, across the chest."

### K2 · FLAT KEYWORD ON STACK — K mid (measured, optional)
**What it is:** a keyword set straight (no arc) in the accent, directly above a white stack, used when the arch zone is occupied (reference: a flat accent word over a two-line white stack on the chest).
**Geometry:** flat accent word, same font and size as C1, left of centre; the white stack sits right under it with a 0.012H gap; no overlap.
**Flow prompt text:** "The word appears straight in big {{ACCENT COLOUR}} capitals with the smaller white words directly under it."

### T1 · ARCH OPENER — T high (design, not measured)
**What it is:** the first spoken keyword is allowed 15 % larger and held 0.3 s longer to introduce the style.
**Use when:** the first phrase of a video. **Avoid when:** the video opens on a cut within 0.3 s.
**Geometry:** C1 with chord ≤ 0.78W and hold +0.3 s. **Flow prompt text:** "The first key word arrives slightly larger and stays a bit longer."

### C5 · BRIGHT-FOOTAGE CONTRAST MODE — C low (design, not measured)
**What it is:** on pale or busy shots, white text keeps the dark outline and the shadow strengthens; the arch keeps its extrusion. On dark footage the outline may be dropped (reference had none).
**Rule:** judge by the median luminance of the lane region (> 0.55 → bright mode).
**Flow prompt text:** "On bright shots the white words get a thin dark outline so they stay readable."

### C6 · SIDE LANE — C low (design, not measured)
**What it is:** the stack in the upper-left lane (1.3) when the face is right of centre and the chest is occupied.
**Use when:** face box left edge ≥ 0.45W. **Geometry:** lane x0 0.105W, y0 0.14H, max width 0.36W.
**Flow prompt text:** "The small white words stack in the upper left, away from the face."

### E1 · ARCHED WHITE SIGN-OFF — E mid (measured shape, design for timing)
**What it is:** on the last two words, a white arched phrase (the reference ends with a two-word white arc, tilted, blurring out) instead of an accent keyword; exits last 0.3 s with a blur-out.
**Use when:** a quiet sign-off ("that's it") rather than a punchline.
**Geometry:** C1 pipeline with white face and no extrusion; apex 0.115H.
**Flow prompt text:** "The final two words curve over the head in white and blur away."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + C2 | C1/C4 per phrase, C3 on a punchline, K1 on shots with a high face | C1 on the payoff word |
| Single talking head | T1 + C2 | C1/C4 alternate, C3 once | E1 or C1 |
| B-roll only | C1 | C1/C4, C2 on the lower lane | C1 |
| Still image | C1 settled + C2 stack | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Demo values (shared 10 s clip, tuned) — word start times (s)
Stack: Saving .10, isn't .55, about .80 (clear ≈1.30) · MORE. solo 1.45–2.04 · Pay 2.10, first, 2.60 · automate 3.20, your 3.55 · and 4.95, only 5.45, what's 5.70 · Do 6.90, it 7.10, for 7.25, one 7.45 · and 8.45, watch 8.65, what 8.95.
Arch holds (s): money .70, earning 1.20, yourself .90, investments, 1.15 (clears before the 4.92 cut), spend .80 (low arch), left. .65 (low arch), year 1.45, happens. 1.0 (runs to the end).
Lane per group: shot 1 chest, shots 2–3 lower, shot 4 upper-left, shot 5 y 0.58H, shot 6 y 0.52H. Tilts: -6, +4, -4, +5, -5, +4.
