# Google Flow prompt · Sliding Card Rail
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 720×1280 · 30 fps · 10.1 s (reference 720×1280, no output scaling)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Sliding Card Rail" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. five perspective image cards on an accent rail with knobs and labels, a fly-in then a continuous glide to the last card.

Five image cards stand in a row on a dark square panel, tilted in perspective. A red rail with a white knob and a label sits under each card. The camera drops in from far away, lands on card 1, glides along the row card by card with constant, gently easing speed, and settles on card 5. It communicates a five-step sequence.
**The graphic in one line:** five perspective image cards on an accent rail with knobs and labels, a fly-in then a continuous glide to the last card.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Label 1 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Label 2 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P3 · Label 3 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P4 · Label 4 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P5 · Label 5 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P6 · Image 1 (REQUIRED, image, any aspect, cover-fit to 5:3, ≥ 900 px wide): <your value>
P7 · Image 2 (REQUIRED, image, any aspect, cover-fit to 5:3, ≥ 900 px wide): <your value>
P8 · Image 3 (REQUIRED, image, any aspect, cover-fit to 5:3, ≥ 900 px wide): <your value>
P9 · Image 4 (REQUIRED, image, any aspect, cover-fit to 5:3, ≥ 900 px wide): <your value>
P10 · Image 5 (REQUIRED, image, any aspect, cover-fit to 5:3, ≥ 900 px wide): <your value>
P11 · Accent colour (optional, hex; default: #FF2300): <your value or NONE>
P12 · Band colour (optional, hex, dark; default: #202020): <your value or NONE>
P13 · Backdrop colour (optional, hex, dark; default: #161616): <your value or NONE>
P14 · Label colour (optional, hex, light; default: #FFFFFF): <your value or NONE>
P15 · Focal points (optional, 5 points, fractions of each image; default: auto (face or subject, else centre)): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Labels: the five stages of the user's process, one or two words each, in order.
- Images: user photos in step order; stills from a user video (frames with a clear subject).
- Accent: may come from a brand colour; keep strong contrast with #202020.
- Focal points: detect a face (OpenCV or mediapipe); else the user's hint; else centre.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Backdrop #161616 over the whole 720×1280 frame.
- Panel: a 720×720 square at y 280–1000, colour #202020. All graphic content is clipped to the panel. No texture, no grain, no vignette.
- Panel coordinates: panel y = frame y - 280. The camera principal point is x 330, y 640 in frame space at rest.
## 3. Elements
World units: 1 unit = 1 px at camera zoom 1 and no perspective. Card i (i = 0..4) has pitch X_i = 540 i. World y is down; y = 0 is the principal row (frame y 640).
### E1 · Image card
Rect 432×259, centre x = X_i + 24, y from -168 to +91. Cover-fit crop with focal point at the crop centre. No border, no shadow, no radius, no filter.
### E2 · Label
Inter SemiBold (opsz 32, wght 600), colour P14, size 36, centred at x = X_i - 4, y = +202. Auto-fit: width ≤ 360, shrink by 5 percent steps to a floor of 70% size.
### E3 · Rail
One straight accent bar (P11), thickness 11, centred on y = +134, from x = -350 to x = 4×540 + 290 = 2450 when fully drawn. Square ends. It is drawn on from the left (B2) and then extended ahead of the camera (B4).
### E4 · Knob
White (#FFFFFF) disc, radius 20, centre (X_i, +134), on top of the rail. Always visible.
## 4. Camera
A pinhole camera looks at a plane that is yawed about the vertical axis so the right side is nearer. Constants: focal f = 1000, yaw φmax = 35°.
Projection of world (X, Y): Xr = X - c·540; D = 1000/zoom; z3 = D - Xr·sin φ; screen x = 330 + f·Xr·cos φ / z3; screen y = cy + f·Y / z3.
Parameters over time:
| t (s) | c (card index) | zoom | yaw φ | cy | ease |
|---|---|---|---|---|---|
| 0 | 2.00 | 0.454 | 0° | 670 | start |
| 0–1.35 | 2.00 → 0.08 | | | | c = 0.08 + 1.92(1-u)², u = t/1.35 |
| 0–1.3 | | 0.454 → 1.00 | | 670 → 640 | smoothstep |
| 0.1–1.4 | | | 0° → 35° | | 1-(1-u)² |
| 1.35 | 0.08 | 1.00 | 35° | 640 | hold values from here |
| 1.35→3.7 | 0.08 → 1 | | | | cubic Hermite, speeds 0 → 0.55 cards/s |
| 3.7→5.3 | 1 → 2 | | | | Hermite, speed 0.55 → 0.60 cards/s |
| 5.3→6.9 | 2 → 3 | | | | Hermite, speed 0.60 → 0.58 cards/s |
| 6.9→9.9 | 3 → 4 | | | | Hermite, speed 0.58 → 0 (ease-out) |
| 9.9–10.1 | 4 | 1.00 | 35° | 640 | still |
Cards pass the screen centre (x 330) at about 3.7, 5.3, 6.9 and 9.9 s. The glide never stops between cards 1 and 5.
## 5. Timeline (beats)
### B1 · Fly-in — 0–1.35 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.3 | camera | zoom | 0.454 → 1.0 | smoothstep |
| 0–1.35 | camera | c | 2 → 0.08 | quad out |
| 0.1–1.4 | camera | yaw | 0° → 35° | quad out |
At t = 0 cards 2–4 are in view (tiny), cards, knobs and labels fully visible, no rail.
### B2 · Rail draw-on — 0.5–1.35 s
| 0.5–1.35 | E3 | right end | -350 → +60 | cubic out  |
### B3 · Hold on card 1 — 1.35–1.6 s
Camera nearly still (speed ramps up from zero).
### B4 · Glide — 1.35–9.9 s
| 1.5–2.1 | E3 | right end | 60 → min(2450, c·540 + 800) | smoothstep  |
| 2.1–9.9 | E3 | right end | = min(2450, c·540 + 800) | leads the camera |
| 1.35–9.9 | camera | c | per section 4 | Hermite |
### B5 · Settle — 9.9–10.1 s
Card 5 centred, nothing moves.
## 8. Never
- Distorted images, or a number of steps other than 5.
- Labels touching the knob, rail or card.
- Content outside the 720×720 panel.
- Reference content (its words or pictures) as defaults.
- Text longer than the auto-fit floor.

## 5. OUTPUT
- One video, format 9:16 · 720×1280 · 30 fps · 10.1 s (reference 720×1280, no output scaling). Keep the motion, timing and order of beats of section 4.
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
