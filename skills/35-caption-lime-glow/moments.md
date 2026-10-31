# moments.md — Lime Glow: Style Bible + Moment Library

This file is the single source of truth for the Lime Glow caption style. Part 1 is the style bible (palette, type, motion, footage rules, safe zones). Part 2 is the moment library: every caption and title move the style knows, measured on a 1080x1920, 24 fps, 10.3 s reference reel and tuned on a 720x1280 render. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: the footage stays full frame.

**The look in one line:** the footage stays full frame while captions pop in as a two-line stack of clean white semibold words over one heavy italic lime keyword with a green glow, over a soft dark floor, and a giant outlined italic title with a red/cyan edge slides across the top.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (24 fps on the reference; at another fps keep the seconds). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Caption white | #FFFFFF fading to #D8DCDE at the baseline | Plain caption words (vertical gradient, measured 252,253,253 at the top) |
| Keyword lime | #CEFD38 | Keyword fill (measured median 206,253,56) |
| Lime glow | #96FF00 at 75 % | Blurred halo behind each keyword |
| Title edge | #FFFFFF 95 %, #FF3C3C 90 % (shifted +5 px at 2x), #28C8FF 90 % (shifted −5 px at 2x) | Outline of the title: white ring with a red copy to the right and a cyan copy to the left |
| Title fill | #000000 at 34 % plus white halftone dots at 14 % | Inside the title letters (footage shows through) |
| Floor | #000000, 0 → 44 % | Vertical scrim from 0.50H to 0.92H, ease power 1.3 |
| Text shadow | #000000 at 80 % | Soft shadow under white words (0, +3 px, blur 5 px at 720 wide) |

Brand-swap rule: replace Keyword lime and Lime glow with the user's brand colour (a bright, saturated hue; keep glow = same hue, slightly deeper). White and the floor never change.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, borders, masks, splits or background changes. |
| Floor scrim | Legibility aid only: darkens the bottom half smoothly, maximum 44 % black at the bottom edge. Always on for the whole video. |
| Crop | Cover-fit only when the source is not 9:16; crop anchor ✎ = the speaker's face. |

### 1.3 Layouts / grid

| Layout | Region (fractions) | Use |
|---|---|---|
| Caption line 1 (white) | centred on x = 0.50W; baseline y = 0.636H [1221] | Plain words before the keyword, or a white-only chunk |
| Caption line 2 (keyword) | centred on x = 0.50W; baseline y = 0.743H [1427]; line pitch 0.107H | The keyword, plus any plain words that follow it on the same baseline |
| Title strip | top of frame, y from 0.015H to ≈ 0.125H [29–240]; centred on x = 0.50W | T1 and T2 |
| Edge margin | every glyph ≥ 0.04W from the left and right edges | All text |

Measured on the reference: white line 1 baseline 0.626–0.641H; lime line baseline 0.743H; a two-word keyword line spans up to 0.65W.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Plain caption word | Clean grotesque, semibold, mixed case as written, vertical white gradient | Inter SemiBold (opsz 28, wght 600) | SF-like: Manrope SemiBold, DM Sans SemiBold | 0.111W [120]; at 720 wide 80 px; word space 0.85 × normal |
| Keyword | Heavy slanted grotesque, mixed case, lime, green glow | Barlow Black Italic | Barlow ExtraBold Italic, Archivo Black Italic | 0.162W [175]; at 720 wide 117 px; word space 0.6 × normal |
| Title | Tall condensed heavy caps, sheared 0.22 to the right, outline only (ring ≈ 2 px at 720 wide), halftone-dotted dark fill | Anton, sheared | Bebas Neue, Barlow Condensed Black Italic | cap height 0.105H (T1) / 0.085H (T2); T1 of 6 letters ≈ 0.66W wide |

Rules: captions keep the user's case. Titles are UPPERCASE (the only forced case). Max one lime keyword group per chunk. No outline-only captions.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Caption word entrance | ease-out cubic alpha 0 → 1, scale 0.92 → 1 about the word centre, rise 8 px → 0 (720 wide) | 4 f (0.17 s) |
| Caption chunk exit | linear alpha fade, ends exactly when the next chunk starts | 3 f (0.125 s) |
| Title entrance | ease-out cubic slide in from the left (x offset −0.7W → 0) with alpha | 0.25 s |
| Title exit | ease-in cubic slide out to the right (+0.7W) fading to 20 % | 0.25 s |
| Echo stack entrance | each row ease-out cubic from 0.05H above, rows staggered 0.07 s | 0.30 s |
| Cuts | footage cuts untouched; captions continue across them | 0 f |

Never: bounce or overshoot beyond the 0.92 → 1 settle, letter-by-letter typing, wipes, shake, flashes, caption rotation, caption shadows in colours, extra colours, effects on the footage.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Bottom floor scrim | Per 1.2: max 44 % black, smooth, whole video |
| Text overlays, glow and title overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; cards, splits, B-roll frames, background swaps, graphic transitions; blur, glitch, warp, zoom, flashes, grading. The footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Captions sit below 0.55H; the title strip stays above the face box top. |
| Title strip | If the face box top is above 0.17H, shrink the title cap height until its bottom edge is ≥ 0.02H above the face box top, or skip titles on that shot. |
| Caption block | If the face box bottom is below 0.56H, move both caption baselines down by the overlap (max +0.06H); if still overlapping, drop line 1 to a white-only chunk below the chin. |
| Footage text (signs, UI) | If readable text sits in the caption block for > 1 s, shift the block up by 0.08H when no face is there. |
| Edges | Glyphs ≥ 0.04W from the edges. A keyword line wider than 0.92W: move the last word of the keyword group to line 1 as plain white. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **T** title · **K** keyword treatment · **X** cut handoff · **E** end.
Energy legend: ● calm · ●● medium · ●●● high.

### C1 · SPLIT-LINE CAPTION — C ●● (signature, the caption system)
**What it is:** a phrase appears word by word. The plain words stand on line 1 in white; the keyword drops to line 2 in heavy lime italic with a green glow.
**Use when:** any speech or voice-over. **Avoid when:** the phrase has no keyword (use C2).
**Text (✎):** the user's exact words. Chunk: 2–5 words, split at punctuation and natural phrases, never end on an article, preposition or conjunction. Keyword ✎: 1 meaning-carrying noun or verb per chunk, ≤ 1 chunk in 3 may skip it.
**Geometry / Graphics:** Caption lines 1 and 2 (1.3). The whole chunk is laid out before it starts, so no word ever moves. Plain words before the keyword go on line 1; the keyword goes on line 2.
**Motion (measured on the reference, 24 fps):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | each word | alpha, scale, rise | 0 → 1, 0.92 → 1, 8 px → 0 | ease-out, 4 f |
| word start ✎ | earlier words | — | unchanged | — |
| chunk end ✎ | all words | alpha | 1 → 0 | linear, 3 f; ends at the next chunk's first word start |

Word start = the word's spoken start time. Chunk end = min(last word start + 1.4 s, next chunk start); the last chunk ends at the end of speech + 0.1 s.
**Footage / plate behaviour:** untouched except the floor scrim.
**Captions during it:** this is the caption system; it continues across cuts without a break.
**Exit:** 3 f linear fade.
**Build notes:** render every word once at 2x with Pillow (white: gradient fill + blurred shadow; keyword: blurred lime glow + shadow + fill), downscale with LANCZOS when pasting; lay out centred lines per chunk; fade by multiplying alpha.
**Flow prompt text:** "In the lower part of the frame, captions appear word by word. Ordinary words are clean white; the important word, {{KEYWORD}}, sits on its own line below in heavy slanted lime green letters with a soft green glow. Each word pops in with a tiny rise, and the phrase fades quickly before the next one."
**Still-image state:** one full chunk.

### C2 · WHITE-ONLY LINE — C ● 
**What it is:** a chunk with no keyword: one centred white line on line 1.
**Use when:** connective phrases between keyword beats, lists of small words. **Avoid when:** two C2 in a row (add a keyword to the second).
**Text (✎):** 2–4 plain words.
**Geometry / Graphics:** line 1 only (baseline 0.636H).
**Motion:** as C1 (same word entrance, 3 f exit).
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** same layer builder as C1.
**Flow prompt text:** "A short line of clean white words, {{WORDS}}, pops in word by word in the lower part of the frame, then fades."
**Still-image state:** the line.

### C3 · SOLO KEYWORD — C ●●
**What it is:** the keyword alone on line 2 with line 1 empty, for one-word beats.
**Use when:** a standalone key word or an exclamation. **Avoid when:** more than 2× in a video.
**Text (✎):** 1 word.
**Geometry / Graphics:** line 2 only (baseline 0.743H), centred.
**Motion:** as C1; hold ≥ 0.5 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** same builder.
**Flow prompt text:** "One big word, {{WORD}}, pops in on its own in heavy slanted lime green letters with a green glow, then fades."
**Still-image state:** the word.

### K1 · KEYWORD WITH TAIL — K ●●
**What it is:** the keyword on line 2 followed on the same baseline by plain white words that continue the phrase.
**Use when:** the keyword sits mid-phrase ("… lime word, then a few plain words").
**Text (✎):** keyword + 1–2 trailing plain words.
**Geometry / Graphics:** line 2 holds [keyword][plain words] centred as one run; the trailing words use the white style at 80 px (720 wide) on the lime baseline.
**Motion:** each word enters at its own start time (C1 motion).
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** layout the whole run once so the keyword does not shift when the tail arrives.
**Flow prompt text:** "The key word {{KEYWORD}} sits on the lower line in lime, and the plain white words {{TAIL}} pop in next to it on the same line."
**Still-image state:** the full run.

### K2 · KEYWORD PAIR — K ●●
**What it is:** two keywords share line 2 in lime, for a two-word idea.
**Use when:** a short noun phrase or number plus unit is the point. **Avoid when:** the pair is wider than 0.92W (keep one word lime).
**Text (✎):** 2 words.
**Geometry / Graphics:** line 2, both words lime with glow, word space 0.6 × normal.
**Motion:** C1 motion for each word; second word at its own start time.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade.
**Build notes:** same builder.
**Flow prompt text:** "Two key words, {{WORDS}}, pop in one after the other on the lower line in lime green with a glow."
**Still-image state:** the pair.

### T1 · OUTLINE TITLE SLIDE — T ●●● (signature opener)
**What it is:** one giant outlined italic title slides in from the left along the top of the frame, holds, and slides out to the right.
**Use when:** the opening line names the topic, or at the first topic word. **Avoid when:** the face box top is above 0.17H and cannot be cleared (1.7).
**Text (✎):** 1 word (≤ 8 letters) from the user's own words, UPPERCASE.
**Geometry / Graphics:** title strip; cap height 0.105H [201]; centred on x = 0.50W; top y = 0.015H. Outlined: white ring 2 px with red and cyan copies ±2.5 px (720 wide); fill black 34 % with halftone dots (9 px pitch at 2x, 3 px dots, 14 % white).
**Motion (measured on the reference, slide in about 6 f, held 2.9 s, out about 4 f):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start ✎ (0.2–0.6 s) | title | x offset, alpha | −0.7W → 0, 0 → 1 | ease-out cubic, 0.25 s |
| hold ✎ (1.5–2.5 s) | title | — | settled | — |
| end ✎ | title | x offset, alpha | 0 → +0.7W, 1 → 0.2 | ease-in cubic, 0.25 s |

The hold may run across a footage cut. It never starts within 3 f after a cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 runs below.
**Exit:** slide out to the right.
**Build notes:** draw text at 2x, shear with an affine (0.22), ring = MaxFilter(7) minus the mask, shift copies, paste.
**Flow prompt text:** "Near the start, a giant slanted outlined word, {{TITLE}}, with thin white edges and a faint red and blue fringe, slides across the top of the frame from the left, stays for a couple of seconds, then slides away to the right. It never covers the speaker's face."
**Still-image state:** settled.

### T2 · ECHO STACK TITLE — T ●●●
**What it is:** the title appears as three stacked copies rising upward and fading, like an echo above the main row.
**Use when:** a payoff word near the end, or a topic repeat. **Avoid when:** T1 played < 3 s ago.
**Text (✎):** 1 word from the user's words, UPPERCASE.
**Geometry / Graphics:** cap height 0.085H [163]; main row top y = 0.02H; echoes shifted up by 0.062H each (partly off the top edge), alpha 1.0 / 0.5 / 0.25; same outline and fill as T1.
**Motion (measured on the reference, held about 1.7 s):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start ✎ | row r (0, 1, 2) | y, alpha | −0.05H → 0, 0 → row alpha | ease-out cubic 0.30 s, delay 0.07 s × r |
| end ✎ | all rows | alpha | → 0 | linear 0.2 s |

**Footage / plate behaviour:** untouched; the stack stays above the face box top.
**Captions during it:** C1 below.
**Exit:** 0.2 s fade.
**Build notes:** one title layer pasted three times.
**Flow prompt text:** "A giant slanted outlined word, {{TITLE}}, repeats three times stacked at the top of the frame, each copy fainter than the one below, and rises in with a soft slide, then fades away."
**Still-image state:** the stack at rest.

### X1 · CUT HANDOFF — X ●
**What it is:** at a footage cut the caption chunk in progress keeps playing; chunk boundaries are placed on cuts when the speech allows.
**Use when:** every cut. **Avoid when:** never.
**Text (✎):** none.
**Geometry / Graphics:** captions stay in the same lines across the cut; the floor stays constant.
**Motion:** no effect on the cut; if a chunk boundary falls within 0.25 s of a cut, move it onto the cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** continue.
**Exit:** none.
**Build notes:** align chunk starts with scene-detect times when speech starts within 0.25 s of a cut.
**Flow prompt text:** "At every cut the captions simply carry on without any effect."
**Still-image state:** n/a.

### E1 · CLOSER KEYWORD HOLD — E ●●
**What it is:** the last chunk holds longer than the others, with its keyword on the lime line, and the video ends on it.
**Use when:** the last line is the payoff or call to action.
**Text (✎):** the last phrase.
**Geometry / Graphics:** C1 layout; optional T2 above.
**Motion:** C1 entrances; chunk end = end of speech + 0.1 s with the 3 f fade.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** 3 f fade at the end of speech.
**Build notes:** extend the last chunk's end only; never past the video end.
**Flow prompt text:** "On the final line, the last key word {{KEYWORD}} lands in lime on the lower line and stays until the speaker finishes."
**Still-image state:** the final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 on the topic word, C1 | C1 / C2 / K1 / X1 on every cut | T2 on the payoff word, E1 |
| Single talking head | T1, C1 | C1, C3 on one-word beats, K2 for a pair | E1 |
| B-roll only | C1 on the first line | C1 / K1, X1 on each cut | E1 |
| Still image | T1 settled + C1 chunk | n/a | n/a |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
