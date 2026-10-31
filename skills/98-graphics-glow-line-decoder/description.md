# description.md: Glow Line Decoder

A black-screen list reveal. A two-line glowing headline types on, six blurry placeholder lines appear under it, turn into grey pixel mosaics, then the camera zooms in hard, scrolls down the list and each mosaic line sharpens into readable glowing text one after another.
**The graphic in one line:** glowing two-line headline over six lines that decode from blur to pixel mosaic to sharp text while the camera zooms in and follows them down.
**Format:** 16:9 · 1920×1080 · 30 fps · 6.03 s (reference 1280×720; all world units below are in 1280×720 px, multiply by 1.5 for output)

## 1. Canvas
- Background pure black #000000 (measured). No grid, no grain, no vignette.
- Everything is additive light on black: glows add to the background.
- Content column centred on x = 640 units. Nothing sits outside x 300–980.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Headline line 1 | yes | none, must ask | text, ≤ 24 chars, 1 line (auto-fit down to 70%) | E1, B1 |
| P2 | Headline line 2 | yes | none, must ask | text, ≤ 24 chars, 1 line (auto-fit down to 70%) | E1, B1 |
| P3 | List line 1 | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit down to 70%) | E2, B2–B5 |
| P4 | List line 2 | yes | none, must ask | text, ≤ 14 chars, 1 line | E2, B2–B5 |
| P5 | List line 3 | yes | none, must ask | text, ≤ 14 chars, 1 line | E2, B2–B5 |
| P6 | List line 4 | yes | none, must ask | text, ≤ 14 chars, 1 line | E2, B2–B5 |
| P7 | List line 5 | yes | none, must ask | text, ≤ 14 chars, 1 line | E2, B2–B5 |
| P8 | List line 6 | yes | none, must ask | text, ≤ 14 chars, 1 line | E2, B2–B5 |
| P9 | Headline colour | no | #FDFE00 (measured) | hex, bright | E1 and its glow |
| P10 | List colour | no | #FFFFFF (measured) | hex, bright | E2 and its glow |
| P11 | Background | no | #000000 (measured) | hex, dark | canvas |

### 2.1 How to infer parameters from user material
- Headline: the video or post title, split into two balanced lines.
- List lines: six short steps, tips or key points from the user's script, shortest strong phrase each.
- Colours: P9 may come from a brand colour; keep strong contrast with the background.

## 3. Elements
World units (1280×720 frame at zoom 1).
### E1 · Headline
Two centred lines, Archivo Bold (wght 700) with the width axis narrowed until the wider line is ≤ 620 units (about wdth 78 for 20 chars); size 64 units; line centres y = 98 and 178 (design, measured about 96 and 177). Colour P9. Glow: text + 0.9 × gaussian(5 units) + 0.4 × gaussian(16 units), clipped.
### E2 · List lines (6)
Centres x = 640, y = 297, 372, 447, 522, 597, 672 (pitch 75, measured). Archivo Bold (wght 700, wdth 100), size 66 units (cap height about 47), colour P10, auto-fit width ≤ 560. Each line has three looks:
- Placeholder: the line's own text in capitals, Archivo ExtraBold size 50, gaussian blur 5 units, gain 2.2, soft glow.
- Mosaic: the sharp line pixelated into blocks 20 × 12 units, soft glow (0.45 × gaussian 8 + 0.3 × gaussian 22).
- Sharp: the same glow with no pixelation.

## 4. Camera
Screen = 1.5 × (zoom × (world − centre) + (640,360)). Centre x stays 640.
| t (s) | centre y | zoom | ease |
|---|---|---|---|
| 0–1.87 | 360 | 1.00 | hold |
| 1.87→2.40 | 360 → 215 | 1.00 → 2.15 | in-out cubic |
| 2.40–2.60 | 215 | 2.15 | hold (measured) |
| 2.60→3.00 | 215 → 372 | 2.15 | in-out cubic |
| 3.00–3.30 | 372 | 2.15 | hold |
| 3.30→3.73 | 372 → 466 | 2.15 | in-out cubic |
| 3.73–4.53 | 466 | 2.15 | hold |
| 4.53→4.73 | 466 → 545 | 2.15 | in-out cubic |
| 4.73–5.13 | 545 | 2.15 | hold |
| 5.13→5.53 | 545 → 685 | 2.15 | in-out cubic |
| 5.53–6.03 | 685 | 2.15 | hold |
Motion blur: temporal supersampling over a 1-frame shutter, N = clamp(ceil(screen px moved / 5), 1, 24) full warps averaged in float32; when more than 120 px move per frame add a vertical 1-D box blur of length min(0.3 × px, 70).

## 5. Timeline (beats)
### B1 · Headline type-on — 0–0.45 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.05–0.45 | E1 letters | alpha 0 → 1, random order, 0.1 s each, jitter up to ±10 units while fading | | linear |
### B2 · Placeholders — 0.1–0.5 s
| 0.1–0.47 | E2 placeholders | alpha 0.1 → 1.0 | | linear |
### B3 · Mosaic flicker — 0.87–1.67 s
| 0.87 + 0.067 × k, 0.4 s each | E2 line k | blocks (20 × 12) flip from placeholder to mosaic in random order, brightness +35% on flip | | linear |
Hold the mosaic list 1.5–1.87 s.
### B4 · Zoom and first decode — 1.87–2.6 s
| 1.87–2.40 | camera | zoom in to the headline-and-list boundary | | see camera |
| 2.33–2.60 | E2 line 1 | mosaic → sharp (level 20×12 → 12×8 → 7×5 → 3×2 → sharp) | | linear |
### B5 · Scroll and decode — 2.6–5.5 s
Each line decodes over 0.27 s (8 frames), starting at 2.33, 3.0, 3.53, 4.27, 4.93, 5.47 s (lines 1–6). Camera steps follow the table in section 4. The headline leaves the top of the frame during 2.6–3.0 s.
### B6 · Hold — 5.5–6.03 s
Lines 4 (clipped), 5 and 6 sharp, still.

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. Render the world once per frame at 3.2 px per unit (3072 × 2304 px, origin at world (160, 20)), warp to 1920×1080 with `cv2.warpAffine`; for zoom below 1.6 warp a half-size copy (INTER_AREA) to avoid aliasing.
- Variable font axes in Pillow are set as [weight, width].
- Pixelation: INTER_AREA down to the block grid, INTER_NEAREST back up. Pre-render the five levels (with glow) per line once.
- Mosaic flicker: a random value per block; blocks with value below progress show the mosaic, the rest the placeholder.
- Everything is additive on the background colour; clip at 1.0. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`. Stream frames to ffmpeg, one worker.

## 7. Still frame
The last frame: black screen, the lower three lines of the list in sharp glowing text (line 4 cut by the top edge), nothing else.

## 8. Never
- Reference words, a different number of list lines, or text outside the frame width.
- A glow that makes text unreadable against the background.
- Skipping the mosaic stage.
- Changing the camera path or the decode order.
