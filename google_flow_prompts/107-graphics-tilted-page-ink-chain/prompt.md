# Google Flow prompt · Tilted Page Ink Chain
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 30 fps · 7.2 s (reference 720×1280, 7.23 s; sizes below are output pixels, reference = value / 1.5)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Tilted Page Ink Chain" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. three paragraphs on a tilted paper page, three key words circled in ink and linked by two hand-drawn arrows, with a camera glide from word to word.

A tilted page of small serif text fills the screen. The camera drifts over it, and three key words (set in bold ink colour) are circled by a hand-drawn ink ellipse one after another. A curved ink arrow grows from each circled word to the next, the camera gliding along each arrow to the next word. It shows a chain of three ideas hidden inside ordinary paragraphs.
**The graphic in one line:** three paragraphs on a tilted paper page, three key words circled in ink and linked by two hand-drawn arrows, with a camera glide from word to word.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Paragraph 1 (REQUIRED, text, 220–320 chars, plain sentences, must contain Key word 1): <your value>
P2 · Key word 1 (REQUIRED, one word, ≤ 12 chars, must occur in Paragraph 1): <your value>
P3 · Paragraph 2 (REQUIRED, text, 220–320 chars, must contain Key word 2): <your value>
P4 · Key word 2 (REQUIRED, one word, ≤ 12 chars, must occur in Paragraph 2): <your value>
P5 · Paragraph 3 (REQUIRED, text, 220–320 chars, must contain Key word 3): <your value>
P6 · Key word 3 (REQUIRED, one word, ≤ 12 chars, must occur in Paragraph 3): <your value>
P7 · Ink colour (optional, hex, dark; default: #1F1F1F): <your value or NONE>
P8 · Paper tone (optional, hex, light; default: #F4F4F4): <your value or NONE>
P9 · Text greys (optional, 3 hex greys, dark to light; default: #3A3A3A / #747474 / #B4B4B4): <your value or NONE>
P10 · Tilt (optional, 0–15 degrees; default: 10 degrees): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Paragraphs: take three consecutive or related passages from the user's script or article, trimmed to the length limit.
- Key words: the single word in each paragraph that carries the idea; the three words, read in order, should form a chain (cause, link, result).
- Ink colour: may be taken from a brand colour; keep strong contrast with the paper.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Paper: neutral light grey #F4F4F4, fine horizontal paper-fibre grain, about ±3 levels.
- Vignette in screen space: corners darken to about 94 percent, starting at r=0.2 of the corner distance, power 1.4.
- The paper, text and grain live in world space and move with the camera. Vignette and ink strokes are drawn in screen space (strokes at world positions).
- The whole page is rotated 10 degrees counter-clockwise (text baselines rise to the right).
- Paragraphs are wider than the screen, so their left and right edges are cropped by the frame, and empty paper shows between and beside blocks.
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
| 0–1.1 | camera | centre | T1+(-70,-420) → T1 | ease-out  |
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
## 8. Never
No distortion or zoom of the page; no extra marks or highlights; no text other than the three paragraphs; no circle that misses its word; keep paragraph blocks from overlapping each other; never change the order of the beats.

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 30 fps · 7.2 s (reference 720×1280, 7.23 s; sizes below are output pixels, reference = value / 1.5). Keep the motion, timing and order of beats of section 4.
- No watermark, no extra frames before or after the animation, no end card.

## 6. NEGATIVE PROMPT (avoid all of these)
- Any element, colour, font or motion that section 4 does not describe; extra logos, brand names, watermarks, people's faces or UI that was not asked for.
- Misspelled, garbled, extra or missing text; text outside the frame; overlapping text; random gibberish letters.
- Camera moves, zooms or transitions that are not in the timeline; flicker, jitter or warped shapes; cartoon filters.
- Black bars, borders, vignettes or grain that the design does not list.

## 7. FINAL CHECK
- [ ] All required inputs appear exactly as typed and nowhere else.
- [ ] Every beat of the timeline happens in order with the described timing and easing.
- [ ] Layout, colours and type match the design; nothing extra is on screen.
- [ ] The video has the right format and length.
