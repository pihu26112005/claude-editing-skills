# moments.md — Shard Dissolve: Style Bible + Moment Library

This file is the single source of truth for the Shard Dissolve style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, measured on a 304x540, 24 fps, 12.0 s reference reel and tuned on a 720x1280 render. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** a hot vermilion-orange reel where slanted orange slats slice across the footage, the picture shrinks into an orange frame with a square B-roll card and a giant outline word ticking along the bottom, shots dissolve through drifting grain, and every caption mixes thin white words with heavy italic white keywords.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 24 fps, so "f" values are 24 fps frames; at another fps keep the seconds. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Vermilion | #DB4B31 | Slats, the frame around the inset window, grain specks (measured 219,75,49) |
| Title yellow | #FDFF62 | The opening title (measured 253,255,98) |
| Caption white | #FFFFFF | All caption words, light and heavy |
| Outline orange | #FFA15C | Stroke of the giant ticker word (measured 255,161,92) |
| Grain dark | #7A2A1A | Dark specks in the grain dissolve (design decision) |
| Grain light | #F0804A | Light specks in the grain dissolve (design decision) |
| Page | #F2F2F2 | Closing word wall background (measured near 234–242) |
| Wall word | #E0E0E0 | Closing word wall letters (measured 224) |
| Caption shadow | #000000 at 62 % | Soft shadow under every caption (blur 9 px, offset +7 px at 720 wide; needed because the reference captions sat on dark clothing and our footage can be bright) |

Brand-swap rule: if the user gives a brand colour, replace Vermilion (and derive Outline orange as a lighter tint of it). Keep the yellow, white and greys. No other colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage, default | Full frame, 100 % of W and H, untouched. |
| Inset window (L1) | x 0.0625–0.9375W [68–1012], y 0.03–0.655H [58–1258]; sharp corners, no border. Shows the primary footage scaled to 0.875 and cropped from the top (crop anchor ✎: source rows shown start at 0 to 0.14H so the subject stays inside). The bottom 0.07H of the window is eaten by orange grain (speckled edge). Around it: flat Vermilion. |
| Card (L1) | Square-ish, x 0.17–0.83W [184–896], y 0.59–0.96H [1133–1843] (0.66W × 0.37H), sharp corners, no shadow, sits on top of the window's lower edge. Content ✎: one of the user's own shots (still frame, cover-fit). |
| Slats (X1, T1) | Parallelograms leaning right at the top: the bottom edge sits 0.156 × height to the left of the top edge (about 9°). Flat Vermilion, no outline. |
| Ticker word (K1) | Giant outline text, cap height 0.082H [157], stroke 0.0045W, no fill, vertical band 0.905–0.99H. Sits behind the card, in front of the orange. |
| Word wall (E1) | Light page with repeated rows of one giant grey word: cap height ≈ 0.10H, row pitch 0.165H, every other row offset by half a word, word width ≈ 0.80W. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Title band | 0.04, 0.032, 0.96, 0.125 | Opening title, width ≈ 0.85W (measured x 0.079–0.928, y 0.033–0.128) |
| Caption lane | centre x 0.50W, baseline 0.715H, max width 0.86W | All captions, in every layout (measured chunk centre y ≈ 0.70H) |
| Full layout | footage 0,0,1,1 | Default |
| Inset layout | window 0.0625,0.03,0.9375,0.655 + card 0.17,0.59,0.83,0.96 + ticker band | L1 |
| Slat opener bands | top 0–0.30H, middle 0.30–0.67H, bottom 0.67–1.0H; bars per band listed in T1 | T1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Heavy italic, UPPERCASE, tight tracking (−0.01em) | Barlow Black Italic | Archivo ExtraBold Italic (slanted), Anton | Sized so the line is ≈ 0.85W wide; cap height ≤ 0.10H |
| Caption heavy word (keyword) | Heavy italic, mixed case as written, tracking −0.02em | Barlow Black Italic | Barlow ExtraBold Italic, Archivo Black (slanted) | 0.105W [113] |
| Caption light word | Regular upright, mixed case as written | Barlow Regular | Inter Regular, Archivo Regular | 0.075W [81]; word gap 0.24 em |
| Ticker word | Heavy upright UPPERCASE, outline only | Barlow Black | Anton, Archivo Black | Cap height 0.082H |
| Wall word | Heavy upright UPPERCASE, flat grey | Barlow Black | Anton, Archivo Black | Cap height ≈ 0.10H |

Font note: identified by letterform only (wide, heavy, slightly humanist grotesque; light words very close to Barlow Regular). Check the render against the reference and fall back in the order above. Download from the Google Fonts GitHub repo (ofl/barlow) if missing.

Captions sit on one baseline: light and heavy words share it. Text case: captions exactly as the user wrote; only the title, ticker and wall words are uppercase. The title, ticker and wall use the same word, taken from the user's own words (the topic word).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Slat retract / slide-out | ease-in (cubic t³), each bar staggered 0.6 f | 11 f (0.46 s) |
| Slat slide-in (title exit) | ease-out (1−(1−t)³) | 5 f |
| Window shrink / grow | smoothstep (ease in-out) | 12 f (0.5 s) shrink, 10 f grow |
| Card rise | ease-out | 12 f |
| Card drop / swap-out | ease-in | 8 f |
| Caption chunk entrance | ease-out alpha ramp, no movement | 5 f |
| Caption chunk exit | hard cut | 1 f |
| Grain dissolve | linear progress, speckle band sweeping left to right | 10 f |
| Punch-in | ease-out scale | 6 f |

Never: bounce, overshoot, spring, rotation of footage, blur, glitch RGB split, shake, flashes, colour grading, letter-by-letter typing, per-word movement in captions.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Default |
| Scale to the inset window (0.875) with a top-anchored crop, then back (L1, L2) | Window always plays live footage in sync with the audio; it never freezes |
| Card with a still of one of the user's other shots (cover-fit) | Still only (or a ≤ 1.5 s silent loop of the user's own footage) |
| Slats and grain over the footage (T1, X1, X2) | Cover ≤ 60 % of the frame at any frame, never the speaking face for more than the grain's sparse specks (X2) |
| Punch-in 1.00 → 1.10 about the face or subject anchor (M1) | At a sentence boundary, never more than 1.12 total, reset only at a cut |
| Word wall dissolve (E1) | Only after the last spoken word, hides the footage for ≤ 1.5 s at the very end |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; freezing the primary window; blur, glitch, warp or colour grading; adding footage the user did not supply. The grain and slat remnants are orange or white specks, never frozen copies of the footage.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by captions, the card, slats, the title or the wall while it speaks. Slats in T1 stay in the outer thirds of the frame and in the bottom band. The title band must be clear of the head: if the head top is above 0.14H, shrink the title (min cap height 0.06H) or skip T1 and use a slat-only opener. |
| Caption lane | Baseline 0.715H. If the face bottom edge is below 0.62H, move the lane to 0.88H baseline in the full layout. In the inset layout the lane is on the card. |
| Inset layout | The subject (face or key object) must sit inside the window after the top-anchored crop. If not, choose crop anchor ✎ 0.05–0.14H, or do not use L1 on that shot. |
| Card | Never covers a face in the window: window bottom 0.655H must be below the chin (face bottom ≤ 0.58H). |
| Footage text (signs, UI) | If readable footage text sits in the caption lane for more than 1 s, use the full layout and move the lane. |
| Edges | Every caption glyph stays ≥ 0.04W from the left and right edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **X** cut treatment · **L** layout change · **K** ticker · **C** caption · **M** footage motion · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · SLAT OPENER — T ●●● (signature opener)
**What it is:** the first frame is already sliced: slanted orange slats cover the edges and the bottom of the picture while a heavy italic yellow title sits across the top. The slats slide away, then the title is cut by orange bars sweeping across its band.
**Use when:** every video, at 0.0 s. **Avoid when:** the head top is above 0.14H and the title cannot shrink (use slats only), or the first frame is a cut into B-roll with no face (still fine, the title is the topic word).
**Text (✎):** one topic word from the user's own words, UPPERCASE, max 10 characters (a short word fills the width at a larger font; a long word shrinks, min cap height 0.06H).
**Geometry / Graphics:** title band (1.3), yellow, heavy italic, no outline, no shadow. Slat bars (x of top edge, width, as fractions of W), per band:

| Band | Bars |
|---|---|
| top 0–0.30H | (−0.06, 0.15), (0.80, 0.07), (0.90, 0.16) |
| middle 0.30–0.67H | (−0.02, 0.07), (0.84, 0.18) |
| bottom 0.67–1.0H | (−0.05, 0.14), (0.22, 0.20), (0.50, 0.05), (0.60, 0.05), (0.69, 0.05), (0.91, 0.12) |

Bars lean right at the top by 0.156 × band height. The face box (about 0.34–0.66W, 0.14–0.40H) is never touched.
**Motion (measured on the reference, tuned on 24 fps):**

| t (f @24) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–6 | slats + title | hold | final opening state | — |
| 6–17 (+0.6 f per bar index) | top-band bars | y | 0 → −(band height + 80 px) | ease-in |
| 6–17 (+0.6 f per bar index) | bottom-band bars | y | 0 → +(band height + 80 px) | ease-in |
| 6–17 (+0.6 f per bar index) | middle-band bars | x | 0 → ±0.4W (outward) | ease-in |
| 26–38 ✎ | four bars over the title band (0–0.15H) | x | slide in from the right over 5 f (stagger 0.6 f), slide out to the left over 6 f | ease-out in, ease-in out |
| 26–32 | title | alpha | present until covered (covered by f 32), then gone | hard (hidden behind bars) |

Title exit start ✎: 1.0–1.3 s, or when the first caption chunk ends, whichever is later.
**Footage / plate behaviour:** footage plays live under everything.
**Captions during it:** C1 runs from the first word; it sits over the bottom slats and the footage (white on orange reads well).
**Exit:** bars off to the left after the title is covered.
**Build notes:** draw polygons at 2×, downscale to a float mask, then `frame = frame*(1−m) + orange*m`. Clip each band's mask to its rows so bars vanish at the band edge while sliding. Title: render with Pillow at 2×, crop to its bbox, downscale.
**Flow prompt text:** "The video opens already sliced: slanted bright orange bars cover the edges and the lower part of the picture, and a heavy slanted yellow title, {{TITLE_WORD}}, in capitals sits across the top without touching the face. After a quarter of a second the bars slide away up, down and outward. About a second later a set of orange bars sweeps across the top, wiping the title, and leaves."
**Still-image state:** title at the top, slats at the edges and the bottom.

### X1 · SLAT REVEAL CUT — X ●●● (signature cut)
**What it is:** on a cut into a shot without a face, the new shot appears already covered by six tall slanted orange bars, which then slide away alternately up and down.
**Use when:** a cut into B-roll, a product or any shot with no speaking face. **Avoid when:** the new shot has a speaking face, use X2.
**Text (✎):** none.
**Geometry / Graphics:** six full-height bars (x of top edge, width): (−0.02, 0.15), (0.20, 0.10), (0.36, 0.17), (0.58, 0.08), (0.70, 0.14), (0.90, 0.16). Lean 0.156 × H. Covers about 55 % of the frame at the cut frame.
**Motion:**

| t (f from the cut) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–2 | bars | hold | covering | — |
| 2–11 (+0.5 f per bar) | even bars | y | 0 → −(H + 300) | ease-in |
| 2–11 (+0.5 f per bar) | odd bars | y | 0 → +(H + 300) | ease-in |

**Footage / plate behaviour:** footage plays live under the bars; the cut itself is the footage's own cut.
**Captions during it:** the chunk in progress is replaced on the cut frame; captions are drawn above the bars.
**Exit:** bars gone by f 12.
**Build notes:** same mask code as T1.
**Flow prompt text:** "On the cut, the new shot appears partly hidden behind six tall slanted orange bars. They slide away, one up, the next down, and so on, until the shot is clear."
**Still-image state:** not used.

### X2 · GRAIN DISSOLVE — X ●● (signature cut)
**What it is:** a band of drifting orange and dark specks sweeps left to right across the new shot at the cut and thins out until the picture is clean.
**Use when:** a cut into a shot with a face, or any cut that needs a softer beat. **Avoid when:** two cuts are closer than 0.5 s.
**Text (✎):** none.
**Geometry / Graphics:** a speckle field of three orange tones (#DB4B31, #7A2A1A, #F0804A), 1 px specks. Per pixel: field = 0.55 × x/W + 0.45 × noise; threshold thr = progress × 1.25 − 0.1; specks appear where thr < field < thr + 0.28 with density 0.55 at the band centre falling to 0 at its edges. Peak coverage ≤ 55 %, sparse enough that a face stays readable.
**Motion (measured: the reference dissolves over about 9 f at 7.75–8.1 s and 9.4–9.8 s):**

| t (f from the cut) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–10 | speckle band | progress | 0 → 1 | linear |

**Footage / plate behaviour:** footage plays live; only specks are drawn over it.
**Captions during it:** unchanged, drawn above.
**Exit:** specks are gone at f 10.
**Build notes:** fixed noise fields (seed fixed); blend `frame*(1−a) + speck*a`.
**Flow prompt text:** "On the cut, a band of tiny orange and dark specks drifts from left to right across the new shot and thins out until the picture is clean."
**Still-image state:** not used.

### L1 · INSET WINDOW AND CARD — L ●●● (signature middle)
**What it is:** the picture shrinks into an orange frame and a square card with another of the user's shots rises into the lower half, while the ticker word (K1) appears behind it.
**Use when:** two or three steps in a row, a list, B-roll sequences of 2–3.5 s, a long calm shot (> 2 s). **Avoid when:** the subject is not inside the window after the crop, or the shot is shorter than 1.2 s.
**Text (✎):** none (the card is footage).
**Geometry / Graphics:** inset layout (1.2, 1.3). Card content ✎: a cover-fit still from the previous shot (previous step) or the next shot (preview). Crop anchor ✎ 0–0.14H.
**Motion (measured: shrink 4.38–4.88 s, card rise about the same; tuned values on 24 fps):**

| t (f @24) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| s ✎ → s+12 | window | rect | full frame → window rect (and crop 0 → anchor) | smoothstep |
| s+2 → s+14 | card | y offset | +(H − 0.59H + 20 px) → 0 | ease-out |
| s+2 → s+14 | ticker | y offset / alpha | +140 px → 0 | ease-out |
| at a cut inside L1 | old card | y offset | 0 → down off screen over 8 f | ease-in |
| cut+4 → cut+16 | new card | y offset | from below → 0 | ease-out |

Start s ✎: ≥ 3 f after a cut (the demo used 3 f after the cut).
**Footage / plate behaviour:** window plays live footage at 0.875 scale; the bottom 0.07H of its edge dissolves into grain. Cuts inside L1 happen in the window as usual.
**Captions during it:** same lane (baseline 0.715H); the text sits on the card.
**Exit:** L2.
**Build notes:** fill the canvas with Vermilion, resize the frame into the window rect with `Image.resize(box=…)`, speckle the bottom edge with a fixed noise (keep pixel if noise < distance to the edge), then ticker, then card.
**Flow prompt text:** "The picture shrinks smoothly into a bright orange frame. A square card with another shot from the video rises into the lower half, and a giant outlined word scrolls slowly along the bottom behind it. The bottom edge of the shrunken picture breaks up into orange grain."
**Still-image state:** settled inset layout with one card.

### L2 · INSET EXIT — L ●● (extension in the same grammar, measured 7.0–7.4 s)
**What it is:** the card drops away, the ticker slides down and the window grows back to full frame.
**Use when:** L1 has run its steps; a section ends; the speaker returns. **Avoid when:** the footage within the next 3 f has a cut (start after the cut).
**Text (✎):** none.
**Geometry / Graphics:** inverse of L1.
**Motion:**

| t (f from start) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–8 | card, ticker | y offset | 0 → down off screen | ease-in |
| 0–10 | window | rect | window → full frame | smoothstep |

Start ✎: on a sentence boundary or ≥ 5 f after a cut.
**Footage / plate behaviour:** live.
**Captions during it:** unchanged.
**Exit:** full layout.
**Build notes:** reverse the L1 parameters.
**Flow prompt text:** "The card slides down out of the frame and the shrunken picture grows smoothly back to fill the whole screen."
**Still-image state:** not used.

### K1 · OUTLINE TICKER — K ● (signature element of L1)
**What it is:** one giant outline-only word, repeated, creeping sideways along the bottom edge.
**Use when:** only inside L1. **Avoid when:** outside the inset layout.
**Text (✎):** the title word (the topic word of T1), UPPERCASE.
**Geometry / Graphics:** cap height 0.082H, band 0.905–0.99H, stroke 0.0045W in Outline orange, no fill, word gap 0.12W. Letters bleed off both edges.
**Motion:** continuous scroll to the left at 0.0085W per frame (0.20W per second), looping seamlessly. Enters and exits with L1.
**Footage / plate behaviour:** none.
**Captions during it:** none (captions sit well above).
**Exit:** slides down with L2.
**Build notes:** draw glyphs with `stroke_width` at 2×, then clear the interior with a glyph mask, so only the outline remains.
**Flow prompt text:** "Along the bottom of the orange frame, a huge outlined word, {{TITLE_WORD}}, in capitals, repeats and drifts slowly sideways, running off both edges."
**Still-image state:** the word as an outline along the bottom.

### C1 · SPLIT-WEIGHT CAPTION — C ●● (signature, the caption system)
**What it is:** a short chunk of white words in one line where plain words are thin and upright and the keywords are heavy and slanted. The whole chunk fades in at once and is replaced by the next one.
**Use when:** always. **Avoid when:** never.
**Text (✎):** the user's exact words, case as written. Chunk rules: 2–4 words per chunk, one line, ≤ 0.86W wide (≈ 24 characters); split at punctuation and natural phrases; never end on an article, preposition or conjunction; 0.5–1.5 s per chunk; prefer chunk changes at cuts. Keywords ✎: 0–2 heavy words per chunk (the meaning-carrying nouns and verbs); a chunk with no keyword is allowed and gives rhythm, at most one in four chunks; never mark more than half the words in a chunk unless it is C2.
**Geometry / Graphics:** caption lane, centred on x = 0.50W, baseline 0.715H. Heavy words 0.105W (Barlow Black Italic, tracking −0.02em), light words 0.075W (Barlow Regular), word gap 0.24 em of the light size, all on one baseline. White, with the caption shadow (1.1).
**Motion (measured on the reference; tuned on 24 fps):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| chunk start ✎ (first word's spoken start) | whole chunk | alpha | 0 → 1 (starts as a dim grey ghost) | ease-out, 5 f |
| chunk end ✎ | whole chunk | alpha | 1 → 0 | hard cut |

Chunk end = the next chunk's start (no gap) or min(last word end + 0.1 s, next cut).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system, above all slats, grain and card (never above the wall's final state if the wall hides the footage: keep it, the shadow keeps it legible).
**Exit:** hard cut.
**Build notes:** render each chunk once to an RGBA layer at 2× (draw light and heavy words with `anchor="ls"` on one baseline, heavy words char by char for tracking), bake the shadow, downscale, fade by multiplying alpha.
**Flow prompt text:** "Near the lower middle of the frame, short captions appear as one line of white words. Ordinary words are thin and upright; important words, {{KEYWORDS}}, are heavy and slanted. The whole line fades in at once and is replaced by the next line. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one chunk.

### C2 · HEAVY SOLO CHUNK — C ●● (extension in the same grammar)
**What it is:** one single word, or a short phrase, all heavy and slanted, for a verdict or a number.
**Use when:** a one-word punch ("overrated", a list item name, a number, an amount). **Avoid when:** two C2 are < 3 s apart (use at most 1 per 3 s).
**Text (✎):** 1–2 user words, case as written, with their punctuation.
**Geometry / Graphics:** as C1 but every word heavy at 0.105W; if a single word is shorter than 0.4W wide it may grow to 0.13W (design decision).
**Motion:** as C1.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** hard cut.
**Build notes:** same layer builder, all kinds = heavy.
**Flow prompt text:** "A single word, {{WORD}}, appears in heavy slanted white letters in the lower middle and holds until the next line."
**Still-image state:** one word.

### M1 · PUNCH-IN — M ●● (extension in the same grammar, measured at the reference's 0.79 s reframing)
**What it is:** the footage is re-framed larger about the speaker's face at a sentence boundary, as a short scale ramp.
**Use when:** a long static talking-head shot (> 2 s) at a sentence or payoff, before the closer. **Avoid when:** a cut is within 3 f, or the face would leave the safe zone.
**Text (✎):** none.
**Geometry / Graphics:** anchor ✎ = face centre (default x 0.50W, y 0.30H). Scale 1.00 → 1.10.
**Motion:**

| t (f from start) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–6 | footage | scale about the anchor | 1.00 → 1.10 | ease-out |

Hold until the shot ends; reset on the next cut.
**Footage / plate behaviour:** crop and scale only, no resample artefacts (Lanczos with `box`).
**Captions during it:** unchanged.
**Exit:** the next cut.
**Build notes:** `Image.resize((W,H), LANCZOS, box=(bx,by,bx+W/s,by+H/s))` with the anchor kept fixed.
**Flow prompt text:** "On this sentence the camera pushes in slightly toward the speaker's face, smoothly, and stays there until the shot ends."
**Still-image state:** not used.

### E1 · WORD WALL DISSOLVE — E ●●● (signature closer)
**What it is:** after the last spoken word the footage disintegrates into white specks from left to right and a light page of giant grey repeated words takes its place.
**Use when:** the last line ends the video (mandatory closer). **Avoid when:** the video ends mid-sentence, or the user needs the footage visible to the last frame (then run only the speck band and stop at 50 %).
**Text (✎):** the title word, UPPERCASE (same word as T1).
**Geometry / Graphics:** word wall (1.2): rows alternate horizontal offset and shift left by 0.13W per row; page #F2F2F2, words #E0E0E0. Speck band 0.16W wide (white and #EBEBEB specks, density up to 0.85).
**Motion (measured: the reference dissolves in about 9 f at 9.96 s and then holds the wall for 2 s; tuned on 24 fps so the wall never covers a speaking face):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| speech end − 0.5 → speech end ✎ | wall front | x | −0.05W → 0.20W | smoothstep (slow creep at the left edge, clear of the face) |
| speech end → speech end + 0.19 | wall front | x | 0.20W → 1.15W | ease-in |
| to the end of the video | wall | hold | wall visible | — |

**Footage / plate behaviour:** footage plays live to the end; the wall hides it only after the speech ends, for ≤ 1.5 s at the end of the video.
**Captions during it:** the final chunk stays above the wall.
**Exit:** none (end of video). For a longer ending ✎: hold the wall up to 1.5 s.
**Build notes:** build the wall once (draw words at 2×, downscale). Per pixel: wall alpha = clamp((front − x) / 0.08); speck alpha = noise < clamp((front + 0.08 − x) / 0.16) × 0.85 where the wall is not yet full; blend wall, white specks, footage.
**Flow prompt text:** "After the last word, the picture breaks into tiny white specks that sweep from left to right and leave behind a pale grey page filled with a giant repeated word, {{TITLE_WORD}}, in capitals, in rows that alternate in position. The last caption stays on top."
**Still-image state:** the wall with one caption.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | X1 on each B-roll cut, L1 over 2–3 B-roll shots (card = previous step), L2, X2 into the speaker | M1 then E1 |
| Single talking head | T1 | M1 at the second sentence, L1 only if there is other footage for the card, C2 on the verdict | E1 |
| B-roll only | T1 (title over the first shot) | X1 on every cut, L1 over the longest run, C2 on a punch line | E1 (hold ≤ 1.5 s) |
| Still image | T1 settled state | C1 chunk, K1 along the bottom | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
