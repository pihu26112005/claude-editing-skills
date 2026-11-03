# Google Flow prompt · Arrow Label Burst
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 4.03 s (121 frames; reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output). Animation is stepped at 15 fps: frame f shows time floor(f/2)×2/30.  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Arrow Label Burst" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. glowing centre text on a dark grid, four crayon arrows in turn, four coloured labels popping at their tips.

A dark grid-paper keyword burst. A centre phrase slides in letter by letter with a motion blur and a glow. Four hand-drawn crayon arrows then grow out of it in turn, and at each arrow tip a coloured, glowing label pops in. A slow push-in runs under everything.
**The graphic in one line:** glowing centre text on a dark grid, four crayon arrows in turn, four coloured labels popping at their tips.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Centre text (REQUIRED, text, ≤ 16 chars, 1 line (auto-fit to 70%)): <your value>
P2 · Label 1 (top-left) (REQUIRED, text, ≤ 20 chars, 1 line (auto-fit to 70%)): <your value>
P3 · Label 2 (top-right) (REQUIRED, text, ≤ 20 chars, 1 line): <your value>
P4 · Label 3 (bottom-left) (REQUIRED, text, ≤ 20 chars, 1 line): <your value>
P5 · Label 4 (bottom-right) (REQUIRED, text, ≤ 20 chars, 1 line): <your value>
P6 · Centre text colour (optional, hex; default: #F9CB04): <your value or NONE>
P7 · Arrow colour (optional, hex; default: #F9CB04): <your value or NONE>
P8 · Label 1 colour (optional, hex; default: #FCFCFC): <your value or NONE>
P9 · Label 2 colour (optional, hex; default: #CE26F1): <your value or NONE>
P10 · Label 3 colour (optional, hex; default: #2DE819): <your value or NONE>
P11 · Label 4 colour (optional, hex; default: #13BEEF): <your value or NONE>
P12 · Background colour (optional, hex, dark; default: #1F1F1F): <your value or NONE>
P13 · Grid (optional, on / off; default: on): <your value or NONE>
P14 · Dust specks (optional, on / off; default: on): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Centre text: the topic or core idea, shortest strong phrase.
- Labels: four parts, causes, effects or keywords of the topic, in reading order top-left, top-right, bottom-left, bottom-right.
- Colours: P7 and P6 may come from a brand colour; keep strong contrast with the background. Labels should be four clearly different hues (or tints).
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Background #1F1F1F. Hand-drawn grid: 11 vertical lines at x = -30,105,240,375,510,645,780,915,1050,1185,1320 and 7 horizontal at y = -34,100,224,362,496,630,764 (world), each wobbling ±3.2 units, width 3 px at 2x, brightness +11 levels × random 0.55–1.0.
- Vignette in screen space: corners 10 percent darker, from r = 0.25 of corner distance, power 1.4.
- Dust: about 34 irregular light-grey specks (#CDCDCD, 3–9 units, alpha 0.35–0.8), each visible 0.07–0.33 s at random places and times, drifting slightly. Drawn over everything.
- The grid and dust live in world space and zoom with the camera.
## 3. Elements
World units (1280×720, camera zoom 1). Centre text baseline-centre C=(640,423).
### E1 · Centre text
Outfit weight 900, nominal size 69 (cap about 50, width 481 for 14 chars), colour P6, centred on C. Auto-fit: width ≤ 520, floor 70 percent. Soft glow: Gaussian σ 10 units, 0.33 strength added. Dark offset shadow (3 px down, 2 px right at 2x), 70 percent black. Face slightly darker toward the bottom (1.04 → 0.9).
### E2 · Arrow 1 (centre to top-left)
Crayon stroke, colour P7. Shaft spline in final-screen units (zoom 1.065; convert to world by dividing the offset from (640,400) by 1.065): (506,322) (470,316) (440,300) (410,278) (380,250) (349,217). Barbs from tip (349,217): via (388,236) to (428,258), and via (380,255) to (405,296).
### E3 · Arrow 2 (centre to top-right)
Shaft: (797,334) (850,343) (900,338) (945,318) (975,285) (1000,250) (1018,224). Barbs from tip (1019,223): to (933,284) via (975,250), and to (968,310) via (990,265).
### E4 · Arrows 3 and 4
Arrow 3 (bottom-left) shaft: (380,378) (340,381) (300,398) (262,425) (235,455) (212,490) (204,512) (214,517); barbs from tip (214,517) to (190,448) via (200,480), and to (247,448) via (235,480).
Arrow 4 (bottom-right) shaft: (910,435) (950,435) (995,446) (1030,468) (1055,492) (1073,516); barbs from tip (1073,516) to (1015,444) via (1040,470), and to (995,487) via (1040,505).
All strokes: width 12.8 units (shaft, tail taper 0.65 → 1 over the first 15 percent), barbs 0.82 of that width tapering 40 percent to the tip; rough crayon edge (blurred mask thresholded against blurred noise), ±5 percent mottled colour, glow σ 7 units at 0.32 strength.
### E5–E8 · Labels
Anton, nominal size 54 (width about 341 for a 16-char label), auto-fit: width ≤ 380, floor 70 percent. Colour per P8–P11 with a vertical shade 1.08 → 0.88, dark offset shadow (1 px right, 3 px down at 2x), glow σ 4.5 units at 0.30 strength in the label colour. Anchor = baseline centre:
| Label | Centre x | Baseline y |
|---|---|---|
| E5 | 274 | 160 |
| E6 | 1010 | 160 |
| E7 | 275 | 580 |
| E8 | 1024 | 578 |
## 4. Camera
Screen = 1.5 × (z × (world − (640,400)) + (640,400)). z = 1.0 until t = 1.0 s, then linear to 1.065 at 4.03 s. No pan. No motion blur except on E1 (below).
## 5. Timeline (beats)
### B1 · Centre text — 0–0.55 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.02 + 0.034 i | E1 | letter i appears (hard cut) | | |
| 0–0.5 | E1 | x offset | +780 → 0 units, offset = 780 (1 − t/0.5)^1.25 | out |
| 0–0.5 | E1 | horizontal box blur, length 0.6 × the offset change of the last 1/15 s | | |
### B2 · Arrow 1 and Label 1 — 0.33–1.0 s
| 0.33–0.85 | E2 | draw-on: shaft first 68 percent, barb 1 to 84 percent, barb 2 to 100 percent (constant speed) | | linear |
| 0.73–1.0 | E5 | scale pop, anchor baseline centre: 0.25 (0 s), 0.85 (0.067), 1.096 (0.133), 1.044 (0.2), 1.0 (0.267 s onward); blur σ = (1 − scale) × 7 units | | interpolated |
### B3 · Arrow 2 and Label 2 — 1.07–1.67 s
| 1.07–1.57 | E3 | draw-on as E2 | | |
| 1.40–1.67 | E6 | scale pop as E5 | | |
### B4 · Arrow 3 and Label 3 — 1.67–2.34 s
| 1.67–2.12 | E4 arrow 3 | draw-on | | |
| 2.07–2.34 | E7 | scale pop | | |
### B5 · Arrow 4 and Label 4 — 2.47–3.0 s
| 2.47–2.83 | E4 arrow 4 | draw-on (shorter, faster) | | |
| 2.73–3.0 | E8 | scale pop | | |
### B6 · Hold — 3.0–4.03 s
Only the push-in continues; dust flickers.
## 8. Never
- A different number of arrows or labels.
- Arrows crossing a label or the centre text.
- Text overflowing its box or shrinking below 70 percent.
- Reference content (its words) as defaults.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 4.03 s (121 frames; reference 1280×720; world units below are 1280×720 px, multiply by 1.5 for output). Animation is stepped at 15 fps: frame f shows time floor(f/2)×2/30.. Keep the motion, timing and order of beats of section 4.
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
