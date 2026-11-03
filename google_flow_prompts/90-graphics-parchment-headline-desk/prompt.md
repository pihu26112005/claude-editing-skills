# Google Flow prompt · Parchment Headline Desk
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 13 s (reference 1280×720; multiply reference pixels by 1.5)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Parchment Headline Desk" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. dated tag, typed headline and detail, rising portrait, rule plus masthead, marker highlights, on vignetted grid parchment.

A story-intro card on aged grid paper. A date tag, a two-line headline and a detail paragraph appear by typing, a cut-out portrait rises from the bottom-right corner, a rule draws and a masthead line types beside it, then a marker highlight sweeps over the headline and over one phrase of the detail text.
**The graphic in one line:** dated tag, typed headline and detail, rising portrait, rule plus masthead, marker highlights, on vignetted grid parchment.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Date tag text (REQUIRED, text, ≤ 14 chars, 1 line): <your value>
P2 · Headline (REQUIRED, text, ≤ 70 chars, 2 lines (auto-fit to 70%)): <your value>
P3 · Detail text (REQUIRED, text, ≤ 170 chars, 2 lines (auto-fit to 70%)): <your value>
P4 · Masthead line (REQUIRED, text, ≤ 22 chars, 1 line): <your value>
P5 · Portrait image (REQUIRED, image, transparent cut-out preferred, ≥ 700 px tall, scaled to box height): <your value>
P6 · Detail highlight phrase (optional, text, must lie inside one line of P3; default: auto (words from the start of line 1 after its first 6 words, about 40 chars)): <your value or NONE>
P7 · Tag colour (optional, hex; default: #D01010): <your value or NONE>
P8 · Highlight colour (optional, hex; default: #F6C500): <your value or NONE>
P9 · Text colour (optional, hex, dark; default: #141210): <your value or NONE>
P10 · Paper colour (optional, hex, mid-light; default: #C2A878): <your value or NONE>
P11 · Grid (optional, on / off; default: on): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Date: the date in the user's story; else today's date in "Mon 00, 0000" form.
- Headline: the strongest one-sentence claim; detail: one or two supporting sentences; masthead: the user's own brand, show or channel name.
- Portrait: user photo of the subject, ideally already cut out; for an opaque photo, feather the left and top edges over 80 px so it blends into the paper.
- Colours: P7 and P8 may come from brand colours; keep contrast with the paper and text.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Paper centre colour P10. Mottling: four noise octaves (scales 240, 90, 30, 8 px; weights 0.5, 0.3, 0.18, 0.08), amplitude ±4.5 percent, plus soft darker stains (5 percent).
- Grid: pitch 72 px, 2 px lines at x offset 2, y offset 40, darkening the paper by 17 percent, blur 0.9 px. P11 turns it off.
- Vignette multiplies everything (portrait included): m = 1 - 0.55 × clamp((r - 0.15) / 0.85)^1.5, r = distance from centre over corner distance.
- Flicker: brightness × (1 + 0.018 sin(5.1 t) + 0.012 sin(11.7 t + 1)). Grain: gaussian, sigma 2.2 levels, new every frame.
- Left margin 90 px.
## 3. Elements
### E1 · Date tag
Rubik Regular 38 px, white, letter-spacing 3.5 px. Rect x 90, y 175, height 94, width = text width + 52, colour P7, edge blur 0.7 px. Text left padding 26.
### E2 · Headline
Rubik Bold (wght 700), colour P9, 60 px, line pitch 81 px, left x 90, line centres y 336 and 417. Wrap width 1340. Shrinks to 70 percent if it needs more than 2 lines.
### E3 · Detail text
Rubik Regular 29 px, P9, line pitch 40, line centres y 499 and 539. Wrap width 1230. First line indented 40 px, second line at x 90.
### E4 · Portrait
Box 676×784 at the bottom-right corner (x 1244–1920, y 296–1080). Image scaled to height 784 (never stretched), right-aligned, cut at the box edges. Converted to black and white (contrast 1.1). Vignette applies.
### E5 · Rule and masthead
Rule: 4 px, colour P9, y 701–705, x 109 to 659. Masthead: blackletter (UnifrakturCook Bold), 58 px, left x 685, centre y 705, colour P9; shrinks down to 40 px so its width stays ≤ 540 px.
### E6 · Headline highlight
Per line: rough marker bar, colour P8, from text start - 10 to text end + 10, height 1.08 × font size, centred on the line. Top and bottom edges wobble (smooth noise, ±3.2 px), edges blurred 1.6 px, 93 percent opacity, drawn under the text. Colour is toned by the paper brightness underneath.
### E7 · Detail highlight
Same bar style, x from the phrase start - 4 to end + 4, height 1.25 × detail font size, behind line 1 text.
## 4. Camera
None. The canvas is fixed; only the vignette flicker and grain change.
## 5. Timeline (beats)
### B1 · Tag — 0.25–0.6 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.25–0.6 | E1 | alpha 0→1, y +14→0 | | out cubic |
### B2 · Headline typing — 0.4–2.55 s
| 0.40 + k × (1.95/(n-1)) | E2 | word k fades in over 0.22 s, n = word count | | linear |
### B3 · Detail typing — 2.0–4.4 s
| 2.0–4.4 | E3 | letters appear evenly, each fades over 0.08 s | | linear |
### B4 · Portrait rise — 2.1–3.3 s
| 2.1–3.3 | E4 | y offset 794 → 0 (rises from below the canvas) | | out cubic |
### B5 · Rule and masthead — 3.6–5.3 s
| 3.6–4.6 | E5 rule | length 0 → 100% left to right | | in-out cubic |
| 4.1–5.3 | E5 masthead | letters fade in left to right, 0.18 s each | | linear |
### B6 · Headline highlight — 5.55–6.65 s
| 5.55–6.10 | E6 line 1 | wipe left to right | | in-out cubic |
| 6.05–6.60 | E6 line 2 | wipe left to right | | in-out cubic |
### B7 · Detail highlight — 7.45–8.3 s
| 7.45–8.3 | E7 | wipe left to right | | in-out cubic |
### B8 · Hold — 8.3–13 s
Only flicker and grain move.
## 8. Never
- A distorted portrait.
- Text running under the portrait or over the rule.
- Reference words, pictures or a real publication name as defaults.
- Highlight over the wrong words, or in front of the text.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 13 s (reference 1280×720; multiply reference pixels by 1.5). Keep the motion, timing and order of beats of section 4.
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
