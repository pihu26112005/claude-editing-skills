# Google Flow prompt · Prompt Pill Reveal
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 14.03 s (reference 1280×720; all units below are 1280×720 px, multiply by 1.5 for output; render at 3840×2160 and downscale)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Prompt Pill Reveal" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. brand pill, prompt box that fills with the request, send tap, working pill with two status words, icon burst into a result image.

An interface-style explainer. A brand name sits in a pill that grows into an AI prompt box. The user's request appears word by word, a pointer taps send, and the box shrinks into a coloured "working" pill with a spinning star. The pill folds into an icon, which bursts open into a full result image with a caption.
**The graphic in one line:** brand pill, prompt box that fills with the request, send tap, working pill with two status words, icon burst into a result image.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Brand name (REQUIRED, text, ≤ 10 chars, 1 line (pill widens, min 472)): <your value>
P2 · Prompt text (REQUIRED, text, ≤ 140 chars, ≤ 4 lines at 44 px (auto-fit to 70%)): <your value>
P3 · Result image (REQUIRED, image, any aspect, cover-fit to 16:9, ≥ 1280 px wide): <your value>
P4 · Image caption (REQUIRED, text, ≤ 24 chars, 1 line): <your value>
P5 · Placeholder text (optional, text, ≤ 40 chars; default: Describe what you want to make ...): <your value or NONE>
P6 · Import button label (optional, text, ≤ 10 chars; default: import): <your value or NONE>
P7 · Send button label (optional, text, ≤ 8 chars; default: Send): <your value or NONE>
P8 · Status word 1 (optional, text, ≤ 12 chars; default: Designing): <your value or NONE>
P9 · Status word 2 (optional, text, ≤ 12 chars; default: Editing): <your value or NONE>
P10 · Accent colour (optional, hex; default: #F89A7C): <your value or NONE>
P11 · Background colour (optional, hex, light; default: #F4F2EC): <your value or NONE>
P12 · Text colour (optional, hex, dark; default: #111111): <your value or NONE>
P13 · Caption colour (optional, hex, light against the image bottom; default: #FAEEDC): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Brand: the product or app name in the user's material.
- Prompt: the request a user would type to make the shown result, one or two sentences.
- Result image: a screenshot, logo card or artwork of the finished product; if only a logo is given, centre it on a flat brand-colour card.
- Caption: the product URL or tagline.
- Accent: a brand colour; keep strong contrast with dark text. Pill border = accent × 0.72.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Flat background #F4F2EC. No grid, vignette or grain.
- No camera. Every object is centred on C = (640,360).
- Font: Poppins (Medium for the brand, Regular elsewhere). Caption: a book serif (Gelasio). Fallbacks: DM Sans, Inter.
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
Star: 12 rounded rays, cream #F6F0E6, radius 47.5, centre at pill left + 73.5, rotating 2.2 rad/s. Status text Poppins Regular 58, #1A1A1A, left-aligned at pill left + 143, vertically centred. Pill width = 26 + 95 + 22 + text width of "<word>..." + 33.
### E6 · Result card
Image cover-cropped to 16:9, square corners, no border, centred on C. Caption centred at 4.5 percent of card height above the bottom, serif size 5 percent of card height, colour P13.
### E7 · Pointer
Small white pointing hand with a black outline (about 46 px tall), fingertip as hot spot.
## 4. Camera
None. The only scaling is the result card's own size (see B8, B9).
## 5. Timeline (beats)
### B1 · Brand hold — 0–0.8 s
Pill E1 static.
### B2 · Squeeze and open — 0.8–1.8 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.8–1.2 | E1 | scale | 1 → 0.9 | in-out cubic |
| 1.2–1.8 | E2 | size | 0.9×pill → 990×329, radius 41 → 44 | out cubic |
| 1.2–1.7 | E1 text | opacity, colour | 1 → 0, to #555 | linear  |
### B3 · Tools and placeholder — 1.8–3.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.8–2.2 | E4 | opacity | 0 → 1 | smooth  |
| 2.05–2.4 | placeholder words | opacity | 0 → 1, 0.05 s stagger | smooth |
| 2.85–3.2 | placeholder words | opacity | 1 → 0, 0.05 s stagger, left to right | smooth |
### B4 · Typing — 3.0–4.2 s
Prompt words fade in one by one (0.14 s fade each), evenly spaced from 3.0 to 4.2. When a word opens a new line, the box grows by 54.5 over 0.25 s, symmetric around C; the tool row stays 48 above the bottom.
### B5 · Send tap — 3.85–5.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 3.85–4.4 | E7 | position | (send x+150, 780) → send centre +(10,12) | out cubic  |
| 4.5–4.95 | Send button, E7 | scale | 1 → 0.93 → 1 | smooth |
### B6 · Collapse and working — 5.0–7.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 5.0–5.6 | E2 | size, fill, border | box → working pill, white → P10 | in-out cubic |
| 5.0–5.25 | E3, E4 | opacity | 1 → 0 | linear  |
| 5.0–5.6 | E7 | position | send → (946,610) | out cubic  |
| 5.35–5.75 | E7 | opacity | 1 → 0 | smooth  |
| 5.3–5.6 | E5 | opacity | 0 → 1 | smooth  |
| 6.4–6.65 | E5 | text and pill width | word 1 → word 2 | cross-fade, in-out cubic |
### B7 · Fold to icon — 7.0–8.17 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 7.0–7.25 | E5 text | opacity | 1 → 0 | smooth |
| 7.0–7.6 | E2 | size | pill → 147×150 | in-out cubic |
| 7.6–7.9 | E2 | scale | 1 → 0.98 | linear |
| 7.9–8.17 | E2 | scale | 0.98 → 0.5 | in cubic |
### B8 · Burst — 8.18–9.0 s
Icon cut to result card E6 at width 1.22 W, settling to 0.821 W (1051 px) by 8.9 s, out cubic. Use 4-sample sub-frame blur from 7.9 to 8.7 s.
### B9 · Push-in and hold — 9.0–14.03 s
Hold 0.821 W to 9.2 s, then width 0.821 W → 0.965 W over 9.2–12.2 s, in-out cubic, then hold to the end.
## 8. Never
Never stretch the image. Never let the prompt leave the box. Never change the beat order or timing. Never show the reference's words or logo.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 14.03 s (reference 1280×720; all units below are 1280×720 px, multiply by 1.5 for output; render at 3840×2160 and downscale). Keep the motion, timing and order of beats of section 4.
- No watermark, no extra frames before or after the animation, no end card.

## 6. NEGATIVE PROMPT (avoid all of these)
- Any element, colour, font or motion that section 4 does not describe; extra logos, brand names, watermarks, people's faces or UI that was not asked for.
- Misspelled, garbled, extra or missing text; text outside the frame; overlapping text; random gibberish letters.
- Camera moves, zooms or transitions that are not in the timeline; flicker, jitter or warped shapes; cartoon filters.
- Black bars, borders, vignettes or grain that the design does not list.

## 7. FINAL CHECK
- [ ] All required inputs appear exactly as typed and nowhere else.
- [ ] Every beat of the timeline happens in order with the described timing and easing.
- [ ] Layout, colours and type match the design; nothing extra is on screen.
- [ ] The video has the right format and length.
