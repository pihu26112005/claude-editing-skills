# description.md: Slip Surface Cuts

A short paper label sits dead centre of a vertical frame. A line of text types onto it, one letter at a time, while the surface under the label hard-cuts every 0.2 s between 14 desk looks (folded graph paper, wood grains, crumpled graph paper, cutting mats). The label changes between three paper colours as the surfaces cut. The text never moves. The last scene holds the label on crumpled paper.
**The graphic in one line:** a typed paper slip over 14 rapid surface cuts, with props on a few surfaces.
**Format:** 9:16 · 1080×1920 · 30 fps · 2.8 s (reference 720×1280, 84 frames; multiply reference px by 1.5)

## 1. Canvas
- No fixed background: each scene has its own procedural surface (section 3, E1), lit by a soft spot (centre per scene, corners darken to 25–45 percent of peak, warm tint) and ±1.6 levels of grain.
- Light comes from the upper right: all shadows fall to the lower left.
- Safe area: the slip stays inside x 0.08–0.92 W; props may be cropped by the frame edges.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Slip text | yes | none, must ask | text, ≤ 18 chars, 1 line (auto-fit down to 70%) | E2, B1 |
| P2 | Prop image 1 (pencil slot, scene 1 top-right) | no | none (surface only) | transparent PNG cut-out, any aspect, ≥ 600 px long side | E3, scene 1 |
| P3 | Prop image 2 (scene 1 bottom-left) | no | none | transparent PNG cut-out, ≥ 400 px | E3, scene 1 |
| P4 | Prop image 3 (scenes 3 and 9, below the slip) | no | none | transparent PNG cut-out, ≥ 500 px | E3, scenes 3 and 9 |
| P5 | Slip colour A (main) | no | #C83A38 (measured) | hex | slip, 9 of 14 scenes |
| P6 | Slip colour B (pale) | no | #DDD0BE (measured) | hex, light | slip, 4 scenes |
| P7 | Slip colour C (alt) | no | #AE835A (measured) | hex | slip, 1 scene |
| P8 | Text colour | no | auto: white on dark slips, #26201C on light (design) | hex | E2 |

### 2.1 How to infer parameters from user material
- Slip text: the shortest strong phrase (title, name, topic) in the user's message.
- Props: objects the user names or attaches that fit the topic; opaque photos are cut out first or placed as a rounded print with a white border.
- Colours: A may come from a brand colour; B and C stay neutral papers unless asked.

## 3. Elements
### E1 · Surface (14 scenes)
Procedural, 1080×1920, regenerated per scene from fixed seeds. Types: folded graph paper (pitch 48 px, vertical crease at 0.5 W, horizontal creases at 0.33 and 0.68 H); wood (grain bands with ring pitch 60–210 px, light/dark pairs amber, dark brown, light honey, vertical dark); crumpled graph paper (ridged noise shading, pitch 42–50 px, grid displaced by the ridges); cutting mat (green, yellow-gridded green and teal, minor lines every 60 px, major every 300 px).
Scene order and slip settings (pad = slip side padding as a fraction of W, h = slip height as a fraction of H):
| # | Surface | Slip colour | pad | h | cx | cy | rot ° |
|---|---|---|---|---|---|---|---|
| 1 | folded graph paper + props P2, P3 | A | .05 | .118 | .483 | .49 | 0 |
| 2 | amber wood | A | .10 | .135 | .512 | .47 | -1 |
| 3 | amber wood + prop P4 | A | .09 | .135 | .515 | .425 | .6 |
| 4 | fine honey wood | B | .075 | .12 | .528 | .485 | 0 |
| 5 | crumpled paper | A | .05 | .118 | .46 | .49 | 1.6 |
| 6 | crumpled paper | C | .08 | .125 | .5 | .488 | -1 |
| 7 | green mat | A | .06 | .13 | .44 | .49 | 2 |
| 8 | dark vertical wood | B | .07 | .125 | .464 | .48 | -1.5 |
| 9 | crumpled paper + prop P4 (rot 25°) | A | .10 | .135 | .5 | .45 | 0 |
| 10 | dark wood | A | .06 | .12 | .46 | .483 | 1 |
| 11 | light wood | B | .075 | .125 | .5 | .489 | -1 |
| 12 | yellow-grid mat | A | .08 | .122 | .524 | .489 | 1.5 |
| 13 | teal mat | B | .05 | .122 | .447 | .473 | 0 |
| 14 | crumpled paper | A × 0.8 (deeper) | .12 | .122 | .5 | .494 | -2 |
### E2 · Slip and text
Paper slip, width = text width + 2 × pad × W, height h × H, centred at (cx, cy), rotated by rot. Top and bottom edges are torn (low-frequency wobble ±13 px at 2x plus fine ±6 px teeth), left and right edges rough (±7 px). A pale fibre rim (#EEE8DE, 60 percent) runs 14–24 px (2x) along the torn edges. Paper grain ±7 percent, shading from 112 percent at the left to 78 percent at the right. Shadows: far (offset (-26, +24) px, blur 16, 55 percent) and near (offset (-7, +6), blur 4, 50 percent).
Text: Poppins Medium, 108 px, centred in the slip, with a soft shadow (28 percent, blur 3). Text width ≤ 0.66 W; longer text shrinks to 70 percent, then ask to shorten.
### E3 · Props
Transparent cut-outs with a shadow (offset (-18, +24), blur 16, 55 percent). P2: centre (0.80 W, 0.13 H), 1000 px long, rotated 128°, partly off-frame. P3: centre (0.16 W, 0.90 H), 520 px, rotated 20°. P4: centre (0.5 W, 0.74 H), 720 px (scene 3) and rotated 25° (scene 9). A missing prop is simply left out.

## 4. Camera
No camera move. Within each scene the whole frame pushes in: zoom 1.000 → 1.022 about the centre, linear over the 6 frames (design, measured as slight drift).

## 5. Timeline (beats)
### B1 · Typing — 0–0.55 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.067 | E2 | empty slip | | hold |
| 0.067–0.55 | E2 text | letters shown | 0 → all, one per interval = min(2 frames, 15 / chars frames) | hard step, no fade |
Typing runs across scenes 1–4 and keeps its place through the cuts.
### B2 · Surface cuts — 0–2.8 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| every 0.2 s (frames 0, 6, 12 … 78) | E1 | scene | n → n+1 | hard cut, no transition |
| each scene | frame | zoom | 1.000 → 1.022 | linear |
### B3 · Hold — 2.6–2.8 s
Scene 14 only; text complete.

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. One worker, stream frames into `ffmpeg -f rawvideo -pix_fmt rgb24 -s 1080x1920 -r 30 -i - -c:v libx264 -crf 16 -preset slow -pix_fmt yuv420p`.
- Surfaces: sum of resized random arrays (fractal noise). Wood: sin of (y / ring + warp ≤ 1.1) raised to 2.2, mixed with stretched streak noise, mapped between a dark and a light colour. Crumple: ridged noise, blur 4, shade = 1 + 26 × (gradient · light direction), grid remapped by 150 × gradient.
- Slip: build at 2x, polygon mask from noisy edge profiles, rim and grain, rotate, downscale with INTER_AREA, composite over the surface with both shadows. Per frame only the text layer changes.
- Zoom: `cv2.warpAffine` with reflect border. Grain added last.

## 7. Still frame
The last frame: the full text on its slip over crumpled graph paper.

## 8. Never
- Cross-fades or wipes between surfaces: cuts only.
- Text that moves, fades or retypes.
- Text outside the slip, or a slip outside the frame.
- Reference words or photos as defaults.
- More or fewer than 14 scenes.
