# Google Flow prompt · Flare Sweep Title
**Type:** motion graphic (animated, generated from your content)  ·  **Format:** 16:9 · 1920×1080 · 30 fps · 4.33 s (reference 1280×720; world values in 1280 px units, multiply by 1.5 for output)  ·  **Source:** your text, script or images

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
Create the animated graphic "Flare Sweep Title" exactly as designed in section 4, using the content from the INPUTS block. Nothing is edited from existing footage: you build the whole graphic. a heavy headline types on with a glowing smear and sunburst flare, holds crisp, flares again and fades out.

A single bold headline on a dark stage. The letters type on one by one, centred as they grow. A smear and a glow follow the newest letter, and a sunburst flare with dark spokes flashes at the leading edge. The smear relaxes, the crisp headline holds, then the smear and flare return at the middle of the text and the headline fades away.
**The graphic in one line:** a heavy headline types on with a glowing smear and sunburst flare, holds crisp, flares again and fades out.

## 2. INPUTS (fill in before pasting)
Values written as text appear on screen exactly as typed (same spelling, same capitals). Images you upload in Flow are used where the design calls for pictures; if a picture is not provided, draw a clean simple illustration in the same visual style instead (no photographs of real people, no logos).
P1 · Headline text (REQUIRED, text, ≤ 12 chars, 1 line, set in capitals (auto-fit down to 70%)): <your value>
P2 · Text colour (optional, hex, bright; default: #FCFD00): <your value or NONE>
P3 · Hot tint (optional, hex; default: #FF9A00): <your value or NONE>
P4 · Stage tone (optional, 2 hex, dark; default: #232120 centre, #121113 edge): <your value or NONE>
P5 · Sunburst rays (optional, on / off; default: on): <your value or NONE>
P6 · Exit flare and fade (optional, on / off; default: on): <your value or NONE>
P7 · Stage rings (optional, on / off; default: on): <your value or NONE>

## 3. HOW TO USE THE INPUTS
- Follow the design strictly: use every REQUIRED value exactly as given, in the place the design assigns to it. Use the stated default for any optional field you leave as NONE.
- If you only have a script or notes and no ready values, turn them into the fields yourself with these rules (then use them exactly as in the line above):
- Headline: the shortest strong phrase of the user's topic (a title, a product name, a hook).
- Text colour: a brand colour; keep it bright on the dark stage. Hot tint: a hue about 40 to 60 degrees away from it.
- No captions, no narration text and no extra words besides the supplied content. This graphic has no spoken audio: do not generate a voice. A soft sound that fits the motion is allowed; no music with lyrics.
- If a text is longer than its limit, shorten it yourself and keep its meaning.

## 4. THE DESIGN (follow it strictly)
## 1. Canvas
- Dark stage. Radial tone lookup from the centre, in 1280 px units: r 0 to 60 = 35, r 140 = 33, r 220 = 31, r 300 = 28, r 440 = 24, r 520 = 23, r 540 and beyond = 20 (grey levels, slightly warm: R 0.95, G 0.91, B 0.90 of the grey). The lookup is blurred with sigma 6 px. This gives two faint concentric discs (edges at about r 290 and r 530) and a darker rim.
- No grid, no grain. Nothing else on the canvas.
## 3. Elements
### E1 · Headline
Rubik (variable), weight 900, capitals. Size: cap height 147 px at 1920 (font size 210, cap 98 at 1280), tracking -0.02 em, word space 1.5 × the font's space. Centred at x 960, cap-centre y 537 (358 at 1280). Measured full width of a 9-char text about 1200 px (800 at 1280). Auto-fit: width ≤ 1440 px; shrink to 70% (font size 147) at most.
Each letter is a mask; letters have colour P2, blended to P3 while new (see B1).
### E2 · Smear and glow
Built from the visible headline: a leftward one-sided horizontal smear (exponential tail), a gaussian glow, and a radial streak blur around the pivot. All scale with the intensity curve I(t) in section 5.
### E3 · Sunburst
Dark wedges cut through the lit text around the pivot: 12 spokes at angles (deg) -100, -84, -66, -38, -8, 14, 62, 82, 98, 118, 150, -150, half-widths 1.2 to 2.6 deg, strength 0.9 × I, falling off with exp(-r/220 px). Off when P5 is off.
### E3b · Flare core
Additive, at the pivot, strength min(1, 1.2 × I): white core exp(-(r/34 px)^2); halo exp(-r/120 px) × 0.55 in P3; 12 bright rays (same angles as E3, half-widths 1.1 to 2.0 deg) of length about 220 px (1.5 × cap height), colour 0.6 × P3 + 0.4 white, amplitude 0.9. Letters near the pivot are tinted toward P3 with weight min(1, 1.3 × I) × exp(-|x - pivot x|/130 px). Dark wedges (E3) strength is 0.5 × I.
### E4 · Pivot
The flare point. During the type-on it is the right edge of the newest letter. From 0.7 to 1.3 s it glides (smoothstep) to 51% of the text width from its left edge, and stays there.
## 4. Camera
None. Static frame.
## 5. Timeline (beats)
Intensity I(t): intro I = smoothstep(0.10, 0.90, t) × (1 - smoothstep(0.90, 1.85, t)); exit I = 0.85 × smoothstep(2.6, 3.3, t); I = max of the two.
### B1 · Type-on — 0.10–0.66 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.10 + k × 0.56/(n-1) | E1 letter k (non-space) | alpha 0 → 1 over 0.05 s | | linear  |
| same | E1 letter k | colour P3 → P2 | decay exp(-t/0.13) | |
| 0.13 on | E1 | visible letters centred at x = 960 - 277 × exp(-(t-0.13)/0.19) px | | |
### B2 · Flare peak — 0.66–0.9 s
Pivot at the right end, I rises to 1. Smear tail length (half-res px) 30 + 110 × I, glow sigma 5 + 5 × I (half-res), mix 0.45 × I of smeared into crisp text.
### B3 · Relax — 0.9–1.85 s
I falls to 0. The pivot glides to mid text. Letters become crisp.
### B4 · Hold — 1.85–2.6 s
Crisp text, no effects.
### B5 · Exit flare — 2.6–3.35 s
I rises to 0.85, pivot at mid text. Same effect recipe as B2.
### B6 · Fade out — 3.35–4.33 s
| 3.35–3.55 | E1 | alpha 1 → 0.25 (dim ghost) | smoothstep | |
| 3.55–3.85 | E1 | alpha 0.25 → 0 | smoothstep | |
| 3.35–3.70 | E1 | x squeeze to 88% about the pivot | smoothstep | |
| 3.85–4.33 | | empty stage | | |
## 8. Never
- Text clipped, off-centre or in lower case.
- Stepped ghost copies in the smear.
- Effects on during the hold.
- More than one line of text.
- Reference content (its words) as a default.

## 5. OUTPUT
- One video, format 16:9 · 1920×1080 · 30 fps · 4.33 s (reference 1280×720; world values in 1280 px units, multiply by 1.5 for output). Keep the motion, timing and order of beats of section 4.
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
