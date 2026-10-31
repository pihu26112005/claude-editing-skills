# moments.md — Outline Fill Caps: Style Bible + Moment Library

This file is the single source of truth for the Outline Fill Caps caption style. Part 1 is the style bible (palette, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, with specs measured on a 1080x1920, 24 fps, 9.0 s reference reel. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: the footage always stays full frame and untouched.

**The look in one line:** tall condensed all-caps white captions that show the whole phrase at once as hollow outline letters, then snap solid white word by word as each word is spoken.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, lane…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 24 fps; at another fps keep the seconds. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Spoken word | #FFFFFF | Solid fill of words already spoken |
| Waiting word | #FFFFFF | Thin hollow outline (no fill) of words not yet spoken |
| Text shadow | #000000, up to 80 % after blur | Soft shadow behind every word on footage (design decision: the reference footage was dark; demo footage was bright and needed it) |

Brand-swap rule: none. The style has no accent colour. Never add colours.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, borders, masks, plates, blur or overlays. |
| Caption block | Text only. No box, bar or underline. Block is centred on x = 0.50W (measured 0.498). |
| Outline stroke | Centred on the glyph edge, ≈ 0.0035W [3.5] on the reference; in the demo 7 px at 2× on a 720 W render (looks right on bright footage). |

### 1.3 Layouts / grid

| Layout | Spec |
|---|---|
| Speaker lane | Block centre y = 0.695H [1334]. Two lines span 0.638–0.752H [1225–1444]; one line spans 0.670–0.720H. Sits under the chin. |
| B-roll lane | Block centre y = 0.50H (measured on faceless B-roll: three lines centred about mid-frame). ✎ shift per 1.7. |
| Line pitch | 0.90 em (0.064H [123] at font size 0.127W). |
| Max line width | 0.84W. Measured lines reached 0.20–0.80W (0.60W) for 14 characters. |
| Lines per chunk | 1–3, centred each on x = 0.50W. |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption word | Tall condensed grotesque, ALL CAPS (forced uppercase), regular weight, solid fill or hollow outline | Bebas Neue Regular | Anton, Barlow Condensed Bold | Font size ≈ 0.127W [137]; cap height ≈ 0.05H [96] |
| Word spacing | 0.25 em | | | |
| Letter-spacing | 0 | | | |
| Solo keyword (K1) | Same face | Bebas Neue | Anton | 1.6× caption size |
| Title (T1, T2, extension) | Same face, same outline-fill behaviour | Bebas Neue | Anton | 1.5× caption size |

Rules: uppercase only (the user's words, converted). Keep punctuation as the user wrote it. No italics, no rotation, no letter-by-letter typing.

Shadow: Gaussian blur σ ≈ 0.008W [8], offset +0.004H downwards, strength 0.65–0.8 of black behind the word shape.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Chunk entrance | hard cut: all words appear at once as outlines | 1 f |
| Word fill | outline → solid white, near-instant snap (alpha ramp) | 2 f (0.083 s), starts at the spoken word start |
| Chunk exit | hard cut, replaced in the same frame by the next chunk | 1 f |
| Lane move at a cut | hard jump on the cut frame | 0 f |

Measured on the reference: chunk 1 at 0.10 s, words filled at about 0.25, 0.42 and 0.58 s; chunks lasted 1.0–1.8 s with no gap between neighbours.

Never: bounce, overshoot, slides, scale pops, typewriter, glow, colour change, rotation, background boxes, lowercase, italic.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text and soft shadow overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; zoom, push-in, cards, split screens, slide or whip transitions, flashes, background swaps, blur, grading or any filter. The reference also had slide-in cards and push transitions; they are not part of this skill. Footage plays live in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Speaker lane starts ≥ 0.04H under the chin. If the face box bottom is below 0.58H, move the block down so its top is ≥ 0.04H under the chin; if that pushes the bottom past 0.92H, use the top lane (centre 0.17H) when the face is low. |
| B-roll lane | Prefer centre y 0.50H. If a key subject (hands, product, UI) sits there, shift to the emptiest band (0.17H–0.30H or 0.72H–0.80H). |
| Footage text (signs, UI) | If readable footage text sits in the lane for more than 1 s, move to another lane. |
| Edges | Every glyph ≥ 0.08W from the left and right edges. |
| Lane consistency | Keep one lane per shot; change lane only on a cut. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **T** title · **K** keyword · **X** cut treatment · **E** end.
Energy legend: ● calm · ●● medium · ●●● high.

### C1 · OUTLINE-FILL TWO-LINER — C ●● (signature, the caption system)
**What it is:** a two-line phrase appears at once as hollow outline capitals. As each word is spoken it snaps to solid white. When the phrase is done the whole block is replaced by the next one.
**Use when:** always, on speaker shots and any shot with speech. **Avoid when:** the phrase has fewer than 3 words (use C2) or more than 6 (split).
**Text (✎):** the user's exact words, converted to UPPERCASE. 3–6 words per chunk; split at punctuation and natural phrases; never end a chunk on an article, preposition or conjunction; each line ≤ 0.84W wide; lines balanced. A chunk lasts 1.0–1.8 s.
**Geometry / Graphics:** Speaker lane (1.3), 2 lines, pitch 0.90 em, each line centred on x = 0.50W, words separated by 0.25 em. The whole block is laid out before it appears, so no word ever moves.
**Motion (measured on the reference, 24 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| chunk start ✎ | all words | state | absent → outline | hard cut (1 f) |
| word start ✎ | that word | state | outline → solid white | 2 f snap |
| word start ✎ | earlier words | — | stay solid, no movement | — |
| chunk end ✎ | block | alpha | 1 → 0, same frame as next chunk | hard cut |

Word start = the word's spoken start. Chunk start = first word start (or the cut frame). Chunk end = min(next chunk start, last word end + 0.4 s, next cut).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** render each word at 2× with Pillow (Bebas Neue). Fill mask = the glyphs. Outline mask = dilate − erode of the glyph mask (elliptical kernel 7 px at 2×). Per frame, alpha = max over words of outline×(1−r) + fill×r, r = clamp((t − start)·fps / 2). Shadow = Gaussian blur of that alpha, shifted down, strength ×2 capped at 0.8; darken the frame by the shadow, then blend white by alpha.
**Flow prompt text:** "In the lower middle of the frame, a short phrase appears at once in tall, narrow capital letters drawn as thin white outlines. As each word is spoken, that word fills in solid white, one after another. When the phrase is finished it is replaced at once by the next phrase. The only words are {{CAPTION_WORDS}}."
**Still-image state:** first word solid, the rest outlined.

### C2 · OUTLINE-FILL ONE-LINER — C ●● (signature variant)
**What it is:** the same behaviour on a single line, for short phrases.
**Use when:** 2–3 words or ≤ 18 characters; a short beat between longer chunks. **Avoid when:** the phrase needs two lines.
**Text (✎):** user's words, UPPERCASE, 2–3 words, one line.
**Geometry / Graphics:** the block is centred on the lane centre (the reference single line sat at 0.670–0.720H, centre 0.695H, the same centre as the two-liner).
**Motion:** as C1.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** as C1 with one line.
**Flow prompt text:** "A short line of tall, narrow white capital letters appears at once as outlines in the lower middle of the frame, and each word fills in solid white as it is spoken. The only words are {{CAPTION_WORDS}}."
**Still-image state:** as C1.

### C3 · OUTLINE-FILL STACK — C ●● (signature variant)
**What it is:** the same behaviour on three short lines, used when a phrase is long or the lane is the B-roll lane.
**Use when:** a 5–6 word phrase whose lines would pass 0.84W as two lines; faceless B-roll lane. **Avoid when:** two lines fit.
**Text (✎):** user's words, UPPERCASE, 2–3 lines of 1–2 words each.
**Geometry / Graphics:** 3 lines, pitch 0.90 em, block centre = lane centre (0.695H on a speaker, 0.50H on B-roll). Height of 3 lines ≈ 0.19H.
**Motion:** as C1.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** as C1.
**Flow prompt text:** "A phrase of {{N}} short stacked lines of tall, narrow white capital letters appears at once as thin outlines, and each word fills in solid white as it is spoken. The only words are {{CAPTION_WORDS}}."
**Still-image state:** as C1.

### L1 · LANE SHIFT — C ● (signature, placement)
**What it is:** the caption block changes lane on a cut so it always sits clear of the subject: under the chin on a speaker, mid-frame (or the emptiest band) on faceless B-roll.
**Use when:** every cut where the subject position changes. **Avoid when:** never mid-shot.
**Text (✎):** none.
**Geometry / Graphics:** lanes per 1.3 and 1.7. Demo values: speaker 0.695H, hands-and-cash shot 0.74H, phone shot 0.50H, plant shot 0.50H.
**Motion:** the new chunk starts on the cut frame in its new lane. No movement.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** pick the lane per shot from the scene table and build each chunk with its shot's lane.
**Flow prompt text:** "At each cut the captions appear in a new place that keeps the main subject clear: just under the speaker's chin on speaker shots, and in the empty middle or lower area on other shots."
**Still-image state:** none.

### X1 · CUT CARRY — X ● (signature treatment of every cut)
**What it is:** shots change with a plain hard cut. The chunk in progress ends on the cut frame and the next chunk starts on that frame in the new lane. No transition.
**Use when:** every footage cut. **Avoid when:** never; add no effect.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** at the cut ✎, old chunk off and new chunk on, same frame; if the speech continues across the cut, the new chunk starts with the first still-unspoken word (words already spoken are solid from its first frame).
**Footage / plate behaviour:** untouched; no flash, blur, slide or push.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** chunk bounds come from the cut table; end chunks 0.03 s before a cut.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the caption phrase changes in the same moment."
**Still-image state:** none.

### K1 · SOLO WORD — K ●●● (extension in the same grammar)
**What it is:** one payoff word alone at 1.6× size, outline for the lead-in and solid on its spoken moment.
**Use when:** a strong turn or payoff word (a number, "never", a name). **Avoid when:** longer than 11 characters; max 2 per video, ≥ 3 s apart.
**Text (✎):** one user word, UPPERCASE.
**Geometry / Graphics:** lane centre, 1.6× size, centred on x = 0.50W.
**Motion:** outline appears with the chunk start (hard cut), fills at the word's start (2 f), holds 0.5–0.9 s, hard cut out.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the chunk.
**Exit:** hard cut.
**Build notes:** C1 renderer with a larger font size.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in very large narrow white capitals, first as an outline, then filled solid white as it is spoken, and is then replaced by the next caption."
**Still-image state:** the filled word.

### T1 · OUTLINE TITLE — T ●● (extension in the same grammar)
**What it is:** a one- or two-word headline at the top, same outline-then-fill grammar, shown while the first caption chunk runs below.
**Use when:** the opening line names a topic and the first 1.5 s allow it. **Avoid when:** the face box top is above 0.20H and cannot be cleared.
**Text (✎):** 1–2 of the user's words, UPPERCASE, max 16 characters; or a title the user supplied.
**Geometry / Graphics:** 1.5× caption size, centre y ✎ = 0.12H, centred on x = 0.50W.
**Motion:** outline appears (hard cut), fills at the word start, holds 1.2 s, hard cut out ≥ 0.3 s before a cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 runs in the lane; the title never overlaps it.
**Exit:** hard cut.
**Build notes:** as K1 at the top.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, appears near the top in very large narrow white capitals, first as an outline, then filled solid, stays about a second, and disappears. It never covers the face."
**Still-image state:** filled title.

### T2 · SECTION TITLE — T ●● (extension in the same grammar)
**What it is:** a smaller T1 for a later topic word.
**Use when:** a new step or topic, ≥ 3 s after T1, ≥ 0.5 s after a cut. **Avoid when:** the video is under 6 s.
**Text (✎):** 1–2 user words, UPPERCASE.
**Geometry / Graphics:** 1.2× caption size, centre y 0.12H, x ✎ = 0.50W.
**Motion:** as T1.
**Footage / plate behaviour:** untouched.
**Captions during it:** unchanged.
**Exit:** hard cut.
**Build notes:** reuse T1.
**Flow prompt text:** "Later, a smaller title, {{TITLE}}, appears at the top in narrow white capitals, outline first and then solid, and disappears after about a second."
**Still-image state:** filled title.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last chunk stays until just before the end, then the picture finishes clean.
**Use when:** every video. **Avoid when:** the last word is a K1 payoff.
**Text (✎):** last chunk.
**Geometry / Graphics:** as C1/C3.
**Motion:** the last chunk ends at min(last word end + 0.4 s, end − 0.25 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 or C3 on the first line | X1 + L1 on every cut; C1/C2/C3 by phrase length; K1 on one payoff word | E1 |
| Single talking head, no cuts | T1 + C1 | C1/C2 alternate; K1 on a payoff word; T2 at a new topic | E1 |
| B-roll only, no speech | C3 (phrases spread across the shot) | X1 + L1; C2 beats | E1 |
| Still image + text | C1 settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Font Bebas Neue, size 0.127W (91.4 px), pitch 0.90 em, word gap 0.25 em, outline kernel 7 px at 2×, fill snap 2 f, shadow σ 6 px at 720 W, offset 4 px, strength ×2 capped at 0.8.
- "SAVING MONEY ISN'T ABOUT EARNING MORE." did not fit two lines under 0.84W (0.88W), so it became a three-line C3. Other chunks fit as C1 or C2 shapes.
- Lanes used: speaker 0.695H; cash/hands shot 0.74H (below the cash); phone shot 0.50H; grocery shot 0.695H (face in the top); plant shot 0.50H.
- Chunk times (s): 0.10–1.80, 2.10–3.20, 3.25–4.88, 4.95–6.55, 6.90–8.35, 8.45–9.75.
- Outline letters on bright footage need the strong shadow; the thin 5 px outline was too faint.
