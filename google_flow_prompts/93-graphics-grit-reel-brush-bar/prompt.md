# Google Flow prompt · Grit Reel Brush Bar
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 6 s (reference 1280×720, 30 fps, 6 s; units below are 1280×720 px, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Grit Reel Brush Bar" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. a title typed on a sweeping dry-brush bar over dark scratched film, with a draw-on line tag and gate HUD marks.

A one-line title card on dark, worn film. A rough dry-brush colour bar sweeps in from its left end while the title types letter by letter inside it. A thin circuit-line tag draws in at the top. Film grain, scratches, dust, flicker and camera-gate marks run throughout, and the bar's brush edge changes shape every few frames. The title card holds to the end.
**The graphic in one line:** a title typed on a sweeping dry-brush bar over dark scratched film, with a draw-on line tag and gate HUD marks.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Main text (REQUIRED, text, ≤ 16 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Bar colour (optional, hex; default: #C00103): <your value or NONE>
P3 · Text colour (optional, hex, light; default: #F3EDED): <your value or NONE>
P4 · Line and HUD colour (optional, hex; default: #D8D8D8): <your value or NONE>
P5 · Film base tone (optional, hex, dark; default: #1F1D1D): <your value or NONE>
P6 · HUD readout (optional, text, ≤ 4 chars; default: 000): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Main text: the shortest strong phrase or question from the user's script.
- P2: a brand colour; keep strong contrast with P3.
- P5: any near-black.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Base tone #1F1D1D. Mottled cloudy texture (blurred noise sigma 40 units, ±12 levels) plus fine paper grain (sigma 3, ±8 levels) plus sparse bright specks. Three textures cycle, randomly offset each frame.
- Vignette: edges darken to 70 percent.
- Per-frame grain: half-res noise, sigma 7 levels, plus fine noise sigma 3.
- Scratches: two bright vertical lines near x=253 and x=584 (2 px wide, flicker, ±5 px jitter), plus 1–3 short thin vertical scratches and 3–9 small dust specks per frame.
- Brightness flicker: ±2.5 percent sine plus ±1.2 percent random per frame.
- HUD marks on a top row (y=8) and a bottom row (y=700): small barcodes at x=10, 300, 1100, 1180; three crosshair circles at x=112, 545, 1190; the HUD readout P6 in mono type beside them (grey, 45 percent).
- Gate roll glitch at frames 11–13 (0.37–0.43 s): whole frame shifts up 70, 70 and 25 px (frames 11, 12, 13); frame 12 is also +18 levels brighter.
## 3. Elements
### E1 · Film base
Canvas of section 1, drawn below everything.
### E2 · Brush bar
Group centred at x=640, y=362 (centre). Width = text width + 40 left + 48 right padding; height = 1.75 × font size. Colour P2 with mottling (±9 percent, blurred noise sigma 6). Edges: left and right edges per row are base + noise (fine sigma 1.5, ±14 units; slow sigma 9, ±12) plus 14 thin right-hand bristle streaks (1–3 rows, 14–40 px longer) and 8 left ones; top and bottom edges wobble ±5 units with a few 6–18 px wide steps. Near both ends rows are thinned by dry streaks (alpha down 85 percent on about 1 in 4 rows, fading over 70 px left, 90 px right). 6 pre-built variants.
### E3 · Title text
Poppins Regular, size 74 units (111 px; cap height about 52 units), colour P3, 97 percent opacity, left-aligned at bar left + 40, cap-height centred on y=362. Auto-fit: text width ≤ 700 units, shrink to 70 percent floor.
### E4 · Line tag
Polyline (649,6) → (722,6) → (748,42) → (842,42), width 2 px, colour P4, a 5 px dot at the start and an 8 px dot at the end (end dot shows only when fully drawn). Flickers to 35 percent opacity for 2 of every 47 frames.
### E5 · Gate HUD
As in section 1; colour P4.
## 4. Camera
Fixed. No camera move. Only the gate roll glitch of section 1.
## 5. Timeline (beats)
### B1 · Sweep and type — 0.1–0.65 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.1–0.65 | E2 | reveal edge x | bar left → bar right | out cubic |
| 0.1–0.65 | E3 | letters | each letter appears (hard cut) once the reveal edge is 12 units past its right edge | follows E2 |
| 0.1–0.7 | E2 | variant | new brush variant every 3 frames | cut |
### B2 · Line tag draw — 0.25–0.6 s
| 0.25–0.6 | E4 | draw-on length | 0 → 100% | out cubic |
### B3 · Roll glitch — 0.37–0.43 s
Frames 11–13 of section 1.
### B4 · Hold — 0.7–6.0 s
Nothing moves except film noise, flicker and the bar's brush variant, which changes every 11 frames (cycling the 6 variants). The brush edge "boils" this way until the end.
## 8. Never
- Text outside the bar or crossing its edge.
- Smooth, vector-clean bar edges or comb-like spikes.
- A camera move.
- Any reference words as defaults.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 6 s (reference 1280×720, 30 fps, 6 s; units below are 1280×720 px, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
