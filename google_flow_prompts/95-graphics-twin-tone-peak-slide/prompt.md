# Google Flow prompt · Twin-Tone Peak Slide
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 30 fps · 4.0 s (reference 720×1280; all values below are in 720×1280 px, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Twin-Tone Peak Slide" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. a glass orb and dome, a one-colour area chart climbing to a peak, a marker line, a second-colour fall, and a two-word label.

A black-stage data explainer for one rise-and-fall story. A glass orb sits on a gradient dome and slides in from the left. A glowing area chart climbs in a zigzag to a single peak. A thin white marker drops from the peak. The chart and the orb then slide past each other in opposite directions, the area right of the marker fills in a second colour as it falls away, and a two-word label rises into place above the peak.
**The graphic in one line:** a glass orb and dome, a one-colour area chart climbing to a peak, a marker line, a second-colour fall, and a two-word label.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Label (REQUIRED, text, 1 or 2 words, ≤ 16 chars, 1 line (auto-fit down to 70%)): <your value>
P2 · Rise colour (optional, hex, bright; default: #12D63A): <your value or NONE>
P3 · Fall colour (optional, hex, bright; default: #FF0A14): <your value or NONE>
P4 · Icon colour (optional, hex; default: #8173EF): <your value or NONE>
P5 · Marker colour (optional, hex; default: #FFFFFF): <your value or NONE>
P6 · Background colour (optional, hex, dark; default: #000000): <your value or NONE>
P7 · Label colour (optional, hex; default: same as P3): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Label: the name of the peak or turning point in the user's story (a date, an event, a record).
- Colours: P2 and P3 should read as "up" and "down" (for example brand colours or a good and a bad signal). Keep P2 and P3 in different hue families.
- P4 may come from a brand colour; the orb rim uses a lighter tint of it.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Background #000000, flat. No grid, grain or vignette.
- Everything is light on black: layers are added together, with the chart punching through the icon (chart alpha = chart brightness^0.8).
- Safe area: label stays inside x 46–530; the orb may leave the frame on the right.
## 3. Elements
### E1 · Dome
Half circle, radius 345, centre (hc, 854), only the upper half drawn (top y 509). Colour blends from P4 on the left to a neutral grey (#B4AAB0) on the right (smoothstep over x/r from -0.1 to 0.9). Brightness = (1 - (y-509)/330)^1.6, so it fades to black by y 840.
### E2 · Glass orb
Circle radius 150, centre (hc, 347). Interior black. Rim from radius 0.55r to r: alpha 0.15 rising to 1 (power 1.4). Rim colour runs from grey (#96968E) at the top to P4 lightened 50 percent at the bottom (smoothstep on y/r from -0.8 to 0.5). A 1.5 px bright edge. A soft white glint (gaussian 26×13, 45 percent) at (hc-55, 287).
### E3 · Rise area
Polyline relative to the peak (dx, dy, y down): (-1000,780), (-760,709), (-561,565), (-431,536), (-328,378), (-213,419), (-40,78), (0,0). Peak P0 at screen y 414. Area under the line, colour P2, intensity (1 - d/300)^1.3 where d is the vertical distance below the line. 2.5 px line in P2 lightened 25 percent on top.
### E4 · Marker line
Vertical line at the peak x, 3.5 px wide, colour P5, from y 412 to the bottom of the frame.
### E5 · Fall area
Polyline relative to the peak: (0,0), (188,306), (332,349), (380,534), (524,606), (700,700). Same fill rule as E3 with colour P3 and fade length 190. Same line style.
### E6 · Label
Barlow Medium, size 84, colour P7. Words are left aligned from x 46 on baseline y 310, 22 px between words. Word 2 starts at the end of word 1 plus 22. Auto-fit: total width ≤ 480, shrink to 70 percent. A single word uses only the first slot.
## 4. Camera
No camera. The two layers move on their own, in screen space.
| t (s) | Icon centre hc | Chart peak x (pk) | ease |
|---|---|---|---|
| 0 | -10 | 760 | |
| 0.13 | 91 | 760 | ease-out |
| 0.27 | 166 | 760 | ease-out |
| 0.40 | 187 | 760 | ease-out |
| 0.53 | 193 | 760 | slow drift |
| 0.93 | 236 | 760 | linear |
| 1.10 | 233 | 760 | hold |
| 1.20 | 233 | 676 | ease-in |
| 1.33 | 233 | 514 | |
| 1.47 | 298 | 334 | |
| 1.60 | 448 | 232 | |
| 1.73 | 606 | 197 | ease-out |
| 1.87 | 690 | 196 | |
| 2.33 | 705 | 196 | hold to end |
Linear interpolation between the measured frame samples (every 4 frames), smoothed with a gaussian of 1 frame. Motion blur: when either layer moves more than 14 px per frame, average 5 sub-frames over a 0.5-frame shutter.
## 5. Timeline (beats)
### B1 · Icon slide-in — 0–0.93 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–0.53 | E1, E2 | x | -10 → 193 | ease-out |
| 0.53–0.93 | E1, E2 | x | 193 → 236 | linear |

### B2 · Rise draws — 0.2–1.13 s
A hard vertical edge reveals E3 left to right.
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.20 | E3 | reveal front x | -20 | start |
| 0.27 | E3 | reveal front x | 103 | |
| 0.40 | E3 | reveal front x | 431 | |
| 0.53 | E3 | reveal front x | 612 | |
| 0.67 | E3 | reveal front x | 680 | |
| 0.80 | E3 | reveal front x | 724 | |
| 1.07 | E3 | reveal front x | 740 | |
| 1.13 | E3 | reveal front x | 800 (fully shown) | |

### B3 · Marker drops — 1.07–1.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.07–1.20 | E4 | bottom end y | 412 → 1280 | smoothstep  |

### B4 · Slide past — 1.1–1.87 s
Chart moves left, icon moves right (table in section 4). Chart peak ends at x 196, orb centre at x 705 (only its left part stays in frame).

### B5 · Fall fills — 1.35–2.15 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.35–2.15 | E5 | reveal bottom y | 405 → 1045 | linear  |

The edge is a 1 px soft horizontal wipe moving down.

### B6 · Label rises — 1.85–3.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.85 | E6 word 1 | alpha, y offset | 0, +124 → | alpha = 1 - e^(-9 (t-1.85)); offset = 46·e^(-4.5 (t-2.07)) |
| 2.03 | E6 word 2 | alpha, y offset | 0, +120 → | alpha = 1 - e^(-7 (t-2.03)); offset = 116·e^(-3.6 (t-2.0)) |
| 3.0 | E6 | settled | 0 offset, alpha 1 | |

### B7 · Hold — 3.0–4.0 s
Nothing moves.
## 8. Never
- Never change the beat order or the opposite-direction slide.
- Never let the label overlap the orb (width ≤ 480).
- Never add axes, numbers, gridlines, faces or people.
- Never use the same hue for the rise and fall areas.

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 30 fps · 4.0 s (reference 720×1280; all values below are in 720×1280 px, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
