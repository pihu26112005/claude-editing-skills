# Google Flow prompt · Glow Line Decoder
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 6.03 s (reference 1280×720; all world units below are in 1280×720 px, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Glow Line Decoder" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. glowing two-line headline over six lines that decode from blur to pixel mosaic to sharp text while the camera zooms in and follows them down.

A black-screen list reveal. A two-line glowing headline types on, six blurry placeholder lines appear under it, turn into grey pixel mosaics, then the camera zooms in hard, scrolls down the list and each mosaic line sharpens into readable glowing text one after another.
**The graphic in one line:** glowing two-line headline over six lines that decode from blur to pixel mosaic to sharp text while the camera zooms in and follows them down.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Headline line 1 (REQUIRED, text, ≤ 24 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Headline line 2 (REQUIRED, text, ≤ 24 chars, 1 line (auto-fit down to 70%)): <your value>
P3 · List line 1 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P4 · List line 2 (REQUIRED, text, ≤ 14 chars, 1 line): <your value>
P5 · List line 3 (REQUIRED, text, ≤ 14 chars, 1 line): <your value>
P6 · List line 4 (REQUIRED, text, ≤ 14 chars, 1 line): <your value>
P7 · List line 5 (REQUIRED, text, ≤ 14 chars, 1 line): <your value>
P8 · List line 6 (REQUIRED, text, ≤ 14 chars, 1 line): <your value>
P9 · Headline colour (optional, hex, bright; default: #FDFE00): <your value or NONE>
P10 · List colour (optional, hex, bright; default: #FFFFFF): <your value or NONE>
P11 · Background (optional, hex, dark; default: #000000): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Headline: the video or post title, split into two balanced lines.
- List lines: six short steps, tips or key points from the user's script, shortest strong phrase each.
- Colours: P9 may come from a brand colour; keep strong contrast with the background.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Background pure black #000000. No grid, no grain, no vignette.
- Everything is additive light on black: glows add to the background.
- Content column centred on x = 640 units. Nothing sits outside x 300–980.
## 3. Elements
World units (1280×720 frame at zoom 1).
### E1 · Headline
Two centred lines, Archivo Bold (wght 700) with the width axis narrowed until the wider line is ≤ 620 units (about wdth 78 for 20 chars); size 64 units; line centres y = 98 and 178. Colour P9. Glow: text + 0.9 × gaussian(5 units) + 0.4 × gaussian(16 units), clipped.
### E2 · List lines (6)
Centres x = 640, y = 297, 372, 447, 522, 597, 672. Archivo Bold (wght 700, wdth 100), size 66 units (cap height about 47), colour P10, auto-fit width ≤ 560. Each line has three looks:
- Placeholder: the line's own text in capitals, Archivo ExtraBold size 50, gaussian blur 5 units, gain 2.2, soft glow.
- Mosaic: the sharp line pixelated into blocks 20 × 12 units, soft glow (0.45 × gaussian 8 + 0.3 × gaussian 22).
- Sharp: the same glow with no pixelation.
## 4. Camera
Screen = 1.5 × (zoom × (world − centre) + (640,360)). Centre x stays 640.
| t (s) | centre y | zoom | ease |
|---|---|---|---|
| 0–1.87 | 360 | 1.00 | hold |
| 1.87→2.40 | 360 → 215 | 1.00 → 2.15 | in-out cubic |
| 2.40–2.60 | 215 | 2.15 | hold |
| 2.60→3.00 | 215 → 372 | 2.15 | in-out cubic |
| 3.00–3.30 | 372 | 2.15 | hold |
| 3.30→3.73 | 372 → 466 | 2.15 | in-out cubic |
| 3.73–4.53 | 466 | 2.15 | hold |
| 4.53→4.73 | 466 → 545 | 2.15 | in-out cubic |
| 4.73–5.13 | 545 | 2.15 | hold |
| 5.13→5.53 | 545 → 685 | 2.15 | in-out cubic |
| 5.53–6.03 | 685 | 2.15 | hold |
## 5. Timeline (beats)
### B1 · Headline type-on — 0–0.45 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.05–0.45 | E1 letters | alpha 0 → 1, random order, 0.1 s each, jitter up to ±10 units while fading | | linear |
### B2 · Placeholders — 0.1–0.5 s
| 0.1–0.47 | E2 placeholders | alpha 0.1 → 1.0 | | linear |
### B3 · Mosaic flicker — 0.87–1.67 s
| 0.87 + 0.067 × k, 0.4 s each | E2 line k | blocks (20 × 12) flip from placeholder to mosaic in random order, brightness +35% on flip | | linear |
Hold the mosaic list 1.5–1.87 s.
### B4 · Zoom and first decode — 1.87–2.6 s
| 1.87–2.40 | camera | zoom in to the headline-and-list boundary | | see camera |
| 2.33–2.60 | E2 line 1 | mosaic → sharp (level 20×12 → 12×8 → 7×5 → 3×2 → sharp) | | linear |
### B5 · Scroll and decode — 2.6–5.5 s
Each line decodes over 0.27 s (8 frames), starting at 2.33, 3.0, 3.53, 4.27, 4.93, 5.47 s (lines 1–6). Camera steps follow the table in section 4. The headline leaves the top of the frame during 2.6–3.0 s.
### B6 · Hold — 5.5–6.03 s
Lines 4 (clipped), 5 and 6 sharp, still.
## 8. Never
- Reference words, a different number of list lines, or text outside the frame width.
- A glow that makes text unreadable against the background.
- Skipping the mosaic stage.
- Changing the camera path or the decode order.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 6.03 s (reference 1280×720; all world units below are in 1280×720 px, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
