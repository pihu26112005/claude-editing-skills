# Google Flow prompt · Shattered Front Page Pullback
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 1:1 · 1080×1080 · 30 fps · 7.0 s (reference 480×480; every size below is given in page px, where the settled page is 855×637 output px)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Shattered Front Page Pullback" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. a front page shatters into nine paper pieces and reforms as the camera pulls back from a giant headline.

A newspaper front page is cut into nine ragged pieces. The video opens zoomed 4.8× on the headline with the pieces slightly apart over a grey underlay. The pieces drift further apart and tilt, then slide back together while the camera pulls out to the whole page, which settles with thin cracks between the pieces over a faint newsprint background with a halftone-dot vignette.
**The graphic in one line:** a front page shatters into nine paper pieces and reforms as the camera pulls back from a giant headline.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Masthead (REQUIRED, text, ≤ 22 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Headline line 1 (REQUIRED, text, ≤ 12 chars, 1 line (auto-fit down to 70%)): <your value>
P3 · Headline line 2 (REQUIRED, text, ≤ 12 chars, 1 line (auto-fit down to 70%)): <your value>
P4 · Subhead (REQUIRED, text, ≤ 90 chars, 1 line (auto-fit down to 70%)): <your value>
P5 · Photo (REQUIRED, image, any aspect, cover-fit, ≥ 500 px short side): <your value>
P6 · Edition tag (optional, text, ≤ 14 chars, caps; default: EXTRA): <your value or NONE>
P7 · Dateline (optional, text, ≤ 28 chars; default: blank): <your value or NONE>
P8 · Photo caption (optional, text, ≤ 48 chars; default: blank): <your value or NONE>
P9 · Body text (optional, text, 700–1600 chars; surplus lines in the columns stay as grey bars; default: grey placeholder lines): <your value or NONE>
P10 · Tag colour (optional, hex; default: #D8452E): <your value or NONE>
P11 · Paper colour (optional, hex, light; default: #D3C2A7): <your value or NONE>
P12 · Ink colour (optional, hex, dark; default: #28221D): <your value or NONE>
P13 · Underlay grey (optional, hex, light grey; default: #B8B8BB): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Masthead, headline and subhead: the story title and its first sentence from the user's script or article. Headline split on two lines of similar length.
- Photo: any user image or a still from a user video with a clear subject.
- Body text: the user's article text, if given. Never write it for them.
- Tag colour: may come from a brand colour; keep strong contrast with the paper. Paper and ink may be changed together for a different print tone.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Background: newsprint #F7F1EA with very faint low-frequency mottling (±1.2 percent) and grey placeholder-text columns (7 columns, pitch 150 px at output scale, lines #DED8D0, headings #CEC8C0).
- Halftone vignette (screen space, static): dot grid pitch 7 px (staggered rows), dots #A8A39C at 55 percent, dot radius 0.52 × pitch × k with k = clamp((e − 0.78) / 0.55, 0, 1)^1.2, e = normalised elliptical distance from the centre (corners about 1.41). Visible only toward the corners.
- Underlay: flat grey #B8B8BB with ±3 percent mottling, a rectangle inset 10 px (output) from the page edge with ragged noise edge, soft shadow. It shows through the gaps between pieces.
- Background parallax: the background scales by 0.5·zoom^0.33 around the screen centre (about 1.7× at the start, 1× at the end).
## 3. Elements
Page coordinates (px of the settled 855×637 page; page top-left is the origin; the page is centred on screen at the end).
### E1 · Page
Paper P11 with low-frequency mottling (±3.5 percent), fine grain (±3 levels), a faint light crease along the horizontal and vertical centre lines (-14 levels, 3 px soft). Ink is the print colour P12 with ink wear: coverage 0.93 − 0.18 × noise, plus about 4 percent of pixels knocked out as speckle.
### E2 · Masthead block
UnifrakturCook Bold, centred at (427, 46), size 62 (auto-fit to width 560, floor 70 percent). Two ear boxes 62×48 at x=24 and x=769, y=22, outline 1.4, each with four grey bars. Double rule at y=78 (2.2) and y=83 (0.8) from x=14 to 841. Dateline P7 in Barlow Condensed Bold 10.5, centred at y=95. Rule at y=106 (1.0).
### E3 · Edition tag
Rectangle centred at x=427, y 114–134, width = text width + 26, fill P10. Text P6 in Barlow Condensed Bold 13, colour #F6EEE0, centred at y=124.4.
### E4 · Headline
Anton, size 112 (auto-fit so the wider line is ≤ 700, floor 70 percent), centred at x=427, line 1 at y=222, line 2 at y=322.
### E5 · Subhead
Newsreader Italic, size 16.5 (auto-fit to width 700), centred at y=382. Rule at y=402 (1.2).
### E6 · Body columns
Three columns at x 26–196, 208–378, 390–540, first line y=416, line height 11.6, 17 lines each. EB Garamond 9.6, colour ink at 92 percent. Text P9 wraps column by column; lines after the text, and every line when P9 is empty, are grey bars (height 3.2, 55–100 percent of column width, fill ink at 37 percent). Column rules at x=202, 384, 547 (0.6, 47 percent).
### E7 · Photo and caption
Photo box x=560, y=414, 270×150. Cover-fit crop, grayscale, contrast 1.25, gamma 0.75 (brightened), inner vignette, grain ±2.5 percent, mapped to a sepia ramp from #28201A to #E2D4BA. Border 1.6 in ink. Caption P8 in Newsreader Italic 8.8 at (560, 574). Four grey bars under the caption (y 586 + 8.5k, widths 200–268).
### E8 · The nine pieces
The page is cut by nearest-seed regions with a domain-warped, jagged border. Seeds (page px): 0 (110,45), 1 (430,45), 2 (750,45), 3 (130,235), 4 (427,262), 5 (730,235), 6 (120,505), 7 (400,505), 8 (730,505). Distance x-weights 0.8 (0.75 for seeds 3 and 5, 0.7 for seed 4). Warp amplitude 9 px at noise scales 160/80/40 px (2× grid), so borders stay mostly straight and angular.
Each piece edge: hard mask from the label map, signed inside-distance at 4×, plus high-frequency jitter 2.6 px (noise scales 10/5/3/2 px at 4×); alpha = clamp((distance + jitter − 5.5) / 1.4 + 0.5), so the settled gap is a thin crack of about 2–3 px at 1080. Torn rim: within 18 px (4× grid) of the edge, a paper-white fibre colour #F6F2E8 at up to 88 percent with noise (scales 12/6/3). Slight edge darkening (6 percent within 40 px). Every piece has its own jitter, so neighbouring edges do not match exactly.
Shadow: the piece alpha blurred sigma 11 (4× grid), offset (2.5 + 12g, 3.5 + 17g) screen px, opacity 0.20 + 0.28g, where g is the scatter factor (B2–B4).
## 4. Camera
Screen px = 540 + zoom × (page point − centre). Zoom is exponential: zoom = 4.8^(1 − u), u = smootherstep((t − 0.35) / 4.1).
| t (s) | centre x | centre y | zoom | ease |
|---|---|---|---|---|
| 0–0.35 | 427 | 262 | 4.8 | hold |
| 0.35–4.45 | 427 → 427.5 | 262 → 318.5 | 4.8 → 1.0 | smootherstep (6t^5 − 15t^4 + 10t^3) |
| 4.45–7.0 | 427.5 | 318.5 | 1.0 | hold |
Motion blur: 3 sub-frames per frame across half a frame interval (shutter 180 degrees), averaged.
## 5. Timeline (beats)
Each piece i has scatter factor g_i(t), peak time tp_i and end time te_i from the table. Piece transform = rotate by rot_i × g about its seed, then move by off_i × g.
| Piece | off (px) | rot (deg) | tp (s) | te (s) |
|---|---|---|---|---|
| 0 | (-70,-62) | -6 | 2.35 | 4.35 |
| 1 | (8,-95) | 3 | 2.05 | 3.95 |
| 2 | (78,-70) | 7 | 2.30 | 4.45 |
| 3 | (-110,6) | -4 | 2.15 | 3.90 |
| 4 (centre) | (0,4) | 1.2 | 2.25 | 4.20 |
| 5 | (115,-18) | 5 | 2.45 | 4.40 |
| 6 | (-85,70) | 6 | 2.00 | 4.00 |
| 7 | (14,98) | -3 | 2.20 | 4.30 |
| 8 | (92,78) | -7 | 2.40 | 4.60 |
Stack order, bottom to top: underlay, pieces 6, 7, 8, 3, 5, 0, 1, 2, 4.
### B1 · Close-up hold — 0–0.35 s
Giant headline fills the frame. Pieces sit slightly apart at g = 0.22.
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.35 | camera | zoom | 4.8 → 4.8 | hold |
### B2 · Drift apart — 0.35–peak s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–tp_i | piece i | g | 0.22 → 1.0 | smoothstep  |
| 0.35–2.4 | camera | zoom | 4.8 → about 2.3 | smootherstep |
### B3 · Full scatter — about 2.0–2.6 s
The underlay shows widest. Masthead pieces float above the headline pieces. Gap shapes are ragged.
### B4 · Snap back — tp_i–te_i s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| tp_i–te_i | piece i | g | 1.0 → 0 | ease in-out cubic  |
| 2.4–4.45 | camera | zoom | 2.3 → 1.0 | smootherstep |
### B5 · Settle — 4.6–7.0 s
All pieces at rest, thin cracks and torn rims visible, the whole page centred. Nothing moves.
## 8. Never
- Never change the number of pieces, their order or the timing.
- Never stretch the photo.
- Never put invented words on the page; empty optional text stays empty.
- Never let the headline be clipped by the page edge in the settled frame.
- Never leave wide gaps after B4; the page must read as one sheet with cracks.

## 5. OUTPUT
- One video, format 1:1 · 1080×1080 · 30 fps · 7.0 s (reference 480×480; every size below is given in page px, where the settled page is 855×637 output px). Keep the motion, timing and order of beats of section 4.
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
