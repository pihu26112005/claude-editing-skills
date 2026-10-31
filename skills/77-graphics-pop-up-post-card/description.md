# description.md: Pop-up Post Card

A generic social post card on a black stage. The card rises into view, its author name and handle wipe in, the post text appears word by word, the reply and share counts fade in, the like count ticks up and the like icon pops with a ring burst. Then everything leaves in reverse and the card drops away.
**The graphic in one line:** a white post card rises on black, text lands word by word, a like counter ticks and bursts, then the card exits.
**Format:** 16:9 · 1920×1080 · 30 fps · 7.27 s (reference 1280×720; all units below are in 1280×720 px, multiply by 1.5 for output)

## 1. Canvas
- Flat background P10, default #000000 (measured). No texture, grid, vignette or grain.
- Card: rectangle 735×250 units at (272,214), centre (640,339), fill P9 default #FFFFFF, corner radius 13 units (measured about 12 to 14). No visible shadow on black.
- Safe area: all card content sits at least 24 units inside the card edge.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Display name | yes | none, must ask | text, ≤ 20 chars, 1 line | E3, B2 |
| P2 | Handle | yes | none, must ask | text, ≤ 20 chars, 1 line, starts with @ | E3, B2 |
| P3 | Post text | yes | none, must ask | text, ≤ 60 chars, 1 line, 4 to 12 words (auto-fit to 70%) | E4, B3 |
| P4 | Avatar image | yes | none, must ask | image, any aspect, cover-fit to a circle, ≥ 128 px short side | E2, B1 |
| P5 | Reply count | yes | none, must ask | integer 0 to 999 | E5, B4 |
| P6 | Share count | yes | none, must ask | integer 0 to 999 | E5, B4 |
| P7 | Like count (final) | yes | none, must ask | integer 10 to 999 | E6, B5 |
| P8 | Accent colour | no | #ED2162 (measured) | hex | like icon, ring burst |
| P9 | Card colour | no | #FFFFFF (measured) | hex, light | card |
| P10 | Stage colour | no | #000000 (measured) | hex | background |
| P11 | Text colour | no | #0A0A0A (measured) | hex, dark | E3 name, E4 |
| P12 | Meta colour | no | #6A7076 (measured) | hex, mid grey | E3 handle, E5 counts |

### 2.1 How to infer parameters from user material
- Name, handle, text: from the user's brand, account or script. Shortest strong sentence for the text.
- Avatar: user logo or photo; a still from a user video. Centre or subject focal point.
- Counts: use the numbers the user states. Never invent them.
- P8 may come from a brand colour; keep strong contrast on the card.

## 3. Elements
Card-local coordinates (origin top-left of the card, units). Font: Inter (opsz 14 to 32, closest free match to the measured grotesque).
### E1 · Card
As section 1.
### E2 · Avatar
Circle, centre (79,81), radius 32. P4 cover-fit crop. No border.
### E3 · Name, handle and menu
Name at x=127, vertical centre y=68, Inter wght 600, size 17, colour P11. Handle at x = name end + 35, same y, wght 400 size 15, colour P12. Menu icon: three dots, radius 1.8, spacing 6, centre (647,59), colour P11. Neutral glyph only, no platform logo.
### E4 · Post text
Words laid out on one line from x=127, vertical centre y=104, Inter wght 400 size 19 (auto-fit: shrink until the line is ≤ 540 wide, floor 70% = 13.3), colour P11, word gap = one space.
### E5 · Action row
Vertical centre y=217. Icons (stroke 1.6, colour #797A7D measured): reply bubble at x=135, share loop arrows at x=228, like heart at x=323 (17 wide), mail envelope at x=416. Counts, Inter 13.5 wght 400, colour P12: reply count at x=162, share count at x=254, like count at x=351.
### E6 · Like pop
Heart icon turns from outline to solid P8, with a ring and eight dots bursting around it (see B5).

## 4. Camera
None. The frame is static; only the card moves (rise and exit).

## 5. Timeline (beats)
### B1 · Card rise — 0.03–0.85 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.03–0.85 | E1 (all content) | y offset | +320 → 0 units (measured: top at 480 px at 0.1 s, settled at 0.8 s) | out cubic |
| 0.03–0.28 | E1 | alpha | 0 → 1 | linear |
### B2 · Name and handle wipe — 0.4–1.1 s
| 0.4–0.9 | name | right-to-left mask wipe, 14 unit soft edge | hidden → shown | out cubic |
| 0.6–1.1 | handle | same wipe | hidden → shown | out cubic |
### B3 · Post text words — 1.05–2.4 s
| 1.05 + g·i | word i | alpha 0 → 1, y +9 → 0 units, 0.28 s each | | out cubic |
g = min(0.13, 1.05/(words-1)) s (measured about 0.13 s per word, 2.1 s for the last of 9).
### B4 · Reply and share counts — 1.0–1.5 s
| 1.0–1.25 | reply count | alpha 0 → 1, y +8 → 0 | | out cubic |
| 1.25–1.5 | share count | same | | out cubic |
### B5 · Like counter and pop — 0.7–3.2 s
| 0.7–0.9 | like count | first value fades in, y +6 → 0 | | out cubic |
| 0.85, 1.25, 1.65, 2.05, 2.45, 2.72 | like count | steps through P7 × (0.2, 0.32, 0.36, 0.4, 0.67, 1.0), rounded, last = P7; old value slides up 8 units and fades while the new one rises in, 0.14 s | | out cubic |
| 2.45–2.57 | heart | scale 1 → 0.6 | | linear |
| 2.57–2.71 | heart | scale 0.6 → 1.28 | | out cubic |
| 2.71–2.91 | heart | scale 1.28 → 1 | | out cubic |
| 2.55 | heart | outline #797A7D → solid P8 (instant) | | |
| 2.55–3.05 | ring | radius 7 → 27, stroke 3.5 → 0.6, alpha 1 → 0 | | out cubic |
| 2.55–3.05 | 8 dots | radius 10 → 32, size 3.2 → 0.5, alpha 1 → 0, alternate P8 and a 45% lighter tint | | out cubic |
### B6 · Hold — 3.2–4.4 s
Everything still.
### B7 · Counts out — 4.4–5.85 s
| 4.4–4.6 | like count | alpha 1 → 0 | | linear |
| 5.6–5.8 | reply and share counts | alpha 1 → 0 (design) | | linear |
### B8 · Words out — 4.85–5.95 s
Words leave last to first: word at index i from the end starts at 4.85 + min(0.12, 0.9/(words-1))·k, alpha 1 → 0 and y 0 → +9 over 0.2 s (design, matched to reference).
### B9 · Name wipe out and card exit — 5.95–7.2 s
| 5.95–6.35 | name, handle | wipe reverses (left edge hides first) | | out cubic |
| 6.35–7.2 | E1 | y offset 0 → +320 | | in cubic |
| 6.8–7.2 | E1 | alpha 1 → 0 | | linear |
| 7.2–7.27 | | black | | |

## 6. Build notes
- Python, Pillow, NumPy, ffmpeg. Draw the card at 3 px per unit (2× the 1.5 output scale), downscale by 2 with Lanczos, alpha-composite at (408, 321 + offset·1.5) on the 1920×1080 stage. Place the vertical offset to half-pixel steps by shifting the 3× layer by 0 or 1 px.
- Text colour fades are done by blending the text colour toward the card colour (card is flat).
- Icons are drawn with Pillow primitives (arcs, polygons, parametric heart). No platform logos.
- Auto-fit text: compute line width at 19, shrink by 0.25 until ≤ 540, floor 13.3.
- Stream frames into ffmpeg: `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`. Frames with zero alpha are the stage colour.

## 7. Still frame
Card settled (t = 4.0 s): avatar, name and handle, full post text, reply and share counts, solid accent like icon with the final like count.

## 8. Never
- Real platform logos, names, verified badges or look-alike marks.
- Text overflowing or clipped by the card.
- Distorted avatar.
- Invented counts or text.
- Moving the camera or adding elements.
