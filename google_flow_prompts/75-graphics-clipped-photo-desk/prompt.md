# Google Flow prompt · Clipped Photo Desk
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 30 fps · 6.0 s (reference 720×1280; all world units below are in 720×1280 px, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Clipped Photo Desk" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. a photo clipped to a desk with a colour caption strip and a paper label, assembled by sliding props and a slow zoom-in, then two typed lines.

A desk-top title card. A dotted grey desk is seen from above. The camera eases in while pens, paper cards, a tape label, a colour caption strip, a metal paper clip and a tilted photo slide onto it. Two short texts then type on and the scene holds.
**The graphic in one line:** a photo clipped to a desk with a colour caption strip and a paper label, assembled by sliding props and a slow zoom-in, then two typed lines.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Strip text (REQUIRED, text, ≤ 18 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Label text (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit down to 70%)): <your value>
P3 · Photo (REQUIRED, image, any aspect, cover-fit, ≥ 1200 px wide): <your value>
P4 · Strip colour (optional, hex; default: #E8F000): <your value or NONE>
P5 · Card colour (optional, hex; default: #8E959E): <your value or NONE>
P6 · Pen colour (optional, hex; default: #C8102E): <your value or NONE>
P7 · Text colour (optional, hex, dark; default: #17161A): <your value or NONE>
P8 · Dot grid (optional, on / off; default: on): <your value or NONE>
P9 · Focal point (optional, point, fractions of the photo; default: auto (face, else centre)): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Strip text: the title or topic in the user's script, shortest strong phrase. Label text: a chapter, number or category word.
- Photo: a user photo or a still from a user video with a clear subject in the left half to centre (the strip covers the lowest 18 percent).
- Colours: P4 may come from a brand colour; keep strong contrast with P7. P5 and P6 may follow the brand palette.
- Focal point: detect a face (OpenCV or mediapipe); else the user's hint; else centre.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Desk: neutral grey, base level 182. Dot grid: dots radius 3.1 units, pitch 56 × 56 units, lattice offset (18,33), dot darkening 30 percent with a 0.6 px soft edge. The dots live in world space and scale with the camera.
- Vignette in screen space, multiplies everything (desk and props): V = (1 − 0.22 dx²)(1 − k dy²) with dx, dy from −1 to 1 about the centre, k = 0.50 above the centre and 0.68 below.
- Fine static grain, sigma 1.3 levels.
- No safe margin: props bleed off all edges.
## 3. Elements
World units, final settled view. Back to front: E1 desk, E2 ghost clip, E3 pens, E4 card A, E5 card B, E6 photo, E7 tape, E8 strip, E9 clip. Every prop has a baked soft drop shadow (offset about 8, 12 units, blur 7, opacity 0.5).
### E1 · Desk
Canvas section. Centre of the camera is fixed at (360,640).
### E2 · Ghost clip
Faint large clip outline, white, opacity 0.22, blurred 1.6 units, scale 1.55 (about 140 × 357 units), centre (650,1160), rotated 12° clockwise. Fades in 1.1–1.8 s.
### E3 · Pens
Black pen: capsule 380 × 38, near-black (#28282C), cylinder shading, two thin grey rings at 250 and 262, out of focus (blur 3.2 units), centre (60,40), rotated −45° (points up-right). Coloured pen (P6): capsule 460 × 46, cylinder shading, white ring 7 wide at 300, silver tip over the last 10 percent, centre (30,1190), rotated 59° (points down-right).
### E4 · Card A
Rect 300 × 380, colour P5, paper noise ±4 percent, dark thickness edge (colour × 0.42) offset +4,+4. Centre (675,110), rotated −1.5°. Runs off the top and right edges.
### E5 · Card B
Rect 540 × 340, colour P5, same texture, slight horizontal brightness gradient ±3 percent. Centre (390,752), rotated −5.5°. Mostly hidden under the photo.
### E6 · Photo
Rect 800 × 470 (aspect 1.70), cover-fit crop of P3 around P9, centre (386,614), rotated −6.3°. It bleeds off both sides. Hard edge, no border. Large soft shadow (9,14, blur 10, 0.55).
### E7 · Tape label
Rect 410 × 66, light grey #D4D4D6, fine noise, centre (95,775), rotated 65° clockwise (long axis runs down-right). Text P2 on it: Liberation Sans Bold (Arial Bold look) 36 units, colour #1A1A1C, left-aligned starting 190 units left of the tape centre, auto-fit max width 205 units (shrink to 70%), reading along the tape.
### E8 · Strip
Rect 520 × 110, colour P4, noise ±1.5 percent, gradient ±2.5 percent, centre (310,830), rotated −4°. Text P1: Liberation Sans Bold 64 units, colour P7, centred, auto-fit max width 400 units (shrink to 70%). The strip sits over the tape and the photo.
### E9 · Paper clip
Steel wire clip, 90 × 230 units, centre (75,820), rotated 27° clockwise. Wire path (clip-local units): (20,45)→(20,185); bottom arc centre (45,185) r25; →(70,35); top arc centre (52,35) r18; →(34,150); arc centre (45,150) r11; →(56,70). Stroke 8.2 dark #585A60, 6.0 light #C4C6CB, 2.0 highlight #FAFAFC offset (−1,−1), 1.2 shade #787A80 offset (1.4,1.4). It sits on top of everything and may cover the first letters of the label.
## 4. Camera
Pure zoom about the screen centre (no pan, no roll). Screen = 360 + Z × (world − 360) horizontally and 640 + Z × (world − 640) vertically, times 1.5 for output. Z is a monotone cubic (PCHIP) through:
| t (s) | Z | ease |
|---|---|---|
| 0 | 0.607 | start |
| 0.5 | 0.68 | smooth |
| 1.0 | 0.75 | smooth |
| 1.5 | 0.766 | near hold |
| 1.85 | 0.785 | |
| 2.0 | 0.83 | speeds up |
| 2.25 | 0.89 | |
| 2.5 | 0.94 | |
| 2.8 | 0.985 | |
| 3.1 | 1.0 | settle, then hold to 6.0 |
## 5. Timeline (beats)
All slide-ins use out-cubic ease on position and rotation from an offset to the final value (props start off-screen; offsets in world units).
### B1 · Empty desk and zoom — 0–1.0 s
Desk only; the camera zooms from 0.607 to 0.75.
### B2 · Pens — 0.25–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.25–0.95 | E3 black pen | offset | (−600,−600) → 0 | out cubic |
| 0.55–1.2 | E3 coloured pen | offset | (−600,+800) → 0 | out cubic |
| 1.1–1.8 | E2 ghost clip | opacity | 0 → 1 | linear |
### B3 · Cards and stack — 0.95–1.7 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.0–1.55 | E4 card A | offset | (+90,−700) → 0 | out cubic |
| 0.95–1.55 | E5 card B | offset, rotation | (−800,0), −6° → 0 | out cubic |
| 1.05–1.6 | E8 strip | offset, rotation | (−800,0), −5° → 0 | out cubic |
| 1.1–1.65 | E7 tape | offset, rotation | (−800,0), −6° → 0 | out cubic |
| 1.15–1.7 | E9 clip | offset, rotation | (−800,0), −8° → 0 | out cubic |
### B4 · Photo — 1.7–2.3 s
| 1.7–2.3 | E6 photo | offset, rotation | (+900,−40), +7° → 0 | out cubic |
| 1.85–3.1 | camera | zoom | 0.785 → 1.0 | see section 4 |
### B5 · Label types on — 2.95–3.6 s
Each letter: opacity 0 → 1 and blur sigma 8.4 → 0 units over 0.16 s (out cubic), stagger 0.04 s per letter, starting 2.95 s (design, matched to reference timing: label complete at about 3.5 s).
### B6 · Strip text types on — 3.85–4.5 s
Same letter effect, starting 3.85 s.
### B7 · Hold — 4.5–6.0 s
Nothing moves.
## 8. Never
- A stretched photo, or a photo whose main subject sits under the strip.
- Text leaving the strip or the label.
- Props visible before their slide starts.
- Reference content (its words or picture) as defaults.
- Camera pan or roll (the camera only zooms).

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 30 fps · 6.0 s (reference 720×1280; all world units below are in 720×1280 px, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
