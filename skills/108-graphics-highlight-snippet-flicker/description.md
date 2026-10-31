# description.md: Highlight Snippet Flicker

A rapid flip-through of nine text snippets that all share one highlighted keyword. Each snippet is a cropped piece of an article page on crumpled paper. The keyword sits in a marker highlight at the same screen spot in every snippet, while the words around it, the page furniture and the blur change every few frames. The loop runs 2.3 times and stops mid-flip. It shows how widely one term appears.
**The graphic in one line:** one marker-highlighted keyword stays put while nine different article snippets flick past at about 10 steps per second, with streaked edges and blurred lower text.
**Format:** 9:16 · 1080×1920 · 30 fps · 2.3 s (69 frames; reference 540×960, multiply by 2)

## 1. Canvas
- Paper #ECECE8 (measured light grey-white), static crumpled texture: low-frequency shading (±1.2 percent), two crease scales (darkening up to 1.1 percent), fine grain ±1.4 levels. Nothing on the paper moves.
- A faint grey panel (alpha 6 percent) from y 0.52 to 0.66 H and a hairline at y 0.495 H (design, matched by eye), both vertically blurred, on every snippet.
- No camera. No vignette.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Keyword | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit to 70%) | E1 highlight in every snippet |
| P2 | Snippet 1 | yes | none, must ask | 3 texts: lead ≤ 28, tail ≤ 24, aside ≤ 24 chars | E2, S1 |
| P3 | Snippet 2 | yes | none, must ask | as P2 | E2, S2 |
| P4 | Snippet 3 | yes | none, must ask | as P2 | E2, S3 |
| P5 | Snippet 4 | yes | none, must ask | as P2 | E2, S4 |
| P6 | Snippet 5 | yes | none, must ask | as P2 | E2, S5 |
| P7 | Snippet 6 | yes | none, must ask | as P2 | E2, S6 |
| P8 | Snippet 7 | yes | none, must ask | as P2 | E2, S7 |
| P9 | Snippet 8 | yes | none, must ask | as P2 | E2, S8 |
| P10 | Snippet 9 | yes | none, must ask | as P2 | E2, S9 |
| P11 | Page title | no | the keyword | text, ≤ 18 chars | E4 |
| P12 | Byline name | no | Staff writer | text, ≤ 20 chars | E4 |
| P13 | Sub-line | no | none | text, ≤ 40 chars | E3, E4 |
| P14 | Tags | no | News, Features, Nature | up to 3 words, ≤ 12 chars each | E3 |
| P15 | Highlight colour | no | #D9E23C (measured, yellow-green) | hex | E1 |
| P16 | Paper colour | no | #ECECE8 (measured) | hex, light | canvas |
| P17 | Ink colour | no | #18181A (measured) | hex, dark | all text |

### 2.1 How to infer parameters from user material
- Keyword: the term the user wants repeated (product, topic, name).
- Snippets: sentences from the user's script or notes that contain the keyword; cut each at the keyword into lead (text before) and tail (text after), and take a few following words as the aside. Write nothing the user did not supply.
- Highlight colour: may come from a brand colour; keep dark ink readable on it.

## 3. Elements
Sizes in 1080×1920 px.
### E1 · Keyword highlight
Marker box behind the keyword, colour P15, alpha 0.92, padding 0.16 em each side, from 0.80 em above to 0.62 em below the line centre. Keyword in ink, DM Sans (weight 500 to 700). Its centre x is set per snippet (table in section 5). Lead text is right-aligned to the box minus 0.26 em, tail left-aligned from the box plus 0.26 em. Lead and tail run off the canvas edges (cropped). Keyword size 84 px (design, measured about 80), shrinks until its width ≤ 0.62 W, floor 70%.
### E2 · Snippet line
The line holding E1, centre y 0.36 to 0.38 H, in the layout of the snippet (section 5). Fonts: DM Sans 600 (headline layouts), DM Sans 500 (single line), Gelasio 400 at 0.62 size (article layout).
### E3 · Page furniture
Tag row (DM Sans 25 px, grey #6E6E70) at y 0.293 H, x 40. Sub-line DM Sans 27 px grey at y 0.455 H. "Sign in" text, "Subscribe" pill (#2846BE, white label) and "Member-only" note in the top-right layout. Fixed labels: Sign in, Subscribe, Member-only, Follow, min read.
### E4 · Article header (article layout only)
Page title in Barlow Condensed Bold 120 px at y 0.012 H, vertical blur 16 px, alpha 0.85. Sub-line below. Round avatar 104 px with the byline initials, byline name (DM Sans 600 32 px), "3 min read", a Follow label in a pink-red accent, and a small reaction count chip.
### E5 · Body text
Five or six lines of Gelasio (30 px, or 0.52 × key size in the article layout), grey ink alpha 0.5 to 0.8, built by chaining all snippets with the keyword, starting at a different offset per snippet, first line cropped at the left edge. Vertical box blur grows per line: start 5 to 6 px, plus 3 px per line.
### E6 · Edge smear
Applied to the finished snippet. Horizontal box blur (110 px then 55 px) mixed in by weight w(x): left (0.15 − x/W)/0.15, right (x/W − 0.84)/0.16, clamped, power 0.8, ×0.95. The centre 0.15 to 0.84 W stays sharp.

## 4. Camera
None. Fixed frame.

## 5. Timeline (beats)
Each snippet holds still (no motion inside a hold). A loop is 30 frames (1.0 s) and shows the nine snippets in order.
### B1 · Flip loop — 0–2.3 s
Snippet start frames inside each 30-frame loop: S1 0, S2 4, S3 8, S4 11, S5 14, S6 18, S7 21, S8 24, S9 27 (holds 4,4,3,3,4,3,3,3,3 frames; measured). Frame f shows the snippet whose start is the largest ≤ f mod 30. The video ends on frame 68 (S3 of the third loop).
| Snippet | Layout | Keyword centre x |
|---|---|---|
| S1 | headline: tags, bold line with keyword, aside as second line, sub-line, body | 0.50 W |
| S2 | article: blurred title, byline, serif line with keyword, body | 0.46 W |
| S3 | single line, quote chip bottom with small keyword highlight, body | 0.50 W |
| S4 | bold analysis: two tags, bold line, aside second line, sub-line, body | 0.50 W |
| S5 | headline (as S1) | 0.50 W |
| S6 | subscribe layout: Sign in, Subscribe pill, keyword near the right, small keyword chip with aside, body | 0.64 W |
| S7 | single line (as S3) | 0.50 W |
| S8 | article (as S2) | 0.46 W |
| S9 | bold analysis (as S4) | 0.48 W |
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| each hold start | whole snippet | hard cut, no fade, no slide | previous → next | none (measured) |
| 0–2.3 | paper | static | | |

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. Render the paper once. Render each of the nine snippets once (text through Pillow at 1080×1920, per-element vertical blur with `cv2.blur` on premultiplied RGBA, then E6), composite over the paper, cache the bytes and write each cached frame repeatedly into ffmpeg stdin.
- Variable fonts: DM Sans axes (opsz = size/2 clamped 9 to 40, wght), Gelasio (wght).
- Keyword autofit: shrink in 2 px steps until width ≤ 0.62 W.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
Snippet S1: tag row, the highlighted keyword mid-line with cropped words either side, a second line, a small grey sub-line and faint blurred body text below, on crumpled paper.

## 8. Never
- Fading, sliding or easing between snippets (they cut).
- The keyword moving off its highlight or changing spelling.
- Text with real brand, league or publication names the user did not give.
- Sharp text at the extreme left and right edges (they stay smeared).
- A different number of snippets.
