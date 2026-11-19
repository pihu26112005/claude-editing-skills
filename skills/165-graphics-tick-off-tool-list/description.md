# description.md: Tick-Off Tool List

A light, app-style checklist page. A two-tone title sits above a column-label line and five rows. Each row has an icon tile, a bold name and short description lines. The rows appear one after another, then a checkbox at the right of each row ticks in turn. It communicates a set of steps or tools being completed one by one.
**The graphic in one line:** five-row checklist on a warm light page; row checkboxes tick one by one.
**Format:** 9:16 · 1080×1920 · 30 fps · 6.7 s (reference: the list occupied the top 720×640 of a 720×1280 frame as three columns; this skill re-lays it for the full portrait frame, all values below are px at 1080×1920)

## 1. Canvas
- Page: radial tone, centre #ECEAE3, corners #E1DED5 (measured reference about #EBE9E2 to #E1DED5), vignette ramp from r=0.25 of the corner distance, power 1.4. Faint grain, sigma 0.8 levels.
- Safe margin 70 px left and right. Content block spans y 250 to 1750.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Title prefix | yes | none, must ask | text, ≤ 10 chars, 1 line | E1, B1 |
| P2 | Title | yes | none, must ask | text, ≤ 24 chars, 1 line (auto-fit to 70%) | E1, B1 |
| P3 | Row names | yes | none, must ask | 5 texts, ≤ 14 chars each | E4, B2 |
| P4 | Role lines | yes | none, must ask | 5 texts, ≤ 28 chars each | E4, B2 |
| P5 | Reason lines | yes | none, must ask | 5 texts, ≤ 30 chars each | E4, B2 |
| P6 | Row icons | no | neutral drawn glyph, else first letter | 5 items: emoji, one letter or image (cover-fit, any aspect) | E3 |
| P7 | Column labels | no | ITEM / DONE | 2 texts, ≤ 8 chars | E2 |
| P8 | Tick colour | no | #222222 (measured) | hex, dark | E5, B3 |
| P9 | Icon tile colours | no | a soft two-stop gradient per row | 5 hex pairs | E3 |
| P10 | Page tone | no | #ECEAE3 | hex, light | canvas |
| P11 | Tick times | no | 1.55, 2.47, 3.27, 3.97, 4.77 s (measured) | 5 seconds values, increasing, ≤ 6.2 | E5, B3 |

### 2.1 How to infer parameters from user material
- Title: the step or stage name in the user's script ("Step 2" plus the task).
- Rows: the five items in the user's list; name is the item, role is what it does, reason is why it is needed.
- Icons: user emoji, letters or images; otherwise draw a neutral glyph (never a brand logo).
- Tick colour: may come from a brand colour; keep strong contrast with white.

## 3. Elements
### E1 · Title
Centred at x=540, baseline y=330. Prefix in Inter 450 size 78, colour #7D7B76; title in Inter 800 size 78, tracking -2, colour #181818; gap 20. Auto-fit so the pair stays within 940 px wide.
### E2 · Column labels
Baseline y=468. Left label at x=70, right label right-aligned at x=1010. Inter 600 size 26, tracking 3, colour #96948D, uppercase.
### E3 · Icon tile
160 px rounded square (radius 34) at x=70, vertically centred in the row. Vertical gradient of two colours, soft shadow (blur 10, offset y 8, alpha 0.27 of warm black), white glyph about 95% of 160/100 units. Image or emoji icons are cover-fit inside the rounded tile.
### E4 · Row text
Row height 250, rows start y=500, pitch 250. Hairline separator at row bottom, x 70 to 1010, #D6D3CA, 1 px. Text x=265, max width 627. Name Inter 800 size 68, tracking -1.5, #181818, baseline row centre -20. Role Inter 500 size 42, #161616, baseline +36. Reason Inter 450 size 36, #8A8780, baseline +86. Each auto-fits down to 70%.
### E5 · Checkbox
88 px rounded square (radius 22), left edge x=922, centred vertically in the row. Empty: fill #F0EEE8, outline 3 px #CECBC2. Ticked: fill P8, white tick (points (-20,2), (-6,16), (21,-14) from the box centre, 8 px round stroke).

## 4. Camera
Whole frame scales about the centre from 1.00 to 1.02 over 0 to 6.7 s, linear (design), with a 8 px upward drift over the same time. The reference page itself was static, so keep the drift very small. Bicubic resample.

## 5. Timeline (beats)
### B1 · Title in — 0.00–0.45 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.00–0.45 | E1, E2 | opacity | 0 → 1 | ease-out cubic (design) |
### B2 · Rows rise — 0.15–1.15 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.15+0.09·i, 0.55 long | row i (E3, E4, E5 empty) | opacity | 0 → 1 | ease-out cubic (design) |
| same | row i | y offset | +26 px → 0 | ease-out cubic (design) |
### B3 · Ticks — P11 times (measured), then hold to 6.7 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| T to T+0.14 | E5 fill | opacity | 0 → 1 | ease-out cubic (design) |
| T to T+0.28 | E5 box | scale | 0.8 → 1.0 with a 10% overshoot bump | sine bump (design) |
| T+0.08 to T+0.33 | E5 tick | path drawn | 0 → 100% | ease-out cubic (design) |
Ticks in the reference landed at 1.55, 2.47, 3.27, 3.97 and 4.77 s; the final tick is held about 1.9 s.

## 6. Build notes
- Draw static layers at 2x and downscale with Lanczos: title and labels as one layer, each row as its own 1080×250 RGBA layer (tile shadow via Gaussian blur on a separate layer).
- Fonts: Inter variable (opsz 14, wght as listed); fall back to Manrope or DM Sans. Per-character drawing for tracking.
- Redraw each checkbox per frame at 4x on a 118 px canvas, downscale, composite at the row's current offset and opacity.
- Compose the flat frame, then apply the camera with one cv2.warpAffine. Stream raw frames into ffmpeg (`libx264 -crf 16 -preset slow -pix_fmt yuv420p`).
- Cover-fit image icons into the tile with a rounded-rect mask.

## 7. Still frame
All five boxes ticked, rows fully settled, camera at the end of its drift.

## 8. Never
Never use real brand logos, a different row count, text overlapping the checkbox or tile, ticks out of order, or the reference's words and icons.
