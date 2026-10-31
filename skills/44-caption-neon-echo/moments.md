# moments.md — Neon Echo: Style Bible + Moment Library

This file is the single source of truth for the Neon Echo caption style. Part 1 is the style bible (palette, type, motion, footage rules, safe zones). Part 2 is the moment library with specs measured on a 540x960, 30 fps, 5.0 s reference reel (one hard cut) and tuned on a 720x1280, 24 fps render. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: footage stays full frame and untouched.

**The look in one line:** small bold white sentence-case captions pop in word by word near the chest, key words turn lime italic with a green glow, one payoff word can blow up into a giant scan-lined neon slab, and a top outline title or a stack of outline echoes behind the speaker carries the topic word.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, lane…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (keep seconds at other rates). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Caption white | #FFFFFF | Plain caption words, stack outlines |
| Neon lime | #C6FA3B | Keyword fill, slab fill (measured median 198,250,59) |
| Neon glow | #6EFF28 | Blurred halo under lime text |
| Title violet | #685CEB | Title outline (measured ≈ 96,82,217), haze fill at 34 % of #504CAA |
| Split red / cyan | #FF465A / #46E6FF | Colour-split ghosts of the echo stack, 55 % |
| Shadow | #080C12 | Soft shadow and thin stroke under all text (design decision for bright footage) |

Brand-swap rule: a user brand colour replaces Neon lime and Neon glow (use a lighter tint as fill, the saturated colour as glow). White never changes.

### 1.2 Containers / shapes
No containers. Footage is always full frame, 100 % of W and H. No boxes, cards, borders, plates, dimming or colour overlays. Cover-fit only if the source is not 9:16.

### 1.3 Layouts / grid

| Layout | Region (fractions) | Use |
|---|---|---|
| Chest lane | first line centre y = 0.64H [1229] (ref 0.61–0.63H), x centred 0.50W | Default caption lane |
| Neck lane | first line centre y = 0.50H [960] (ref 0.47H) | Lane hop, and the caption lane when a slab is on screen |
| Slab lane | centre y = 0.715H [1373] (ref 0.69H) | K2 slab |
| Title lane | centre y = 0.073H [140]; cap height ≤ 0.09H | T1 |
| Stack field | rows from y = 0.012H, pitch 0.115H [221], 9 rows, 0.90W wide | T2 |
| Line pitch | 1.30 × caption font size | Lines inside a chunk |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption word | Bold grotesque, sentence case as written, tight | Inter Bold (wght 760) | Roboto Bold, Manrope Bold | 0.092W [99]; word gap 0.26 em |
| Keyword | Bold italic, lime, glow | Inter Tight ExtraBold Italic | Inter Bold Italic, Roboto Bold Italic | 1.18 × caption size |
| Slab (K2) | Heavy italic, UPPERCASE, lime, scan-line slits, glow | Barlow Black Italic | Archivo Black, Anton | em 0.27W, fit so width ≤ 0.74W |
| Title and stack | Extra-bold italic, UPPERCASE, outline only | Barlow ExtraBold Italic | Barlow Condensed Bold Italic, Roboto Condensed | T1 width 0.64W; T2 row cap height 0.098H, stretched to 0.90W |

Rules: captions keep the user's case and punctuation. Slab, title and stack words are uppercase copies of user words. No boxes behind text. Shadow on all text: blurred 7 px at 75 % plus a 1 px dark stroke at 55 %.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Caption word entrance | ease-out alpha ramp, no movement | 0.125 s [4 f @30] (ref 2 f @15) |
| Chunk exit / swap | hard cut | 1 f |
| Slab entrance | ease-out alpha + scale 1.07 → 1.00 | 0.15 s |
| Title pass | enter from the left ease-out, slow drift, exit to the right ease-in | 0.30 s in, 0.38 s out |
| Stack entrance | rows alpha ramp ease-out, 0.05 s stagger top to bottom | 0.125 s per row |

Never: letter-by-letter typing, bounce, spring, slides on captions, boxes behind captions, shake, flashes, caption rotation.

### 1.6 What may happen to the user's footage
Allowed: full-frame display untouched; text overlays; for T2 only, the stack drawn behind a person cut-out (the person is the live footage, the stack is only added behind). Forbidden: replacing, regenerating, retiming, trimming, reordering; blur, grading, background swaps, cards, splits, B-roll frames, graphic transitions. The primary footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by captions, slab or title. Lane y must be ≥ 0.03H under the chin; if the face bottom is below 0.46H use only the chest lane or lower. |
| Title lane | Needs the face top ≥ 0.12H; else shrink T1 or skip it. |
| Stack | Only on a shot with one clear person (mask from a person segmenter); the face is never covered because the person stays in front. Skip on shots with no person. |
| Edges | Glyphs ≥ 0.04W from left and right (chunks ≤ 0.88W wide). |
| Bright footage | Keep the shadow and stroke on; keep text off pure-white regions if a lane alternative exists. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **K** keyword · **T** title · **X** cut · **E** end.
Energy: ● calm · ●● medium · ●●● high.

### C1 · POP CAPTION — C ●● (signature, the caption system)
**What it is:** a short chunk pops in word by word in white bold, laid out in full before the first word so nothing moves; the chunk is replaced by the next in one frame.
**Use when:** always. **Avoid when:** never.
**Text (✎):** user's exact words. 2–5 words, 0.7–1.6 s, split at punctuation, never end on an article, preposition or conjunction, never straddle a cut. Lines break where the word type changes (white to keyword or back); white words stay together on one line.
**Geometry / Graphics:** Chest lane, centred on x = 0.50W, first line y per the lane, line pitch 1.30 em.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha | 0 → 1 | ease-out, 0.125 s |
| word start ✎ | earlier words | — | unchanged | — |
| chunk end ✎ | chunk | alpha | 1 → 0 | hard cut |

Ref words: One 0.80, bright 1.13, choice 1.60, can 2.07 (chunk gaps 0.05 s). Chunk end = next chunk start, or min(last word end + 0.4, next cut − 0.03).
**Footage:** untouched. **Exit:** hard cut.
**Build notes:** pre-render every word at 2× with shadow; one layout per chunk; alpha per word.
**Flow prompt text:** "Captions appear near the middle of the frame, word by word, in bold white lettering with a soft shadow. Each word fades in softly in place and the phrase is replaced at once by the next. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### K1 · NEON KEYWORD — K ●● (signature)
**What it is:** the meaning-carrying word of a chunk is lime bold italic with a green glow, on its own line.
**Use when:** a noun or verb carries the point. **Avoid when:** articles, prepositions; more than 1 per chunk or 4 per 5 s.
**Text (✎):** one word per chunk as written, 1.18 × size.
**Geometry / Graphics:** inside the chunk per C1 line rules (keyword alone on its line; trailing white words go on the line below).
**Motion:** same entrance as C1.
**Footage:** untouched. **Exit:** with the chunk.
**Build notes:** glow = blurred mask (9 px) ×1.6 at 85 % in #6EFF28, under a lime fill.
**Flow prompt text:** "The important word, {{KEYWORD}}, is lime green, slanted and glowing, on its own line."
**Still-image state:** settled.

### K2 · NEON SLAB — K ●●● (signature payoff)
**What it is:** one payoff word blows up as a giant uppercase lime slab with horizontal scan-line slits and a green glow, while its chunk moves to the neck lane and the small lime keyword stays above it.
**Use when:** a turn, number, action or payoff word (max 2 per video, ≥ 3 s apart). **Avoid when:** word > 8 letters, or over a face.
**Text (✎):** one user word, uppercase, without punctuation.
**Geometry / Graphics:** slab lane centre y = 0.715H, width ≤ 0.74W, em 0.27W (4 letters ≈ 0.55W); scan slits every 3 px at 35 %; its chunk uses the neck lane.
**Motion:** alpha 0 → 1 and scale 1.07 → 1.00 over 0.15 s ease-out at the keyword start; hold until the chunk ends, then hard cut (ref held 0.55 s).
**Footage:** untouched. **Exit:** hard cut with the chunk.
**Build notes:** fill alpha multiplied by (1 − 0.35) on odd 3 px bands.
**Flow prompt text:** "The word {{WORD}} appears huge in glowing lime green slanted capitals with thin horizontal slits cut through the letters, below the small caption, then disappears with it."
**Still-image state:** settled.

### T1 · OUTLINE TITLE PASS — T ●● (signature)
**What it is:** the topic word in uppercase outline letters (violet line, faint violet haze, lime ghost line) slides across the top in the same direction, holds and drifts, then leaves.
**Use when:** opening line or topic word, speaker below. **Avoid when:** face top < 0.12H, or a cut within 0.3 s.
**Text (✎):** one user word, uppercase, width 0.64W.
**Geometry / Graphics:** title lane centre y = 0.073H; violet outline 2 px, haze 34 %, lime ghost outline offset (+4,+3) at 70 %.
**Motion:**

| t | Property | From → To | Ease |
|---|---|---|---|
| start ✎ (+0–0.30 s) | x offset | −0.95W → 0 | ease-out |
| hold | x drift | +0.03W per s | linear |
| end ✎ − 0.38 s | x offset | → +0.95W | ease-in |

Ref: in 0.67–0.83 s, out 1.5–1.9 s. Demo: 0.40–1.62 s. Finish ≥ 0.2 s before a cut.
**Footage:** untouched. **Exit:** slide right.
**Flow prompt text:** "Near the top, the word {{TITLE}} in large outlined capitals slides in from the left, drifts slowly and slides out to the right, never covering the face."
**Still-image state:** settled.

### T2 · ECHO STACK — T ●●● (signature)
**What it is:** the topic word in uppercase outline repeated in 9 rows filling the frame behind the speaker, white lines with red and cyan splits, lower rows lime-tinted, rows appearing top to bottom.
**Use when:** a payoff or closing section on a shot with one clear person. **Avoid when:** no person, or the person fills the whole frame.
**Text (✎):** one user word, uppercase.
**Geometry / Graphics:** Stack field; row alpha 1.0 at the top to 0.45 at the bottom; last 3 rows tinted #BEFF78; the stack is composited behind the person mask (EMA 0.6/0.4, 1.5 px blur).
**Motion:** each row alpha 0 → 1 over 0.125 s ease-out, row r starts at start + 0.05 r; then holds to the end of the video (ref: until the end).
**Footage:** live person in front; nothing else changed. **Exit:** none (video end).
**Build notes:** render one outline row, stretch to 0.90W, tile; mask from a segmenter in VIDEO mode.
**Flow prompt text:** "Behind the speaker, the word {{WORD}} repeats in rows of white outlined capitals with faint red and blue edges, filling the frame from top to bottom. The speaker stays in front, unchanged."
**Still-image state:** settled.

### C2 · LANE HOP — C ●● (extension in the same grammar)
**What it is:** a chunk sits in the neck lane instead of the chest lane to vary the rhythm or clear a hands area.
**Use when:** two chunks in a row would repeat the lane, or K2 is on. **Avoid when:** the neck lane is under the face (face bottom > 0.46H).
**Text (✎):** as C1; lane ✎. Everything else as C1.
**Flow prompt text:** "This caption sits a little higher, just under the speaker's chin."

### C3 · BRIGHT-FOOTAGE GUARD — C ● (extension in the same grammar)
**What it is:** on bright or pale footage the shadow and 1 px stroke are kept at full strength and the lane moves to the darker half.
**Use when:** lane luminance > 0.6. **Flow prompt text:** "On bright shots the captions keep a soft dark shadow so they stay readable."

### X1 · CUT RESET — X ● (signature)
**What it is:** on each footage cut the current chunk ends at cut − 0.03 s and the next chunk starts on the cut or its first spoken word, in the lane suited to the new shot. No effect on the cut.
**Use when:** every cut. **Flow prompt text:** "At each cut the picture simply cuts; the caption in progress ends just before and a new one starts at the cut."

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last chunk holds to min(last word end + 0.4 s, end − 0.25 s), then the picture finishes clean (T2 stays).
**Flow prompt text:** "The last caption stays until just before the end, then disappears."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1/K1 | K2 on one payoff word, C2 lane hops, X1 on cuts | T2 on the final speaker shot + E1 |
| Single talking head | T1 + C1/K1 | K2 on the turn word, C2 | T2 + E1 |
| B-roll only | C1/K1 (T1 if a title word exists) | K2 on a number or action, X1 | E1 (no T2) |
| Still image + text | T1 settled | one chunk with K1 | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (demo2 render, 720x1280, 24 fps)

- Caption size 0.092W (0.080W looked small against the reference). Chunk widths all ≤ 0.88W.
- Lanes used: chest 0.64H for chunks on the speaker and phone/grocery shots; neck 0.50H on the K2 chunks (cash and plant shots).
- T1 "MONEY" 0.40–1.62 s, clear of the face (title bottom ≈ 0.12H, face top 0.15H).
- K2 FIRST at 2.60 s and YEAR at 7.65 s. Lime slab is weaker on green plants; the dark shadow keeps it readable.
- T2 WATCH from 8.65 s to the end behind the speaker mask.
- Chunk 4 starts at 3.25 s (the cut), not at the word time 3.20.
