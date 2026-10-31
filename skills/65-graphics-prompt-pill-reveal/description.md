# description.md: Prompt Pill Reveal

An interface-style explainer. A brand name sits in a pill that grows into an AI prompt box. The user's request appears word by word, a pointer taps send, and the box shrinks into a coloured "working" pill with a spinning star. The pill folds into an icon, which bursts open into a full result image with a caption.
**The graphic in one line:** brand pill, prompt box that fills with the request, send tap, working pill with two status words, icon burst into a result image.
**Format:** 16:9 · 1920×1080 · 30 fps · 14.03 s (reference 1280×720; all units below are 1280×720 px, multiply by 1.5 for output; render at 3840×2160 and downscale)

## 1. Canvas
- Flat background #F4F2EC (measured 244,242,236). No grid, vignette or grain.
- No camera. Every object is centred on C = (640,360).
- Font: Poppins (Medium for the brand, Regular elsewhere). Caption: a book serif (Gelasio). Fallbacks: DM Sans, Inter.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Brand name | yes | none, must ask | text, ≤ 10 chars, 1 line (pill widens, min 472) | E1, B1–B3 |
| P2 | Prompt text | yes | none, must ask | text, ≤ 140 chars, ≤ 4 lines at 44 px (auto-fit to 70%) | E3, B4 |
| P3 | Result image | yes | none, must ask | image, any aspect, cover-fit to 16:9, ≥ 1280 px wide | E6, B8 |
| P4 | Image caption | yes | none, must ask | text, ≤ 24 chars, 1 line | E6, B8 |
| P5 | Placeholder text | no | Describe what you want to make ... | text, ≤ 40 chars | E3, B3 |
| P6 | Import button label | no | import | text, ≤ 10 chars | E4 |
| P7 | Send button label | no | Send | text, ≤ 8 chars | E4 |
| P8 | Status word 1 | no | Designing | text, ≤ 12 chars | E5, B6 |
| P9 | Status word 2 | no | Editing | text, ≤ 12 chars | E5, B6 |
| P10 | Accent colour | no | #F89A7C (measured 248,154,124) | hex | send button, E5 pill |
| P11 | Background colour | no | #F4F2EC (measured) | hex, light | canvas |
| P12 | Text colour | no | #111111 | hex, dark | E1 |
| P13 | Caption colour | no | #FAEEDC | hex, light against the image bottom | E6 |

### 2.1 How to infer parameters from user material
- Brand: the product or app name in the user's material.
- Prompt: the request a user would type to make the shown result, one or two sentences.
- Result image: a screenshot, logo card or artwork of the finished product; if only a logo is given, centre it on a flat brand-colour card.
- Caption: the product URL or tagline.
- Accent: a brand colour; keep strong contrast with dark text. Pill border = accent × 0.72.

## 3. Elements
### E1 · Brand pill
White (#FFFEFC) rounded rectangle, border 2 px #C4C4C0, radius 46. Size: w = max(472, text + 116), h = 186. Text Poppins Medium 80, colour P12, centred.
### E2 · Morphing container
The same rounded rectangle becomes the prompt box (990×329, radius 44), the working pill (h 155, radius 40, fill P10, border P10 × 0.72) and the icon square (147×150). Border 2 px. Always centred on C.
### E3 · Prompt text and placeholder
Poppins Regular 44, line pitch 54.5, text width 902 (box left + 44). First baseline = box top + 88. Prompt is wrapped greedily and justified (last line left). Placeholder colour #666666, prompt colour #0F0F0F.
### E4 · Tool row
Bottom of the box minus 48, height 82. Three square icon buttons 82×82 (gear, paperclip, pencil; radius 22, border 2.2 px #B0B0B0, icons #787878), 20 apart, starting 42 from the box left. Import button after them: Poppins Regular 38, #787878, width text + 60. Send button right-aligned 42 from the box right: fill P10, white outline triangle plus label (Poppins Regular 38, white), width text + 112.
### E5 · Star and status text
Star: 12 rounded rays, cream #F6F0E6, radius 47.5, centre at pill left + 73.5, rotating 2.2 rad/s. Status text Poppins Regular 58, #1A1A1A, left-aligned at pill left + 143, vertically centred. Pill width = 26 + 95 + 22 + text width of "<word> ..." + 33.
### E6 · Result card
Image cover-cropped to 16:9, square corners, no border, centred on C. Caption centred at 4.5 percent of card height above the bottom, serif size 5 percent of card height, colour P13.
### E7 · Pointer
Small white pointing hand with a black outline (about 46 px tall), fingertip as hot spot.

## 4. Camera
None. The only scaling is the result card's own size (see B8, B9).

## 5. Timeline (beats)
### B1 · Brand hold — 0–0.8 s
Pill E1 static. (measured)
### B2 · Squeeze and open — 0.8–1.8 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.8–1.2 | E1 | scale | 1 → 0.9 | in-out cubic (measured) |
| 1.2–1.8 | E2 | size | 0.9×pill → 990×329, radius 41 → 44 | out cubic (measured) |
| 1.2–1.7 | E1 text | opacity, colour | 1 → 0, to #555 | linear (design) |
### B3 · Tools and placeholder — 1.8–3.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.8–2.2 | E4 | opacity | 0 → 1 | smooth (design) |
| 2.05–2.4 | placeholder words | opacity | 0 → 1, 0.05 s stagger | smooth (measured) |
| 2.85–3.2 | placeholder words | opacity | 1 → 0, 0.05 s stagger, left to right | smooth (measured) |
### B4 · Typing — 3.0–4.2 s
Prompt words fade in one by one (0.14 s fade each), evenly spaced from 3.0 to 4.2. When a word opens a new line, the box grows by 54.5 over 0.25 s, symmetric around C; the tool row stays 48 above the bottom. (measured)
### B5 · Send tap — 3.85–5.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 3.85–4.4 | E7 | position | (send x+150, 780) → send centre +(10,12) | out cubic (design) |
| 4.5–4.95 | Send button, E7 | scale | 1 → 0.93 → 1 | smooth (measured) |
### B6 · Collapse and working — 5.0–7.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 5.0–5.6 | E2 | size, fill, border | box → working pill, white → P10 | in-out cubic (measured) |
| 5.0–5.25 | E3, E4 | opacity | 1 → 0 | linear (design) |
| 5.0–5.6 | E7 | position | send → (946,610) | out cubic (design) |
| 5.35–5.75 | E7 | opacity | 1 → 0 | smooth (design) |
| 5.3–5.6 | E5 | opacity | 0 → 1 | smooth (design) |
| 6.4–6.65 | E5 | text and pill width | word 1 → word 2 | cross-fade, in-out cubic (measured) |
### B7 · Fold to icon — 7.0–8.17 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 7.0–7.25 | E5 text | opacity | 1 → 0 | smooth (measured) |
| 7.0–7.6 | E2 | size | pill → 147×150 | in-out cubic (measured) |
| 7.6–7.9 | E2 | scale | 1 → 0.98 | linear (measured) |
| 7.9–8.17 | E2 | scale | 0.98 → 0.5 | in cubic (measured) |
### B8 · Burst — 8.18–9.0 s
Icon cut to result card E6 at width 1.22 W, settling to 0.821 W (1051 px) by 8.9 s, out cubic. Use 4-sample sub-frame blur from 7.9 to 8.7 s. (measured)
### B9 · Push-in and hold — 9.0–14.03 s
Hold 0.821 W to 9.2 s, then width 0.821 W → 0.965 W over 9.2–12.2 s, in-out cubic, then hold to the end. (measured)

## 6. Build notes
- Render at 3840×2160 (unit = 3 px) with Pillow, composite RGBA layers, downscale with Lanczos. One frame costs about 0.5 s and 100 MB; use one or two workers.
- Prompt layout: greedy wrap at width 902, justify by spreading spaces; compute line start times from the word times.
- Star: 12 round-capped lines, ray length pattern 1, .78, .95, .72, ... repeating, width 0.17 of the radius.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The result card at 0.965 W on the off-white background with its caption near the bottom.

## 8. Never
Never stretch the image. Never let the prompt leave the box. Never change the beat order or timing. Never show the reference's words or logo.
