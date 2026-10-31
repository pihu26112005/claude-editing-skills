# description.md: Twin-Tone Peak Slide

A black-stage data explainer for one rise-and-fall story. A glass orb sits on a gradient dome and slides in from the left. A glowing area chart climbs in a zigzag to a single peak. A thin white marker drops from the peak. The chart and the orb then slide past each other in opposite directions, the area right of the marker fills in a second colour as it falls away, and a two-word label rises into place above the peak.
**The graphic in one line:** a glass orb and dome, a one-colour area chart climbing to a peak, a marker line, a second-colour fall, and a two-word label.
**Format:** 9:16 · 1080×1920 · 30 fps · 4.0 s (reference 720×1280; all values below are in 720×1280 px, multiply by 1.5 for output)

## 1. Canvas
- Background #000000, flat. No grid, grain or vignette.
- Everything is light on black: layers are added together, with the chart punching through the icon (chart alpha = chart brightness^0.8).
- Safe area: label stays inside x 46–530; the orb may leave the frame on the right.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Label | yes | none, must ask | text, 1 or 2 words, ≤ 16 chars, 1 line (auto-fit down to 70%) | E6, B6 |
| P2 | Rise colour | no | #12D63A (measured) | hex, bright | E3 |
| P3 | Fall colour | no | #FF0A14 (measured) | hex, bright | E5, E6 |
| P4 | Icon colour | no | #8173EF (measured) | hex | E1, E2 |
| P5 | Marker colour | no | #FFFFFF (measured) | hex | E4 |
| P6 | Background colour | no | #000000 (measured) | hex, dark | canvas |
| P7 | Label colour | no | same as P3 | hex | E6 |

### 2.1 How to infer parameters from user material
- Label: the name of the peak or turning point in the user's story (a date, an event, a record).
- Colours: P2 and P3 should read as "up" and "down" (for example brand colours or a good and a bad signal). Keep P2 and P3 in different hue families.
- P4 may come from a brand colour; the orb rim uses a lighter tint of it.

## 3. Elements
### E1 · Dome
Half circle, radius 345, centre (hc, 854), only the upper half drawn (top y 509). Colour blends from P4 on the left to a neutral grey (#B4AAB0) on the right (smoothstep over x/r from -0.1 to 0.9). Brightness = (1 - (y-509)/330)^1.6, so it fades to black by y 840.
### E2 · Glass orb
Circle radius 150, centre (hc, 347). Interior black. Rim from radius 0.55r to r: alpha 0.15 rising to 1 (power 1.4). Rim colour runs from grey (#96968E) at the top to P4 lightened 50 percent at the bottom (smoothstep on y/r from -0.8 to 0.5). A 1.5 px bright edge. A soft white glint (gaussian 26×13, 45 percent) at (hc-55, 287).
### E3 · Rise area
Polyline relative to the peak (dx, dy, y down): (-1000,780), (-760,709), (-561,565), (-431,536), (-328,378), (-213,419), (-40,78), (0,0). Peak P0 at screen y 414. Area under the line, colour P2, intensity (1 - d/300)^1.3 where d is the vertical distance below the line. 2.5 px line in P2 lightened 25 percent on top.
### E4 · Marker line
Vertical line at the peak x, 3.5 px wide, colour P5, from y 412 to the bottom of the frame.
### E5 · Fall area
Polyline relative to the peak: (0,0), (188,306), (332,349), (380,534), (524,606), (700,700). Same fill rule as E3 with colour P3 and fade length 190. Same line style.
### E6 · Label
Barlow Medium, size 84, colour P7. Words are left aligned from x 46 on baseline y 310, 22 px between words. Word 2 starts at the end of word 1 plus 22. Auto-fit: total width ≤ 480, shrink to 70 percent. A single word uses only the first slot.

## 4. Camera
No camera. The two layers move on their own, in screen space.
| t (s) | Icon centre hc | Chart peak x (pk) | ease |
|---|---|---|---|
| 0 | -10 | 760 | (measured) |
| 0.13 | 91 | 760 | ease-out |
| 0.27 | 166 | 760 | ease-out |
| 0.40 | 187 | 760 | ease-out |
| 0.53 | 193 | 760 | slow drift |
| 0.93 | 236 | 760 | linear |
| 1.10 | 233 | 760 | hold |
| 1.20 | 233 | 676 | ease-in |
| 1.33 | 233 | 514 | |
| 1.47 | 298 | 334 | |
| 1.60 | 448 | 232 | |
| 1.73 | 606 | 197 | ease-out |
| 1.87 | 690 | 196 | |
| 2.33 | 705 | 196 | hold to end |
Linear interpolation between the measured frame samples (every 4 frames), smoothed with a gaussian of 1 frame. Motion blur: when either layer moves more than 14 px per frame, average 5 sub-frames over a 0.5-frame shutter.

## 5. Timeline (beats)
### B1 · Icon slide-in — 0–0.93 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.53 | E1, E2 | x | -10 → 193 | ease-out (measured) |
| 0.53–0.93 | E1, E2 | x | 193 → 236 | linear (measured) |

### B2 · Rise draws — 0.2–1.13 s
A hard vertical edge reveals E3 left to right.
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.20 | E3 | reveal front x | -20 | start |
| 0.27 | E3 | reveal front x | 103 | (measured) |
| 0.40 | E3 | reveal front x | 431 | |
| 0.53 | E3 | reveal front x | 612 | |
| 0.67 | E3 | reveal front x | 680 | |
| 0.80 | E3 | reveal front x | 724 | |
| 1.07 | E3 | reveal front x | 740 | |
| 1.13 | E3 | reveal front x | 800 (fully shown) | |

### B3 · Marker drops — 1.07–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.07–1.20 | E4 | bottom end y | 412 → 1280 | smoothstep (design) |

### B4 · Slide past — 1.1–1.87 s
Chart moves left, icon moves right (table in section 4). Chart peak ends at x 196, orb centre at x 705 (only its left part stays in frame).

### B5 · Fall fills — 1.35–2.15 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.35–2.15 | E5 | reveal bottom y | 405 → 1045 | linear (design) |

The edge is a 1 px soft horizontal wipe moving down.

### B6 · Label rises — 1.85–3.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.85 | E6 word 1 | alpha, y offset | 0, +124 → | alpha = 1 - e^(-9 (t-1.85)); offset = 46·e^(-4.5 (t-2.07)) (measured) |
| 2.03 | E6 word 2 | alpha, y offset | 0, +120 → | alpha = 1 - e^(-7 (t-2.03)); offset = 116·e^(-3.6 (t-2.0)) (measured) |
| 3.0 | E6 | settled | 0 offset, alpha 1 | |

### B7 · Hold — 3.0–4.0 s
Nothing moves.

## 6. Build notes
- Canvas 720×1280, output upscaled to 1080×1920 with Lanczos (or render at 1.5 scale). Pre-render the chart layers at 2× supersampling on a 1700 px wide strip (x -900…800 around the peak) and downsample with area averaging. Pre-render the icon once at 2× on an 800 px wide sprite centred on x 400.
- Per frame: translate sprites with `cv2.warpAffine` (bilinear), mask E3 with the reveal front, E5 with the wipe, E4 with the line growth. Composite: `out = icon·(1-a) + chart`, `a = max(chart)^0.8`.
- Text: draw each word at 2× with PIL, anchor `ls`, downsample with Lanczos, alpha-blend in colour P7.
- Stream raw RGB frames into `ffmpeg … libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`. One worker, never all frames in memory.

## 7. Still frame
Settled frame (t ≥ 3.0 s): the label top left at y 252–311, the rise area as a straight slope up to the marker at x 196, the fall area to its right, and the orb and dome cut by the right edge.

## 8. Never
- Never change the beat order or the opposite-direction slide.
- Never let the label overlap the orb (width ≤ 480).
- Never add axes, numbers, gridlines, faces or people.
- Never use the same hue for the rise and fall areas.
