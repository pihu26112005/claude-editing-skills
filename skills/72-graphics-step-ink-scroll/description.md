# description.md: Step Ink Scroll

Three stacked headlines in distressed serif capitals sit on crumpled grey-green paper. They are wider than the frame, so only their left parts show. The whole stack then slides left in five hard, held steps, like a ticker, until the endings of the lines come into view, and holds. The middle line is sharp and heavily ink-worn. The top and bottom lines are soft (out of focus) and lighter.
**The graphic in one line:** three oversized headlines on crumpled paper, stepped sideways in five snaps to reveal their endings.
**Format:** 16:9 · 1920×1080 · 30 fps · 3.93 s (118 frames; reference 1280×720, base units below are 1280×720 px, multiply by 1.5)

## 1. Canvas
- Paper base #AFAFA1 (measured 175,175,161 at centre), lit with soft crumple relief: low-frequency lumps plus ridged-noise creases, shading clamp 0.86–1.12 (design, matched by eye).
- Vignette: corners darken to about 67 percent (measured 115 of 172), radial, starts at r=0.2 of the corner distance, slightly darker on the left (3 percent).
- Fine grain ±1.2 percent. Paper is fixed to the screen and never moves.
- Chromatic fringe on ink: red channel shifted -1 px, blue +1 px (measured faint red edges).

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Headline 1 (top, soft) | yes | none, must ask | text, 16–26 chars, 1 line, capitals (auto-fit to 70%) | E1, all beats |
| P2 | Headline 2 (middle, sharp) | yes | none, must ask | text, 16–26 chars, at least 2 words, 1 line, capitals (auto-fit to 70%) | E2, all beats |
| P3 | Headline 3 (bottom, soft) | yes | none, must ask | text, 16–26 chars, 1 line, capitals (auto-fit to 70%) | E3, all beats |
| P4 | Ink colour | no | #000000 (measured) | hex, dark | E1–E3 |
| P5 | Paper colour | no | #AFAFA1 (measured) | hex, mid-light | canvas |
| P6 | Ink wear | no | on | on / off | E1–E3 distress |

### 2.1 How to infer parameters from user material
- Headlines: three related titles from the user's script or list, similar in length, 16–26 characters each. The middle one is the hero.
- Colours: P4 may come from a brand colour (keep it very dark); P5 from a paper or background tone in the user's material.

## 3. Elements
Base units 1280×720. Rows are vertical cap-centres.
### E1 · Headline 1 (top)
Cinzel wght 760, size 105 (cap height about 73), tracking +0.035 em, uppercase, left edge x=45, cap centre y=62. Soft: gaussian blur sigma 3 units, opacity 92 percent, light wear (55 percent of E2). Auto-fit: if width exceeds 1750, shrink to a floor of 70 percent.
### E2 · Headline 2 (middle)
Same font and size, cap centre y=358. Sharp, full ink, heavy wear: rough eroded edges (edge noise up to 5.5 px), small holes, ink splatter dots around the letters (density falls off with distance, radius 0.6–2.8 px), and a dotted ink ring around the second word (140 specks, 75 percent kept, ellipse rx = word half-width + 0.1 em, ry 0.62 em, open at the top-left).
### E3 · Headline 3 (bottom)
As E1, cap centre y=645.
All lines share the same left edge and move together. Wear is baked in once per line and does not change between frames.

## 4. Camera
No zoom. The stack of lines is offset horizontally by a step function. Each step is a hard cut with no easing and no motion blur.
| frame | t (s) | stack offset x (base units) |
|---|---|---|
| 0–7 | 0–0.23 | 0 |
| 8–14 | 0.27 | -148 |
| 15–22 | 0.50 | -296 |
| 23–29 | 0.77 | -444 |
| 30–37 | 1.00 | -590 |
| 38–117 | 1.27–3.93 | -650 (hold) |

## 5. Timeline (beats)
### B1 · Opening hold — 0–0.27 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 | E1–E3 | offset x | 0 (measured) | none |
### B2 · Four equal snaps — 0.27–1.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.267 | E1–E3 | offset x | 0 → -148 (measured) | hard cut |
| 0.500 | E1–E3 | offset x | -148 → -296 (measured) | hard cut |
| 0.767 | E1–E3 | offset x | -296 → -444 (measured) | hard cut |
| 1.000 | E1–E3 | offset x | -444 → -590 (measured) | hard cut |
### B3 · Short last snap and hold — 1.27–3.93 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.267 | E1–E3 | offset x | -590 → -650 (measured) | hard cut |
| 1.27–3.93 | all | | still (measured, frames identical) | |

## 6. Build notes
- Python, NumPy, SciPy, OpenCV, Pillow, ffmpeg. Output 1920×1080. Only six distinct images exist: render each once, then write the frames from the schedule above into ffmpeg (`libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`).
- Each line is drawn as its own layer at 2× output size, distressed there, then downscaled with INTER_AREA. Letters are placed one by one with tracking.
- Wear: distance transform of the glyph mask. Erode inside by (0.5 + 0.5 × noise) × width, add a thin bleed outside, subtract blobs where a smoothed noise exceeds 1.25 sigma, then add splatter dots chosen by exp(-distance/18 units).
- Ink compositing: out = paper × (1-a) + ink × a × (paper shade), per channel with the ±1 px fringe.
- Paper: sum of gaussian-smoothed noise at sigma 90, 35 and 8 px, plus ridged noise creases (1-|n|)^2, shaded by the height gradient, times the vignette.

## 7. Still frame
The final frame: the endings of the three headlines in the left half of the frame (middle one ends further right), paper empty on the right, top and bottom soft, middle sharp and worn.

## 8. Never
- Easing, blur or interpolation between the steps.
- Lines that fit inside the frame at the start (they must overflow on the right).
- Different offsets for different lines.
- Text over 26 characters at full size, clipped letters, or lines overlapping each other.
- Reference words as defaults.
