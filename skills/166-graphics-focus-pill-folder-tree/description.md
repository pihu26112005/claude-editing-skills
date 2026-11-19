# description.md: Focus Pill Folder Tree

A light-page project tree. A white root card (folder icon, name, sub-label) hangs a thin tree line with indented child folders. The tree appears, one folder takes a dark outlined pill while the others dim to grey, a new sub-folder appears as "untitled folder" and is renamed by typing, a file with a thumbnail lands inside it, then a second sub-folder with a sub-label takes the pill. The camera drifts down to follow the focus and ends pulled back on the whole tree.
**The graphic in one line:** a folder tree where the outlined focus pill hops from folder to new sub-folder to file to second sub-folder while the camera follows.
**Format:** 9:16 · 1080×1920 · 30 fps · 8.8 s (reference 720×1280, 30 fps; world units below are 720×1280 px, multiply by 1.5 for output). The reference graphic starts after a 0.9 s unrelated lead-in, which is not part of this graphic.

## 1. Canvas
- Page: radial gradient, centre #EFEEE7 to corners #E6E2DA (measured), radius 1.25 of half-diagonal, power 1.5, plus ±0.9 level dither against banding. Fixed to the screen, not the camera.
- No grid. Safe margin: all text at least 24 units from the left and right edge at every camera position.
- Tree line colour #C8C7C0, width 2 units. Dim folder #D4D9D8, dim text #7A7874, sub-label #77757A (measured).

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Root name | yes | none, must ask | text, ≤ 16 chars, 1 line | E1 |
| P2 | Root sub-label | yes | none, must ask | text, ≤ 24 chars | E1 |
| P3 | Folder names 1 to 4 | yes | none, must ask | 4 texts, ≤ 14 chars each | E3, B1, B2 |
| P4 | Focus folder name | yes | none, must ask | text, ≤ 14 chars | E4, B1 |
| P5 | Focus folder sub-label | yes | none, must ask | text, ≤ 24 chars | E4 |
| P6 | Last folder name | yes | none, must ask | text, ≤ 14 chars | E3, B2 |
| P7 | New sub-folder name | yes | none, must ask | text, ≤ 20 chars | E5, B3 |
| P8 | File name | yes | none, must ask | text, ≤ 32 chars, wraps to 2 lines | E6, B4 |
| P9 | File thumbnail | yes | none, must ask | image, any aspect, cover-fit to 88:52, ≥ 300 px wide | E6, B4 |
| P10 | Second sub-folder name | yes | none, must ask | text, ≤ 14 chars | E7, B5 |
| P11 | Second sub-folder sub-label | yes | none, must ask | text, ≤ 26 chars | E7, B5 |
| P12 | Placeholder name | no | untitled folder | text, ≤ 20 chars | E5, B3 |
| P13 | Folder colour | no | #6BB0EF front, #529BE7 back (measured) | hex pair, light front and darker back | all bright folders |
| P14 | Text colour | no | #131313 (measured) | hex, dark | titles |
| P15 | Page tone | no | #EFEEE7 centre, #E6E2DA edge (measured) | hex pair, light | canvas |
| P16 | Pill colour | no | #333333 (measured) | hex, dark | pills |

### 2.1 How to infer parameters from user material
- Root name: the project or brand. Folder names: the real top-level folders of that project; the focus folder is the one the story is about. Last folder: a closing stage (exports, archive).
- New sub-folder, file, second sub-folder: the next level of the focus folder, in story order.
- Thumbnail: a user image or a still of the file's content. Folder colour: a brand colour (keep a lighter front and a darker back, about 12 percent apart).

## 3. Elements
World units, camera at zoom 1. Font Inter variable (opsz 28), weight 800 for titles with tracking -0.035 em, weight 400 for sub-labels with no tracking.
### E1 · Root card
Rounded rect x 42 to (151 + widest text + 26, capped 690), y 130 to 222, radius 22, fill #FAFAFA, soft shadow (blur 13, offset 9, #55503F, 15 percent). Folder icon 64 wide at x 67, vertically centred. Title 34 at x 151, centre y card top + 32. Sub-label 16.5, #77757A, centre y card top + 64.
### E2 · Tree lines
Main vertical at x 103 from y 238 to the last row, ticks to x 147 at every L1 row. Level 2 vertical at x 181 from Focus row +30 to the new row, tick to x 224. Level 3 vertical at x 257 from the new row +30 to the lowest row, ticks to x 300 (file) and x 306 (second sub-folder).
### E3 · Plain rows
Row centres y 330, 430, 530, 630 (folders 1 to 4) and 1110 (last). Folder icon 41 wide at x 163, label x 216, size 20.5. Bright: front/back folder colour, text P14. Dim: folder #D4D9D8 (flat), text #7A7874.
### E4 · Focus row
Centre y 730. Grows from 41 to 52 wide icon, title 20.5 to 23 at x 215 + 15, sub-label 15.5 fades in at +13 below the title (title moves up 12). Pill around icon and text: left x 153, y ±30, width = icon + longest text + 22, radius 15, border 2.5 in P16, fill #302E28 at 7 percent. Stays bright after the pill leaves.
### E5 · New sub-folder
Centre y 818, icon 52 wide at x 240, text x 305, size 26. Pill pad 11, radius 16, height 64.
### E6 · File
Centre y 914. Thumbnail 88×52 at x 316, radius 5, cover-fit. Name size 22 at x 416, wrapped at 260 units, line pitch 25, centred on the row. Pill left x 306, height 72.
### E7 · Second sub-folder
Centre y 1004. Icon 46 wide at x 316, title 22 at x 376 (centre y −11), sub-label 14.5 (+13). Pill left x 306, height 62.

## 4. Camera
Screen = 1.5 × (zoom × (world − centre) + (360, 640)). Between keys: 50 percent smoothstep, 50 percent linear (steady drift).
| t (s) | centre x | centre y | zoom | ease |
|---|---|---|---|---|
| 0 | 330 | 520 | 1.15 | drift |
| 2.8 | 350 | 590 | 1.08 | drift |
| 5.0 | 362 | 690 | 1.04 | drift |
| 6.6 | 364 | 700 | 1.04 | drift |
| 8.0 | 366 | 640 | 1.00 | smooth |
| 8.8 | 366 | 640 | 1.00 | hold |
No motion blur (moves are slow). The reference pans about 49 px up and zooms about 5 percent in; this graphic spreads the rows further apart and ends pulled back so the tree fills the 9:16 frame (design).

## 5. Timeline (beats)
### B1 · Build and focus — 0–1.3 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.4 | E1 | opacity, y +14 → 0 | 0 → 1 | ease-out (design) |
| 0–0.5 | E2 | main line length | 0 → full | ease-out (design) |
| 0.08–0.45 + 0.05 per row | E3, E4 | opacity, tick length | 0 → 1 | ease-out (design) |
| 0.05–0.45 | E4 | icon, title size, sub-label | small → big | ease-out (measured: pill in about 0.4 s) |
| 0.25–0.65 | E4 | pill opacity | 0 → 1 | ease-out |
### B2 · Dim the others — 0.7–1.8 s
| 0.7–1.3 + 0.05 per row | E3 | colour bright → dim | 0 → 1 | smoothstep (measured: others dim within 1 s) |
Then hold to 3.0 s.
### B3 · New sub-folder and rename — 3.0–3.9 s
| 3.0–3.3 | E2, E5 | level 2 line and tick grow, folder fades in as pale placeholder with P12 in grey | 0 → 1 | ease-out |
| 3.0–3.3 | E4 | pill opacity | 1 → 0 | ease-out |
| 3.35–3.65 | E5 | pill opacity | 0 → 1 | ease-out |
| 3.5–3.9 | E5 | placeholder replaced by P7 typed at 38 chars/s, folder pale → bright (3.45–3.6) | | linear (measured about 37 chars/s) |
### B4 · File lands — 4.7–6.4 s
| 4.7–5.0 | E2 | level 3 line grows | 0 → 1 | ease-out |
| 4.8–5.1 | E5 | pill out | 1 → 0 | ease-out |
| 4.8–5.1 | E6 | file opacity (grey, thumbnail 45 percent) | 0 → 1 | ease-out |
| 5.1–5.4 | E6 | text grey → dark, thumbnail 45 → 100 percent | | smoothstep |
| 5.15–5.45 | E6 | pill in | 0 → 1 | ease-out |
### B5 · Second sub-folder — 6.1–8.8 s
| 6.1–6.4 | E6 | pill out | 1 → 0 | ease-out |
| 6.1–6.4 | E7 | line extends, tick and folder fade in | 0 → 1 | ease-out |
| 6.3–6.6 | E7 | pill in | 0 → 1 | ease-out |
| 6.6–8.0 | camera | pull back to zoom 1.0 | | smooth |
| 8.0–8.8 | all | hold | | |

## 6. Build notes
- Python with Pillow and NumPy. Draw each frame at 2160×3840 (world × 1.5 × 2) straight from the camera transform, then Lanczos down to 1080×1920. Pre-render the page gradient once (with dither). Stream raw frames to `ffmpeg` (`libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`), one worker.
- Text: Inter variable font, set axes (opsz 28, wght). Draw per character with kerning from `getlength(prefix)` plus tracking. Compute widths at a large size and divide so pills fit the final text.
- Folder icon: back plate with a tab (rounded, darker colour), lighter front panel starting 24 percent down; draw at 4× and downscale.
- Pill: rounded rect with 7 percent dark fill and a 2.5 unit border, composited from a small RGBA patch.
- Thumbnail: cover-fit the user image to 88:52 around its focal point, round corners.
- File name: greedy word wrap at 260 units; if a single word is wider, shrink to 70 percent.

## 7. Still frame
The settled frame at 8.7 s: root card top left, four dim folders, bright focus folder with sub-label, indented bright sub-folder, file with thumbnail, second sub-folder in the dark pill, dim last folder. The tree spans about y 130 to 1130 of 1280 units.

## 8. Never
- Never let text leave its card or pill, or clip the root card at the frame edge.
- Never more or fewer folders; the structure is fixed.
- Never show the placeholder and the typed name together.
- Never stretch the thumbnail.
- Never leave the pill on two rows at once after a hand-off completes.
