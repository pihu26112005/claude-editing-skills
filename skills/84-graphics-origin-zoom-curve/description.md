# description.md: Origin Zoom Curve

A dark-mode growth chart. The camera starts tight on the origin of two dashed axes. A jagged glowing line grows from the origin while the camera pulls back. As the full chart appears, a grid fades in and a title and two axis labels blur in.
**The graphic in one line:** dashed axes seen close up, a glowing exponential line drawn from the origin during a zoom-out, then grid, title and labels fade in.
**Format:** 9:16 · 1080×1920 · 30 fps · 7.5 s (reference 720×1280; all world units below are 720×1280 px, multiply by 1.5 for output)

## 1. Canvas
- Background: elliptical glow centred (360,780) units, colour #272526 (39,37,38) fading to #121114 (18,17,20) at the corners. Gaussian falloff, sigma x 261, sigma y 434 above and 200 below the centre. (measured)
- Add ±0.6 level dither noise to avoid banding in the dark gradient. (design)
- No grain, no logo.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Title | yes | none, must ask | text, ≤ 24 chars, 1 line (auto-fit down to 70%) | E5, B3 |
| P2 | Y-axis label | yes | none, must ask | text, ≤ 16 chars, 1 line | E6, B3 |
| P3 | X-axis label | yes | none, must ask | text, ≤ 16 chars, 1 line | E7, B3 |
| P4 | Accent colour | no | #BA00D2 (measured) | hex, bright on dark | E3, E5 |
| P5 | Label and axis colour | no | #FFFFFF (measured) | hex | E1, E4, E6, E7 |
| P6 | Background centre and corner | no | #272526 and #121114 (measured) | 2 hex, dark | canvas |
| P7 | Grid | no | on | on / off | E4 |
| P8 | Curve seed | no | 7 | integer | E3 |

### 2.1 How to infer parameters from user material
- Title: the metric or topic in the user's script, shortest strong phrase.
- Axis labels: the measured quantity (Y) and the time or step (X).
- Accent: a brand colour from a logo; keep strong contrast with the dark background.

## 3. Elements
World units, z = 1 view. Origin O = (139,816) on screen. Chart box 441×441 (right and up from O).
### E1 · Axes
Two dashed white (P5) lines from O, along x and up, each 441 long. Width 3, dashes 13 on, 13 off, first dash starts 17 from O. Faint white glow (blur 5, alpha 0.12). (measured)
### E2 · Origin dot
White disc radius 4.5 at O. (measured)
### E3 · Growth line
Colour P4, width 2.4, round, polyline with a vertex every 5.5 units. Height h(x) follows knots (x/441 : h) 0:0, .09:12.5, .18:13.5, .27:24.5, .36:33, .45:63, .54:76, .63:92, .73:118, .82:174, .91:305, 1:441, smoothed with a 7-vertex box. Jitter per vertex: normal noise (seeded by P8) with sigma 1.6 + 3.2 (x/441)^0.7; first and last vertex exact. Glow: blur 6 units, alpha 0.55.
### E4 · Grid
7 vertical and 7 horizontal lines, pitch 63, from the axes to the box edge (top and right lines included). White, width 1.3, final alpha 0.33. Hidden when P7 is off.
### E5 · Title
Outfit Medium 500, size 42.3 (cap height 29.6), colour P4, centred on x 364.5, cap top y 264, baseline y 293. Soft glow (blur 7, alpha 0.35). Auto-fit: width ≤ 420, shrink to 70% floor.
### E6 · Y-axis label
Outfit 500, size 35, colour P5, rotated 90° counter-clockwise (reads bottom to top), centred at (108.5, 608). Length ≤ 380.
### E7 · X-axis label
Outfit 500, size 35, colour P5, centred at (361, 845).

## 4. Camera
Screen = pivot + z × (point − pivot), pivot (139,849), in reference px; ×1.5 for output. The origin therefore stays at x = 139.
| t (s) | zoom | ease |
|---|---|---|
| 0 | 2.42 | |
| 0.8 | 2.40 | hold, then ease out |
| 1.0 | 2.30 | |
| 1.5 | 2.08 | |
| 2.0 | 1.60 | |
| 2.67 | 1.24 | |
| 3.0 | 1.15 | |
| 3.5 | 1.09 | |
| 4.0 | 1.03 | |
| 4.6 | 1.00 | hold to 7.5 |
Linear between keys, then gaussian smoothing sigma 0.12 s. Motion blur: average N sub-frames over a 0.5-frame shutter, N = clamp(ceil(zoom change × 900 × 1.5 / 5), 1, 8).

## 5. Timeline (beats)
### B1 · Close-up hold — 0–0.3 s
Axes and dot visible at zoom 2.42. Nothing moves.
### B2 · Draw and pull back — 0.3–4.6 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.3–4.4 | E3 | head x (units) | 0 → 441, keys (0.5:17) (1.0:77) (1.5:164) (2.0:289) (2.5:379) (3.0:418) (3.5:432) (4.0:442) | smooth, fast mid, slow end |
| 0–4.6 | camera | zoom | 2.42 → 1.0 | section 4 |
### B3 · Chart dress-up — 3.7–5.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 3.7–4.67 | E4 | alpha | 0 → 0.50 | sine ^1.3 |
| 4.67–4.97 | E4 | alpha | 0.50 → 0.33 | sine |
| 3.7–4.6 | E5 | blur 12 → 0 units, alpha 0 → 1 in 0.35 s | | sine, out |
| 3.9–4.8 | E6, E7 | same blur-in | | sine, out |
### B4 · Hold — 5.0–7.5 s
Nothing moves.

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. Draw masks (axes, line, grid) per frame on a 2x canvas (2160×3840) with `cv2` fixed-point anti-aliased lines, downscale with INTER_AREA, composite in float32.
- Text: PIL sprites at 3 px per unit, blurred then warped with the camera zoom.
- Frames after 5.0 s are identical; render once. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
Final frame: axes with dashes, the glowing line ending on the top-right grid corner, 7×7 grid, title above, Y label left, X label below.

## 8. Never
- A line that leaves the chart box.
- Text overlapping the grid or axes.
- Extra elements (logos, legends, data points).
- Reference content (its words) as defaults.
