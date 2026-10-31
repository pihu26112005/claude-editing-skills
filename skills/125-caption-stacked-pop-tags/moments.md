# moments.md — Stacked Pop Tags: Style Bible + Moment Library

This file is the single source of truth for the Stacked Pop Tags caption style. Part 1 is the style bible, Part 2 the moment library (measured on a 360x640, 32 fps, 7.25 s reference reel with a single talking head; values are fractions so they scale), Part 3 starting combinations. SKILL.md says how to pick and place moments.

**The look in one line:** on clean full-frame footage, each phrase appears as a little stack of tiny white wide-sans helper words around one huge slanted condensed keyword in a vivid accent colour that slides in from the side, then the whole stack hard-cuts to the next phrase.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's spec unchanged into the plan.
3. Change only fields marked ✎ (time, text, lane, alignment…). Everything else is the style.
4. Final video → build from the spec. Flow master prompt → use each moment's **Flow prompt text**, filling {{…}}.

Units: W, H, seconds. Reference values are measured on the reference reel unless marked "(design, not measured)".

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Keyword accent | #BBDD32 (measured, a lime) — a parameter; the public demo uses #FF2E93 | Big keywords |
| Helper text | #FFFFFF | Small words |
| Keyword shadow | #2A0016 at 90 % in the demo (dark tone of the accent; the reference used a dark green-black) | Hard drop shadow |
| Helper shadow | #000000 | Dark halo under small words |

Brand-swap rule: replace the accent with the user's colour (bright, saturated, readable on footage). White stays white.

### 1.2 Containers / shapes
Footage full frame, untouched. No boxes, plates, strokes or gradients. Text only, plus shadow.

### 1.3 Layouts / grid

| Lane | Region | Use |
|---|---|---|
| Top | stack top at 0.10H (reference: keyword at y 0.13–0.22 above the head) | Only when no face or subject occupies it (reference had headroom; the demo uses it on faceless B-roll) |
| Low | stack top at 0.60H, stack bottom ≤ 0.90H | Default on a talking head or when the face is high |
| Alignment ✎ | Left edge at 0.07W, right edge at 0.93W, or centred | Reference was left; vary per chunk (design, not measured) |

Stack: lines top to bottom in reading order, line gap 0.012H. A key line is as tall as its cap height + 0.032H (descender room); a small line is its cap height + 0.25 × small size.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Very condensed heavy sans, mixed case as written, sheared right 0.2 (about 11°) | Anton | Bebas Neue, Barlow Condensed Bold | Cap height 0.09H (reference ≈ 0.10H); shrink until ink width ≤ 0.86W |
| Solo keyword | Same | Anton | same | Cap height 1.22 × 0.09H, same width cap |
| Helper word | Wide geometric sans, medium weight | Montserrat Medium (500) | Manrope, Poppins Medium | 0.066W (reference ≈ 0.042W; enlarged for legibility on bright footage) |

Helper rule: first word of a small line at full size on the baseline; each following word on the same line at 0.9 × size, dropped 0.25 × (0.9 size) below the baseline, word gap 0.3 em (measured on the reference: the second helper word is smaller and lower).

Shadows: keyword hard drop shadow offset (0.06 × font size) right and down, 1.2 px blur; helper words a dark halo (5 px max-filter of the glyph, +2 px down, 2 px blur, 95 %).

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Helper word entrance | ease-out cubic, alpha 0 → 1 with a rise of 0.012H | 0.125 s |
| Keyword entrance | ease-out cubic, alpha 0 → 1 with a slide of 0.04W toward its rest place from the side it is aligned to (reference: slid from the left edge) | 0.17 s |
| Phrase exit | hard cut in the next phrase's first frame (or at the phrase end) | 1 frame |
Never: bounce, overshoot, scale pops, typing, wipes, glitch, shake, rotation, flashes, effects on cuts, boxes.

### 1.6 What may happen to the user's footage
Full-frame display untouched; text with shadow on top. Forbidden: replacing, retiming, trimming, reordering, blurring, grading, cards, splits, backgrounds, B-roll frames. Footage is never darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never overlapped by any word or shadow; assert bboxes against the shot's face box |
| Edges | Ink at rest ≥ 0.05W from left and right, ≥ 0.02H from top, ≤ 0.97H bottom; while sliding ≥ 0.02W |
| Text vs text | No overlap between any two words of a chunk |
| Footage text (UI, signs) | Helper words may cross it briefly; keyword may not hide a readable label for > 1 s: move lane |

---

## PART 2 — MOMENT LIBRARY

Families: **C** caption · **K** keyword · **P** placement · **X** cut · **E** ending. Energy: ● calm · ●● medium · ●●● high.

### C1 · STACKED PHRASE — C ●● (signature, the caption system)
**What it is:** a phrase builds word by word as a left-aligned (or right or centred) stack: tiny helper words above and below one big keyword.
**Use when:** always. **Avoid when:** the chunk is a single word (use C2).
**Text (✎):** the user's exact words, case as written; 2–6 words, one keyword.
**Geometry:** lines per 1.3. Reading order = line order; keyword on its own line; helper words that follow each other share a line (staggered per 1.4). Whole layout fixed before the first word shows.
**Motion (reference: words every 0.3–0.5 s, phrase hold 1.5–2.8 s):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | helper word | alpha + rise | 0 → 1, 0.012H → 0 | ease-out, 0.125 s |
| word start ✎ | keyword | K1 | — | — |
| phrase end ✎ | whole stack | alpha | 1 → 0 | hard cut |

Phrase end = next phrase's first word or min(last word start + 0.7 s, next cut); at least 0.25 s after the last word.
**Footage:** untouched. **Exit:** hard cut.
**Build notes:** pre-render each word as an RGBA sprite at 2×, downscale; position by baseline.
**Flow prompt text:** "In the lower part of the frame, a short phrase builds word by word as a small stack. Tiny white words sit above and below one large slanted condensed word, {{KEYWORD}}, in {{ACCENT_COLOUR}}. The only words are {{CAPTION_WORDS}}. The phrase is replaced at once by the next phrase."
**Still-image state:** the full stack.

### K1 · KEY SLIDE-IN — K ●●● (signature)
**What it is:** the keyword arrives with a short side slide and fade, the main hit of every phrase.
**Use when:** every chunk. **Avoid when:** never.
**Text (✎):** one meaning-carrying word.
**Geometry:** Anton, cap 0.09H, shear 0.2, accent fill, hard shadow.
**Motion:** alpha 0 → 1 and x offset 0.04W (from the aligned side) → 0, ease-out cubic, 0.17 s.
**Footage:** untouched. **Exit:** with the phrase.
**Build notes:** shear the glyph mask with an affine about the baseline before downscaling.
**Flow prompt text:** "The key word {{KEYWORD}} slides in a short distance from the side while fading in, in large slanted condensed {{ACCENT_COLOUR}} lettering with a hard dark shadow."
**Still-image state:** keyword at rest.

### C2 · SOLO KEY — C ●●● (measured: reference closing word)
**What it is:** a one-word chunk, the keyword alone, larger.
**Use when:** a short punchy word or sentence end ("left.", "now"). **Avoid when:** longer than 10 characters.
**Text (✎):** one word. **Geometry:** key size 1.22×, lane and alignment ✎.
**Motion:** as K1; hold 0.5–0.9 s; hard cut.
**Footage:** untouched. **Exit:** hard cut.
**Build notes:** same renderer, larger cap height.
**Flow prompt text:** "One word, {{WORD}}, appears alone in very large slanted condensed {{ACCENT_COLOUR}} lettering, then is replaced by the next caption."
**Still-image state:** the word.

### C3 · DOUBLE KEY — C ●●● (measured: reference showed two keywords stacked in one chunk)
**What it is:** two keywords in one stack separated by one small word, for a payoff line.
**Use when:** last line, a two-part contrast. **Avoid when:** more than once per video or on a face lane that cannot hold 0.35H.
**Text (✎):** 2 keywords + helper words, ≤ 5 words.
**Geometry:** key / small / key stack in the low lane; the stack may rise to 0.54H.
**Motion:** each keyword K1 at its own word time.
**Footage:** untouched. **Exit:** hard cut or E1.
**Build notes:** stack height ≈ 0.35H; assert margins.
**Flow prompt text:** "Two important words, {{KEYWORD_1}} and {{KEYWORD_2}}, appear one after the other in large slanted condensed {{ACCENT_COLOUR}} lettering with one small white word between them."
**Still-image state:** full stack.

### P1 · LANE PLACEMENT — P ● (signature rule)
**What it is:** where each stack sits: low lane by default; top lane where no face or subject is there; alignment alternates between chunks.
**Use when:** every chunk. **Text:** none.
**Spec (✎ lane, alignment):** per 1.3 and 1.7. Check against the shot's face box. Never keep the same alignment for more than two chunks in a row (design, not measured).
**Motion:** none. **Footage:** untouched.
**Flow prompt text:** "The caption sits in the lower part of the frame, or near the top when the picture's subject is lower, never over a face."

### X1 · CUT HAND-OFF — X ● (signature treatment of cuts)
**What it is:** footage cuts plainly; the caption in progress hard-cuts to the next phrase on the same frame.
**Use when:** every cut. **Text:** none.
**Motion:** old phrase ends on the cut frame; the next phrase starts at the cut (or at its first word if later); lane may switch.
**Footage:** no effect. **Flow prompt text:** "At each cut the picture cuts plainly and the current caption is replaced at once."

### E1 · END HOLD — E ● (extension in the same grammar, design, not measured)
**What it is:** last phrase holds to min(last word start + 0.6 s, end − 0.25 s), then clean.
**Spec:** per C1. **Flow prompt text:** "The last caption stays until just before the end, then disappears."

---

## PART 3 — RECOMMENDED COMBINATIONS

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 (low) | X1 each cut, P1 top lane on faceless B-roll, C2 on a one-word sentence | C3 + E1 |
| Single talking head | C1 | C1 with alternating alignment, C2 on punchy words | E1 |
| B-roll only, no speech | C1 | P1 lanes by subject | C2 |
| Still image + text | C1 settled | — | — |

Each video gets its own selection. Never paste a row blindly.

---

## TUNING NOTES (demo2 render, 720x1280, 24 fps)

- Helper size 0.066W with a dark halo stays readable on beige sweater and the white app screen; 0.05W was too faint.
- Key row height needs the descender allowance (0.032H) or "money" collides with the helper line below.
- Eight phrases: top lane on faceless shots (cash, plant), low lane elsewhere; alignments L, R, L, centre, R, L, R, L.
- Longest key "investments," shrinks to fit 0.86W.
- Chunk ends at the next phrase start; last phrase holds to 9.75 s.
