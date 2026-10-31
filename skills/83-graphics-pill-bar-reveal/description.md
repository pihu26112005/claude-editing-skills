# description.md: Pill Bar Reveal

A round icon bubble rises from below on a soft gradient, stretches sideways into a pill-shaped search bar while its magnifier tilts upright, the user's text fades in word by word, the bar swells slightly, then shrinks and fades away to the empty gradient.
**The graphic in one line:** icon bubble rises, widens into a pill search bar, words fade in, bar swells and vanishes.
**Format:** 16:9 · 1920×1080 · 30 fps · 7.77 s (reference 1280×720; units below are 1280×720 px, multiply by 1.5)

## 1. Canvas
- Radial gradient centred on the bottom-left corner. Colour = lerp(P5, P6, t), t = interp(d, [0, .49, .871, 1], [0, .38, .74, 1]) where d = distance from the bottom-left corner divided by the frame diagonal. Reference measured: P5 #D6B0ED, P6 #F1E5FA.
- Faint noise ±0.5 levels to avoid banding. No vignette, no shadow under the bar.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Main text | yes | none, must ask | text, ≤ 24 chars, 1 line (auto-fit down to 70%) | E3, B4 |
| P2 | Icon colour | no | #CDA8EA (measured) | hex | E2 |
| P3 | Pill colour | no | #F4EBF9 (measured) | hex, light | E1 |
| P4 | Text colour | no | #322C35 (measured) | hex, dark | E3 |
| P5 | Gradient inner colour | no | #D6B0ED (measured) | hex | canvas |
| P6 | Gradient outer colour | no | #F1E5FA (measured) | hex | canvas |

### 2.1 How to infer parameters from user material
- Main text: the search phrase, topic or question from the user's script; 2 to 4 words suit the word-by-word fade.
- Colours: P2 may come from a brand colour; P5 and P6 a dark and light tint of it. Keep P4 strongly contrasting with P3. Never copy a real search brand's palette.

## 3. Elements
Centre C=(640,360) in reference units.
### E1 · Pill
Height 97 (144 px out), fully rounded, colour P3, centred on C. Starts as a circle of diameter 96. Final width W = max(522, textWidth + 218) units (text width 304 for a 14-char reference text); text width auto-fits to ≤ 467 units (700 px).
### E2 · Magnifier icon
Ring outer radius 23, stroke 4.2, centre 9.5 above the icon centre; handle from the ring edge to 39 below ring centre, round cap, same stroke. Colour P2. Icon centre x = pill left + 48, y = pill centre. Tilt about the icon centre.
### E3 · Text
Inter Medium (wght 500, opsz 14), 64 px out, colour P4, baseline 18.5 units (27.75 px) below pill centre, starting 89 units (133.5 px) right of pill left. Right padding 129 units. Clipped by the pill. Each word fades in separately.

## 4. Camera
None. Static.

## 5. Timeline (beats)
### B1 · Icon rises — 0.3–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.3–0.5 | E1/E2 | opacity | 0 → 1 | linear (design) |
| 0.3–1.2 | E1/E2 | y offset | +380 units → 0 | (1-u)^2 ease-out (measured) |
### B2 · Stretch into pill — 1.0–2.35 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.0–2.35 | E1 | width progress p | 0 → 1 (knots 1.1 .036, 1.3 .117, 1.5 .35, 1.6 .59, 1.7 .756, 1.8 .86, 2.0 .953, 2.2 .993) | S-curve, smoothed (measured) |
| 1.0–2.35 | E2 | tilt | -25° (handle down-left) → +25° (down-right), linear in p | (measured) |
### B3 · Words fade in — 2.0–3.3 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.0 / 2.25 / 2.55 | E3 words 1 / 2 / 3 | opacity | 0 → 1 over 0.25 / 0.30 / 0.50 s (further words start 2.75, 2.9, 0.4 s) | smoothstep (measured) |
### B4 · Hold — 3.3–4.3 s
Everything still.
### B5 · Swell — 4.3–4.95 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.3–4.95 | group | scale about C | 1 → 1.109 (4.5 1.025, 4.6 1.07, 4.8 1.10) | ease-out (measured) |
### B6 · Collapse — 4.95–5.7 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.95–5.7 | group | scale | 1.109 → 0.1 (5.2 1.03, 5.3 .92, 5.4 .65, 5.5 .38, 5.6 .19) | ease-in (measured) |
| 5.2–5.7 | group | opacity | 1 → 0 | (measured) |
### B7 · Empty hold — 5.7–7.77 s
Bare gradient.

## 6. Build notes
Pre-compute the radial gradient once. Draw the group (pill mask, clipped text, icon) per frame into a 2× RGBA layer of 1700×300 px (units out), downscale with Lanczos by the group scale, alpha-composite at the frame centre (rise offset applied as a y shift). Draw the ring as a 120-point polyline and the handle as a round-capped line, rotated about the icon centre. Smooth timing tables on a 1 ms grid with a gaussian of 0.03–0.04 s. Stream frames into ffmpeg `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The full pill at t = 3.8 s: icon at left, full text, on the gradient.

## 8. Never
No real search-engine or brand logo, name or colours. Text never leaves the pill. No shadow, no extra elements. The pill never changes height.
