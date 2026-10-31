# description.md: Cursor Morph Widget

A single black-and-white UI element on a warm grey canvas that is never cut. A cursor clicks and drags it, and it becomes a button, loader, check, island, music player, scrub bar, volume slider, toggle, tab bar, chart card, command palette and toast, then returns to the button. Every state is the same shape changing width, height, radius and fill on springs; the content swaps with a short blur. The last frame equals the first.
**The graphic in one line:** one shape morphs through 12 UI states driven by a cursor, ending where it began so it loops.
**Format:** 1:1 · 1080×1080 · 60 fps · 14 s (reference 720×720, 60 fps, 14.08 s; all units below are reference units U at 720, multiply by 1.5 for output)

## 1. Canvas
- Warm grey #EFEFEB centre falling to about #E9E9E5 at the corners (measured 234/255 at the corner), radial, power 1.4, plus static noise of ±0.6 level to stop banding.
- No grid, no vignette beyond the radial falloff. The shape is always centred at (360,360) U. The camera is baked in: each state's size is its screen size, so every state fills the frame about the same way.
- Shadow under the shape: offset +11 U down, Gaussian sigma about 13 U, alpha 0.23 under a black shape and 0.10 under a white one.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Button label | yes | none, must ask | text, ≤ 12 chars, 1 line | S1, S12 |
| P2 | Track title | yes | none, must ask | text, ≤ 18 chars | S5 |
| P3 | Track subtitle | yes | none, must ask | text, ≤ 22 chars | S5 |
| P4 | Tab labels | yes | none, must ask | 3 texts, ≤ 7 chars each | S9, S10 |
| P5 | Metric caption | yes | none, must ask | text, ≤ 14 chars | S10 |
| P6 | Metric values | yes | none, must ask | 2 whole numbers (month-like first, smaller second) | S10 |
| P7 | Search word | yes | none, must ask | text, ≤ 8 chars, typed one letter at a time | S11 |
| P8 | Result labels | yes | none, must ask | 2 texts, ≤ 22 chars | S11 |
| P9 | Toast text | yes | none, must ask | text, ≤ 24 chars | S12 |
| P10 | Accent colour | no | warm artwork gradient, black chart line (measured) | hex | S5 artwork, S10 line, dot |
| P11 | Artwork gradient | no | 3 colours derived from P10 | 3 hex | S4, S5 |
| P12 | Canvas tone | no | #EFEFEB (measured) | hex, light | canvas |
| P13 | State list | no | all 12, reference order | ordered list of S1..S12, ≥ 8, S1 first | whole timeline |

State list note: the shipped renderer uses the absolute times in section 5. Dropping a state means deleting its rows and keeping the next state's entry time; the neighbours then spring across the gap.

### 2.1 How to infer parameters from user material
- Pick one coherent product (a music app, a coffee timer, a fitness tracker) and fill every label from its vocabulary.
- Metric values: a big first number and a smaller second one.
- Result labels: two phrases that both contain or relate to the search word.
- Accent: a brand colour from a logo or image; the UI stays black and white.

## 3. Elements
### E1 · The shape
Rounded rectangle centred at (360,360). Properties: width, height, radius, fill colour. Each property follows a closed-form damped spring (sum of one spring step per target change, section 6). Default spring: omega 28 to 30 rad/s, zeta 0.72 (tiny overshoot). Ink = #050505. Corner radius is half the height for pills.
### E2 · Content groups
Each state's content is drawn in a layer clipped to the shape. Enter: alpha 0→1 over 0.12–0.22 s with Gaussian blur 7 U→0. Exit: alpha 1→0 over 0.1–0.12 s with blur 0→7 U. Exit and enter overlap slightly so text never overlaps text.
### E3 · Cursor
macOS-style arrow, black fill, white outline 1.9 U, tip at the target. Height 20 U. Click: scale to 0.84 and back over 0.2 s. Moves on springs (omega 12–30, zeta 0.9). During drags it is locked to the dragged handle. Motion-blurred like everything else.
### E4 · Type
Geist (weights 400/500/600/700), IBM Plex Mono for the track times. Text centred on its row by cap height (baseline = centre + 0.355 × size).
### E5 · Colours
Ink #050505 on white states; white text on ink; secondary grey on black #8C8C8C, on white #8D8D89; row highlight #EEEEEB; toggle off grey #C4C4BF; track on black #333333.

## 4. Camera
None. Sizes are already framed (section 5). Frame the longest state (the 630-wide palette) inside 0.88 of the width.

## 5. Timeline (beats)
Shape targets (w × h, radius, fill). Each row starts a spring at time t.
| t (s) | State | Shape target | Spring (omega, zeta) |
|---|---|---|---|
| 0 | S1 Button | 322 × 102 (text width + 182, min 250), r 51, ink | rest |
| 0.50 | S2 Loader | 112 × 112, r 56 | 30, 0.72 |
| 1.15 | S3 Check | 114 × 114, r 57 | 30, 0.72 |
| 1.32 | S4 Island | 430 × 112, r 56 | 28, 0.75 |
| 1.70 | S5 Player | 494 × 315, r 38 (reference overshoots to 526 × 332) | 26, 0.62 |
| 3.74 | S6 Volume | 540 × 92, r 46 | 28, 0.70 |
| 4.62 | S6 stretch | 585 × 92 (drag past max) | 34, 0.80 |
| 5.12 | S6 spring back | 540 × 92 | 26, 0.60 |
| 5.30 | S7 Toggle on | 248 × 134, r 67, ink | 28, 0.70 |
| 5.70 / 6.00 / 6.27 | S7 flips | fill #C4C4BF / ink / #C4C4BF | 40, 0.90 |
| 6.37 | S8 Tabs | 584 × 84, r 42, white | 28, 0.74 |
| 7.33 | S9 Chart card | 550 × 422, r 34, white | 26, 0.68 |
| 9.60 | S10 Search bar | 433 × 84, r 42, white | 30, 0.78 |
| 10.10 | S10 Palette | 540 × 368, r 32 | 26, 0.72 |
| 10.66 | S10 Filtered | 630 × 290, r 30 | 28, 0.78 |
| 11.72 | S11 Toast | text width + 134 × 92, r 46, ink | 26, 0.72 |
| 12.72 | S12 Button | as S1 | 26, 0.72 |

(The reference's chart and palette are S9 and S10 here; the 12 states are Button, Loader, Check, Island, Player, Volume, Toggle, Tabs, Chart, Search bar, Palette, Toast, with Button repeating.)

### B1 · Button, loader, check — 0–1.4 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.32 | cursor | path | (650,607) → (452,395) | spring 24, 0.9 |
| 0.45 | cursor | click | scale 0.84 | |
| 0.48 | label | exit | alpha 1→0, blur | |
| 0.55–1.18 | ring | spinner | dim ring r 21, stroke 5 (alpha 0.22) plus a white 105° arc rotating 520 °/s | linear |
| 1.17–1.42 | check | glyph | grey #8C8C8C polyline 5 U, pops from 1.25 to 1.0 | out |
Cursor then drifts to (460,410) at 0.75 and (576,561) at 1.25.
### B2 · Island and player — 1.38–3.78 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.38–1.8 | island | artwork 58 U r 16 at x 200; 5 EQ bars at x 470, gap 9.5, width 4, height 8 + 16·|sin(9t + 1.3i)| | | |
| 1.85–3.78 | player | artwork 112 U r 24 at (198,288); title (275,272) 21 U/600; subtitle (275,302) 16.5 U/400 grey; progress bar x 142–578, y 390, 5 U high; times y 419 (mono 12.5); controls y 467 at x 267, 360, 453 | | |
| 2.0–2.35 | cursor | to the play/pause button (368,468) | | spring |
| 2.35 / 2.78 | glyph | pause → play → pause morph (two quads, vertices interpolated over 0.22 s) | | smooth |
| 3.0–3.2 | scrub knob | 15 U white dot grows on the progress end | | smooth |
| 3.2–3.65 | cursor and progress | drag, progress 0.27 → 0.85, elapsed time follows (total 2:59) | | in-out cubic |
### B3 · Volume slider — 3.9–5.38 s
Speaker glyph at (135,360), track x 195–588 (393 U, 12 U high, #333), white fill pill from x 195. Cursor on the fill end.
| 4.4–4.95 | volume | fill 0.09 → 1.0, cursor follows, then 30 U beyond the end | | in-out cubic |
| 4.62–5.12 | shape | stretches to 585 wide while dragged past max, springs back | | spring |
### B4 · Toggle — 5.28–6.37 s
A white knob (108 U circle) inside the 248 × 134 shape. On at 5.30 (knob right, x 417), off at 5.70 (x 303, shape grey), on at 6.00, off at 6.27. Flips on 120 BPM beats, knob left and right edges ride springs (omega 26 and 38) so the knob stretches during the move. Cursor rests at (392,398).
### B5 · Tab indicator and chart — 6.37–9.6 s
The knob becomes the tab indicator (same entity, colour white → ink). Edges ride separate springs so the leading edge stretches ahead (leading omega 40–44, trailing 22–26).
| t (s) | Property | Target |
|---|---|---|
| 6.37 | indicator | first tab: centre 170.5, 189 × 68 |
| 6.74 | indicator | second tab: centre 360 (cursor click at 6.72) |
| 7.08 | indicator | third tab: centre 549.5 (click 7.07) |
| 7.33 | indicator and labels | card layout: pill centre (477.5, 202.5), 111 × 39; labels at x 243, 360, 477, y 202.5, size 22 → 18 |
| 9.14 | indicator | second tab in the card: centre 360 (click 9.12) |
Labels are grey #737370 on white; the same labels redrawn in white and clipped to the indicator.
Chart content (enters 7.40): number at (120,271) 49 U/700 with a count-up roll from 80 % to 100 % over 7.5–8.3 (blur by speed); caption at (120,309) 13.5 U grey; four grid lines at y 330, 393, 459, 508 (1.6 U, #EDEDEA); line x 129–591, y 345–480, 3.4 U, accent colour, drawn on over 7.55–8.5 (out cubic) with a soft accent area fill under it (alpha 0.22 fading to 0 at the baseline).
| 7.85–8.95 | hover | cursor rides the line; dot 13 U white ring with 8 U accent centre; vertical hairline to the baseline; black tooltip pill 28 U high, r 9, text 13.5 U/600 | | in-out cubic |
| 9.12–9.55 | week switch | number rolls to the second value, line morphs to a flatter wavy series | | smooth |
### B6 · Search bar and palette — 9.6–11.78 s
| 9.6 | search bar | magnifier (centre x left + 44), placeholder "Search" 22 U grey, key chip at right | | |
| 10.10 | palette | header at top + 47: magnifier at left + 46, placeholder "Type a command" 22 U with blinking caret; divider at top + 97; three rows at top + 160 / 229 / 298: icon chip 26 U r 7 at left + 60, label 19.5 U/500 at left + 93, shortcut 13 U grey at right − 34; third row at 35 % alpha | | |
| 10.50, 10.62, 10.95, 11.12 | typing | one letter of the search word each | | |
| 10.60–10.80 | list swap | rows crossfade to the two result rows (rows at top + 160 / 229); shape to 630 × 290 | | |
| 10.62 | highlight | #EEEEEB bar 60 U high r 14, inset 17 U, on row 1 | | |
| 11.18 | highlight | slides to row 2 (spring 34, 0.85); enter glyph on that row | | |
| 11.55 | enter | highlight turns ink, row text white | | 40, 0.9 |
Cursor drifts bottom-right: (431,400) at 9.45, (415,372) at 9.9, (507,454) at 10.3, (596,526) at 10.55, (625,547) at 10.7, (650,566) at 10.85, then rests.
### B7 · Toast and return — 11.72–14 s
| 11.86–12.86 | toast | white circle 33 U at left + 59.5 with an ink check (3.2 U); text at left + 90, 22 U/500 white | | |
| 12.0 | cursor | to (690,600) | | spring 14 |
| 12.72 | shape | back to the button; label fades in from 12.92 | | |
| 12.9–13.5 | cursor | to (650,607) | | spring 12 |
| 13.5–14 | | still; equals frame 0 including the cursor | | |

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. Output 1080 × 1080; geometry in U × 1.5. Every style is a pure function of t.
- Spring step response (zeta < 1): S(τ) = 1 − e^(−ζωτ)(cos ω_d τ + ζω/ω_d · sin ω_d τ), ω_d = ω√(1 − ζ²). A property's value is v0 plus the sum over target changes of Δ_i · S(t − t_i).
- Rounded rectangles use an analytic signed-distance mask (anti-aliased). Polygons, arcs and lines are drawn with `cv2` sub-pixel anti-aliasing into local masks and composited in float32.
- Shadow: shape mask at 1/3 resolution, Gaussian blur, upsample.
- Content groups render to a clip-sized float RGBA layer, blur by `7 × (1 − alpha)` U, multiply by alpha and the shape mask, composite.
- Text: Pillow masks cached by (text, size, weight). Button and toast widths = text width + padding.
- Chart: two 90-point series (cosine-interpolated knots); the second is scaled 0.62 and lifted 0.05. Tooltip value = first number × (0.38 + 0.57 × series).
- Motion blur: 4 sub-frames over a full-frame shutter, 8 sub-frames during 1.2–2.2, 3.6–4.1, 5.2–7.7, 9.0–10.3 and 11.5–13.0 s.
- Gotcha: swapping text inside a morphing container needs its own enter and exit timing (section 5 overlap values) or old and new text collide.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 60`, streaming frames into ffmpeg.

## 7. Still frame
The settled music player: artwork top-left, title and subtitle, progress at 85 %, three controls with the pause glyph, black card on the grey canvas.

## 8. Never
- A cut between states, or a second shape.
- Bouncy easing, particle bursts, glows, gradients on UI chrome.
- Text overlapping text during a swap, or text outside the shape.
- Reference words or artwork colours as defaults.
- A last frame that differs from the first.
