# Google Flow prompt · Shard Dissolve
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Shard Dissolve" motion style to it.

The look in one sentence: Slanted vermilion slats slice the footage, the picture shrinks into an orange inset with a B-roll card and giant outline word, shots dissolve through grain, thin white captions with heavy italic keywords.

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
| Vermilion | #DB4B31 | Slats, the frame around the inset window, grain specks |
| Title yellow | #FDFF62 | The opening title |
| Caption white | #FFFFFF | All caption words, light and heavy |
| Outline orange | #FFA15C | Stroke of the giant ticker word |
| Grain dark | #7A2A1A | Dark specks in the grain dissolve |
| Grain light | #F0804A | Light specks in the grain dissolve |
| Page | #F2F2F2 | Closing word wall background |
| Wall word | #E0E0E0 | Closing word wall letters |
| Caption shadow | #000000 at 62 % | Soft shadow under every caption (blur 9 px, offset +7 px at 720 wide; needed because the reference captions sat on dark clothing and our footage can be bright) |

Brand-swap rule: if the user gives a brand colour, replace Vermilion (and derive Outline orange as a lighter tint of it). Keep the yellow, white and greys. No other colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage, default | Full frame, 100 % of W and H, untouched. |
| Inset window (L1) | x 0.0625–0.9375W [68–1012], y 0.03–0.655H [58–1258]; sharp corners, no border. Shows the primary footage scaled to 0.875 and cropped from the top (crop anchor : source rows shown start at 0 to 0.14H so the subject stays inside). The bottom 0.07H of the window is eaten by orange grain (speckled edge). Around it: flat Vermilion. |
| Card (L1) | Square-ish, x 0.17–0.83W [184–896], y 0.59–0.96H [1133–1843] (0.66W × 0.37H), sharp corners, no shadow, sits on top of the window's lower edge. Content : one of the user's own shots (still frame, cover-fit). |
| Slats (X1, T1) | Parallelograms leaning right at the top: the bottom edge sits 0.156 × height to the left of the top edge (about 9°). Flat Vermilion, no outline. |
| Ticker word (K1) | Giant outline text, cap height 0.082H [157], stroke 0.0045W, no fill, vertical band 0.905–0.99H. Sits behind the card, in front of the orange. |
| Word wall (E1) | Light page with repeated rows of one giant grey word: cap height ≈ 0.10H, row pitch 0.165H, every other row offset by half a word, word width ≈ 0.80W. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Title band | 0.04, 0.032, 0.96, 0.125 | Opening title, width ≈ 0.85W |
| Caption lane | centre x 0.50W, baseline 0.715H, max width 0.86W | All captions, in every layout |
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
| Inset layout | The subject (face or key object) must sit inside the window after the top-anchored crop. If not, choose crop anchor 0.05–0.14H, or do not use L1 on that shot. |
| Card | Never covers a face in the window: window bottom 0.655H must be below the chin (face bottom ≤ 0.58H). |
| Footage text (signs, UI) | If readable footage text sits in the caption lane for more than 1 s, use the full layout and move the lane. |
| Edges | Every caption glyph stays ≥ 0.04W from the left and right edges. |

---

## 7. MOMENT LIBRARY
Family codes: **T** title · **X** cut treatment · **L** layout change · **K** ticker · **C** caption · **M** footage motion · **E** ending.

### MOMENT T1 · SLAT OPENER
**What it is:** the first frame is already sliced: slanted orange slats cover the edges and the bottom of the picture while a heavy italic yellow title sits across the top. The slats slide away, then the title is cut by orange bars sweeping across its band.
**Use when:** every video, at 0.0 s. **Avoid when:** the head top is above 0.14H and the title cannot shrink (use slats only), or the first frame is a cut into B-roll with no face (still fine, the title is the topic word).
**Text:** one topic word from the user's own words, UPPERCASE, max 10 characters (a short word fills the width at a larger font; a long word shrinks, min cap height 0.06H).
**Geometry / Graphics:** title band (1.3), yellow, heavy italic, no outline, no shadow. Slat bars (x of top edge, width, as fractions of W), per band:

| Band | Bars |
|---|---|
| top 0–0.30H | (−0.06, 0.15), (0.80, 0.07), (0.90, 0.16) |
| middle 0.30–0.67H | (−0.02, 0.07), (0.84, 0.18) |
| bottom 0.67–1.0H | (−0.05, 0.14), (0.22, 0.20), (0.50, 0.05), (0.60, 0.05), (0.69, 0.05), (0.91, 0.12) |

Bars lean right at the top by 0.156 × band height. The face box (about 0.34–0.66W, 0.14–0.40H) is never touched.
**Motion:**

| t (f @24) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–6 | slats + title | hold | final opening state | — |
| 6–17 (+0.6 f per bar index) | top-band bars | y | 0 → −(band height + 80 px) | ease-in |
| 6–17 (+0.6 f per bar index) | bottom-band bars | y | 0 → +(band height + 80 px) | ease-in |
| 6–17 (+0.6 f per bar index) | middle-band bars | x | 0 → ±0.4W (outward) | ease-in |
| 26–38 | four bars over the title band (0–0.15H) | x | slide in from the right over 5 f (stagger 0.6 f), slide out to the left over 6 f | ease-out in, ease-in out |
| 26–32 | title | alpha | present until covered (covered by f 32), then gone | hard (hidden behind bars) |

Title exit start: 1.0–1.3 s, or when the first caption chunk ends, whichever is later.
**Footage / plate behaviour:** footage plays live under everything.
**Captions during it:** C1 runs from the first word; it sits over the bottom slats and the footage (white on orange reads well).
**Exit:** bars off to the left after the title is covered.
**Flow prompt text:** "The video opens already sliced: slanted bright orange bars cover the edges and the lower part of the picture, and a heavy slanted yellow title, {{TITLE_WORD}}, in capitals sits across the top without touching the face. After a quarter of a second the bars slide away up, down and outward. About a second later a set of orange bars sweeps across the top, wiping the title, and leaves."
**Still-image state:** title at the top, slats at the edges and the bottom.

### MOMENT X1 · SLAT REVEAL CUT
**What it is:** on a cut into a shot without a face, the new shot appears already covered by six tall slanted orange bars, which then slide away alternately up and down.
**Use when:** a cut into B-roll, a product or any shot with no speaking face. **Avoid when:** the new shot has a speaking face, use X2.
**Text:** none.
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
**Flow prompt text:** "On the cut, the new shot appears partly hidden behind six tall slanted orange bars. They slide away, one up, the next down, and so on, until the shot is clear."
**Still-image state:** not used.

### MOMENT X2 · GRAIN DISSOLVE
**What it is:** a band of drifting orange and dark specks sweeps left to right across the new shot at the cut and thins out until the picture is clean.
**Use when:** a cut into a shot with a face, or any cut that needs a softer beat. **Avoid when:** two cuts are closer than 0.5 s.
**Text:** none.
**Geometry / Graphics:** a speckle field of three orange tones (#DB4B31, #7A2A1A, #F0804A), 1 px specks. Per pixel: field = 0.55 × x/W + 0.45 × noise; threshold thr = progress × 1.25 − 0.1; specks appear where thr < field < thr + 0.28 with density 0.55 at the band centre falling to 0 at its edges. Peak coverage ≤ 55 %, sparse enough that a face stays readable.
**Motion:**

| t (f from the cut) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–10 | speckle band | progress | 0 → 1 | linear |

**Footage / plate behaviour:** footage plays live; only specks are drawn over it.
**Captions during it:** unchanged, drawn above.
**Exit:** specks are gone at f 10.
**Build notes:** fixed noise fields (seed fixed); blend `frame*(1−a) + speck*a`.
**Flow prompt text:** "On the cut, a band of tiny orange and dark specks drifts from left to right across the new shot and thins out until the picture is clean."
**Still-image state:** not used.

### MOMENT L1 · INSET WINDOW AND CARD
**What it is:** the picture shrinks into an orange frame and a square card with another of the user's shots rises into the lower half, while the ticker word (K1) appears behind it.
**Use when:** two or three steps in a row, a list, B-roll sequences of 2–3.5 s, a long calm shot (> 2 s). **Avoid when:** the subject is not inside the window after the crop, or the shot is shorter than 1.2 s.
**Text:** none (the card is footage).
**Geometry / Graphics:** inset layout (1.2, 1.3). Card content: a cover-fit still from the previous shot (previous step) or the next shot (preview). Crop anchor 0–0.14H.
**Motion:**

| t (f @24) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| s → s+12 | window | rect | full frame → window rect (and crop 0 → anchor) | smoothstep |
| s+2 → s+14 | card | y offset | +(H − 0.59H + 20 px) → 0 | ease-out |
| s+2 → s+14 | ticker | y offset / alpha | +140 px → 0 | ease-out |
| at a cut inside L1 | old card | y offset | 0 → down off screen over 8 f | ease-in |
| cut+4 → cut+16 | new card | y offset | from below → 0 | ease-out |

Start s: ≥ 3 f after a cut (the demo used 3 f after the cut).
**Footage / plate behaviour:** window plays live footage at 0.875 scale; the bottom 0.07H of its edge dissolves into grain. Cuts inside L1 happen in the window as usual.
**Captions during it:** same lane (baseline 0.715H); the text sits on the card.
**Exit:** L2.
**Build notes:** fill the canvas with Vermilion, resize the frame into the window rect with `Image.resize(box=…)`, speckle the bottom edge with a fixed noise (keep pixel if noise < distance to the edge), then ticker, then card.
**Flow prompt text:** "The picture shrinks smoothly into a bright orange frame. A square card with another shot from the video rises into the lower half, and a giant outlined word scrolls slowly along the bottom behind it. The bottom edge of the shrunken picture breaks up into orange grain."
**Still-image state:** settled inset layout with one card.

### MOMENT L2 · INSET EXIT
**What it is:** the card drops away, the ticker slides down and the window grows back to full frame.
**Use when:** L1 has run its steps; a section ends; the speaker returns. **Avoid when:** the footage within the next 3 f has a cut (start after the cut).
**Text:** none.
**Geometry / Graphics:** inverse of L1.
**Motion:**

| t (f from start) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–8 | card, ticker | y offset | 0 → down off screen | ease-in |
| 0–10 | window | rect | window → full frame | smoothstep |

Start: on a sentence boundary or ≥ 5 f after a cut.
**Footage / plate behaviour:** live.
**Captions during it:** unchanged.
**Exit:** full layout.
**Build notes:** reverse the L1 parameters.
**Flow prompt text:** "The card slides down out of the frame and the shrunken picture grows smoothly back to fill the whole screen."
**Still-image state:** not used.

### MOMENT K1 · OUTLINE TICKER
**What it is:** one giant outline-only word, repeated, creeping sideways along the bottom edge.
**Use when:** only inside L1. **Avoid when:** outside the inset layout.
**Text:** the title word (the topic word of T1), UPPERCASE.
**Geometry / Graphics:** cap height 0.082H, band 0.905–0.99H, stroke 0.0045W in Outline orange, no fill, word gap 0.12W. Letters bleed off both edges.
**Motion:** continuous scroll to the left at 0.0085W per frame (0.20W per second), looping seamlessly. Enters and exits with L1.
**Footage / plate behaviour:** none.
**Captions during it:** none (captions sit well above).
**Exit:** slides down with L2.
**Build notes:** draw glyphs with `stroke_width` at 2×, then clear the interior with a glyph mask, so only the outline remains.
**Flow prompt text:** "Along the bottom of the orange frame, a huge outlined word, {{TITLE_WORD}}, in capitals, repeats and drifts slowly sideways, running off both edges."
**Still-image state:** the word as an outline along the bottom.

### MOMENT C1 · SPLIT-WEIGHT CAPTION
**What it is:** a short chunk of white words in one line where plain words are thin and upright and the keywords are heavy and slanted. The whole chunk fades in at once and is replaced by the next one.
**Use when:** always. **Avoid when:** never.
**Text:** the user's exact words, case as written. Chunk rules: 2–4 words per chunk, one line, ≤ 0.86W wide (≈ 24 characters); split at punctuation and natural phrases; never end on an article, preposition or conjunction; 0.5–1.5 s per chunk; prefer chunk changes at cuts. Keywords: 0–2 heavy words per chunk (the meaning-carrying nouns and verbs); a chunk with no keyword is allowed and gives rhythm, at most one in four chunks; never mark more than half the words in a chunk unless it is C2.
**Geometry / Graphics:** caption lane, centred on x = 0.50W, baseline 0.715H. Heavy words 0.105W (Barlow Black Italic, tracking −0.02em), light words 0.075W (Barlow Regular), word gap 0.24 em of the light size, all on one baseline. White, with the caption shadow (1.1).
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| chunk start (first word's spoken start) | whole chunk | alpha | 0 → 1 (starts as a dim grey ghost) | ease-out, 5 f |
| chunk end | whole chunk | alpha | 1 → 0 | hard cut |

Chunk end = the next chunk's start (no gap) or min(last word end + 0.1 s, next cut).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system, above all slats, grain and card (never above the wall's final state if the wall hides the footage: keep it, the shadow keeps it legible).
**Exit:** hard cut.
**Flow prompt text:** "Near the lower middle of the frame, short captions appear as one line of white words. Ordinary words are thin and upright; important words, {{KEYWORDS}}, are heavy and slanted. The whole line fades in at once and is replaced by the next line. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one chunk.

### MOMENT C2 · HEAVY SOLO CHUNK
**What it is:** one single word, or a short phrase, all heavy and slanted, for a verdict or a number.
**Use when:** a one-word punch ("overrated", a list item name, a number, an amount). **Avoid when:** two C2 are < 3 s apart (use at most 1 per 3 s).
**Text:** 1–2 user words, case as written, with their punctuation.
**Geometry / Graphics:** as C1 but every word heavy at 0.105W; if a single word is shorter than 0.4W wide it may grow to 0.13W.
**Motion:** as C1.
**Footage / plate behaviour:** untouched.
**Captions during it:** itself.
**Exit:** hard cut.
**Build notes:** same layer builder, all kinds = heavy.
**Flow prompt text:** "A single word, {{WORD}}, appears in heavy slanted white letters in the lower middle and holds until the next line."
**Still-image state:** one word.

### MOMENT M1 · PUNCH-IN
**What it is:** the footage is re-framed larger about the speaker's face at a sentence boundary, as a short scale ramp.
**Use when:** a long static talking-head shot (> 2 s) at a sentence or payoff, before the closer. **Avoid when:** a cut is within 3 f, or the face would leave the safe zone.
**Text:** none.
**Geometry / Graphics:** anchor = face centre (default x 0.50W, y 0.30H). Scale 1.00 → 1.10.
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

### MOMENT E1 · WORD WALL DISSOLVE
**What it is:** after the last spoken word the footage disintegrates into white specks from left to right and a light page of giant grey repeated words takes its place.
**Use when:** the last line ends the video (mandatory closer). **Avoid when:** the video ends mid-sentence, or the user needs the footage visible to the last frame (then run only the speck band and stop at 50 %).
**Text:** the title word, UPPERCASE (same word as T1).
**Geometry / Graphics:** word wall (1.2): rows alternate horizontal offset and shift left by 0.13W per row; page #F2F2F2, words #E0E0E0. Speck band 0.16W wide (white and #EBEBEB specks, density up to 0.85).
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| speech end − 0.5 → speech end | wall front | x | −0.05W → 0.20W | smoothstep (slow creep at the left edge, clear of the face) |
| speech end → speech end + 0.19 | wall front | x | 0.20W → 1.15W | ease-in |
| to the end of the video | wall | hold | wall visible | — |

**Footage / plate behaviour:** footage plays live to the end; the wall hides it only after the speech ends, for ≤ 1.5 s at the end of the video.
**Captions during it:** the final chunk stays above the wall.
**Exit:** none (end of video). For a longer ending: hold the wall up to 1.5 s.
**Build notes:** build the wall once (draw words at 2×, downscale). Per pixel: wall alpha = clamp((front − x) / 0.08); speck alpha = noise < clamp((front + 0.08 − x) / 0.16) × 0.85 where the wall is not yet full; blend wall, white specks, footage.
**Flow prompt text:** "After the last word, the picture breaks into tiny white specks that sweep from left to right and leave behind a pale grey page filled with a giant repeated word, {{TITLE_WORD}}, in capitals, in rows that alternate in position. The last caption stays on top."
**Still-image state:** the wall with one caption.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | X1 on each B-roll cut, L1 over 2–3 B-roll shots (card = previous step), L2, X2 into the speaker | M1 then E1 |
| Single talking head | T1 | M1 at the second sentence, L1 only if there is other footage for the card, C2 on the verdict | E1 |
| B-roll only | T1 (title over the first shot) | X1 on every cut, L1 over the longest run, C2 on a punch line | E1 (hold ≤ 1.5 s) |
| Still image | T1 settled state | C1 chunk, K1 along the bottom | none |

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
