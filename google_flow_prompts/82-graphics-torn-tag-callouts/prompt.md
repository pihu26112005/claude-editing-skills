# Google Flow prompt · Torn Tag Callouts
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 11.5 s (reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Torn Tag Callouts" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. striped two-word label tears apart, halves recolour, dashed leaders and callouts label each half.

A glowing striped label carrying two words rises on a dark violet frame, tears in two along a zigzag crack, and the halves tilt apart and change colour. Each half gets a dashed looping leader line and a bold italic callout. It communicates a two-part idea that separates into two named pieces.
**The graphic in one line:** striped two-word label tears apart, halves recolour, dashed leaders and callouts label each half.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Left word (REQUIRED, text, ≤ 12 chars, 1 line): <your value>
P2 · Right word (REQUIRED, text, ≤ 12 chars, 1 line): <your value>
P3 · Callout 1 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit to 70%)): <your value>
P4 · Callout 2 (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit to 70%)): <your value>
P5 · Start colour (optional, hex; default: #FF9419): <your value or NONE>
P6 · Left half colour (optional, hex; default: #FF0A14): <your value or NONE>
P7 · Right half colour (optional, hex; default: #09FB02): <your value or NONE>
P8 · Background glow colour (optional, hex, dark-friendly; default: #4A08C0): <your value or NONE>
P9 · Leader line colour (optional, hex; default: #FFFFFF): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Label words: the two halves of a concept in the user's script (for example a pair, a verb and object, or before and after).
- Callouts: a short name or note for each word.
- Colours: P6 and P7 may come from brand colours; keep them clearly different from each other. P5 may be a third brand colour.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Base colour near-black violet #0D051E (13,5,30). Violet glow in the bottom-left corner: P8 added with weight exp(-d/540) from the point (0,740). Weaker glow top-right: 0.34 × exp(-d/380) from (1280,0). Measured corners: bottom-left (73,8,192), top-right (39,10,99) at the start, centre (20,5,50), bottom-right (11,4,20).
- Faint noise ±1 level. No grid, no vignette beyond the glows.
- Everything but the background lives in a world moved by the camera (section 4). The background is fixed on screen.
## 3. Elements
World units, 1280×720 frame, settled layout. Label centre at (640,478) before the tear.
### E1 · Label
Rounded rectangle 752×192, corner radius 28. Fill: base colour with diagonal stripes. Stripes angle 62° from the horizontal leaning right, pitch 26.5, width 5.6. Before the tear: base P5, stripes white. After the tear a half uses base = 0.68 × its colour, stripes = its full colour.
Soft glow outside the label: blurred copy (sigma 7 and 18 units) tinted with the current half colour, strength 0.62 before the tear, 0.30 after.
### E1a · Label text
Rubik, weight 800, synthetic italic (shear 0.2). Both words on one line, two spaces between them. Size 64 units, auto-fit so the width stays ≤ 70 percent of the label, floor 70 percent of size. Colour #6B1A05 before the tear, #140308 after. Centred on the label.
### E2 · Left half
The label part left of the crack, used from the tear on.
### E3 · Right half
The part right of the crack.
### E4 · Crack
Zigzag polyline centred on the gap between the words: points relative to the gap centre uc: (0,-120) (-4,-96) (+24,-40) (-4,+6) (+34,+30) (+6,+100) (+6,+130). The left half owns everything left of it.
### E5 / E6 · Callout and leader
Leader: dashed white line, width 4, dash 13, gap 10, round caps, Catmull-Rom path ending at the top edge of its half. Path 1 points: (320,388) (300,368) (280,343) (262,308) (270,277) (298,268) (318,290) (316,322) (298,352) (272,358) (245,338) (228,300) (224,250) (225,205). Path 2 points: (1090,421) (1112,392) (1128,352) (1118,315) (1082,298) (1045,305) (1036,340) (1020,380) (995,388) (972,365) (967,320) (967,243). Each path draws from its first point to its last.
Callout: Rubik 800 italic caps, colour = half colour, size 62 (callout 1) and 58 (callout 2), centre (222,140) and (972,182). Types on per letter (0.07 s stagger, 0.22 s each, blur-in). Width limit 330 units: auto-fit to the limit, floor 70 percent.
## 4. Camera
Screen = 1.5 × (zoom × (world − centre) + (640,360)).
| t (s) | zoom | centre x | centre y | ease |
|---|---|---|---|---|
| 0–0.8 | 1.17 | 640 | 478 | hold |
| 0.8→1.4 | 1.0 | 640 | 478 | out cubic |
| 1.4–2.5 | 1.0 | 640 | 478 | hold |
| 2.5→3.4 | 1.0 | 640 | 360 | in-out cubic |
| 3.4–4.4 | 1.0 | 640 | 360 | hold |
| 4.4→5.0 | 1.2 | 825 | 392 | in-out cubic |
| 5.0–8.2 | 1.2 | 825 | 392 | hold |
| 8.2→9.0 | 1.0 | 640 | 360 | in-out cubic |
| 9.0–11.5 | 1.0 | 640 | 360 | hold |
Motion blur: 5 sub-frames over a half-frame shutter during 0.3–1.5, 2.3–3.5, 4.3–5.4 and 8.2–9.1 s; one sample elsewhere.
## 5. Timeline (beats)
### B1 · Rise — 0.3–1.4 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.3–0.9 | E1 | y offset | +400 → 0 | back (s 0.9) |
| 0.8–1.4 | camera | zoom | 1.17 → 1.0 | out cubic |
### B2 · Hold — 1.4–2.35 s
Label rests, glowing.
### B3 · Tear — 2.35–3.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.35–3.0 | E2 | move, tilt | (0,0) 0° → (−39,0) −8° | back (s 1.0) |
| 2.4–3.0 | E3 | move, tilt | (0,0) 0° → (+60,0) +2° | out cubic |
| 2.6–2.85 | E2 | colour | P5 → P6 | linear |
### B4 · Flicker — 3.0–3.7 s
| 3.15–3.2 | E2 | colour mix | 1 → 0.45 (flash back toward P5) | step |
| 3.5–3.62 | E2 | colour mix | 0.45 → 1 | linear |
### B5 · Left callout — 2.95–5.0 s
| 2.95–3.5 | E5 leader | draw-on | 0 → 100% | sine in-out |
| 3.4–4.1 | E5 text | type-on at 0.5 scale | | out cubic |
| 4.5–4.9 | E5 text | scale | 0.5 → 1.0 | out cubic |
| 4.3–5.4 | E3 | move, tilt | (+60,0) 2° → (+67,+7) 12° | in-out cubic |
### B6 · Right recolour — 5.35–6.5 s
| 5.35–5.55 | E3 | colour mix | P5 → P7 | linear |
| 5.8–5.95 | E3 | colour mix | P7 → P5 | linear |
| 6.3–6.5 | E3 | colour mix | P5 → P7, stays | linear |
### B7 · Right callout — 5.0–7.8 s
| 5.0–5.5 | E6 leader | draw-on | 0 → 100% | sine in-out |
| 6.8–7.5 | E6 text | type-on at full size | | out cubic |
### B8 · Pull-back and hold — 8.2–11.5 s
Camera pulls back (section 4) then everything rests.
## 8. Never
- A crack through the middle of a word when a gap exists.
- Text leaving the label or callouts leaving their width limit.
- Leaders crossing the label text.
- Reference words or colours as defaults beyond the measured look defaults.
- More or fewer than two halves.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 11.5 s (reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
