# Google Flow prompt · Thread Word Relay
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 1:1 · 1080×1080 · 30 fps · 4.8 s (reference 250×250, 30 fps, 4.8 s; all fractions below are of W and H, multiply by 1080)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Thread Word Relay" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. a fixed post slot cycles through many different users' posts of the same word, crossfading, one word after another.

A square, generic social-thread card. A sentence is spoken one word at a time. For each word the card flickers rapidly through several different invented posters who all wrote that same word, so the word stays locked in place while avatar, handle, age and likes change around it. Faded posts above and below drift with the flicker. After the last word the card holds.
**The graphic in one line:** a fixed post slot cycles through many different users' posts of the same word, crossfading, one word after another.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Words (REQUIRED, list of exactly 6 words (a sentence split in order), each ≤ 10 chars): <your value>
P2 · Handles (optional, list of ≥ 8 invented handles, ≤ 14 chars each; default: 15 neutral generated handles (@user_01 …)): <your value or NONE>
P3 · Avatars (optional, any number of square images, circle-cropped, or auto; default: procedural generated avatars): <your value or NONE>
P4 · Neighbour lines (optional, ≥ 6 short sentences, ≤ 60 chars; default: grey skeleton bars): <your value or NONE>
P5 · Accent colour (optional, hex; default: #2F7BE0): <your value or NONE>
P6 · Background colour (optional, hex, light; default: #FAFAFA): <your value or NONE>
P7 · Text colour (optional, hex, dark; default: #0F0F0F): <your value or NONE>
P8 · Ages and like counts (optional, lists; default: generated mix (minutes to months, 12 to 12K)): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Words: split the user's sentence or slogan into 6 words, in order. If it has fewer or more, ask for a 6-word line.
- Handles and neighbour lines: take from a user list of names or sample comments; else defaults.
- Avatars: user photos or logos, circle-cropped around the focal point; else procedural.
- Accent colour: a brand colour with good contrast on the background.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Flat near-white background #FAFAFA. No grid, no vignette, no grain.
- No platform logos, names or UI chrome anywhere. The post UI is generic.
- Content is left-weighted and clips at the right edge.
## 3. Elements
Focal slot centre line y = 0.43 (avatar centre). All x are from the left edge.
### E1 · Slot
Fixed. Never moves while words change (the match cut). Everything below sits inside it.
### E2 · Avatar
Circle, diameter 0.176 (190 px), centre (0.20, 0.43). Changes with every flicker slot. Procedural default: gradient disc with a simple face, cat, robot or ghost figure. User images cover-fit.
### E3 · Handle and age
Handle at x 0.36, y 0.376 (centre 406 px), Inter SemiBold 54 px, colour P7. Age follows 22 px right, Inter 44 px, grey #828282.
### E4 · Word
x 0.36, y 0.50 (centre 540 px), Inter Bold 84 px, colour P7. Always the current word of P1; in non-final flicker slots the casing varies (as typed, lower, capitalised), in the last slot of each word it is exactly as the user typed it.
### E5 · Action row
y 0.64 (centre 691 px). Thumb-up outline icon at x 0.36 (52 px), like count at x 0.40, thumb-down icon at x 0.56, "Reply" at x 0.64. Inter Medium 44 px, grey #606060.
### E6 · Reply link
Present in about 55 percent of slots, y 0.705, a chevron and "N replies" at 44 px in the accent P5.
### E7 · Neighbour posts
Same layout, one above (centre y 467-520) and one below (467+520), blurred (gaussian 2.2 px), faded to 42 percent. Body lines at 50 px in place of the word. They change with the flicker slot like the focal post.
## 4. Camera
None. Static.
## 5. Timeline (beats)
Flicker slot length 0.15 s (4.5 frames). Each word owns 5 slots (0.75 s). 6 words × 0.75 s = 4.5 s, then 0.3 s hold on the last slot.
### B1–B6 · Word 1 to word 6 — 0.75 s each, starts at 0, 0.75, 1.5, 2.25, 3.0, 3.75 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| slot start + 0.00 to 0.55 × 0.15 | whole card | hold slot k | static | none |
| slot start + 0.55 × 0.15 to 0.15 | whole card | crossfade slot k to k+1 (all elements incl. avatar, neighbours) | 0 → 1 | smoothstep  |
| last slot of word | E4 | casing | exact user casing | none |
| across a word boundary | E4 | word | word n → word n+1 | same crossfade |
### B7 · Hold — 4.5–4.8 s
Last slot stays, no fade.
## 8. Never
- Never move the slot; only its content changes.
- Never show a real platform name, logo or colour scheme, or real people's names.
- Never use other words than P1 in the focal slot.
- Never use a different number of words.

## 5. OUTPUT
- One video, format 1:1 · 1080×1080 · 30 fps · 4.8 s (reference 250×250, 30 fps, 4.8 s; all fractions below are of W and H, multiply by 1080). Keep the motion, timing and order of beats of section 4.
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
