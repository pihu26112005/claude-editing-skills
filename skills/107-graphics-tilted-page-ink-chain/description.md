# description.md: Tilted Page Ink Chain

A tilted page of small serif text fills the screen. The camera drifts over it, and three key words (set in bold ink colour) are circled by a hand-drawn ink ellipse one after another. A curved ink arrow grows from each circled word to the next, the camera gliding along each arrow to the next word. It shows a chain of three ideas hidden inside ordinary paragraphs.
**The graphic in one line:** three paragraphs on a tilted paper page, three key words circled in ink and linked by two hand-drawn arrows, with a camera glide from word to word.
**Format:** 9:16 · 1080×1920 · 30 fps · 7.2 s (reference 720×1280, 7.23 s; sizes below are output pixels, reference = value / 1.5)

## 1. Canvas
- Paper: neutral light grey #F4F4F4 (measured 244), fine horizontal paper-fibre grain, about ±3 levels (measured std small, matched by eye).
- Vignette in screen space: corners darken to about 94 percent (measured 230 vs 244), starting at r=0.2 of the corner distance, power 1.4.
- The paper, text and grain live in world space and move with the camera. Vignette and ink strokes are drawn in screen space (strokes at world positions).
- The whole page is rotated 10 degrees counter-clockwise (text baselines rise to the right) (measured about 10 degrees).
- Paragraphs are wider than the screen, so their left and right edges are cropped by the frame, and empty paper shows between and beside blocks.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Paragraph 1 | yes | none, must ask | text, 220–320 chars, plain sentences, must contain Key word 1 | E1, B1–B3 |
| P2 | Key word 1 | yes | none, must ask | one word, ≤ 12 chars, must occur in Paragraph 1 | E1, E4, B2 |
| P3 | Paragraph 2 | yes | none, must ask | text, 220–320 chars, must contain Key word 2 | E2, B3–B5 |
| P4 | Key word 2 | yes | none, must ask | one word, ≤ 12 chars, must occur in Paragraph 2 | E2, E5, B4 |
| P5 | Paragraph 3 | yes | none, must ask | text, 220–320 chars, must contain Key word 3 | E3, B5–B6 |
| P6 | Key word 3 | yes | none, must ask | one word, ≤ 12 chars, must occur in Paragraph 3 | E3, E6, B6 |
| P7 | Ink colour | no | #1F1F1F (measured near-black) | hex, dark | key words, circles, arrows |
| P8 | Paper tone | no | #F4F4F4 (measured) | hex, light | canvas |
| P9 | Text greys | no | #3A3A3A / #747474 / #B4B4B4 | 3 hex greys, dark to light | body text |
| P10 | Tilt | no | 10 degrees | 0–15 degrees | page |

### 2.1 How to infer parameters from user material
- Paragraphs: take three consecutive or related passages from the user's script or article, trimmed to the length limit.
- Key words: the single word in each paragraph that carries the idea; the three words, read in order, should form a chain (cause, link, result).
- Ink colour: may be taken from a brand colour; keep strong contrast with the paper.

## 3. Elements
### E1 · Paragraph block 1 (P1)
Slab-serif text (Roboto Slab or similar), size 57 px, line height 87 px, wrap width 1000 px (about 8 lines), left aligned, rotated by the tilt. Word runs alternate in three greys (P9) with run lengths 4,3,6,2,5,3,7,4 words cycling; runs give a faded reading rhythm. Block centre world (0, 0).
### E2 · Paragraph block 2 (P3)
Same style. Block centre world (220, 840).
### E3 · Paragraph block 3 (P5)
Same style. Block centre world (-160, 1830).
### E4–E6 · Key words (P2, P4, P6)
The first occurrence of the key word in its paragraph is set in the ink colour at weight 800 (bold), other text weight 400. The word keeps its position in the paragraph.
### E7–E9 · Ink circles
Ellipse around each key word: half width = word width / 2 + 38 px, half height 46 px, axes rotated with the text. Stroke 5.5 px, round caps, ink colour. Drawn as a spiral starting at the left (angle 180 degrees), 1.12 turns, radius growing 6 percent over the draw (overshoot, hand-drawn feel).
### E10–E11 · Ink arrows
Cubic Bezier from beside circle N to just before circle N+1 (end at quarter word width plus 30 px from the target centre). Arrow 1 bows gently (about 6 percent of its length); arrow 2 swings out about 30 percent, leaving upward first and curving down. Low-frequency wobble 2.2 px perpendicular. Stroke 5.5 px. The arrowhead is two barbs, 46 px long and 22 px wide, aligned to the end tangent, drawn in the last 0.35 s.

Adaptation: long words widen the circle; text is fixed-size and never rescaled, paragraphs over the limit are shortened by the user.

## 4. Camera
World pixel space, centre of view. Keyword target T_k = key word centre with the view centre 190 px above it (so the word sits lower on screen).
| t (s) | centre | ease |
|---|---|---|
| 0–1.1 | T1 + (-70, -420) → T1 | ease-out cubic |
| 1.1–1.5 | hold T1 | none |
| 1.5–3.0 | T1 → T2 | ease-in-out cubic |
| 3.0–3.8 | hold T2 | none |
| 3.8–5.1 | T2 → T3 | ease-in-out cubic |
| 5.1–7.2 | hold T3 | none |
Pure translation, no zoom or rotation. Motion blur: 7 sub-samples across a 0.4-frame shutter, averaged.

## 5. Timeline (beats)
### B1 · Page drift — 0–1.1 s
The first paragraph block is in view, the camera drifts down-right onto key word 1.
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.1 | camera | centre | T1+(-70,-420) → T1 | ease-out (design) |
### B2 · Circle 1 — 0.9–1.55 s
| 0.9–1.55 | E7 | stroke draw | 0 → 1 | ease-in-out |
### B3 · Arrow 1 and glide — 1.5–3.0 s
| 1.5–2.6 | E10 | stroke draw | 0 → 1 | ease-in-out |
| 2.5–2.85 | E10 head | barbs scale | 0 → 1 | ease-out |
| 1.5–3.0 | camera | T1 → T2 | ease-in-out |
### B4 · Circle 2 — 3.0–3.65 s
| 3.0–3.65 | E8 | stroke draw | 0 → 1 | ease-in-out |
### B5 · Arrow 2 and glide — 3.65–5.1 s
| 3.65–4.95 | E11 | stroke draw | 0 → 1 | ease-in-out |
| 4.85–5.2 | E11 head | barbs scale | 0 → 1 | ease-out |
| 3.8–5.1 | camera | T2 → T3 | ease-in-out |
### B6 · Circle 3 and hold — 5.1–7.2 s
| 5.1–5.75 | E9 | stroke draw | 0 → 1 | ease-in-out |
| 5.75–7.2 | all | hold | still | none |
Timings are read from the reference by eye at 4 fps and refined by design.

## 6. Build notes
- Render each paragraph at 2x with PIL (per-word draw so each word box is known), rotate by the tilt with bicubic, downscale to 1x, alpha-composite onto a world canvas of 3400×4200 px that already holds paper and grain.
- Map the key word centre through the same rotation (x' = dx cos t + dy sin t, y' = -dx sin t + dy cos t about the block centre) to place circles and arrows.
- Per frame: warpAffine the world with the camera shift, average 7 sub-samples, multiply by the vignette, then draw strokes on a 2x mask with anti-aliased polylines, downscale with area filter, composite ink.
- Stream frames to ffmpeg: `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The last frame: paragraph 2 and 3 in view, arrow 2 landing on a circled key word 3 at lower centre, empty paper below.

## 8. Never
No distortion or zoom of the page; no extra marks or highlights; no text other than the three paragraphs; no circle that misses its word; keep paragraph blocks from overlapping each other; never change the order of the beats.
