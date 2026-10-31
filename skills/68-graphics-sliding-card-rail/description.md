# description.md: Sliding Card Rail

Five image cards stand in a row on a dark square panel, tilted in perspective. A red rail with a white knob and a label sits under each card. The camera drops in from far away, lands on card 1, glides along the row card by card with constant, gently easing speed, and settles on card 5. It communicates a five-step sequence.
**The graphic in one line:** five perspective image cards on an accent rail with knobs and labels, a fly-in then a continuous glide to the last card.
**Format:** 9:16 · 720×1280 · 30 fps · 10.1 s (reference 720×1280, no output scaling)

## 1. Canvas
- Backdrop #161616 (measured 22,22,22) over the whole 720×1280 frame.
- Panel: a 720×720 square at y 280–1000, colour #202020 (measured 32,32,32). All graphic content is clipped to the panel. No texture, no grain, no vignette.
- Panel coordinates: panel y = frame y - 280. The camera principal point is x 330 (measured, cards pass the centre at x about 330), y 640 in frame space at rest.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Label 1 | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit down to 70%) | E2, card 1 |
| P2 | Label 2 | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit down to 70%) | E2, card 2 |
| P3 | Label 3 | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit down to 70%) | E2, card 3 |
| P4 | Label 4 | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit down to 70%) | E2, card 4 |
| P5 | Label 5 | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit down to 70%) | E2, card 5 |
| P6 | Image 1 | yes | none, must ask | image, any aspect, cover-fit to 5:3, ≥ 900 px wide | E1, card 1 |
| P7 | Image 2 | yes | none, must ask | image, any aspect, cover-fit to 5:3, ≥ 900 px wide | E1, card 2 |
| P8 | Image 3 | yes | none, must ask | image, any aspect, cover-fit to 5:3, ≥ 900 px wide | E1, card 3 |
| P9 | Image 4 | yes | none, must ask | image, any aspect, cover-fit to 5:3, ≥ 900 px wide | E1, card 4 |
| P10 | Image 5 | yes | none, must ask | image, any aspect, cover-fit to 5:3, ≥ 900 px wide | E1, card 5 |
| P11 | Accent colour | no | #FF2300 (measured) | hex | E3 rail |
| P12 | Band colour | no | #202020 (measured) | hex, dark | panel |
| P13 | Backdrop colour | no | #161616 (measured) | hex, dark | canvas |
| P14 | Label colour | no | #FFFFFF (measured) | hex, light | E2 |
| P15 | Focal points | no | auto (face or subject, else centre) | 5 points, fractions of each image | E1 crops |

### 2.1 How to infer parameters from user material
- Labels: the five stages of the user's process, one or two words each, in order.
- Images: user photos in step order; stills from a user video (frames with a clear subject).
- Accent: may come from a brand colour; keep strong contrast with #202020.
- Focal points: detect a face (OpenCV or mediapipe); else the user's hint; else centre.

## 3. Elements
World units: 1 unit = 1 px at camera zoom 1 and no perspective. Card i (i = 0..4) has pitch X_i = 540 i. World y is down; y = 0 is the principal row (frame y 640).
### E1 · Image card
Rect 432×259 (5:3, measured), centre x = X_i + 24 (measured), y from -168 to +91. Cover-fit crop with focal point at the crop centre. No border, no shadow, no radius, no filter.
### E2 · Label
Inter SemiBold (opsz 32, wght 600), colour P14, size 36 (measured "Main Text 5" width about 213 px), centred at x = X_i - 4, y = +202. Auto-fit: width ≤ 360, shrink by 5 percent steps to a floor of 70% size.
### E3 · Rail
One straight accent bar (P11), thickness 11, centred on y = +134, from x = -350 to x = 4×540 + 290 = 2450 when fully drawn. Square ends. It is drawn on from the left (B2) and then extended ahead of the camera (B4).
### E4 · Knob
White (#FFFFFF) disc, radius 20 (diameter 40, measured), centre (X_i, +134), on top of the rail. Always visible.

## 4. Camera
A pinhole camera looks at a plane that is yawed about the vertical axis so the right side is nearer. Constants: focal f = 1000, yaw φmax = 35° (measured from knob width 31 px at x 44, 38 at x 326, 48 at x 668).
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
Cards pass the screen centre (x 330) at about 3.7, 5.3, 6.9 and 9.9 s (measured). The glide never stops between cards 1 and 5.
Motion blur: temporal supersampling over a 0.3-frame shutter. N = clamp(ceil(card speed in px per frame / 5), 1, 10); during the first 1.4 s the zoom change also counts. No kernel blur.

## 5. Timeline (beats)
### B1 · Fly-in — 0–1.35 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.3 | camera | zoom | 0.454 → 1.0 | smoothstep (measured) |
| 0–1.35 | camera | c | 2 → 0.08 | quad out (measured) |
| 0.1–1.4 | camera | yaw | 0° → 35° | quad out (measured) |
At t = 0 cards 2–4 are in view (tiny), cards, knobs and labels fully visible, no rail.
### B2 · Rail draw-on — 0.5–1.35 s
| 0.5–1.35 | E3 | right end | -350 → +60 | cubic out (design) |
### B3 · Hold on card 1 — 1.35–1.6 s
Camera nearly still (speed ramps up from zero).
### B4 · Glide — 1.35–9.9 s
| 1.5–2.1 | E3 | right end | 60 → min(2450, c·540 + 800) | smoothstep (design) |
| 2.1–9.9 | E3 | right end | = min(2450, c·540 + 800) | leads the camera |
| 1.35–9.9 | camera | c | per section 4 | Hermite (measured) |
### B5 · Settle — 9.9–10.1 s
Card 5 centred, nothing moves.

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. Output 720×1280.
- Pre-render the world strip once (cards and labels, x -800..3000, y -200..260) at 2.5 px/unit and at 1.25 px/unit (use the smaller one when zoomed out), premultiplied RGBA.
- Per frame: crop the strip to x in c·540 ± (900 / zoom) on the left and 520 / zoom + 100 on the right, warp with `cv2.getPerspectiveTransform` from the projected corners, composite on the panel colour at 2× (1440×1440), then draw the rail polygon and the knob polygons (projected points, `cv2.fillPoly` with LINE_AA and shift 2), then average sub-frames and downscale with INTER_AREA.
- Frames after 9.9 s are identical. Render in chunks of 60 frames if memory is tight.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The settled frame at t = 10: card 5 (centred, label under it) with the right end of the rail, knob 5 on the rail, card 4 cut by the panel edge on the left.

## 8. Never
- Distorted images, or a number of steps other than 5.
- Labels touching the knob, rail or card.
- Content outside the 720×720 panel.
- Reference content (its words or pictures) as defaults.
- Text longer than the auto-fit floor.
