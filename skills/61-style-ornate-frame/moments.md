# moments.md — Ornate Frame: Style Bible + Moment Library

This file is the single source of truth for the Ornate Frame style. Part 1 is the style bible (palette, frame geometry, type, motion, footage rules, safe zones). Part 2 is the moment library. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. Source: one still image of a Victorian gothic floral poster (palette, ornament feel, arch window); all motion and timing are (design, not measured), tuned on a 720x1280, 24 fps, 10 s render.

**The look in one line:** the footage sits inside a pointed-arch window on warm ivory paper, framed by engraved gold rules, a beaded line and vine corners with oxblood rosettes, while black-lacquer plates carry gold and ivory serif type.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s). Values are for 720x1280 at 24 fps; at another size scale by W/720. Reference values for 1080x1920 are 1.5x.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Paper | #E9E2D0 | Page background (fibre noise, faint diamond lattice at 7 %, vignette to #B9A883 at the edges) |
| Gold ramp | #5E3F10 · #B9882E · #F6DE8C · #D2A445 · #7A5517 | All metal: rules, beads, scroll vines, medallion rings; banded diagonal gradient, period 240 px |
| Gold text ramp | #FFF4C0 → #E6BD58 → #A87822 | Title and emphasis words (vertical gradient) |
| Oxblood | #4A0810 · #9C1E2A · #C23A44 | Rosettes, jewels, numeral discs, ribbon |
| Leaf green | #223A2E · #4A6C56 · #6F8F72 | Vine leaves only |
| Lacquer plate | #332417 → #1B110B (top to bottom) | Title and caption plates |
| Ivory ink | #F3EAD2 | Caption text, numerals, ribbon text |
| Engraving dark | 40–60 % black multiply | Edge line, hatch lines, drop shadow #1E1206 at 45 % |

Brand-swap rule: replace Oxblood with the user's brand colour only if it is dark and saturated. Never change gold, ivory or the paper.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Window | Pointed-arch window, x 81–639, y 150–1126 [121–959, 225–1689]. Arch: cubic bezier from (81,340) via (81,232) and (236,214) to the apex (360,150), mirrored. Bottom corners rounded 16. Footage scale 0.775 of the full frame, centre (360,639). |
| Frame | Outer rectangle x 52–668, y 100–1156: 7 px gold rule, 2.2 px thin rule at 11 px inset. Beaded rule (2.5 px beads, pitch 10.5) 11.5 px outside the window outline. 5.5 px gold ring hugging the window. |
| Corner pieces | Four medallions at (84,132), (636,132), (84,1124), (636,1124): gold ring r 19–27 with 14 scallops, oxblood disc r 19.5 with engraved concentric arcs, gold 8-petal rosette boss. Top corners add two scroll arms and a vine that follows the arch 26 px outside it (curls every ~0.16 of its length, leaves in green, oxblood-and-gold buds). Bottom corners add one short arm. |
| Finial | Gold fleur-de-lis (46 px high) on the arch apex with two small curls. Gold lozenge jewels at the side centres (66,640), (654,640) and bottom centre (360,1141). |
| Plates | Notched-corner lacquer plates with a 2.4 px and a 1.1 px gold rule. Title plate 300x64 at (210,20). Caption plate 612x92 at (48,1160) (inner 600x80). |
| Header | Gold double rule with diamond caps, y 52, x 38–205 and 515–682. Centre piece (x 205–515): title plate, idle medallion or numeral medallion (r 31). |
| Crop | Never crop the footage except by the window. Non-9:16 sources: cover-fit into the 558x992 window, crop anchor ✎ = face box or main subject. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Header | 0.05, 0.015, 0.95, 0.075 | Title plate, medallions |
| Window | 0.113, 0.117, 0.887, 0.880 | Live footage |
| Caption plate | 0.083, 0.906, 0.917, 0.984 | Captions (text baseline centre y = 0.947H [1212]) |
| Ribbon lane | centre (0.50W, 0.81H) | K1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Small caps, gold gradient, 1x2 px dark engraved shadow | Cormorant SC SemiBold | Playfair Display SC, IM Fell English SC | 40 px [60], fits plate width 300 |
| Caption | Mixed case, ivory, dark shadow (1,2) at 70 % | Cormorant Garamond SemiBold (wght 600) | EB Garamond, Playfair Display | auto-fit 54 → 34 px so the chunk is ≤ 540 px wide |
| Emphasis word | Same as caption in the gold text ramp | Cormorant Garamond SemiBold | — | same |
| Ribbon / numeral | Small caps, ivory on oxblood | Cormorant SC SemiBold | as title | 46 px / 32 px |

Case: title and ribbon text render in small caps (the font does it), numerals are Roman (I, II, III) only for list counters. No uppercase conversion of the user's words in captions.

### 1.5 Motion language
- Easing: ease-out cubic for entrances (0.3–0.55 s), smoothstep for travel, no overshoot except the 14 % corner swell.
- Typical durations: word fade 0.14 s with 8 px rise; plate fade 0.35 s; frame draw-on 0.9 s.
- Footage motion: only the settle (F1) and a slow push (B1).
- Never: bounce, shake, glitch, spin of the footage, wipes over the footage, flashes, filters, tilt.

### 1.6 What may happen to the user's footage
Allowed: scale to 0.775 and clip to the window (F1); slow push-in up to 1.035 per shot, 1.06 on the last shot, reset at each cut (B1, E1); frame and plates drawn around and below it. Forbidden: any change inside the window (no grading, glow, glint or blur on the footage), speed changes, trimming, reordering, replacement, extra windows. The primary window always plays live footage in sync with the audio.

### 1.7 Safe zones
- Face box stays inside the window and away from the header and the caption plate. Nothing is ever placed over the window except the ribbon (K1), the glint (on gold only) and corner medallions.
- The arch clips the top corners of the footage (about 45 px at the shoulders); at F1 start the footage is full frame so the face is visible from frame 0.
- Footage text near the top corners may be clipped by the arch: prefer a lower crop anchor when the user's footage has titles there.

---

## PART 2 — MOMENT LIBRARY

Families: **F** frame · **T** title · **M** medallion · **C** caption · **K** keyword · **X** transition accent · **B** background/ambient · **E** end · **P** poster. Energy: low / mid / high. Signature moments are mandatory.

### F1 · FRAME SETTLE — F high (signature, design not measured)
**What it is:** the footage starts full frame, shrinks into the arch window while the ivory page appears and the gold frame is drawn around it.
**Use when:** always, at the start. **Avoid when:** never.
**Text (✎):** none.
**Geometry / Graphics:** window and frame per 1.2.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.0 | Footage | scale about (360,639) | 1.0 → 0.775 | ease-out cubic |
| 0.55–1.0 | Footage clip | rectangle → arch mask | 0 → 1 | smoothstep |
| 0.12–1.05 | Frame ring | drawn by an angle sweep from top centre both ways (0 → 1.12π) | hidden → drawn | smoothstep |
| 0.35–0.9 (+0.1 per corner) | Corner pieces | scale about the medallion, alpha | 0.55 → 1, 0 → 1 | ease-out cubic |
| 0.15–0.6 | Header rules | alpha | 0 → 1 | ease-out |
| 0.25–0.6 | Caption plate | alpha | 0 → 1 | ease-out |

**Footage / plate behaviour:** live, in sync, face visible from frame 0.
**Captions during it:** first chunk may start at 0.55 s (plate already ≥ 80 %).
**Exit:** none; the frame stays to the end.
**Build notes:** pre-render ornaments at 3x with Pillow (bezier tapered strokes, spiral vines, leaf polygons with vein lines, scalloped rings), shade through the gold ramp with diagonal bands, 3.6 px hatch lines at 22 % darker, 1 px dark edge and a 2 px top-left highlight, downscale with BOX. Draw-on = alpha multiplied by clip((θ − angle)/0.14).
**Flow prompt text:** "The video starts full screen, then smoothly shrinks into a tall pointed-arch window on warm ivory paper while a fine engraved gold frame with a dotted line, vine corners and deep red rosettes draws itself around it."
**Still-image state:** frame fully drawn, photo in the window.

### T1 · ENGRAVED TITLE — T mid (signature, design not measured)
**What it is:** a black-lacquer plate in the header unfolds and the title words appear in small-caps gold.
**Use when:** opening line, topic words. **Avoid when:** the first words are a long phrase (> 3 words).
**Text (✎):** the first 1–3 user words, exact case; they leave the caption stream (audit).
**Geometry:** plate 300x64 at (210,20); text 40 px centred.
**Motion:** plate scaleX 0.6 → 1 and alpha 0 → 1 over 0–0.4 s; each word fades in over 0.25 s at its speech start with a 7 px rise; whole title fades 1.62–1.86 s (before the first cut, never across a cut).
**Footage:** untouched. **Captions during it:** caption plate runs normally.
**Exit:** plate and words fade; the idle medallion fades in (T2).
**Build notes:** gold text = glyph mask filled with a vertical gradient + 1x2 px shadow.
**Flow prompt text:** "A small dark lacquered plate with a gold border opens at the top of the screen and the words {{TITLE}} appear on it in engraved golden small capitals."
**Still-image state:** plate with the title.

### T2 · HEADER CREST — T low (extension in the same grammar)
**What it is:** the resting header: gold double rules with diamond caps and a round medallion with a gold fleur-de-lis on a dark disc.
**Use when:** whenever no title or numeral is shown. **Text (✎):** none.
**Motion:** idle medallion alpha 0 → 1 over 0.24 s after the title leaves. **Exit:** flips out for numerals (M1).
**Flow prompt text:** "A gold double rule with small diamond ends runs across the top, with a round gold medallion holding a lily flower in the centre."

### M1 · NUMERAL MEDALLION — M mid (design, not measured)
**What it is:** the header medallion flips (scaleX 0 → 1, 0.3 s, ease-out) into an oxblood disc with an ivory Roman numeral and stays for the item.
**Use when:** list items, steps, numbered tips. **Avoid when:** fewer than 2 items.
**Text (✎):** I, II, III… (counters only), max 3 characters.
**Geometry:** ring r 31 with 16 scallops, disc r 25.5, numeral 32 px.
**Timing:** start at max(item start, previous cut + 0.12 s); hold until the item ends; the next numeral replaces it directly.
**Exit:** returns to the idle medallion (T2) with the same flip.
**Flow prompt text:** "The round medallion at the top turns over like a coin and shows a deep red disc with the numeral {{NUMERAL}} in ivory."

### C1 · PLATE CAPTION — C mid (signature, design not measured)
**What it is:** word-by-word captions on the lacquer plate under the window, ivory serif, one chunk at a time.
**Use when:** every spoken line. **Text (✎):** user words only, chunks of 1–4 words, one line, never ending on an article or preposition.
**Geometry:** centred at x = 0.5W, baseline centre y = 1212; max width 540 px; font auto-fit 54 → 34 px.
**Motion:** the chunk is laid out at its final position from the start; each word fades 0 → 1 over 0.14 s at its start with an 8 px rise (ease-out); chunk fades out over the last 0.1 s; the plate stays.
**Timing:** start = first word start; end = min(last word end + 0.1, next start − 0.05); min 0.4 s.
**Footage:** untouched. **Exit:** fade.
**Flow prompt text:** "The spoken words appear one by one in a soft ivory serif on a dark lacquered plate under the window, always centred."

### C2 · GILT EMPHASIS — C low (design, not measured)
**What it is:** one word of a chunk is set in the gold text ramp instead of ivory.
**Use when:** a contrast word, a payoff word, a key action. **Limits:** ≤ 1 word per chunk, ≤ 3 per video. **Text (✎):** one user word.
**Flow prompt text:** "One word in the line shines in engraved gold while the others stay ivory."

### K1 · SCROLL RIBBON — K mid (design, not measured)
**What it is:** an oxblood ribbon with folded swallow tails and gold edges unfurls across the lower window carrying a keyword or time phrase.
**Use when:** numbers, durations, amounts, one standout noun. **Avoid when:** a face sits low in the shot. **Text (✎):** 1–3 user words (they leave the caption stream), small caps.
**Geometry:** body 70 px high, width = text + 80, tails 70 px, folded tails darker with a 35 % shadow; centre (0.5W, 1040), gold 2.6 px outline and 1 px inner rule.
**Motion:** 0.3 s: scaleX 0.6 → 1, scaleY 0.5 → 1, alpha 0 → 1 (ease-out); hold; fade 0.2 s.
**Footage:** ribbon is the only element over the window.
**Flow prompt text:** "A deep red ribbon with gold edges and folded swallow tails unfurls across the lower part of the window and shows the words {{KEYWORD}} in ivory small capitals."

### X1 · GILT GLINT — X mid (signature, design not measured)
**What it is:** a soft diagonal light sweep that runs over the gold only (frame, corners, rules), 0.75 s, on a cut.
**Use when:** person to B-roll and B-roll to person cuts, and once near the end. **Limits:** ≤ 4 per video.
**Motion:** gaussian band (σ ≈ 70 px along x + 0.55y) travels from −150 to 1550 with smoothstep; adds warm white (255,236,170) at 90 % through the gold alpha only. The footage is never lit.
**Flow prompt text:** "A soft glint of light slides across the gold frame from the top left to the bottom right."

### X2 · CORNER BLOOM — X mid (design, not measured)
**What it is:** on a cut, the four corner pieces swell 1.0 → 1.14 → 1.0 around their medallions (0.55 s, sin curve) and a thin gold ring expands from the top medallions (r 30 → 64, alpha 200 → 0).
**Use when:** cuts between two B-roll shots. **Limits:** alternate with X1; ≤ 3 per video.
**Flow prompt text:** "The four vine corners gently swell for a moment and a thin gold ring spreads out from the top corners."

### B1 · WINDOW BREATHE — B low (design, not measured)
**What it is:** a slow push-in of the footage inside the window.
**Motion:** scale 1.0 → 1.035 over each shot (smoothstep), reset at each cut; centre fixed at the window centre. **Use when:** every shot longer than 1.2 s.
**Flow prompt text:** "Inside the window the picture drifts very slowly closer."

### E1 · SEAL CLOSER — E mid (design, not measured)
**What it is:** the last line: the header medallion pulses 1.0 → 1.2 → 1.0 (0.7 s), the footage push rises to 1.06, a final glint runs over the frame, and the last chunk uses C2.
**Use when:** payoff or call to action. **Text (✎):** last chunk, one emphasis word.
**Flow prompt text:** "For the last line the round medallion at the top swells once, a last glint runs over the frame and the final word glows gold."

### F2 · WIDE WINDOW — F low (extension in the same grammar)
**What it is:** for landscape or very busy footage, the window widens to x 40–680 (scale 0.89) with the arch flattened to a gentle ogee, plates unchanged.
**Use when:** 16:9 or 1:1 sources. **Avoid when:** 9:16 talking heads. Build: scale both mask and frame; keep the face box inside the clip.

### P1 · POSTER — P low (extension in the same grammar)
**What it is:** still mode. Photo in the window (cover-fit, anchor ✎), title plate with the user's headline, caption plate with a subline, all ornaments settled, no glint.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | F1 + T1 | C1 + B1, M1 on lists, X1/X2 on cuts, K1 on a number | E1 |
| Single talking head | F1 + T1 | C1, C2, one K1, one X1 every ~3 s | E1 |
| B-roll only | F1 + T2 | C1, X2 on cuts, B1 | E1 |
| Still image | P1 | none | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
