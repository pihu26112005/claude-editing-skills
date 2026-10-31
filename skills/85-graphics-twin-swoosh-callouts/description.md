# description.md: Twin Swoosh Callouts

A dark-stage callout graphic. A tall glowing image card slides in from the left, the camera pushes in and pans right, two tapered gradient brush swooshes draw out beside the card, a glowing label types in at the end of each, and the camera eases back to a still composition.
**The graphic in one line:** glowing portrait card, camera push-in, two gradient swooshes ending in two glowing labels, ease-out to a settled layout.
**Format:** 16:9 · 1920×1080 · 30 fps · 6.0 s (reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output)

## 1. Canvas
- Stage: near-black, #121114 (18,17,20) at the corners. A soft radial lift in screen space centred on the frame: colour = (18,17,20) + exp(-(r/400)²) × (17,16,11), r in world units from the centre (centre measured (35,33,31)).
- Faint film grain, ±0.8 levels. No grid, no texture.
- All elements live in world space and move with the camera; the stage lift stays in screen space.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Card image | yes | none, must ask | image, portrait about 9:16, cover-fit, ≥ 540 px short side | E1, B1–B7 |
| P2 | Label 1 | yes | none, must ask | text, ≤ 18 chars, 1 line (auto-fit down to 70%) | E4, B4 |
| P3 | Label 2 | yes | none, must ask | text, ≤ 18 chars, 1 line (auto-fit down to 70%) | E5, B5 |
| P4 | Swoosh tail colour | no | #E97C11 (measured) | hex | E2, E3 |
| P5 | Swoosh head colour | no | #FFFF59 (measured) | hex | E2, E3 |
| P6 | Label colour | no | #FDDF00 (measured) | hex | E4, E5 |
| P7 | Glow colour | no | #FFC800 (design) | hex | label and swoosh glow |
| P8 | Card border colour | no | #EED89B (measured) | hex | E1 |
| P9 | Stage colour | no | #121114 (measured) | hex, dark | canvas |
| P10 | Focal point | no | auto (face or subject, else centre) | fractions of the image | E1 crop |

### 2.1 How to infer parameters from user material
- Card image: a user photo or a still from a user video with a clear vertical subject.
- Labels: two short tags from the user's script, the first is the lower one.
- Colours: P4–P8 may come from a brand colour: tail = the deeper shade, head = a lighter tint, label = the tint, border = a pale tint. Keep strong contrast with the stage.
- Focal point: detect a face (OpenCV or mediapipe); else the user's hint; else centre.

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
All values measured from the reference (card edges and label widths per frame). Motion blur: temporal supersampling over a 0.6-frame shutter centred on the frame; N = clamp(ceil(largest screen displacement in px / 5), 1, 24) full renders averaged in float32.

## 5. Timeline (beats)
### B1 · Card slide-in — 0–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.2 | camera | cx 1203 → 640 | card slides in from the left, heavy motion blur | ease-out (about cubic, measured) |
### B2 · Push-in — 1.2–2.0 s
| 1.2–2.0 | camera | zoom 1.04 → 1.60, centre to (776,437) | card slides left out of frame | smooth (measured table) |
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

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, SciPy (gaussian smoothing of the camera), ffmpeg. Output 1920×1080, composited in float32.
- Card and letters are pre-rendered premultiplied RGBA sprites at 2.4 px per unit (card at 768×1363 plus a glow margin) and placed per sub-frame with `cv2.warpAffine` (scale = 1.5 × zoom / 2.4, never above 1).
- Swooshes are drawn at 2× in screen space as a strip of quads between left and right offset curves (no anti-alias seams), with a round cap at the head, then area-downscaled. The glow is a gaussian of the alpha.
- Label letters are separate sprites so each can fade and scale on its own clock.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`. Render once for the static tail.

## 7. Still frame
The settled frame (4.7 s on): card at left, two swooshes sweeping to the right, Label 2 at the end of the upper swoosh and Label 1 at the end of the lower one, all on the dark stage.

## 8. Never
- A distorted or letterboxed image.
- A different number of swooshes or labels.
- Labels overlapping a swoosh or leaving the frame.
- Reference content (its words or pictures) as defaults.
- Text longer than the auto-fit floor.
