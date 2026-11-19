# Google Flow prompt · Scrubline Clip Card
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 30 fps · 3.5 s (reference 720×1280; units below are reference px of the unscaled card scene; section 4 gives the layout scale for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Scrubline Clip Card" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. clip card with panel, counting timecode and a playhead that reveals a timeline, then a checklist that ticks.

A short editor-UI explainer on a light page. A rounded card shows a chat-style panel over the clip, a timecode below it and a timeline panel under that. A playhead sweeps the timeline while the timecode counts, revealing filmstrip, overlay snapshots and a waveform. The chat panel swaps for a checklist whose boxes tick off one by one.
**The graphic in one line:** clip card with panel, counting timecode and a playhead that reveals a timeline, then a checklist that ticks.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Clip (REQUIRED, image or video, any aspect, cover-fit, ≥ 720 px wide): <your value>
P2 · Title lead (REQUIRED, text, ≤ 10 chars): <your value>
P3 · Title bold (REQUIRED, text, ≤ 22 chars): <your value>
P4 · Row names (5) (REQUIRED, 5 texts, ≤ 14 chars each): <your value>
P5 · Row roles (5) (REQUIRED, 5 texts, ≤ 20 chars each): <your value>
P6 · Row reasons (5) (REQUIRED, 5 texts, ≤ 24 chars each): <your value>
P7 · Window title (REQUIRED, text, ≤ 16 chars): <your value>
P8 · Prompt message (REQUIRED, text, ≤ 70 chars (clipped to one line)): <your value>
P9 · Result line (REQUIRED, text, ≤ 34 chars): <your value>
P10 · Pasted message (REQUIRED, text, ≤ 170 chars, wraps to 4 lines): <your value>
P11 · Column headers (optional, 3 texts, ≤ 16 chars; default: ITEM / ROLE / REASON): <your value or NONE>
P12 · Composer hint (optional, text, ≤ 16 chars; default: Type a message): <your value or NONE>
P13 · Footer labels (optional, 3 texts, ≤ 8 chars; default: Auto / Model / Std): <your value or NONE>
P14 · Playhead colour (optional, hex; default: #E34554): <your value or NONE>
P15 · Waveform colour (optional, hex; default: #3C9C6A): <your value or NONE>
P16 · Page colour (optional, hex, light; default: #E8E4DC): <your value or NONE>
P17 · Timeline length (s) (optional, 30–120, multiple of 10; default: 60): <your value or NONE>
P18 · Focal point (optional, fractions; default: auto (face, else centre)): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Clip: a still or clip from the user's video (clear subject).
- Title, rows, window texts: from the user's script or workflow; rows are three-part facts (what, role, why).
- Colours: P14 from a brand colour; P15 should contrast with the white timeline.
- Focal point: detect a face, else the user's hint, else centre.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Page #E8E4DC, faint radial lightening to +(3,5,5) around (300,520) (radius 520 x, 700 y), grain ±1 level.
## 3. Elements
Units are reference px of the settled, unzoomed card scene. Centre line x=360.
### E1 · Card and title
Card x 200–520, y 104–672, radius 22, page gradient #E9E8E0 to #E0DFD4 with a soft inner glow, 2 px white edge, shadow (blur 14, dy 8, 22%). Top part y 104–388 is the page, bottom y 388–672 the clip (E8). Title baseline y 129.6, centred x 358: lead Inter 400 10.4 px #6E6D68, bold Inter 700 10.4 px #181816, tracking −0.1.
### E2 · Checklist
Header row baseline y 153.8, Inter 600 6.2 px #C4C3BE tracking 0.5, columns x 214, 320.9, 400.8. Rows centres y = 178.3 + 37.55·i. Icon tile 18×18 radius 4.5 at x 223.5 (letter tile in a palette colour, or the user's icon), name Inter 700 9.2 px #161614 at x 239.8, role Inter 500 7.2 px #343432 at x 320.9, reason Inter 400 6.1 px #807F7A at x 400.8. Checkbox 14×14 radius 3.5 at x 499 (empty: #EEEDE6 with #CECDC6 border; ticked: #1E1E1D with white tick).
### E3 · Chat window
Window x 218–502, y 140–373, radius 9, #F1F0E9, hairline border, tiny shadow. Traffic lights at y 148.5 x 227.5, 235.1, 242.7 (r 2.6). Title Inter 550 6.2 px at x 288. Prompt bubble x 277–491, y 168–195, #E8E7DC, text grey #A09E96 clipped, "Show more" Inter 650 5.8 px. Result line baseline y 224, x 230. Composer empty: x 231–490, y 319–351, radius 7, hint Inter 6.3 px #A8A69E. Composer pasted: x 228–492, y 279–351, 0.9 px #3A3936 outline, text Inter 6.5 px #1E1E1C, line height 12.4, first baseline y 298. Footer baseline y 361.
### E4 · Key chip
Dark pill 32×18 (#2C2B29, radius 5) centred (465,251), white command key plus V.
### E5 · Card clip
x 200–520, y 388–672, cover-fit, bottom corners radius 22, slow push 1.00→1.05 with 3 px leftward drift over the scene.
### E6 · Timecode and playhead
Timecode: IBM Plex Mono Medium 26 px #111, x 206, centre y 708, format hh:mm:ss:ff at 30 ff. Total: IBM Plex Mono 15.5 px #807E78 "/ 00:01:00:00" at x 392. Playhead: 2 px line y 747–914 plus 10×9 pentagon head at the panel top, colour P14, x from 90.5 to 628.6.
### E7 · Timeline panel
Panel x 60–660, y 747–920, radius 12, #FBFBFB, shadow (blur 10, dy 5, 16%). Ruler band y 747–775 #F4F4F3 with hairline. Ticks every second (minor y 768.5–775 #B9B9B9, major every 10 s y 762–775 #5A5A5A), labels IBM Plex Mono 8.6 px #6E6E6C centred on majors at y 760; the label under the playhead turns bold black. x(s) = 91.4 + s·(537.6/length). Row labels V2 (y 792.5), V1 (838), A1 (883) Inter 650 8.6 px #8A8A88 at x 74.
### E8 · Timeline content
Revealed only left of the playhead. V1 filmstrip x 91–629, y 826–865, radius 5, thumbs 22 wide cover-crops of the clip with varying zoom 1.0–1.36. A1 band y 872–908 radius 4, tint of the wave colour; bars 2.4 wide, pitch 4.8, height 5–31 (seeded smooth random), colour P15. V2 snapshot clips (y 781–819, radius 6, 21×38 snapshots): x 109 (2, panel+clip, opacity 1), 253 (3→2, list,.85), 307 (3, panel+clip), 476 (3, list,.55), 584 (2, list,.35).
## 4. Camera and layout
The page is rendered in the reference layout, then re-laid out for the phone canvas. Output 1080×1920 = reference ×1.5 at base. Step 1: the card block (everything above y 688) scales ×1.35 about the page centre line, its top lands at y 132 and its bottom at y 899; the timecode and timeline block shifts down by 227 so the group (y 132–1147) is vertically centred. Step 2: the whole group scales about (360,640) by 1.018·(1 + 0.048·smoothstep(f/71)), f = frame (zoom ends at 2.37 s, then holds 1.066). At the end the timeline panel is 960 px wide in the output (60 px margins) and the card is about 690 px wide.
## 5. Timeline (beats)
Clip starts at reference frame 22 of the measured scene (the first 21 frames of the reference belong to a different graphic and are not used). Times below are in output seconds from 0.
### B1 · Card settle — 0–0.20 s
Static card, empty timeline, playhead at 90.5, timecode 00:00:00:00. The zoom runs from 0 s.
### B2 · Paste — 0.30–0.93 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.30–0.37 | E7 | opacity, scale | 0 → 1, 0.75 → 1 | smoothstep |
| 0.34 | E6 | composer | empty → pasted (hard swap) | cut |
| 0.77–0.93 | E7 | opacity | 1 → 0 | smoothstep |
### B3 · Scrub — 0.20–0.93 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.20–0.93 | E9 | playhead x | 90.5 → 628.6 | smootherstep |
| 0.20–0.93 | E9 | timecode | 0 → full length, ff at 30 | follows playhead |
| 0.20–0.93 | E11 | reveal | columns left of playhead | follows playhead |
| 0.93 | E9 | timecode | locks to the total | cut |
### B4 · Panel swap — 0.92–1.07 s
Window crossfades to the checklist over 0.92–1.07 s (smootherstep). Rows fade in staggered 0.8 frame each from 0.97 s (3.5 frame fade); headers fade over 1.00–1.40 s.
### B5 · Ticks — 1.70–3.5 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 1.70 | E5 box 1 | tick | scale 0.5 → 1.15 → 1 over 0.17 s | smoothstep |
| 2.10 | E5 box 2 | tick | same | |
| 2.50 | E5 box 3 | tick | same | |
| 1.70–3.5 | all | hold, card keeps pushing in | | |
## 8. Never
Never show the reference's words or pictures; never stretch images; never let text overflow its box; never reveal timeline content right of the playhead; never change the number of rows (5) or ticks (3); never add elements.

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 30 fps · 3.5 s (reference 720×1280; units below are reference px of the unscaled card scene; section 4 gives the layout scale for output). Keep the motion, timing and order of beats of section 4.
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
