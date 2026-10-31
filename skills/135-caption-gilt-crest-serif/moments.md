# moments.md — Gilt Crest Serif: Style Bible + Moment Library

This file is the single source of truth for the Gilt Crest Serif caption style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel of one talking head with no cuts; everything marked "(design, not measured)" is tuned on a 720x1280, 24 fps demo clip. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while each phrase becomes a tiny condensed serif line that fades in word by word, plus one giant heavy high-contrast serif keyword in a soft two-tone metallic gradient that rises in tucked just behind the top of the speaker's head (or in a lower lane when there is no room above).

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
| Keyword gradient top | #EBCE92 (measured, soft champagne gold) | Top of the keyword, vertical gradient |
| Keyword gradient bottom | #C8A06E (measured, deeper gold) | Bottom of the keyword |
| Small line | #FFFFFF | Helper words |
| Shadow | #000000 at 40 % (keyword), stacked 90 / 100 / 80 % (small words) | Soft shadow, keeps text readable on bright footage (design, not measured) |

Brand-swap rule: the accent is a parameter ✎. Give the keyword any two-tone gradient (light top, deeper bottom, same hue). Keep it saturated enough to read on the shot. White and shadow never change. Demo uses a pink-to-magenta gradient (#FF96CD to #CD1E7D).

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, boxes, bars, borders, blur plates or colour overlays. Text only, plus one soft shadow.

### 1.3 Layouts / lanes

| Lane | Keyword baseline y | Small words | Use |
|---|---|---|---|
| Crest (signature) | head top + 0.02H (measured on reference: keyword sits just above the hair, its lower edge tucked behind the head) | one line above, baseline = keyword top − 0.012H | Speaker shots with ≥ 0.17H of free space above the head |
| Free top | 0.19H (design) | one line above | B-roll or any shot with no person near the top |
| Chest | 0.60H (design; reference: 0.50H on a speaker) | one line above, one line below at baseline + 0.058H | Speaker shots with no room above the head; face stays above 0.40H |
| Low | 0.745H (design) | one line above, optional line below | B-roll and shots where the subject is high in frame |

All lanes centre on x = 0.50W. Side margin ≥ 0.05W on every text box. Keyword ascender top ≥ 0.02H.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Heavy, very high stroke contrast, sharp hairline serifs, tight tracking, mixed case as written | Playfair Display weight 800 | Bodoni Moda Bold, DM Serif Display | cap-to-descender ≈ 0.13H; font size ≈ 0.21W [150 at 720 wide], shrunk so the word is ≤ 0.78W wide; top lane ≤ 0.19W |
| Small words | Light condensed text serif, mixed case, centred | Instrument Serif Regular | Newsreader, EB Garamond | font size ≈ 0.08W [58 at 720 wide] (reference small cap height 0.03H); line ≤ 0.90W |

### 1.5 Motion language

| Element | Motion |
|---|---|
| Small word | fade 0 → 100 % over 0.20 s, ease-out, at its spoken time; the whole line is laid out first so no word moves |
| Keyword | fade 0 → 100 % over 0.30 s plus rise from 0.02H below its rest position, ease-out cubic (design, not measured; reference shows a short fade-up), starting at the keyword's spoken time |
| Exit | whole chunk fades out over 0.14 s (reference: about 3 frames at 32 fps) |
| Never | bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, boxes, outlines, effects on cuts |

### 1.6 What may happen to the user's footage

Allowed: text and shadow overlays; a person cut-out (segmentation mask smoothed with EMA 0.6 / 0.4) used only to draw the keyword behind the head in the Crest lane. Forbidden: any colour change, blur, zoom, crop change, background swap, retime, reorder. The footage plays live and in sync.

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head) never receives visible text. Crest keyword hides only behind hair; descenders end beside or behind the head.
- Crest keyword: at least 85 % of its glyph pixels visible on every frame (assert in the build; measured 0 to 8 % hidden on the demo).
- All text boxes inside 0.05W side margins.
- Two chunks are never visible on the same frame (windows disjoint, assert in the build).

---

## PART 2 — MOMENT LIBRARY

Family codes: C caption, K keyword, E end. Energy: low / medium / high.

### K1 · CREST KEYWORD — K medium (signature, measured)
**What it is:** one giant gradient serif keyword rises behind the top of the head, with a tiny line of helper words above it.
**Use when:** speaker shot with head room, and the phrase has one strong word. **Avoid when:** head top is above 0.12H or the head moves out of frame (use K3).
**Text (✎):** 1 keyword (≤ 10 characters ideal, as written), 1–4 helper words above (never after the keyword; helper words that follow the keyword go to the next chunk).
**Geometry:** lane Crest (1.3); keyword 1.4; helper line centred above.
**Motion:** small words per 1.5; keyword fade + rise 0.30 s at its spoken time; exit fade 0.14 s. Chunk visible 0.7–1.6 s.
**Footage behaviour:** untouched; mask only hides the keyword where the head covers it.
**Captions during it:** this is the caption.
**Exit:** fade.
**Build notes:** fix the lane from the lowest head-top row (highest head) over the chunk's frames; composite text then re-paste the original frame where mask = 1.
**Flow prompt text:** "Just above the speaker's head, one very large heavy serif word '{{KEYWORD}}' in a soft {{ACCENT}} gradient fades in, its lower edge tucked behind the hair, with a tiny white serif line '{{HELPERS}}' above it."
**Still-image state:** keyword fully in, helper line complete.

### K2 · CHEST KEYWORD — K medium (design, not measured; reference shows the same grammar in a lower lane)
**What it is:** helper words above, giant keyword, helper words below, centred on the chest.
**Use when:** speaker shot with no head room, or a phrase with words before and after its keyword. **Avoid when:** hands or a phone sit at 0.45–0.70H and the text would hide the subject's action.
**Text (✎):** 1 keyword, 0–2 words above, 0–3 words below.
**Geometry:** lane Chest. **Motion/Exit:** as K1.
**Flow prompt text:** "Across the chest, tiny white serif words '{{ABOVE}}' fade in word by word over one giant {{ACCENT}} gradient serif word '{{KEYWORD}}', with '{{BELOW}}' underneath."

### K3 · FREE-TOP KEYWORD — K medium (design, not measured)
**What it is:** the K1 layout with no occlusion, used on B-roll or when the head leaves the frame.
**Geometry:** lane Free top (keyword baseline 0.19H). **Motion/Exit:** as K1.
**Flow prompt text:** "Near the top of the frame, a tiny white serif line '{{HELPERS}}' fades in word by word above one large {{ACCENT}} gradient serif word '{{KEYWORD}}'."

### K4 · LOW KEYWORD — K medium (design, not measured)
**What it is:** the keyword in the lower lane with helper words above (and below).
**Use when:** B-roll with a clear lower area; subject high in frame. **Avoid when:** a face sits in the lower half.
**Geometry:** lane Low. **Motion/Exit:** as K1.
**Flow prompt text:** "In the lower part of the frame, tiny white serif words '{{ABOVE}}' fade in above one giant {{ACCENT}} gradient serif word '{{KEYWORD}}'."

### C1 · WHISPER LINE — C low (measured)
**What it is:** the helper line alone, building word by word, no keyword. **Use when:** a phrase has no strong word, or between keyword chunks.
**Geometry:** 1.4 small words, centred, lane baseline at the Free top or Chest lane. **Motion:** 1.5. Chunk 3–6 words.
**Flow prompt text:** "A tiny white serif line '{{LINE}}' fades in word by word near the top of the frame."

### C2 · SOLO KEYWORD — K high (design, not measured)
**What it is:** only the giant keyword, no helper line, for a punchline word. **Use when:** payoff or a number. **Limit:** ≤ 1 per 6 s.
**Geometry:** any keyword lane. **Motion/Exit:** as K1, keyword time = chunk start.
**Flow prompt text:** "One giant {{ACCENT}} gradient serif word '{{KEYWORD}}' fades in with a small rise and fades out."

### E1 · CLOSING CREST — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 or K3, held 0.4 s past the last spoken word (never past the end of the shot or the head leaving frame).
**Flow prompt text:** "For the last line the keyword '{{KEYWORD}}' fades in large in the soft {{ACCENT}} gradient and stays until the speech ends."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | K2 | K4 / K3 on B-roll, K1 on any speaker | E1 (K1) |
| Single talking head | K1 | K2, C1, K1 (alternate lanes) | E1 |
| B-roll only | K3 | K4, C2 | E1 (K3) |
| Still image | K3 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Keyword gradient #FF96CD → #CD1E7D, size 150 px (top lanes 138 px, width-capped at 0.78W), small words 58 px, shadows as 1.1, crest tuck 0.02H, chunk fade-out 0.14 s, keyword rise 0.02H over 0.30 s. Chunks: 0.10–1.02 K2 (money), 1.10–1.80 K1 (more.), 2.10–3.17 K4 (yourself), 3.25–4.88 K3 (investments,), 4.95–6.55 K4 (left.), 6.90–8.30 K3 (year), 8.45–9.55 E1/K1 (happens.; ended early because the speaker leans toward the camera at 9.6 s).
