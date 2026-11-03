# Google Flow prompt · Pinned Stamp Timeline
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 24 fps · 16.0 s (reference 720×1280 at 30 fps, scene part about 0 to 8 s; output is a 1.5× upscale of reference units)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Pinned Stamp Timeline" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. three dated picture stamps pinned on a scrolling paper ruler, counted gaps, a pull-back with a measuring bracket, a note card, and a horizontal ruler recap.

A paper-toned explainer that puts three dated events on one ruler and shows how far apart they are. A vertical ruler scrolls from event to event, each event lands as a torn-border picture stamp pinned to its date by a dashed leader, and tape labels count the years between events. The camera then pulls back to the whole ruler with a torn headline stack and a bracket measuring the gap, a dark note card lists the three events, and a closing horizontal ruler shows the three stamps with two gap brackets.
**The graphic in one line:** three dated picture stamps pinned on a scrolling paper ruler, counted gaps, a pull-back with a measuring bracket, a note card, and a horizontal ruler recap.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Opening chip text (REQUIRED, text, 1 or 2 lines, ≤ 16 chars per line): <your value>
P2 · Event 1 year (REQUIRED, integer (negative = BC), earliest): <your value>
P3 · Event 1 name (REQUIRED, text, ≤ 26 chars (shown upper-case on the sticker)): <your value>
P4 · Event 1 date tag (REQUIRED, text, ≤ 14 chars, e.g. "May 1952"): <your value>
P5 · Event 1 image (REQUIRED, image, any aspect, cover-fit, ≥ 400 px short side): <your value>
P6 · Event 2 year (REQUIRED, integer, later than P2): <your value>
P7 · Event 2 name (REQUIRED, text, ≤ 26 chars): <your value>
P8 · Event 2 date tag (REQUIRED, text, ≤ 14 chars): <your value>
P9 · Event 2 image (REQUIRED, image, cover-fit): <your value>
P10 · Event 3 year (REQUIRED, integer, later than P6): <your value>
P11 · Event 3 name (REQUIRED, text, ≤ 26 chars): <your value>
P12 · Event 3 date tag (REQUIRED, text, ≤ 14 chars): <your value>
P13 · Event 3 image (REQUIRED, image, cover-fit): <your value>
P14 · Headline lines (REQUIRED, 3 short texts: upper-case line ≤ 24 chars, upper-case tape line ≤ 18 chars, sentence-case line ≤ 30 chars): <your value>
P15 · Note card headline (REQUIRED, 2 texts, upper-case, ≤ 18 chars each): <your value>
P16 · Note card kicker (optional, text, ≤ 30 chars, upper-case; default: "NOTES"): <your value or NONE>
P17 · Closing chip text (optional, text, ≤ 22 chars, upper-case; default: "ON ONE LINE"): <your value or NONE>
P18 · Gap wording (optional, N is computed from the years; unit word may change (e.g. DAYS); default: "~N YEARS LATER" / "~N YEARS"): <your value or NONE>
P19 · Accent colour (optional, hex; default: #D7472B): <your value or NONE>
P20 · Tape colour (optional, hex, light enough for dark text; default: #E3C121): <your value or NONE>
P21 · Paper colour (optional, hex, light; default: #DDD3C4): <your value or NONE>
P22 · Dark colour (optional, hex, dark; default: #253232): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Years and names come from the user's list of events. Order them by year; if unsorted, sort them.
- Date tags: the precise date in the user's words, else the year.
- Headline: compare the two gaps and state which is shorter (the demo style: "A flew closer to C than to B"). Split into the three lines.
- Images: user pictures; if none, make procedural stamp pictures (gradient sky plus simple shapes) in a palette unlike the accent.
- On a dark scene the accent is lightened 45 percent toward white (derived) so it stays visible.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Scenes 1 and 2: paper #DDD3C4 with a fixed dot grid, pitch 12 px, dot radius about 1.8 px, dots 11 levels darker; grain ±1.6 levels.
- Scenes 3 and 4: dark ground with the same dot grid. Default dark ground is #253232.
- Safe margin 52 px left and right. The dots do not move with the camera.
- Ink colour #1C1816. Shadows: soft, offset 6 to 12 px down, blur 7 to 14 px, 70 to 110 of 255 alpha.
## 3. Elements
Sizes in output px (1080×1920). Ruler centre x = 190.
### E1 · Opening chip
Black (#0A080A) rounded boxes (radius 16), one per line, centred, stepped like inline pills; white Poppins ExtraBold 62 px, line height 93. Centre x 540, y 250. Soft shadow.
### E2 · Vertical ruler
Torn-edge paper strip #E7DDCB, width 46, edges jittered ±2.6 px by a function of the year (so the tear scrolls with the dates). It spans (first year − 60) to (last year + 60). Ticks: minor every major/5, 2.4 px, 18 px long; major 3.2 px, 36 px, label right-aligned 44 px left of the strip, IBM Plex Mono Medium 26 px, ink. Major step is the smallest of 5, 10, 20, 25, 50, 100, 200, 250, 500, 1000, 2000 giving ≤ 9 labels in view.
### E3 · Event dot and leader
Dot radius 14 in the accent colour with a 3 px cream ring (#FAF7F0) on the ruler at x = 202. Dashed leader 5 px, dash 12, gap 9, from the dot to the sticker's left edge, left = 250 + 140k px, where k is the sticker scale.
### E4 · Sticker
Photo 440×420 (cover-fit, centre focus) with a torn white border (18 px, jitter 3.2, colour #FAF7F0) and tilt (−2.2°, +1.8°, −1.4°), centred vertically on the event's date. Below it, overlapping the photo's lower edge by 45 px, a black torn caption strip with the event name in Poppins ExtraBold 30 px white upper-case (tilt +1.6, −1.4, +1.2), and below that a tape tag in the tape colour (IBM Plex Mono 26, dark text, tilt −1, +1.4, −1.6) offset 35 px right of centre. Scale k = (s/9)^1.8 where s is the camera scale in px per year.
### E5 · Gap tape (scroll scenes)
Torn tape in the tape colour, Poppins ExtraBold 38 px, text "~N YEARS LATER" dark #24181E, tilt −1.5°, centre (540, 1560). N counts up from 0 to the gap as the camera travels.
### E6 · Headline stack
Three torn strips centred at x 540, y 205, 318, 428: black strip with white Poppins ExtraBold 46 (P14 line 1, tilt −2°), tape strip with dark text (line 2, tilt +1.2°), cream strip #F8F4EC with Playfair Display SemiBold 50 in ink (line 3, tilt −0.8°).
### E7 · Gap bracket (overview)
Vertical bracket at x = 610 in the accent colour, 7 px, ticks 26 px pointing left, between the dates of two neighbouring events (second one starts 14 px lower). Tape label "~N YEARS" at x 840, centred on the bracket, scale 0.9.
### E8 · Note card headline
Black strip with white text (line 1, tilt −1.6°) at y 270 and tape strip with dark text (line 2, tilt +1°) at y 385; Poppins ExtraBold 48.
### E9 · Note card
Torn paper #F3EEE2, 960×860, centre (540, 925), tilt 0.7°. Blue-grey rules every 52 px from y 150, accent margin line at x = 66, kicker in IBM Plex Mono 28 grey at (110, 50). Two translucent pink-tone tape strips (tape colour at 75 percent, ±27° tilt) at the top corners. Three rows at y 215, 425, 635 (card coordinates): 130 px stamp at left, event name in Playfair Display SemiBold 50 at x 330, date tag on tape (IBM Plex Mono 30) below it.
### E10 · Closing chip
As E1, one line, Poppins ExtraBold 46, centre (540, 300).
### E11 · Horizontal ruler
Torn strip #E7DDCB, x 52 to 1028, y 1020 to 1070. Span = first year − 18 to last year + 18. Ticks hang down from the top edge; labels below in IBM Plex Mono 24, cream. Event dots (lightened accent) on the ruler at y 1045.
### E12 · Recap stamps
160 px stamps (border 12) centred at y 790 above each date, dashed leader (lightened accent) from the stamp down to the dot.
### E13 · Recap brackets
Horizontal brackets at y 1170 under the ruler between neighbouring dates (inset 10 px at the shared date), lightened accent, 7 px, ticks 26 px down. Tape labels "~N YEARS" centred beneath at y 1250, scale 0.9.
## 4. Camera
Scroll scenes only. Screen y of a date = ycen + (year − cy) × s.
| t (s) | cy | s (px/yr) | ycen |
|---|---|---|---|
| 0.0–1.9 | year 1 | 9 | 940 |
| 1.9 → 3.5 | year 1 → year 2 | 9 | 940 (ease in-out) |
| 3.5–4.3 | year 2 | 9 | 940 |
| 4.3 → 5.5 | year 2 → year 3 | 9 | 940 (ease in-out) |
| 5.5–6.2 | year 3 | 9 | 940 |
| 6.2 → 7.4 | year 3 → middle of ruler span | 9 → 5 | 940 → 1140 (ease in-out) |
Motion blur: none.
## 5. Timeline (beats)
### B1 · Scroll and stamp — 0.0–6.2 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.10–0.55 | E1 | y offset, alpha | −70 px, 0 → 0, 1 | back |
| 0.5–0.9 | E4 #1, E3 | scale 1.3 → 1, alpha 0 → 1 | | back |
| 0.6–0.9 | E3 #1 leader | dash growth | 0 → 1 | linear |
| 1.5–1.85 | E5 | pop in, count shows 0 | | back |
| 1.9–3.5 | camera | event 1 → 2, E5 counts 0 → gap 1 | | in-out |
| 3.4–3.8 | E4 #2, E3 #2 | stamp as above | | back |
| 4.0 | E5 | swaps to gap 2 | | back |
| 4.3–5.5 | camera | event 2 → 3, E5 counts to gap 2 | | in-out |
| 5.3–5.7 | E4 #3, E3 #3 | stamp | | back |
| 6.2–6.5 | E1, E5 | fade out | 1 → 0 | in-out |
### B2 · Pull-back — 6.2–9.3 s
Camera zoom-out per section 4. E6 strips drop in at 7.0, 7.22, 7.44 (0.45 s each, back ease, 60 px). E7 bracket 1 draws 7.9–8.5, its label pops 8.4–8.8; bracket 2 draws 8.25–8.85, label 8.75–9.15. A dark panel wipes up from the bottom 9.3–9.7 (in-out, 3 px accent-tone edge line).
### B3 · Note card — 9.7–13.1 s
E8 strips drop in 9.9 and 10.1. E9 rises 260 px 10.3–11.0 (ease-out). Rows at 11.05, 11.55, 12.05: stamp pops (back, 0.4 s), name fades in 0.15 s later (0.4 s, 20 px slide), tag wipes in left to right 0.35 s later (0.35 s). Exit 12.6–13.1: card slides up 1500 px; E8 slides up 400 px and fades 12.6–13.0.
### B4 · Horizontal recap — 13.0–16.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 13.0–13.45 | E10 | y offset −50 → 0, alpha | | back |
| 13.2–14.0 | E11 | ruler draws left to right | 0 → 1 | in-out |
| 14.0, 14.35, 14.7 | E12 | stamp pops 0 → 1 (0.45 s), leader and dot draw | | back |
| 14.9–15.4 | E13 bracket 1 | draws left to right | 0 → 1 | in-out |
| 15.2–15.7 | E13 bracket 2 | draws | 0 → 1 | in-out |
| 15.35–15.7, 15.65–16.0 | tape labels | pop | | back |
Hold to 16.0 s.
## 8. Never
- Never show text the user did not supply (except computed gap numbers and defaults of P16–P18).
- Never let a sticker overlap another sticker's photo in the overview (spacing: shrink s only through the table above;
- Never stretch pictures. Never use a different number of events than three.

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 24 fps · 16.0 s (reference 720×1280 at 30 fps, scene part about 0 to 8 s; output is a 1.5× upscale of reference units). Keep the motion, timing and order of beats of section 4.
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
