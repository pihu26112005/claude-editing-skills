# Google Flow prompt · Tabletop Card Fan
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 10.1 s (reference 1280×720; all values are fractions or scene units, so they scale)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Tabletop Card Fan" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. one card becomes a fan of five on a table; a tilting, panning camera types three captions on the table surface.

A single card slides up onto an empty table, fans out into five cards, and the camera tilts down to a low table-level view. It tours the fan from left to right while a caption types onto the table under three of the cards, then settles on a wide shot of all three captions.
**The graphic in one line:** one card becomes a fan of five on a table; a tilting, panning camera types three captions on the table surface.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Caption 1 (REQUIRED, text, ≤ 16 chars, 1 line (auto-fit to 70%)): <your value>
P2 · Caption 2 (REQUIRED, text, ≤ 16 chars, 1 line (auto-fit to 70%)): <your value>
P3 · Caption 3 (REQUIRED, text, ≤ 16 chars, 1 line (auto-fit to 70%)): <your value>
P4 · Card-back artwork (optional, image, portrait 7:10, ≥ 700×1000 px, or "generated"; default: procedural ornament (book and wreath style, ink on cream)): <your value or NONE>
P5 · Card ink colour (optional, hex, dark; default: #3C280F): <your value or NONE>
P6 · Card edge colour (optional, hex, light; default: #EDD2B2): <your value or NONE>
P7 · Caption colour (optional, hex, dark; default: #5C4225): <your value or NONE>
P8 · Table colour (optional, hex, mid tone; default: #AA9F8B): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Captions: three short headings from the user's script or list, in reading order.
- Card colours: from a brand colour (ink) and its pale tint (edge). Caption colour may equal the ink or a mid tone of it; keep strong contrast with the table.
- Card back: a user image of a card back or pattern, cover-cropped to 7:10 with a rounded-corner mask; otherwise generate an ornament in the P5 and P6 colours.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Table: flat warm grey-beige #AA9F8B, no texture except the overlay below. The table is a real plane seen through a pinhole camera.
- Vignette (screen space): corners darken to 74 percent, starting at r=0.2 of the corner distance, power 1.3.
- Dot screen (screen space): square dot grid, pitch 6 px at 1080p (4 px at 720p), dots darken the surface by 13 percent. Faint noise grain, sigma 1.6 levels.
- Scene units: card width 0.70, card height 1.00, table x to the right, y away from the camera.
## 3. Elements
### E1 · Cards
Five cards of 0.70×1.00 units, corner radius 0.034, edge band 0.028, back artwork inside. Final pose (x, y, rotation in degrees, positive counter-clockwise):
| Card | x | y | rot | Draw order (final) |
|---|---|---|---|---|
| A | -0.90 | -0.05 | -10 | 1 |
| E | 0.90 | -0.05 | 10 | 2 |
| C | 0.00 | -0.10 | 0 | 3 |
| B | -0.40 | 0.00 | -5 | 4 |
| D | 0.40 | 0.00 | 5 | 5 |
Soft drop shadow: blurred copy offset (0.02, -0.03), 38 percent black. Each card is a texture warped onto the table plane by the camera.
### E2 · Camera
Pinhole, focal length 1500 px at 1080p. See section 4.
### E3 · Captions
Inter SemiBold (opsz 32, wght 600), colour P7, lying flat on the table at y = -0.74, centred at x = -0.90, 0.00, 0.90 (under cards A, C, E). Font size 0.13 units, auto-fit to max width 0.56 units. Appear per character: each character fades in over 0.16 s, 0.055 s apart. They are warped by the camera like the cards.
### E4 · Overlays
Vignette and dot screen of section 1, drawn after everything else.
## 4. Camera
Parameters: target (x, y) on the table, distance d, pitch (90 = straight down).
| t (s) | target x | target y | d | pitch | ease |
|---|---|---|---|---|---|
| 0–2.0 | 0.00 | -0.04 | 2.65 | 90 | hold |
| 2.9 | -0.60 | -0.30 | 1.55 | 36 | smoothstep (d in log space) |
| 4.7 | -0.55 | -0.30 | 1.55 | 36 | linear drift |
| 5.6 | 0.00 | -0.30 | 1.55 | 36 | smoothstep |
| 6.4 | 0.00 | -0.30 | 1.55 | 36 | hold |
| 7.6 | 0.00 | -0.20 | 2.60 | 32 | smoothstep |
| 10.1 | 0.00 | -0.20 | 2.60 | 32 | hold |
Motion blur: 3 sub-frames at ±0.005 s while the camera moves (speed > 0.03).
## 5. Timeline (beats)
### B1 · Empty table — 0–0.2 s
Table only.
### B2 · Card rises — 0.2–1.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.2–1.0 | Card C | y | -1.60 → -0.10 | ease-out cubic |
### B3 · Fan out — 1.0–1.95 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.0–1.95 | Cards A, B, D, E | x, y, rotation | card C pose → final pose | ease-out cubic |
| 1.5 | draw order | switch | C on top → C behind B and D | cut  |
### B4 · Tilt down — 2.0–2.9 s
Camera moves from top view to the first table view (section 4).
### B5 · Caption 1 — 3.0–4.7 s
Caption 1 types on from 3.0 s, then the view holds with a slow drift.
### B6 · Pan and caption 2 — 4.7–6.4 s
Camera pans to the centre; caption 2 types on from 4.95 s.
### B7 · Pull back and caption 3 — 6.4–7.6 s
Camera rises and widens to the final view; caption 3 types on from 6.9 s.
### B8 · Hold — 7.6–10.1 s
Static wide view.
## 8. Never
- Never mirror or distort the card artwork. Never add a fourth caption or a different card count.
- Never let two captions overlap or touch: each caption appears once, at its own x, with a gap of at least 0.25 units between neighbours, and the final view keeps all three fully inside the frame (shrink text or widen the camera distance instead).
- Never show text upright on screen; captions lie on the table.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 10.1 s (reference 1280×720; all values are fractions or scene units, so they scale). Keep the motion, timing and order of beats of section 4.
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
