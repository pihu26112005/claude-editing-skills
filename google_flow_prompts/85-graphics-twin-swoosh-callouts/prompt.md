# Google Flow prompt · Twin Swoosh Callouts
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 6.0 s (reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Twin Swoosh Callouts" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. glowing portrait card, camera push-in, two gradient swooshes ending in two glowing labels, ease-out to a settled layout.

A dark-stage callout graphic. A tall glowing image card slides in from the left, the camera pushes in and pans right, two tapered gradient brush swooshes draw out beside the card, a glowing label types in at the end of each, and the camera eases back to a still composition.
**The graphic in one line:** glowing portrait card, camera push-in, two gradient swooshes ending in two glowing labels, ease-out to a settled layout.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Card image (REQUIRED, image, portrait about 9:16, cover-fit, ≥ 540 px short side): <your value>
P2 · Label 1 (REQUIRED, text, ≤ 18 chars, 1 line (auto-fit down to 70%)): <your value>
P3 · Label 2 (REQUIRED, text, ≤ 18 chars, 1 line (auto-fit down to 70%)): <your value>
P4 · Swoosh tail colour (optional, hex; default: #E97C11): <your value or NONE>
P5 · Swoosh head colour (optional, hex; default: #FFFF59): <your value or NONE>
P6 · Label colour (optional, hex; default: #FDDF00): <your value or NONE>
P7 · Glow colour (optional, hex; default: #FFC800 (design)): <your value or NONE>
P8 · Card border colour (optional, hex; default: #EED89B): <your value or NONE>
P9 · Stage colour (optional, hex, dark; default: #121114): <your value or NONE>
P10 · Focal point (optional, fractions of the image; default: auto (face or subject, else centre)): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Card image: a user photo or a still from a user video with a clear vertical subject.
- Labels: two short tags from the user's script, the first is the lower one.
- Colours: P4–P8 may come from a brand colour: tail = the deeper shade, head = a lighter tint, label = the tint, border = a pale tint. Keep strong contrast with the stage.
- Focal point: detect a face (OpenCV or mediapipe); else the user's hint; else centre.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Stage: near-black, #121114 (18,17,20) at the corners. A soft radial lift in screen space centred on the frame: colour = (18,17,20) + exp(-(r/400)²) × (17,16,11), r in world units from the centre (centre measured (35,33,31)).
- Faint film grain, ±0.8 levels. No grid, no texture.
- All elements live in world space and move with the camera; the stage lift stays in screen space.
## 3. Elements
World units (1280×720 reference frame, settled view).
### E1 · Image card
Rect (203,69) 320×568, corner radius 22. Image cover-fitted to the whole rect with the focal point P10. Border 4 wide, colour P8. Inner glow: the border blurred (sigma 4) at 55 percent over the image edge. Outer glow: the border blurred (sigma 7) at up to 80 percent, colour P8. Card sprite built at 2.4 px per unit.
### E2 · Lower swoosh
Spline (Catmull-Rom) through (575,410) (588,430) (620,452) (670,460) (740,460) (800,468) (860,487) (913,504). Tapered brush stroke: width by path fraction s: 3.5 to 13 (sine in) for s < 0.4, then 13 × cos((s-0.4)/0.6 × π/2)^1.25 + 0.6 to a point at the head. Colour runs from P4 at the tail to P5 at the head, c = P4 × (1-s^0.8) + P5 × s^0.8. Glow: stroke alpha blurred (sigma 7 units), colour P7, 55 percent.
### E3 · Upper swoosh
Same style through (595,316) (612,326) (640,328) (690,315) (740,285) (800,255) (860,240) (915,233).
### E4 · Label 1
Barlow Condensed Bold, size 61 (cap height about 43), left edge x=934, baseline y=538. Fill: vertical gradient from P6 lightened 45 percent (top) to P6 × 0.85 (bottom). Glow: blur sigma 6.5 units, colour P7, up to 85 percent. Auto-fit: width ≤ 300, shrink to 70% floor.
### E5 · Label 2
Same style, left x=934, baseline y=241.
## 4. Camera
Screen = 1.5 × (640 + zoom × (world x - cx), 360 + zoom × (world y - cy)). Keyframes are linearly interpolated, then smoothed with a gaussian of sigma 0.05 s.
| t (s) | cx | cy | zoom |
|---|---|---|---|
| 0 | 1203 | 376 | 1.00 |
| 0.1 | 1032 | 375 | 1.00 |
| 0.2 | 915 | 373 | 1.00 |
| 0.3 | 841 | 371 | 1.00 |
| 0.4 | 789 | 369 | 1.00 |
| 0.5 | 749 | 367 | 1.00 |
| 0.6 | 718 | 366 | 1.00 |
| 0.7 | 694 | 365 | 1.00 |
| 0.8 | 676 | 364 | 1.00 |
| 0.9 | 662 | 363 | 1.00 |
| 1.0 | 651 | 362 | 1.00 |
| 1.1 | 644 | 361 | 1.01 |
| 1.2 | 640 | 362 | 1.04 |
| 1.3 | 638 | 369 | 1.125 |
| 1.4 | 643 | 369 | 1.27 |
| 1.5 | 654 | 385 | 1.40 |
| 1.6 | 666 | 400 | 1.50 |
| 1.7 | 686 | 415 | 1.57 |
| 1.8 | 729 | 428 | 1.60 |
| 1.9 | 770 | 435 | 1.60 |
| 2.0 | 776 | 437 | 1.60 |
| 2.6 | 755 | 425 | 1.58 |
| 2.7 | 748 | 422 | 1.58 |
| 3.0 | 688 | 330 | 1.29 |
| 3.3 | 690 | 320 | 1.27 |
| 3.7 | 680 | 325 | 1.24 |
| 4.0 | 668 | 340 | 1.16 |
| 4.3 | 646 | 347 | 1.06 |
| 4.6 | 640 | 360 | 1.00 |
## 5. Timeline (beats)
### B1 · Card slide-in — 0–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.2 | camera | cx 1203 → 640 | card slides in from the left, heavy motion blur | ease-out |
### B2 · Push-in — 1.2–2.0 s
| 1.2–2.0 | camera | zoom 1.04 → 1.60, centre to (776,437) | card slides left out of frame | smooth |
### B3 · Swoosh seeds — 1.5 s
| 1.5 | E2, E3 | seed dot (progress 0.012) | | cut |
### B4 · Lower swoosh and Label 1 — 1.55–2.7 s
| 1.55–2.15 | E2 | draw-on 0.012 → 1 | smoothstep |
| 2.05–2.7 | E4 | letters fade in, 0.08 s stagger, 0.25 s each, scale 0.9 → 1, out cubic. Order: first letter, last letter, then the rest in a fixed shuffle |
### B5 · Upper swoosh and Label 2 — 2.3–3.3 s
| 2.3–2.8 | E3 | draw-on 0.012 → 1 | smoothstep |
| 2.65–3.3 | E5 | letters fade in as E4 | |
### B6 · Ease-out — 2.7–4.6 s
Camera follows the table: swing to (688,330) zoom 1.29 by 3.0 s, hold near 1.25, ease to the settled view by 4.6 s.
### B7 · Hold — 4.6–6.0 s
Still. Frames after 4.7 s are identical.
## 8. Never
- A distorted or letterboxed image.
- A different number of swooshes or labels.
- Labels overlapping a swoosh or leaving the frame.
- Reference content (its words or pictures) as defaults.
- Text longer than the auto-fit floor.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 6.0 s (reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
