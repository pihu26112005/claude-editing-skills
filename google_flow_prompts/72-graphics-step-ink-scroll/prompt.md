# Google Flow prompt · Step Ink Scroll
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 3.93 s (118 frames; reference 1280×720, base units below are 1280×720 px, multiply by 1.5)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Step Ink Scroll" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. three oversized headlines on crumpled paper, stepped sideways in five snaps to reveal their endings.

Three stacked headlines in distressed serif capitals sit on crumpled grey-green paper. They are wider than the frame, so only their left parts show. The whole stack then slides left in five hard, held steps, like a ticker, until the endings of the lines come into view, and holds. The middle line is sharp and heavily ink-worn. The top and bottom lines are soft (out of focus) and lighter.
**The graphic in one line:** three oversized headlines on crumpled paper, stepped sideways in five snaps to reveal their endings.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Headline 1 (top, soft) (REQUIRED, text, 16–26 chars, 1 line, capitals (auto-fit to 70%)): <your value>
P2 · Headline 2 (middle, sharp) (REQUIRED, text, 16–26 chars, at least 2 words, 1 line, capitals (auto-fit to 70%)): <your value>
P3 · Headline 3 (bottom, soft) (REQUIRED, text, 16–26 chars, 1 line, capitals (auto-fit to 70%)): <your value>
P4 · Ink colour (optional, hex, dark; default: #000000): <your value or NONE>
P5 · Paper colour (optional, hex, mid-light; default: #AFAFA1): <your value or NONE>
P6 · Ink wear (optional, on / off; default: on): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Headlines: three related titles from the user's script or list, similar in length, 16–26 characters each. The middle one is the hero.
- Colours: P4 may come from a brand colour (keep it very dark); P5 from a paper or background tone in the user's material.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Paper base #AFAFA1, lit with soft crumple relief: low-frequency lumps plus ridged-noise creases, shading clamp 0.86–1.12.
- Vignette: corners darken to about 67 percent, radial, starts at r=0.2 of the corner distance, slightly darker on the left (3 percent).
- Fine grain ±1.2 percent. Paper is fixed to the screen and never moves.
- Chromatic fringe on ink: red channel shifted -1 px, blue +1 px.
## 3. Elements
Base units 1280×720. Rows are vertical cap-centres.
### E1 · Headline 1 (top)
Cinzel wght 760, size 105 (cap height about 73), tracking +0.035 em, uppercase, left edge x=45, cap centre y=62. Soft: gaussian blur sigma 3 units, opacity 92 percent, light wear (55 percent of E2). Auto-fit: if width exceeds 1750, shrink to a floor of 70 percent.
### E2 · Headline 2 (middle)
Same font and size, cap centre y=358. Sharp, full ink, heavy wear: rough eroded edges (edge noise up to 5.5 px), small holes, ink splatter dots around the letters (density falls off with distance, radius 0.6–2.8 px), and a dotted ink ring around the second word (140 specks, 75 percent kept, ellipse rx = word half-width + 0.1 em, ry 0.62 em, open at the top-left).
### E3 · Headline 3 (bottom)
As E1, cap centre y=645.
All lines share the same left edge and move together. Wear is baked in once per line and does not change between frames.
## 4. Camera
No zoom. The stack of lines is offset horizontally by a step function. Each step is a hard cut with no easing and no motion blur.
| frame | t (s) | stack offset x (base units) |
|---|---|---|
| 0–7 | 0–0.23 | 0 |
| 8–14 | 0.27 | -148 |
| 15–22 | 0.50 | -296 |
| 23–29 | 0.77 | -444 |
| 30–37 | 1.00 | -590 |
| 38–117 | 1.27–3.93 | -650 (hold) |
## 5. Timeline (beats)
### B1 · Opening hold — 0–0.27 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 | E1–E3 | offset x | 0 | none |
### B2 · Four equal snaps — 0.27–1.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.267 | E1–E3 | offset x | 0 → -148 | hard cut |
| 0.500 | E1–E3 | offset x | -148 → -296 | hard cut |
| 0.767 | E1–E3 | offset x | -296 → -444 | hard cut |
| 1.000 | E1–E3 | offset x | -444 → -590 | hard cut |
### B3 · Short last snap and hold — 1.27–3.93 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.267 | E1–E3 | offset x | -590 → -650 | hard cut |
| 1.27–3.93 | all | | still | |
## 8. Never
- Easing, blur or interpolation between the steps.
- Lines that fit inside the frame at the start (they must overflow on the right).
- Different offsets for different lines.
- Text over 26 characters at full size, clipped letters, or lines overlapping each other.
- Reference words as defaults.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 3.93 s (118 frames; reference 1280×720, base units below are 1280×720 px, multiply by 1.5). Keep the motion, timing and order of beats of section 4.
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
