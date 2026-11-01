# moments.md — Mosaic Gloss: Style Bible + Moment Library

Style bible and moment library for the "Mosaic Gloss" style. Reference measured on a 720x1280, 24 fps, 10 s reel; values marked (design, not measured) are extensions in the same grammar.
**The look in one line:** a soft gradient page with pale grid lines and diagonal light streaks, footage in one big rounded card or full-bleed under cartoon clouds, pixel-mosaic wipes on every cut, small white whisper words with one big glowing gradient keyword typed in, a glossy pill slot with a ball knob, and a rounded speech-bubble caption.

How to use it:
1. Pick moments by ID (SKILL.md steps 4-5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked (✎).
4. Final video: build from the spec. Flow master prompt: use each moment's Flow prompt text, filling its {{...}} placeholders.

Units: W, H, seconds at 24 fps (f = frame). Reference values in brackets are for 1080x1920.

## PART 1 — STYLE BIBLE
### 1.1 Palette
Measured defaults (reference: light blue family). The accent family is a parameter {{ACCENT}}; swap the whole family together.
| Role | Measured default | Used for |
|---|---|---|
| Page top / bottom | #81C2FC / #B9DFFB | page behind the card, pill page |
| Bottom fade | deep navy ~#0A1E3C, alpha 0 to 0.93 over the lowest 22% | icons sit on it |
| Keyword | cyan #17C8F0 to azure #3A9AED gradient, same-hue glow | big keyword |
| Whisper | white, soft darker shadow | small words |
| Bubble / pill | cyan-azure gradient, white text | bubble, pill |
| Mosaic tiles | 6-7 shades of the page hue, 0.95 alpha | cut wipe |
| Clouds / glass icons | white / frosted white | decoration |
Demo accent family (warm sunset, rule: different hue from reference): page #FFB28E to #FFDAC0, plum fade #280A30, keyword amber #FFC93C to hot pink #FF3D8B, bubble #FF4E8C to #FF8A5A, knob amber, tiles peach/coral/pink/amber.

### 1.2 Containers / Shapes
- Card: x 0.09W-0.905W, y 0.03H-0.83H (587x1024 at 720), radius 38 [57], footage cover-fit, soft shadow (blur 20, offset y 14), bottom 22% of the frame carries the dark fade over card and page.
- Pill page card (design): same x, y 0.03H-0.60H, radius 38, crop anchor (0.5,0.5) (✎).
- Full-bleed: footage untouched, clouds on top.
- Pill: dashed capsule halo 576x126 at y 0.755H, inner gradient pill inset 16 with a white gloss line, ball knob r 33 overlapping the bottom edge.
- Bubble: rounded rect radius 36, gradient, top gloss band, tail bottom-right, text Poppins SemiBold 36.
- Glass icon tile 112x112, radius 26, white 0.92 alpha, glyph inside (calendar, coin, spark; any generic glyph).
- Mosaic: 9x16 grid of 80 px tiles.

### 1.3 Layouts
| Name | Footage rect | Extras |
|---|---|---|
| FULL | 0,0,1,1 | clouds at top |
| CARD | 0.09,0.03,0.905,0.83 | page, fade, icon bottom-left |
| PILL PAGE | 0.09,0.03,0.905,0.60 | whisper line y 0.715H, pill y 0.755-0.855H |

### 1.4 Typography
| Use | Look | Font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | weight 800, gradient fill, 2 px dark outline, glow, typed per letter | Montserrat | Poppins ExtraBold | auto-fit to max width 0.80W, start 104 |
| Whisper | white regular-medium, words fade 0.28 to 1 alpha over 0.18 s | Poppins Medium | Inter | 32 |
| Pill label top | UPPERCASE bold tracked +4 | Montserrat 700 | Poppins | 26 |
| Pill keyword | white heavy, typed | Montserrat 800 | Poppins | 50 |
| Bubble | white semibold, last word soft yellow | Poppins SemiBold | Inter | 36 |

### 1.5 Motion language
Ease-out cubic for settles and slides; back-ease overshoot (1.2-1.8) for pops (icons, pill, bubble); caption keyword types one letter every 0.05 s (max 0.32 s total); caption chunks hard-cut out; no bounce on the card itself; mosaic is stepwise (pixel-like, one frame steps).

### 1.6 What may happen to the footage
Allowed: scale and crop into the card, full-bleed with overlays, rounded mask, shadow, dark bottom fade, clouds and tiles on top for at most 0.45 s per cut. Primary footage always plays live, in sync. Forbidden: recolour, blur, speed change, replacing the shot with a blank page (the reference shows a text-only pill page for 2 s; here the shot stays in a card above the pill).

### 1.7 Safe zones
Face box never covered while speaking. Tiles over a speaking face: at most 3 frames (face tiles go last out of an outgoing speaker shot and first out of an incoming one). Keyword at y 0.56-0.64H on card/low shots, y 0.2H on top-zone B-roll; bubble inside the top 0.14H of the card. All text at least 0.05W from the side edges.

## PART 2 — MOMENT LIBRARY
Families: L layout, T transition, K keyword caption, C caption, G graphic. Energy: low, mid, high.

### L1 · FULL-BLEED OPEN — L low (signature)
**What it is:** first shot plays full frame, untouched, for 0.40 s while the first caption starts.
**Use when:** every video start. **Avoid when:** never.
**Motion:** none. Footage live.
**Flow prompt text:** "The video starts full frame exactly as shot."

### L2 · CARD SETTLE — L mid (signature)
**What it is:** the full frame shrinks into the big rounded card while the gradient page, streaks and fade grow in behind.
**Use when:** after the opening line, speaker shots, calm shots. **Avoid when:** footage with text near the edges.
**Geometry:** CARD (1.3); fade starts at 0.78H.
**Motion:** | t | Element | Property | From to To | Ease | 0.40-0.95 s | rect | full to CARD | ease-out cubic |; radius 0 to 38; fade alpha 0 to 1.
**Footage:** live, scaled cover (0.82x).
**Exit:** mosaic wipe.
**Build notes:** `Image.resize(box=...)` for cover crop; rounded mask at 2x.
**Flow prompt text:** "The shot smoothly shrinks into a large rounded card floating on a soft {{ACCENT}} gradient page with faint grid lines and light streaks."

### L3 · CLOUD FULL-BLEED — L mid (signature)
**What it is:** B-roll full frame with 3 soft cream clouds sliding down from the top and drifting.
**Geometry:** clouds y 4-100 at x 150, -40, 570; keep below y 0.08H over faces.
**Motion:** | 0.20-0.65 s after the cut | cloud | y -70 to 0, alpha 0 to 1 | ease-out |; then +-10 px sine drift, 1.1 s period.
**Captions during it:** top zone (whisper y 0.115H, keyword y 0.205H) or low zone (keyword y 0.64H) when a face is in the upper area (✎).
**Flow prompt text:** "Soft white clouds drift in along the top edge of the shot."

### L4 · PILL PAGE — L mid (signature)
**What it is:** the shot sits in a shorter card, with a glossy capsule slot below that fills with the keyword while a ball knob slides right.
**Geometry:** PILL PAGE (1.3), pill 1.2.
**Motion:** | 0-0.3 s | pill | scale 0.9 to 1 and fade | back-ease |; knob left to right 0.6 s starting 0.1 s before the keyword; keyword typed 0.055 s per letter.
**Text (✎):** 1-2 whisper words in uppercase above, one keyword (max 14 characters) inside.
**Flow prompt text:** "Below the shot a glossy rounded slot with a dashed outline fills with the word {{KEYWORD}} while a round knob slides to the right."

### T1 · MOSAIC WIPE — T high (signature)
**What it is:** a grid of 9x16 pixel tiles in page colours builds over the last 6 frames before a cut, fully covers the cut frame, then clears in random order over 10 frames.
**Use when:** every footage cut (5 cuts in a 10 s clip). **Avoid when:** a cut within 0.5 s of another.
**Motion:** tile appear frame = cut-6+rand(0..5), clear frame = cut+1+rand(0..10), alpha 0.95, nearest-neighbour. Face rule: face tiles appear at cut-1 on a speaker going out, and clear within 3 frames on a speaker coming in.
**Flow prompt text:** "At the cut, a grid of small pixel squares in {{ACCENT}} shades builds over the picture and then dissolves square by square to reveal the next shot."

### K1 · GLOW KEYWORD — K high (signature)
**What it is:** one big keyword typed in letter by letter with a gradient fill, dark outline and glow.
**Text (✎):** 1-2 spoken words, never more; the chunk's most meaningful word(s).
**Geometry:** 1.4; centre y per zone; rises 10 px while typing.
**Flow prompt text:** "One large glowing {{ACCENT}} word types onto the screen letter by letter."

### C1 · WHISPER LINE — C low (signature)
**What it is:** the rest of the chunk as one small white line directly above (words before the keyword) or below (words after) the keyword; words fade from ghost to solid as spoken.
**Text (✎):** 1-4 words, at most 26 characters, never ending on an article.
**Flow prompt text:** "Small white words appear one by one in a single line next to the big word."

### C2 · BUBBLE CAPTION — C mid (signature)
**What it is:** the chunk's words type word by word inside a gradient speech bubble with a tail, last word in soft yellow.
**Geometry:** 1.2, top of card y 0.052H, width at most 0.74W of text; tail ends above the face box.
**Motion:** pop 0.6 to 1 scale over 0.24 s, back-ease, anchored at the tail.
**Flow prompt text:** "A rounded speech bubble pops in near the top and its words appear one at a time."

### G1 · GLASS ICON TILE — G mid
**What it is:** a frosted white tile with a simple glyph pops in bottom-left on the dark fade. **Text:** none; glyph chosen from the chunk's meaning (✎).
**Motion:** pop 0 to 1 over 0.3 s, back-ease 1.8; leaves with the shot.
**Flow prompt text:** "A small frosted icon tile pops in at the bottom left."

### G2 · PAGE STREAK — G low
**What it is:** diagonal soft light bands slide slowly across the page (60 px/s). Always on with CARD and PILL PAGE.

### L5 · CARD SWELL (extension in the same grammar, design not measured) — L mid
Card grows back to full frame over 0.5 s (inverse of L2) before a cut, instead of the mosaic, when the next shot should be full-bleed.

### E1 · BUBBLE CLOSER (extension, design not measured) — C mid
Final line as C2 on the last card shot, held until 0.02 s before the end.

## PART 3 — RECOMMENDED COMBINATIONS
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| talking head, B-roll, talking head | L1, L2, K1+C1 | L3, L4, T1 on every cut | L2 card, C2 bubble |
| single talking head | L1, L2 | K1+C1 chunks, G1 icons, C2 for questions | C2 |
| B-roll only | L1 full, K1 | L3, L4, L2 alternating | K1 on last line |
| still image | CARD with K1+C1 | - | - |
Each video gets its own selection based on its own hook points. Never paste a row blindly.
