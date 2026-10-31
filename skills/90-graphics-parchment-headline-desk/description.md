# description.md: Parchment Headline Desk

A story-intro card on aged grid paper. A date tag, a two-line headline and a detail paragraph appear by typing, a cut-out portrait rises from the bottom-right corner, a rule draws and a masthead line types beside it, then a marker highlight sweeps over the headline and over one phrase of the detail text.
**The graphic in one line:** dated tag, typed headline and detail, rising portrait, rule plus masthead, marker highlights, on vignetted grid parchment.
**Format:** 16:9 · 1920×1080 · 30 fps · 13 s (reference 1280×720; multiply reference pixels by 1.5)

## 1. Canvas
- Paper centre colour P10 (measured #C2A878, 194,168,124). Mottling: four noise octaves (scales 240, 90, 30, 8 px; weights 0.5, 0.3, 0.18, 0.08), amplitude ±4.5 percent, plus soft darker stains (5 percent).
- Grid: pitch 72 px (measured 48 at 1280), 2 px lines at x offset 2, y offset 40, darkening the paper by 17 percent, blur 0.9 px. P11 turns it off.
- Vignette multiplies everything (portrait included): m = 1 - 0.55 × clamp((r - 0.15) / 0.85)^1.5, r = distance from centre over corner distance (corners 45 percent, measured).
- Flicker: brightness × (1 + 0.018 sin(5.1 t) + 0.012 sin(11.7 t + 1)). Grain: gaussian, sigma 2.2 levels, new every frame.
- Left margin 90 px.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Date tag text | yes | none, must ask | text, ≤ 14 chars, 1 line | E1, B1 |
| P2 | Headline | yes | none, must ask | text, ≤ 70 chars, 2 lines (auto-fit to 70%) | E2, B2 |
| P3 | Detail text | yes | none, must ask | text, ≤ 170 chars, 2 lines (auto-fit to 70%) | E3, B3 |
| P4 | Masthead line | yes | none, must ask | text, ≤ 22 chars, 1 line | E5, B5 |
| P5 | Portrait image | yes | none, must ask | image, transparent cut-out preferred, ≥ 700 px tall, scaled to box height | E4, B4 |
| P6 | Detail highlight phrase | no | auto (words from the start of line 1 after its first 6 words, about 40 chars) | text, must lie inside one line of P3 | E7, B7 |
| P7 | Tag colour | no | #D01010 (measured) | hex | E1 |
| P8 | Highlight colour | no | #F6C500 (measured) | hex | E6, E7 |
| P9 | Text colour | no | #141210 (measured) | hex, dark | E2, E3, E5, rule |
| P10 | Paper colour | no | #C2A878 (measured) | hex, mid-light | canvas |
| P11 | Grid | no | on | on / off | canvas |

### 2.1 How to infer parameters from user material
- Date: the date in the user's story; else today's date in "Mon 00, 0000" form.
- Headline: the strongest one-sentence claim; detail: one or two supporting sentences; masthead: the user's own brand, show or channel name.
- Portrait: user photo of the subject, ideally already cut out; for an opaque photo, feather the left and top edges over 80 px so it blends into the paper.
- Colours: P7 and P8 may come from brand colours; keep contrast with the paper and text.

## 3. Elements
### E1 · Date tag
Rubik Regular 38 px (design), white, letter-spacing 3.5 px. Rect x 90, y 175, height 94, width = text width + 52, colour P7, edge blur 0.7 px. Text left padding 26.
### E2 · Headline
Rubik Bold (wght 700), colour P9, 60 px, line pitch 81 px, left x 90, line centres y 336 and 417. Wrap width 1340. Shrinks to 70 percent if it needs more than 2 lines.
### E3 · Detail text
Rubik Regular 29 px, P9, line pitch 40, line centres y 499 and 539. Wrap width 1230. First line indented 40 px (measured), second line at x 90.
### E4 · Portrait
Box 676×784 at the bottom-right corner (x 1244–1920, y 296–1080). Image scaled to height 784 (never stretched), right-aligned, cut at the box edges. Converted to black and white (contrast 1.1). Vignette applies.
### E5 · Rule and masthead
Rule: 4 px (measured 3 at 1280 scaled), colour P9, y 701–705, x 109 to 659. Masthead: blackletter (UnifrakturCook Bold), 58 px, left x 685, centre y 705, colour P9; shrinks down to 40 px so its width stays ≤ 540 px.
### E6 · Headline highlight
Per line: rough marker bar, colour P8, from text start - 10 to text end + 10, height 1.08 × font size, centred on the line. Top and bottom edges wobble (smooth noise, ±3.2 px), edges blurred 1.6 px, 93 percent opacity, drawn under the text. Colour is toned by the paper brightness underneath.
### E7 · Detail highlight
Same bar style, x from the phrase start - 4 to end + 4, height 1.25 × detail font size, behind line 1 text.

## 4. Camera
None. The canvas is fixed; only the vignette flicker and grain change.

## 5. Timeline (beats)
### B1 · Tag — 0.25–0.6 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.25–0.6 | E1 | alpha 0→1, y +14→0 | | out cubic (measured start 0.3) |
### B2 · Headline typing — 0.4–2.55 s
| 0.40 + k × (1.95/(n-1)) | E2 | word k fades in over 0.22 s, n = word count | | linear (measured: last word half-faded while typing) |
### B3 · Detail typing — 2.0–4.4 s
| 2.0–4.4 | E3 | letters appear evenly, each fades over 0.08 s | | linear |
### B4 · Portrait rise — 2.1–3.3 s
| 2.1–3.3 | E4 | y offset 794 → 0 (rises from below the canvas) | | out cubic |
### B5 · Rule and masthead — 3.6–5.3 s
| 3.6–4.6 | E5 rule | length 0 → 100% left to right | | in-out cubic |
| 4.1–5.3 | E5 masthead | letters fade in left to right, 0.18 s each | | linear |
### B6 · Headline highlight — 5.55–6.65 s
| 5.55–6.10 | E6 line 1 | wipe left to right | | in-out cubic |
| 6.05–6.60 | E6 line 2 | wipe left to right | | in-out cubic |
### B7 · Detail highlight — 7.45–8.3 s
| 7.45–8.3 | E7 | wipe left to right | | in-out cubic |
### B8 · Hold — 8.3–13 s
Only flicker and grain move.

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg, one process, frames piped to ffmpeg. Background (paper, mottling, grid) built once; vignette array built once.
- Text: render each word (headline) or letter (detail, masthead) at 2x into a small RGBA sprite, downscale with Lanczos, place at x = prefix width (includes kerning). Sprite alpha = fade ramp.
- Highlight: per-column top and bottom edge from smooth noise, blurred mask, reveal by multiplying a left-to-right step with 8 px soft edge.
- Order per frame: base, highlights, tag, rule, text, portrait, then vignette, flicker, grain. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Demo files are re-encoded at crf 22 and the GIF is denoised (grain bloats it).

## 7. Still frame
Settled frame at 9 s: tag, headline with highlight, detail with highlighted phrase, rule with masthead, portrait at the right.

## 8. Never
- A distorted portrait.
- Text running under the portrait or over the rule.
- Reference words, pictures or a real publication name as defaults.
- Highlight over the wrong words, or in front of the text.
