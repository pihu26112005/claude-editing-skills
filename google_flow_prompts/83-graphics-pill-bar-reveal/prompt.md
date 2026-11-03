# Google Flow prompt · Pill Bar Reveal
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 7.77 s (reference 1280×720; units below are 1280×720 px, multiply by 1.5)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Pill Bar Reveal" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. icon bubble rises, widens into a pill search bar, words fade in, bar swells and vanishes.

A round icon bubble rises from below on a soft gradient, stretches sideways into a pill-shaped search bar while its magnifier tilts upright, the user's text fades in word by word, the bar swells slightly, then shrinks and fades away to the empty gradient.
**The graphic in one line:** icon bubble rises, widens into a pill search bar, words fade in, bar swells and vanishes.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Main text (REQUIRED, text, ≤ 24 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Icon colour (optional, hex; default: #CDA8EA): <your value or NONE>
P3 · Pill colour (optional, hex, light; default: #F4EBF9): <your value or NONE>
P4 · Text colour (optional, hex, dark; default: #322C35): <your value or NONE>
P5 · Gradient inner colour (optional, hex; default: #D6B0ED): <your value or NONE>
P6 · Gradient outer colour (optional, hex; default: #F1E5FA): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Main text: the search phrase, topic or question from the user's script; 2 to 4 words suit the word-by-word fade.
- Colours: P2 may come from a brand colour; P5 and P6 a dark and light tint of it. Keep P4 strongly contrasting with P3. Never copy a real search brand's palette.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Radial gradient centred on the bottom-left corner. Colour = lerp(P5, P6, t), t = interp(d, [0,.49,.871, 1], [0,.38,.74, 1]) where d = distance from the bottom-left corner divided by the frame diagonal. Reference measured: P5 #D6B0ED, P6 #F1E5FA.
- Faint noise ±0.5 levels to avoid banding. No vignette, no shadow under the bar.
## 3. Elements
Centre C=(640,360) in reference units.
### E1 · Pill
Height 97 (144 px out), fully rounded, colour P3, centred on C. Starts as a circle of diameter 96. Final width W = max(522, textWidth + 218) units (text width 304 for a 14-char reference text); text width auto-fits to ≤ 467 units (700 px).
### E2 · Magnifier icon
Ring outer radius 23, stroke 4.2, centre 9.5 above the icon centre; handle from the ring edge to 39 below ring centre, round cap, same stroke. Colour P2. Icon centre x = pill left + 48, y = pill centre. Tilt about the icon centre.
### E3 · Text
Inter Medium (wght 500, opsz 14), 64 px out, colour P4, baseline 18.5 units (27.75 px) below pill centre, starting 89 units (133.5 px) right of pill left. Right padding 129 units. Clipped by the pill. Each word fades in separately.
## 4. Camera
None. Static.
## 5. Timeline (beats)
### B1 · Icon rises — 0.3–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.3–0.5 | E1/E2 | opacity | 0 → 1 | linear  |
| 0.3–1.2 | E1/E2 | y offset | +380 units → 0 | (1-u)^2 ease-out |
### B2 · Stretch into pill — 1.0–2.35 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.0–2.35 | E1 | width progress p | 0 → 1 (knots 1.1 .036, 1.3 .117, 1.5 .35, 1.6 .59, 1.7 .756, 1.8 .86, 2.0 .953, 2.2 .993) | S-curve, smoothed |
| 1.0–2.35 | E2 | tilt | -25° (handle down-left) → +25° (down-right), linear in p | |
### B3 · Words fade in — 2.0–3.3 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.0 / 2.25 / 2.55 | E3 words 1 / 2 / 3 | opacity | 0 → 1 over 0.25 / 0.30 / 0.50 s (further words start 2.75, 2.9, 0.4 s) | smoothstep |
### B4 · Hold — 3.3–4.3 s
Everything still.
### B5 · Swell — 4.3–4.95 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.3–4.95 | group | scale about C | 1 → 1.109 (4.5 1.025, 4.6 1.07, 4.8 1.10) | ease-out |
### B6 · Collapse — 4.95–5.7 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.95–5.7 | group | scale | 1.109 → 0.1 (5.2 1.03, 5.3 .92, 5.4 .65, 5.5 .38, 5.6 .19) | ease-in |
| 5.2–5.7 | group | opacity | 1 → 0 | |
### B7 · Empty hold — 5.7–7.77 s
Bare gradient.
## 8. Never
No real search-engine or brand logo, name or colours. Text never leaves the pill. No shadow, no extra elements. The pill never changes height.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 7.77 s (reference 1280×720; units below are 1280×720 px, multiply by 1.5). Keep the motion, timing and order of beats of section 4.
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
