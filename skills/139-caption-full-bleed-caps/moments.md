# moments.md — Full Bleed Caps: Style Bible + Moment Library

This file is the single source of truth for the Full Bleed Caps caption style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel of one talking head with no cuts; everything marked "(design, not measured)" is tuned on a 720x1280, 24 fps demo clip. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while each phrase gets one giant, ultra-heavy, tightly set condensed capital word in a single flat accent colour that spans almost the full width of the frame, sits at the very top and tucks just behind the speaker's hair, plus a tiny clean sans line near the chest that fades in word by word with the keyword repeated in bold accent colour.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, lane, accent colour…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text**, filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Keyword fill | #FCE813 (measured, saturated yellow, one flat colour, no gradient) | Giant keyword and the bold keyword inside the small line |
| Small words | #FFFFFF (design; reference uses a pale yellow-green) | Helper words |
| Shadow | #0A0A0E at 45 % blurred 7 px, offset 6 px (keyword); stacked soft dark halo on small words (design, not measured) | Keeps text readable on bright footage |

Brand-swap rule: the accent is a parameter ✎. One flat, fully saturated colour for the keyword and the small-line keyword; pick one that reads on the shot (warm or strongly saturated, not pastel). White and shadow never change. Demo uses vermilion #FF4B2B.

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, boxes, bars, borders, outlines, blur plates or colour overlays. Text only, plus soft shadow.

### 1.3 Layouts / lanes

| Lane | Keyword ink | Small line baseline | Use |
|---|---|---|---|
| Crest (signature, measured) | ink bottom = head top + 0.006H (tucked behind the hair; reference tucks about 0.07H and loses about 15–25 % of the letters, the skill caps it lower, see 1.7) | 0.66H (reference 0.77H) | Speaker shots with ≥ 0.15H free above the head |
| Free top | ink top at 0.02H, cap height 0.12H | 0.80H | B-roll with nothing important along the top edge |
| Low | ink top at 0.80H, bottom ≤ 0.92H | 0.755H (above the keyword) | B-roll or a person shot whose face is in the upper half and whose lower area is free |

All lanes centre on x = 0.50W. Side margin ≥ 0.05W on every text box.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Ultra-heavy condensed grotesque capitals, very tight letter fit, no outline, no italic, always uppercase | Anton Regular | Bebas Neue, League Gothic, Oswald Bold | cap height 0.12H [about 154 at 720x1280]; if the word is wider than 0.88W, shrink until it is exactly 0.88W (measured: reference spans 0.91W) |
| Small words | Clean medium sans, mixed case as written, light spacing; the keyword inside it in a black-weight sans in the accent colour | Barlow Medium + Barlow Black | Inter, Manrope | 46 px (keyword inside: 52 px) at 720 wide; line ≤ 0.90W |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Keyword | fade 0 → 100 % over 0.25 s, ease-out cubic, starting at the chunk start (measured: reference shows a dim-to-full fade); non-crest lanes also rise 0.015H over 0.30 s (design, not measured) |
| Small word | fade 0 → 100 % over 0.20 s, ease-out, at its spoken time; the whole line is laid out first so no word moves |
| Exit | whole chunk fades out over 0.14 s |
| Never | bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, boxes, outlines, gradients, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: text and shadow overlays; a person cut-out (segmentation mask smoothed with EMA 0.6 / 0.4, light blur on the edge) used only to draw the keyword behind the head in the Crest lane. Forbidden: any colour change, blur, zoom, crop change, background swap, retime, reorder. The footage plays live and in sync.

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head) never receives visible text. The Crest keyword hides only behind hair.
- Crest keyword: at least 85 % of its glyph pixels visible on every frame (assert in the build; measured 99.6 % or better on the demo).
- All text boxes inside 0.05W side margins, keyword ink top ≥ 0.02H.
- Keyword and small line never overlap: keep ≥ 0.012H between their boxes (assert).
- Two chunks are never visible on the same frame (windows disjoint, fade-out included; assert).
- A chunk never runs across a cut.

---

## PART 2 — MOMENT LIBRARY

Family codes: T title, K keyword, C caption, E end. Energy: low / medium / high.

### T1 · OPENING CREST — T high (signature, measured)
**What it is:** the first phrase of the video: one giant keyword fades in tucked behind the hair, small line below it on the chest.
**Use when:** the video opens on a speaker with head room. **Avoid when:** the head top is above 0.12H (use K2) or the opening shot is B-roll (use K2 / K3).
**Text (✎):** 1 keyword (a noun or the topic word), 2–5 words in the small line including the keyword.
**Geometry:** lane Crest (1.3), keyword 1.4 at cap height 0.12H, small line 1.4.
**Motion:** keyword fade 0.25 s from chunk start (chunk start = first word, 0.10 s on the demo); small words 1.5; exit fade 0.14 s. Chunk visible 0.8–1.2 s.
**Footage behaviour:** untouched; mask only hides the keyword where hair covers it. Face box clear from frame 0.
**Captions during it:** this is the caption.
**Exit:** fade.
**Build notes:** fix the keyword lane from the highest head top (smallest y) over the chunk's frames; composite text, then re-paste the original frame where mask = 1.
**Flow prompt text:** "Across the very top of the frame, one huge, ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in, its lower edge just tucked behind the speaker's hair, and a small clean white line '{{LINE}}' fades in word by word on the chest with '{{KEYWORD}}' in bold {{ACCENT}}."
**Still-image state:** keyword fully in, small line complete.

### K1 · CREST KEYWORD — K medium (signature, measured)
**What it is:** the T1 layout used for any later phrase on a speaker shot.
**Use when:** speaker shot with head room, phrase has one strong word. **Limit:** ≤ 3 per video, never three lane repeats in a row.
**Text (✎):** 1 keyword, 2–5 words in the small line.
**Geometry / Motion / Exit:** as T1.
**Flow prompt text:** as T1.

### K2 · FREE-TOP KEYWORD — K medium (design, not measured; same grammar, no occlusion)
**What it is:** the keyword along the top edge with no head to tuck behind, small line low.
**Use when:** B-roll whose top edge is calm, or a speaker who leaves the frame top. **Avoid when:** a face or a key object sits at the top (use K3).
**Geometry:** lane Free top: ink top 0.02H, small line baseline 0.80H.
**Motion:** keyword fade 0.25 s plus rise 0.015H over 0.30 s; small words 1.5; exit 0.14 s.
**Flow prompt text:** "Along the top edge, one huge ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in with a small rise, and a small white line '{{LINE}}' fades in word by word near the bottom with '{{KEYWORD}}' in bold {{ACCENT}}."

### K3 · LOW KEYWORD — K medium (design, not measured)
**What it is:** the keyword along the lower part of the frame with the small line just above it.
**Use when:** B-roll with a face or subject in the upper half (grocery shot, product on a shelf). **Avoid when:** hands or the key action sit at 0.75–0.92H.
**Geometry:** lane Low: ink top 0.80H, small line baseline 0.755H, gap ≥ 0.012H.
**Motion / Exit:** as K2.
**Flow prompt text:** "Along the lower part of the frame, one huge ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in with a small rise, with a small white line '{{LINE}}' just above it, the keyword in bold {{ACCENT}}."

### C1 · WHISPER LINE — C low (measured)
**What it is:** the small line alone, building word by word with its bold accent word, no giant keyword. **Use when:** a phrase has no strong word, or to rest between keywords.
**Geometry:** small line 1.4, lane baseline 0.66H on speakers, 0.80H on B-roll. Chunk 3–6 words.
**Flow prompt text:** "A small clean white line '{{LINE}}' fades in word by word near the bottom with '{{WORD}}' in bold {{ACCENT}}."

### C2 · SOLO KEYWORD — K high (design, not measured)
**What it is:** only the giant keyword, no small line, for a punchline word or number. **Limit:** ≤ 1 per 6 s.
**Geometry:** any keyword lane. **Motion / Exit:** as K1, keyword at chunk start.
**Flow prompt text:** "One huge ultra-heavy condensed capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in and fades out."

### E1 · CLOSING CREST — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 (or K2 on B-roll), ended before the speaker leans out of the lane (assert the 85 % rule) or the shot ends.
**Flow prompt text:** "For the last line the huge capital word '{{KEYWORD}}' in flat {{ACCENT}} fades in behind the top of the head and stays until the speech ends."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | K3 / K2 on B-roll, K1 on any speaker | E1 |
| Single talking head | T1 | K1, C1, K1 (keep the same lane, change the word) | E1 |
| B-roll only | K2 | K3, C2 | E1 (K2) |
| Still image | K2 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Keyword Anton, cap height 154 px, flat #FF4B2B, tuck 0.006H, shrink to 0.88W, small words Barlow Medium 46 px / Black 52 px, keyword fade 0.25 s, small word fade 0.20 s, exit 0.14 s. Chunks: 0.10–1.02 T1 (money), 1.10–1.78 K1 (earning), 2.10–3.17 K3 (yourself), 3.25–4.85 K2 (investments), 4.95–6.55 K3 (spend), 6.90–8.30 K2 (year), 8.45–9.50 E1 (watch). Keyword is shown in uppercase with trailing punctuation dropped; the small line carries the full text as written.
