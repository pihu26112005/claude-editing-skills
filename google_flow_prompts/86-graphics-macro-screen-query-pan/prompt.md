# Google Flow prompt · Macro Screen Query Pan
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 29.97 fps · 7.0 s (reference 1280×720; all world units below are reference pixels at zoom 1, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Macro Screen Query Pan" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. query typed into a pill search bar on a macro pixel-grid screen, slow zoom-in, hold, motion-blurred pan to the magnifier, cursor arrives.

A generic search page filmed from very close on a pixel-grid monitor. A rounded search bar sits under a one-word title. The camera zooms in while a query types into the bar, holds, pans quickly along the bar to its magnifier icon, rests, and a cursor glides to the icon. It communicates "a question is being asked" and reveals a topic as a search query.
**The graphic in one line:** query typed into a pill search bar on a macro pixel-grid screen, slow zoom-in, hold, motion-blurred pan to the magnifier, cursor arrives.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Query text (REQUIRED, text, ≤ 32 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Title word (optional, text, ≤ 8 chars, 1 line, never a real search engine name; default: Search): <your value or NONE>
P3 · Title colour (optional, hex, single flat colour; default: #34495E (design)): <your value or NONE>
P4 · Ink colour (optional, hex, dark; default: #151515): <your value or NONE>
P5 · Screen tone (optional, hex, mid to light; default: #B2B1B3): <your value or NONE>
P6 · Pixel-grid strength (optional, 0 to 150%; default: 100%): <your value or NONE>
P7 · Cursor (optional, on / off; default: on): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Query text: the topic, question or keyword in the user's script, as a short search phrase.
- Title word: a neutral label for the page; take the user's channel or section word if given and not a real search engine name.
- Colours: P3 may come from a brand colour; P4 must contrast strongly with P5.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Flat screen tone P5. No vignette.
- Screen overlay, fixed in screen space (never moves with the camera): pixel cell 8.9 units square (13.35 px at 1920). Inside each cell: a bright row band centred at v=0.79 (gaussian sigma 0.14), a green dot at u=0.28 and a magenta dot (red plus blue) at u=0.78, dot sigma 0.10. Row multiplier 0.90 to 1.07, dot adds about (-16,+34,-16) green and (+30,-20,+30) magenta at full strength. Overlay strength scales with P6. The add is weighted by local brightness (0.35 plus 0.65 of lum/178).
- Colour fringe: red channel shifted 2 px left, blue 2 px right at 1920. Soft blur sigma 0.7 px. Gaussian grain sigma 2 levels.
## 3. Elements
World units, 1280×720 frame at zoom 1.
### E1 · Title word
Outfit SemiBold (wght 600), colour P3, nominal size 141 (cap height about 99), baseline y=357, centred on x=642.5. Auto-fit: width ≤ 400, shrink to 60%. A short word may leave no fragment at the top-left at the end.
### E2 · Search bar
Rounded rectangle (pill), centre line x 165.8 to 1119.7, y 390.8 to 456.2 (height 65.4, radius 32.7), stroke 1.7 in P4, no fill.
### E3 · Query text
Inter (opsz 14, wght 450), size 28 (cap height about 20), colour P4, left edge x=195, baseline y=432.6. Width ≤ 500, shrink to 70%. Types on one character at a time. Caret: 1.5 wide, y 410.5 to 436, colour P4, 1.6 units after the last character.
### E4 · Magnifier icon
Ring centre (1084.5, 421.5), outer radius 10, stroke 2.6; handle from the ring at 45 degrees, 8 long, stroke 3.2 with round end. Colour P4.
### E5 · Cursor
Arrow pointer, tip at its origin, 12.3 wide by 19.8 tall, white fill (92 percent), outline 1.5 in P4. Hidden when P7 is off.
## 4. Camera
Screen = 1.5 × (640 + zoom × (world - centre)), same for y with 360.
| t (s) | centre x | centre y | zoom | ease |
|---|---|---|---|---|
| 0–0.17 | 640 | 360 | 1.00 | hold |
| 0.17→2.0 | 640→379 | 360→418 | 1.00→1.912 | monotone cubic through measured knots: zoom (t:z) 0.33:1.03, 0.5:1.074, 0.67:1.162, 0.83:1.309, 1.0:1.529, 1.17:1.706, 1.33:1.794, 1.5:1.853, 1.67:1.897, 1.84:1.912; centre progress (t:p) 0.33:.06, 0.5:.13, 0.67:.28, 0.83:.475, 1.0:.70, 1.17:.845, 1.33:.918, 1.5:.96, 1.67:.98, 1.84:1.0 |
| 2.0–4.0 | 379 | 418 | 1.912 | hold |
| 4.0→5.28 | 379→1042 | 418→419.25 | 1.912→2.706 | monotone cubic through e: 4.17:.11, 4.34:.26, 4.5:.46, 4.67:.68, 4.84:.83, 5.01:.94, 5.15:.985, 5.28:1 |
| 5.28–7.0 | 1042 | 419.25 | 2.706 | hold |
Motion blur: sub-frame average. For each frame use shutter 0.7 frame. Pixels moved d = largest screen displacement of three probe points over the shutter. N = clamp(ceil(d / 5), 1, 24) sub-frames averaged in float32. When d exceeds 100 px, add a horizontal box blur of length min(0.3 d, 60) px.
## 5. Timeline (beats)
### B1 · Zoom-in and typing — 0–2.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.17–2.0 | camera | zoom and centre | see section 4 | measured |
| 0.10–1.90 | E3 | characters shown | 0 → all, evenly (rate adapts to length) | linear  |
| 0.10–2.0 | caret | visible, solid while typing | on | none |
### B2 · Hold with blinking caret — 2.0–4.0 s
| 2.0–4.0 | caret | blink, period 1.06 s, on first | | step  |
### B3 · Pan to the icon — 4.0–5.28 s
| 4.0–5.28 | camera | pan and zoom to the bar's right end | | measured knots |
| 4.0–5.28 | motion blur | as section 4 | | |
Text slides out left; the title slides out left and only a letter fragment may remain at the top-left.
### B4 · Rest — 5.28–5.92 s
Camera still. Nothing moves.
### B5 · Cursor glide — 5.92–6.5 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 5.92–6.0 | E5 | alpha | 0 → 1 at world (840,534) | linear |
| 5.98–6.5 | E5 | tip position | (840,534) → (1083,427) | out quad |
### B6 · Rest — 6.5–7.0 s
Cursor tip rests on the icon. Nothing moves.
## 8. Never
- A real search engine's name, logo, wordmark colours or branded layout.
- Overlay that moves with the camera.
- Query text running past the bar or under the icon.
- A different order of beats.
- Reference content (its words) as defaults.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 29.97 fps · 7.0 s (reference 1280×720; all world units below are reference pixels at zoom 1, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
