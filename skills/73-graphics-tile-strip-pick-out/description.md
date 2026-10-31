# description.md: Tile Strip Pick-Out

A dark, softly lit stage. A long strip of 15 numbered rounded-square tiles streams in on a tilt, flattens into an overlapping row, a hand cursor glides along it, hovers tiles and clicks one. The chosen tile lifts out, the rest of the strip fans away to both sides, and the chosen tile grows to the centre and holds.
**The graphic in one line:** a numbered tile strip, a hand cursor picks one tile, the strip fans away and the picked tile settles large in the centre.
**Format:** 16:9 · 1920×1080 · 30 fps · 6.0 s (reference 1280×720; fractions below apply to any size, px values are at 1920×1080 unless marked)

## 1. Canvas
- Background: near-black navy base #050B11 (measured 5,11,17) plus one soft elliptical glow. Start glow: centre (0.59 W, 0.14 H), sigma (0.26 W, 0.42 H), peak colour #1D578D (29,87,141). End glow: centre (0.79 W, 0.58 H), sigma (0.30 W, 0.47 H), peak colour #1E3E5C. The glow drifts start to end between 1.0 s and 5.2 s (smoothstep). Colour at a pixel = base + gaussian × (peak − base).
- No grid, grain or text on the canvas. No safe-margin rule: tiles run off both sides on purpose.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Label word | yes | none, must ask | text, ≤ 10 chars, 1 line (auto-fit down to 70%) | E2 on every tile |
| P2 | Chosen number | yes | none, must ask | integer 1 to 15 | E3 pick, B4–B7 |
| P3 | Emblem | no | ring | ring / peak / bars | E2 mark on every tile |
| P4 | Tile palette | no | #625B9F #676499 #838DB1 #9293CA #8367C9 #9A71CD #B39FCD #CCBEDB #5599E1 #007FAB #60ACBA #5E93A7 #588697 #56667A #2C5575 (measured, tile 1 to 15) | 15 hex colours | E1 |
| P5 | Background tone | no | base #050B11, glow #1D578D to #1E3E5C (measured) | 3 hex colours | canvas |
| P6 | Label colour | no | #FFFFFF (measured) | hex, light | E2 text |
| P7 | Cursor | no | on | on / off | E4 |

### 2.1 How to infer parameters from user material
- Label word: the noun the user is browsing (clip, recipe, trail, slide). One word, as plain as possible.
- Chosen number: the item the user says to highlight; if they name it by title, ask for its number.
- Palette: may be built from a brand colour by spreading its hue and lightness across 15 steps; keep every tile dark or mid enough for white text (contrast ≥ 3:1 where the label shows).
- Emblem: pick by topic (ring generic, peak outdoors, bars data).

## 3. Elements
Sizes are fractions of H. A tile at rest is 0.3375 H tall (365 px).
### E1 · Tile
Rounded square, corner radius 0.16 × side, flat fill from P4 (tile number i uses colour i). A soft shadow (black, 42% alpha, blur 0.02 × side, offset 0.014 × side down) sits behind each tile and darkens the tile below it where tiles overlap. Stacking: tile 1 in front, tile 15 at the back, always, including the chosen tile.
### E2 · Tile face
Two centred lines, "P1" over "No.<i>" (i = tile number). Font Gelasio Bold (wght 700; fallbacks Droid Serif Bold, Noto Serif Bold), colour P6, line centres at 0.40 and 0.62 of tile height. Size = min(0.19 × side, the size that makes the wider line 0.71 × side). Soft drop shadow (dark, 75% alpha, offset 0.006 × side, blur 0.003 × side). Under the text sits the emblem, filled with the tile colour made deeper: HSV saturation + 0.39, value × 0.77 (measured: tile #B39FCD gives mark #5B3D9D). Emblem spans 0.12 to 0.86 of the tile height and 0.1 to 0.9 of its width. Ring: stroke 0.12 × side, outer diameter 0.53 × side. Peak: two stacked triangular summits, base on the lower edge. Bars: three rounded bars, heights 0.41, 0.62, 0.51 × side.
### E3 · Chosen tile
Tile number P2. Same as the others until the hover phase, then it lifts (B5) and ends as the one tile left on screen.
### E4 · Hand cursor
White pointing hand with 4.5 unit black outline, index finger up, three short knuckle lines. Height 0.15 H. Hotspot is the tip of the index finger. Rotated 28° clockwise while it arrives, 0° from 2.4 s. Pressed scale 0.86 at the click.

## 4. Camera
No camera. The strip itself moves; the view is fixed.

## 5. Timeline (beats)
Row geometry: tile i centre x = head − (i−1) × pitch while the strip is in motion; row centre y 0.5 H. Natural head x at rest = 0.855 W, pitch 0.0547 W (70 px at 1280). All curves below are monotone cubic (PCHIP) through the keys, so there are no stop-start kinks.
### B1 · Stream in — 0–1.7 s
| t (s) | Element | Property | Keys | Ease |
|---|---|---|---|---|
| 0–1.7 | head x | centre of tile 1, fraction of W | 0 −0.12, 0.2 0.065, 0.4 0.315, 0.6 0.51, 0.8 0.66, 1.0 0.70, 1.2 0.805, 1.4 0.836, 1.7 0.855 | pchip (measured) |
| 0–2.1 | pitch | W fraction | 0 .15, 0.6 .135, 1.0 .11, 1.4 .077, 1.8 .058, 2.1 .0547 | pchip (measured) |
| 0–1.7 | tile roll | degrees (negative is counter-clockwise) | 0 −42, 0.6 −42, 1.0 −22, 1.4 −4, 1.7 0 | pchip (measured) |
| 0–1.8 | tile width squeeze q | × side | 0 1.0, 0.6 .95, 1.0 .85, 1.4 .70, 1.8 .64 | pchip (design) |
| 0–1.6 | row y | H fraction | 0 .45, 0.6 .45, 1.0 .47, 1.6 .50 | pchip |
Tiles are sheared in depth: right edge taller than the left by k = 0.045 × (1 − q) / 0.36 (each side ±k). Tiles enter from the left edge one after another because each is placed behind the head by the current pitch.
### B2 · Cursor arrives — 1.0–2.4 s
| t (s) | Element | Property | Keys (x W, y H) | Ease |
|---|---|---|---|---|
| 1.0–1.2 | E4 | alpha | 0 → 1 | smoothstep |
| 1.0–2.3 | E4 | position | 1.0 (.30,1.04), 1.25 (.37,.80), 1.5 (.46,.79), 1.75 (.55,.82), 2.0 (.88,.68), 2.3 (.95,.54) | pchip (measured) |
| 1.0–2.4 | E4 | rotation | 28° → 0° | pchip |
### B3 · Glide and hover — 2.4–3.6 s
Cursor glides left along the row: 2.55 (.90,.50), 2.8 (target x + .2, .49), 3.0 (target x, .49), where target x = 0.855 − (P2 − 1) × 0.0547. While the cursor is over the strip (envelope 2.45–2.8 in, 3.4–3.7 out), each tile within 0.8 × pitch of the cursor lifts by up to 0.022 H with a gaussian falloff. The chosen tile lifts to 0.478 H at 3.1 s and sits at 0.482 H at 3.35 s.
### B4 · Click — 3.5–3.7 s
Cursor pressed scale 0.86 at 3.6 s (gaussian, width 0.08 s), then back to 1.
### B5 · Lift — 3.6–4.15 s
Chosen tile centre y keys: 3.6 .45, 4.0 .33, 4.15 .33. Cursor follows: 3.7 (target x, .49), 4.2 (target x + .01, .37), 4.4 (+.02, .35); alpha 1 → 0 over 4.2–4.45.
### B6 · Fan away — 4.15–5.5 s
Tile i centre x = selX + (P2 − i) × pitch2; pitch2 (W fraction) keys 4.15 .0547, 4.5 .16, 4.85 .45, 5.15 1.0, 5.5 1.8 (pchip). selX moves from the natural x to 0.5 between 4.15 and 4.9. Tile size scales 1 → 1.37 (to 0.4625 H) and q → 1 (smoothstep 4.2–4.9). Chosen tile y moves 0.33 → 0.46 between 4.15 and 4.9 s. All other tiles leave the screen.
### B7 · Hold — 5.5–6.0 s
Chosen tile centred at (0.5 W, 0.46 H), 0.4625 H square. Nothing moves except the glow settling.

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, SciPy (PchipInterpolator), ffmpeg. Pipe raw frames into ffmpeg; never hold all frames in RAM.
- Tile sprites: draw each at 2048 px, downscale to 1024, pad 128 px for the shadow halo, premultiply alpha. Pre-render all 15 once.
- Frame: tile layer at 2× (3840×2160) as premultiplied RGBA uint8; for each tile back to front, `cv2.perspectiveTransform` the sprite onto its quad (width ×q, shear k, rotate by roll), `warpPerspective` into the quad's bounding box only, alpha-over into the layer. Downscale with INTER_AREA, composite over the background, then draw the cursor (4× supersampled sprite, `warpAffine` rotating about the fingertip).
- Motion blur: average N sub-frames across a 0.4-frame shutter; N = clamp(ceil(0.4 × px moved per frame / 5), 1, 24). px moved = largest tile-centre move plus roll × radius, and the cursor move.
- Background: outer product of two 1-D gaussians per frame.
- Frames after 5.6 s are identical; render once. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The settled frame: the chosen tile centred, 0.4625 H square, label and emblem on it, nothing else, glow drifted to the right of centre.

## 8. Never
- A different tile count, or a chosen number outside 1 to 15.
- Text overflowing a tile, or the label on a tile that cannot be read (poor contrast).
- Tile order changes: tile 1 is always rightmost and in front at rest.
- Reference content (its words, emblem or numbers) as defaults.
- Cursor still visible after the lift.
