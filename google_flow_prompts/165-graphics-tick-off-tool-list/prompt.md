# Google Flow prompt · Tick-Off Tool List
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 30 fps · 6.7 s (reference: the list occupied the top 720×640 of a 720×1280 frame as three columns; this skill re-lays it for the full portrait frame, all values below are px at 1080×1920)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Tick-Off Tool List" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. five-row checklist on a warm light page; row checkboxes tick one by one.

A light, app-style checklist page. A two-tone title sits above a column-label line and five rows. Each row has an icon tile, a bold name and short description lines. The rows appear one after another, then a checkbox at the right of each row ticks in turn. It communicates a set of steps or tools being completed one by one.
**The graphic in one line:** five-row checklist on a warm light page; row checkboxes tick one by one.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Title prefix (REQUIRED, text, ≤ 10 chars, 1 line): <your value>
P2 · Title (REQUIRED, text, ≤ 24 chars, 1 line (auto-fit to 70%)): <your value>
P3 · Row names (REQUIRED, 5 texts, ≤ 14 chars each): <your value>
P4 · Role lines (REQUIRED, 5 texts, ≤ 28 chars each): <your value>
P5 · Reason lines (REQUIRED, 5 texts, ≤ 30 chars each): <your value>
P6 · Row icons (optional, 5 items: emoji, one letter or image (cover-fit, any aspect); default: neutral drawn glyph, else first letter): <your value or NONE>
P7 · Column labels (optional, 2 texts, ≤ 8 chars; default: ITEM / DONE): <your value or NONE>
P8 · Tick colour (optional, hex, dark; default: #222222): <your value or NONE>
P9 · Icon tile colours (optional, 5 hex pairs; default: a soft two-stop gradient per row): <your value or NONE>
P10 · Page tone (optional, hex, light; default: #ECEAE3): <your value or NONE>
P11 · Tick times (optional, 5 seconds values, increasing, ≤ 6.2; default: 1.55, 2.47, 3.27, 3.97, 4.77 s): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Title: the step or stage name in the user's script ("Step 2" plus the task).
- Rows: the five items in the user's list; name is the item, role is what it does, reason is why it is needed.
- Icons: user emoji, letters or images; otherwise draw a neutral glyph (never a brand logo).
- Tick colour: may come from a brand colour; keep strong contrast with white.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Page: radial tone, centre #ECEAE3, corners #E1DED5, vignette ramp from r=0.25 of the corner distance, power 1.4. Faint grain, sigma 0.8 levels.
- Safe margin 70 px left and right. Content block spans y 250 to 1750.
## 3. Elements
### E1 · Title
Centred at x=540, baseline y=330. Prefix in Inter 450 size 78, colour #7D7B76; title in Inter 800 size 78, tracking -2, colour #181818; gap 20. Auto-fit so the pair stays within 940 px wide.
### E2 · Column labels
Baseline y=468. Left label at x=70, right label right-aligned at x=1010. Inter 600 size 26, tracking 3, colour #96948D, uppercase.
### E3 · Icon tile
160 px rounded square (radius 34) at x=70, vertically centred in the row. Vertical gradient of two colours, soft shadow (blur 10, offset y 8, alpha 0.27 of warm black), white glyph about 95% of 160/100 units. Image or emoji icons are cover-fit inside the rounded tile.
### E4 · Row text
Row height 250, rows start y=500, pitch 250. Hairline separator at row bottom, x 70 to 1010, #D6D3CA, 1 px. Text x=265, max width 627. Name Inter 800 size 68, tracking -1.5, #181818, baseline row centre -20. Role Inter 500 size 42, #161616, baseline +36. Reason Inter 450 size 36, #8A8780, baseline +86. Each auto-fits down to 70%.
### E5 · Checkbox
88 px rounded square (radius 22), left edge x=922, centred vertically in the row. Empty: fill #F0EEE8, outline 3 px #CECBC2. Ticked: fill P8, white tick (points (-20,2), (-6,16), (21,-14) from the box centre, 8 px round stroke).
## 4. Camera
Whole frame scales about the centre from 1.00 to 1.02 over 0 to 6.7 s, linear, with a 8 px upward drift over the same time. The reference page itself was static, so keep the drift very small. Bicubic resample.
## 5. Timeline (beats)
### B1 · Title in — 0.00–0.45 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.00–0.45 | E1, E2 | opacity | 0 → 1 | ease-out cubic  |
### B2 · Rows rise — 0.15–1.15 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.15+0.09·i, 0.55 long | row i (E3, E4, E5 empty) | opacity | 0 → 1 | ease-out cubic  |
| same | row i | y offset | +26 px → 0 | ease-out cubic  |
### B3 · Ticks — P11 times, then hold to 6.7 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| T to T+0.14 | E5 fill | opacity | 0 → 1 | ease-out cubic  |
| T to T+0.28 | E5 box | scale | 0.8 → 1.0 with a 10% overshoot bump | sine bump  |
| T+0.08 to T+0.33 | E5 tick | path drawn | 0 → 100% | ease-out cubic  |
Ticks in the reference landed at 1.55, 2.47, 3.27, 3.97 and 4.77 s; the final tick is held about 1.9 s.
## 8. Never
Never use real brand logos, a different row count, text overlapping the checkbox or tile, ticks out of order, or the reference's words and icons.

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 30 fps · 6.7 s (reference: the list occupied the top 720×640 of a 720×1280 frame as three columns; this skill re-lays it for the full portrait frame, all values below are px at 1080×1920). Keep the motion, timing and order of beats of section 4.
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
