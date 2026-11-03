# Google Flow prompt · Highlight Snippet Flicker
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 9:16 · 1080×1920 · 30 fps · 2.3 s (69 frames; reference 540×960, multiply by 2)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Highlight Snippet Flicker" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. one marker-highlighted keyword stays put while nine different article snippets flick past at about 10 steps per second, with streaked edges and blurred lower text.

A rapid flip-through of nine text snippets that all share one highlighted keyword. Each snippet is a cropped piece of an article page on crumpled paper. The keyword sits in a marker highlight at the same screen spot in every snippet, while the words around it, the page furniture and the blur change every few frames. The loop runs 2.3 times and stops mid-flip. It shows how widely one term appears.
**The graphic in one line:** one marker-highlighted keyword stays put while nine different article snippets flick past at about 10 steps per second, with streaked edges and blurred lower text.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Keyword (REQUIRED, text, ≤ 14 chars, 1 line (auto-fit to 70%)): <your value>
P2 · Snippet 1 (REQUIRED, 3 texts: lead ≤ 28, tail ≤ 24, aside ≤ 24 chars): <your value>
P3 · Snippet 2 (REQUIRED, as P2): <your value>
P4 · Snippet 3 (REQUIRED, as P2): <your value>
P5 · Snippet 4 (REQUIRED, as P2): <your value>
P6 · Snippet 5 (REQUIRED, as P2): <your value>
P7 · Snippet 6 (REQUIRED, as P2): <your value>
P8 · Snippet 7 (REQUIRED, as P2): <your value>
P9 · Snippet 8 (REQUIRED, as P2): <your value>
P10 · Snippet 9 (REQUIRED, as P2): <your value>
P11 · Page title (optional, text, ≤ 18 chars; default: the keyword): <your value or NONE>
P12 · Byline name (optional, text, ≤ 20 chars; default: Staff writer): <your value or NONE>
P13 · Sub-line (optional, text, ≤ 40 chars; default: none): <your value or NONE>
P14 · Tags (optional, up to 3 words, ≤ 12 chars each; default: News, Features, Nature): <your value or NONE>
P15 · Highlight colour (optional, hex; default: #D9E23C): <your value or NONE>
P16 · Paper colour (optional, hex, light; default: #ECECE8): <your value or NONE>
P17 · Ink colour (optional, hex, dark; default: #18181A): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Keyword: the term the user wants repeated (product, topic, name).
- Snippets: sentences from the user's script or notes that contain the keyword; cut each at the keyword into lead (text before) and tail (text after), and take a few following words as the aside. Write nothing the user did not supply.
- Highlight colour: may come from a brand colour; keep dark ink readable on it.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Paper #ECECE8, static crumpled texture: low-frequency shading (±1.2 percent), two crease scales (darkening up to 1.1 percent), fine grain ±1.4 levels. Nothing on the paper moves.
- A faint grey panel (alpha 6 percent) from y 0.52 to 0.66 H and a hairline at y 0.495 H, both vertically blurred, on every snippet.
- No camera. No vignette.
## 3. Elements
Sizes in 1080×1920 px.
### E1 · Keyword highlight
Marker box behind the keyword, colour P15, alpha 0.92, padding 0.16 em each side, from 0.80 em above to 0.62 em below the line centre. Keyword in ink, DM Sans (weight 500 to 700). Its centre x is set per snippet (table in section 5). Lead text is right-aligned to the box minus 0.26 em, tail left-aligned from the box plus 0.26 em. Lead and tail run off the canvas edges (cropped). Keyword size 84 px, shrinks until its width ≤ 0.62 W, floor 70%.
### E2 · Snippet line
The line holding E1, centre y 0.36 to 0.38 H, in the layout of the snippet (section 5). Fonts: DM Sans 600 (headline layouts), DM Sans 500 (single line), Gelasio 400 at 0.62 size (article layout).
### E3 · Page furniture
Tag row (DM Sans 25 px, grey #6E6E70) at y 0.293 H, x 40. Sub-line DM Sans 27 px grey at y 0.455 H. "Sign in" text, "Subscribe" pill (#2846BE, white label) and "Member-only" note in the top-right layout. Fixed labels: Sign in, Subscribe, Member-only, Follow, min read.
### E4 · Article header (article layout only)
Page title in Barlow Condensed Bold 120 px at y 0.012 H, vertical blur 16 px, alpha 0.85. Sub-line below. Round avatar 104 px with the byline initials, byline name (DM Sans 600 32 px), "3 min read", a Follow label in a pink-red accent, and a small reaction count chip.
### E5 · Body text
Five or six lines of Gelasio (30 px, or 0.52 × key size in the article layout), grey ink alpha 0.5 to 0.8, built by chaining all snippets with the keyword, starting at a different offset per snippet, first line cropped at the left edge. Vertical box blur grows per line: start 5 to 6 px, plus 3 px per line.
### E6 · Edge smear
Applied to the finished snippet. Horizontal box blur (110 px then 55 px) mixed in by weight w(x): left (0.15 − x/W)/0.15, right (x/W − 0.84)/0.16, clamped, power 0.8, ×0.95. The centre 0.15 to 0.84 W stays sharp.
## 4. Camera
None. Fixed frame.
## 5. Timeline (beats)
Each snippet holds still (no motion inside a hold). A loop is 30 frames (1.0 s) and shows the nine snippets in order.
### B1 · Flip loop — 0–2.3 s
Snippet start frames inside each 30-frame loop: S1 0, S2 4, S3 8, S4 11, S5 14, S6 18, S7 21, S8 24, S9 27. Frame f shows the snippet whose start is the largest ≤ f mod 30. The video ends on frame 68 (S3 of the third loop).
| Snippet | Layout | Keyword centre x |
|---|---|---|
| S1 | headline: tags, bold line with keyword, aside as second line, sub-line, body | 0.50 W |
| S2 | article: blurred title, byline, serif line with keyword, body | 0.46 W |
| S3 | single line, quote chip bottom with small keyword highlight, body | 0.50 W |
| S4 | bold analysis: two tags, bold line, aside second line, sub-line, body | 0.50 W |
| S5 | headline (as S1) | 0.50 W |
| S6 | subscribe layout: Sign in, Subscribe pill, keyword near the right, small keyword chip with aside, body | 0.64 W |
| S7 | single line (as S3) | 0.50 W |
| S8 | article (as S2) | 0.46 W |
| S9 | bold analysis (as S4) | 0.48 W |
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| each hold start | whole snippet | hard cut, no fade, no slide | previous → next | none |
| 0–2.3 | paper | static | | |
## 8. Never
- Fading, sliding or easing between snippets (they cut).
- The keyword moving off its highlight or changing spelling.
- Text with real brand, league or publication names the user did not give.
- Sharp text at the extreme left and right edges (they stay smeared).
- A different number of snippets.

## 5. OUTPUT
- One video, format 9:16 · 1080×1920 · 30 fps · 2.3 s (69 frames; reference 540×960, multiply by 2). Keep the motion, timing and order of beats of section 4.
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
