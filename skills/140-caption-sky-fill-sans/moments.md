# moments.md — Sky Fill Sans: Style Bible + Moment Library

This file is the single source of truth for the Sky Fill Sans caption style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel of one talking head; everything marked "(design, not measured)" is tuned on a 720x1280, 24 fps demo clip. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while each phrase becomes a few small bold white sans words fading in around one giant heavy sans keyword whose letters are filled with a soft cloud-and-sky texture, sitting across the chest, or in a top or low lane when the middle is busy.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, lane, texture colours…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text**, filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Texture, measured default | sky blue #5FA3D6 through pale #EAF1F8 with white cloud wisps (measured: photographic sky seen through the letters) | Fill of the keyword |
| Texture, demo recolour | top #FFC454 amber, middle #FF4870 coral-pink, bottom #8C0A8C violet, white wisps #FFFAF5 in the upper half, 30 % violet wisps in the lower half | Fill of the keyword (design, not measured) |
| Helper words | #FFFFFF | Small words |
| Shadow | #000000 at 85 % blurred 8 px (keyword); stacked 90 / 100 / 80 % (small words) | Keeps text readable on bright footage (design, not measured) |

Brand-swap rule: the texture palette is a parameter ✎. Any three-stop vertical gradient (light top, saturated middle, deep bottom) with white wisps works. Keep it saturated enough to read on the shot. White helper words and shadows never change.

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, boxes, bars, borders, blur plates or colour overlays. Text only, plus soft shadow.

### 1.3 Layouts / lanes

| Lane | Keyword baseline y | Small words | Use |
|---|---|---|---|
| Mid (signature, measured: the reference keyword sits across the chest) | 0.575H; helper top ≥ 0.41H so nothing touches the face | one line above (baseline = keyword cap top − 0.032H), optional line below at baseline + 0.062H | Speaker shots whose face ends above 0.40H |
| Top | 0.215H (design) | one line above | B-roll with a clear top fifth |
| Low | 0.80H (design) | one line above, optional line below | B-roll or shots with action in the middle |

All lanes centre on x = 0.50W. Side margin ≥ 0.05W on every text box. Text top ≥ 0.02H, bottom ≤ 0.97H. The reference puts the keyword over the mouth; this skill never does: the face box (x 0.34–0.66, y 0.15–0.40) stays clear.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Extra-heavy geometric sans, tight tracking, mixed case as written, letters filled with the sky texture | Poppins ExtraBold | Montserrat Black, Archivo Black | font size 150 px at 720 wide, shrunk so the word is ≤ 0.88W wide; Top lane ≤ 140 px (cap height ≈ 0.075H at 150) |
| Small words | Bold sans, mixed case, white, centred | Poppins Bold | Montserrat Bold, Inter Bold | 46 px at 720 wide (about 0.064W); line ≤ 0.90W |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Small word | fade 0 → 100 % over 0.20 s, ease-out cubic, at its spoken time; the whole line is laid out first so no word moves |
| Keyword | fade 0 → 100 % over 0.30 s plus rise from 0.02H below its rest position, ease-out cubic, at its spoken time |
| Texture | drifts 34 px/s sideways inside the letters, capped at 40 px total (reference: the sky pattern shifts slowly through the letters) |
| Exit | whole chunk fades out over 0.14 s |
| Never | bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, boxes, outlines, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: text and shadow overlays only. Forbidden: any colour change, blur, dimming, zoom, crop change, background swap, retime, reorder, person cut-out. The footage plays live and in sync. (The reference dims the footage under its opening title; this skill does not.)

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head; shot-specific on others) never receives visible text. Assert the text bbox against it per speaker shot.
- All text boxes inside 0.05W side margins.
- Two chunks are never visible on the same frame (windows disjoint, assert in the build). A chunk never runs across a cut.
- Helper line and keyword keep ≥ 0.012H between them.

---

## PART 2 — MOMENT LIBRARY

Family codes: C caption, K keyword, T title, E end. Energy: low / medium / high.

### K1 · MID SKY KEYWORD — K medium (signature, measured)
**What it is:** one giant sky-filled keyword across the chest with small white words above (and optionally below).
**Use when:** speaker shot whose face ends above 0.40H and the phrase has one strong word. **Avoid when:** hands or a phone sit at 0.45–0.70H and the text would hide the subject's action (use K2 or K3).
**Text (✎):** 1 keyword (≤ 10 characters ideal, as written), 0–4 small words above, 0–2 below.
**Geometry:** lane Mid (1.3); keyword 1.4; texture 1.1.
**Motion:** small words per 1.5; keyword fade + rise 0.30 s at its spoken time; texture drift; exit fade 0.14 s. Chunk visible 0.7–1.6 s.
**Footage behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** fade.
**Build notes:** glyph mask drawn at 2x, downscaled; fill = texture crop × mask; shadow layer under it; fixed seed per chunk.
**Flow prompt text:** "Across the speaker's chest, one very large heavy sans word '{{KEYWORD}}' whose letters are filled with a soft {{TEXTURE}} cloud-and-sky pattern fades in, with small bold white words '{{HELPERS}}' fading in one by one around it."
**Still-image state:** keyword fully in, helper words complete.

### K2 · LOW SKY KEYWORD — K medium (design, not measured)
**What it is:** the K1 layout in the lower lane. **Use when:** the middle holds action, or a speaker has a clear chest area below 0.70H. **Avoid when:** a face sits in the lower half.
**Geometry:** lane Low. **Motion/Exit:** as K1.
**Flow prompt text:** "In the lower part of the frame, small bold white words '{{ABOVE}}' fade in above one giant {{TEXTURE}} cloud-and-sky filled sans word '{{KEYWORD}}'."

### K3 · TOP SKY KEYWORD — K medium (design, not measured)
**What it is:** the K1 layout near the top, on B-roll with a clear top fifth.
**Geometry:** lane Top. **Motion/Exit:** as K1. **Avoid when:** a face or the main subject is in the top fifth.
**Flow prompt text:** "Near the top of the frame, small bold white words '{{HELPERS}}' fade in above one large {{TEXTURE}} cloud-and-sky filled sans word '{{KEYWORD}}'."

### C1 · WHISPER LINE — C low (measured)
**What it is:** the small white line alone, building word by word, no keyword. **Use when:** a phrase has no strong word, or between keyword chunks.
**Geometry:** 1.4 small words, centred, at the Top lane or the Mid helper line. **Motion:** 1.5. Chunk 3–6 words.
**Flow prompt text:** "A small bold white line '{{LINE}}' fades in word by word near the top of the frame."

### C2 · SOLO KEYWORD — K high (design, not measured)
**What it is:** only the giant keyword, no small words, for a punchline word. **Use when:** payoff or a number. **Limit:** ≤ 1 per 6 s.
**Geometry:** any keyword lane. **Motion/Exit:** as K1, keyword time = chunk start.
**Flow prompt text:** "One giant {{TEXTURE}} cloud-and-sky filled sans word '{{KEYWORD}}' fades in with a small rise and fades out."

### T1 · STACKED OPENER — T high (design, not measured; the reference opens with a stacked two-line title)
**What it is:** two short title lines in the sky-filled sans, stacked, in the Top lane above the face, as the first chunk. Footage is not dimmed.
**Use when:** the video opens on a speaker and the first words are a hook. **Avoid when:** the face box would be touched: lines must end above 0.15H or sit in the Low lane.
**Text (✎):** 2 lines of 1–2 words each, ≤ 0.88W wide, font 120 px, line gap 0.012H. Counts as the first caption chunk.
**Motion/Exit:** as K1, second line starts at its spoken word.
**Flow prompt text:** "At the very top of the frame, two short lines '{{LINE1}}' and '{{LINE2}}' in large {{TEXTURE}} cloud-and-sky filled sans fade in one after the other."

### E1 · CLOSING KEYWORD — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 or K3, held 0.4 s past the last spoken word (never past the end of the shot).
**Flow prompt text:** "For the last line the keyword '{{KEYWORD}}' fades in large, filled with the {{TEXTURE}} cloud-and-sky pattern, and stays until the speech ends."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | K1 | K3 / K2 on B-roll, K1 on any speaker | E1 (K1) |
| Single talking head | T1 or K1 | K1, C1, K2 (alternate lanes) | E1 |
| B-roll only | K3 | K2, C2 | E1 (K3) |
| Still image | K3 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Keyword 150 px (Top lane 140, width-capped at 0.88W), small words 46 px, gap above 0.032H, below +0.062H, shadow 85 % blur 8 offset 6, texture drift 34 px/s cap 40 px, fade-out 0.14 s. Chunks: 0.10–1.02 K1 (money, Mid), 1.10–1.80 K2 (more., Low), 2.10–3.17 K3 (yourself, Top), 3.25–4.88 K2 (investments,, Low), 4.95–6.55 K1 (left., Mid), 6.90–8.30 K3 (year, Top), 8.45–9.55 E1/K1 (happens., Mid). Demo texture: amber #FFC454 → coral #FF4870 → violet #8C0A8C.
