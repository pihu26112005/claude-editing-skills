# moments.md — Zine Mix: Style Bible + Moment Library

This file defines the Zine Mix style (Part 1) and every moment the style may use (Part 2). Values were measured on a reference video (540×960, 30 fps) and then proven on a 720×1280, 24 fps render.

**The look in one line:** pale powder-blue paper with a cloud-scalloped edge, a giant heavy black word and tiny handwritten notes dropped over untouched footage, tilted blue-bordered photo cards, hand-drawn doodles and slanted spaced-out white captions, closing on a cloud-shaped window with a fat white word.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, f (frames; the reference ran at 30 fps, keep seconds at other rates). Reference values in brackets are for 1080×1920 (multiply fractions by 1080 / 1920).

## PART 1 — STYLE BIBLE

### 1.1 Palette
| Role | Hex | Used for |
|---|---|---|
| PAPER | #C4D4DF | cloud header, card borders, closing page (fine paper grain: noise ±3 levels, blurred 0.8 px) |
| INK | #1E120E | giant header word, tagline, doodles on paper |
| WHITE | #FFFFFF | captions, closing word, doodles on footage |
| DOODLE-DARK | #282C38 | doodles on the closing page |
| SHADOW | black 55 % alpha, blur 3 px, offset (2, 3) | caption shadow only |

Brand-swap rule: PAPER may be swapped for the user's brand colour if it stays a light, low-saturation tint (luminance ≥ 75 %); INK stays near-black. Never more than one paper colour.

### 1.2 Containers / Shapes
- **Footage:** full-frame, sharp, untouched. Under a header it is moved down (see Z01), never scaled.
- **Cloud header (Z01):** paper band over the top, flat top edge, bottom edge made of 6 round lobes (union of circles). At W=720, H=1280: flat part to y=215 [0.168 H]; lobes (cx, cy, r) = (40,170,75), (175,225,85), (330,250,85), (470,235,95), (640,190,80), (730,150,60). Lowest point ≈ 0.26 H at x ≈ 0.46 W. Faint shadow under it (alpha 30 %, blur 7, down 5 px).
- **Photo cards (Z03):** paper-coloured border 0.022 W [24] around a cover-fit crop; no radius; rotated. Card A 0.47 W × 0.265 H, centre (0.255 W, 0.19 H), +6.5° (counter-clockwise). Card B 0.50 W × 0.27 H, centre (0.69 W, 0.565 H), −3.5° (clockwise). Reference: A at x 0.04–0.58, y 0.03–0.37 (+7°); B at x 0.38–0.98, y 0.31–0.67 (−3°). No shadow.
- **Cloud window (Z08):** footage in a cloud shape on the paper page. Box (0.11, 0.055, 0.91, 0.775) W,H: a rounded rectangle inset 10 % (radius 0.12 bw) plus 14 circles of radius 0.115 bw (×0.9–1.15 random per lobe, fixed) placed round the box edge. Reference window: x 0.11–0.91, y 0.06–0.78.
- **Doodles:** thin line art (stroke 2–3 px at 720 W), round joins: paper plane, heart, star (5-point, inner radius 0.45), zigzag, spiral, squiggle, bulb, floppy disk. Ink on paper, white on footage, dark grey on the closing page. Never filled.

### 1.3 Layouts
| Name | Layout |
|---|---|
| HEADER | cloud header on top 0–0.26 H, footage below (moved down 0.12 H), caption line at y 0.70 H |
| CARDS | full-frame footage, card A top-left, card B centre-right, caption line at y 0.875 H |
| PAGE | paper page, cloud window (0.11, 0.055, 0.91, 0.775), big word centre y 0.835 H, caption line y 0.915 H |

### 1.4 Typography
| Use | Look | Preferred free font | Fallbacks | Size (W=720) |
|---|---|---|---|---|
| Header word | heavy, extra-wide, UPPERCASE, black, tracking −0.01 em, centre x 0.5 W, centre y 0.165 H | Archivo (wght 900, wdth 125) | Archivo Black, Montserrat ExtraBold | width 0.50 W for a 5-letter word (≈ 105 px); shorter words keep the same size |
| Tagline | handwritten, slanted 12°, UPPERCASE, INK, tracking 0.07 em, 2–3 lines, rotated −4°, top-left (24, 28) | Gaegu Regular | Gochi Hand, Caveat Brush | 34 px, line pitch 33 px |
| Caption | handwritten, slanted 11°, UPPERCASE, white, tracking 0.1 em, centred, words fade in place | Gaegu Bold | Gochi Hand, Caveat Brush | 52 px, word gap 26 px |
| Closing word | same heavy face, white, soft dark shadow (blur 6, offset 2/6, alpha 47 %) | Archivo (900, 125) | Archivo Black | width 0.62 W |

### 1.5 Motion language
- Hard pops for paper (2-step snap), ease-out cubic for things that land (cards, header drop, closing word), ease-in cubic for exits, ease-in-out cubic for the window morph.
- Typical durations: card slide 0.33 s, header drop 0.25 s, exit 0.25 s, window morph 0.5 s, caption word fade 2 f.
- No bounce, no overshoot, no rotation animation, no glow. Paper never fades: it snaps or slides.
- Hard switches only on footage cuts.

### 1.6 What may happen to the user's footage
- Allowed: move the whole frame down by up to 0.12 H while a cloud header covers the vacated top; cover-fit crops inside cards (stills, or ≤ 1.5 s silent loops); the closing cloud window (cover-fit, uniform scale ≤ 1.12 over 0.5 s); overlays (paper, cards, doodles, text).
- The primary footage always plays live in sync with the audio: full-frame behind header and cards, or inside the cloud window.
- Forbidden: blur, grading, speed change, trimming, replacing, mirroring; any card showing non-user imagery; covering the footage beyond the header/cards/page areas.

### 1.7 Safe zones
- Face never under the header, a card or a doodle. With HEADER the face top must be at or below 0.27 H after the 0.12 H shift (source face top ≤ 0.15 H is fine). If a face top is above 0.15 H in the source, shift less (header lowest point must stay above the face top − 0.01 H) or skip Z01 on that shot.
- Cards go where the face is not: choose the card sides from the face box (swap A/B horizontally if the face is on the left). Card A's right edge ≤ face left − 0.01 W, or its bottom ≤ face top.
- Captions: HEADER y 0.70 H, CARDS y 0.875 H, PAGE y 0.915 H. Move up by 0.05 H if a face or hands reach that line.
- Max 3 words, max 20 characters per caption chunk.

## PART 2 — MOMENT LIBRARY

Families: **H** header, **C** cards, **P** page, **T** text, **D** doodle. Energy: ● calm, ●● medium, ●●● strong.

### Z01 · CLOUD HEADER — H ●●● (signature, opener)
**What it is:** a cloud-edged paper band snaps over the top of the footage with one giant heavy word and a tiny handwritten note; the footage is moved down to clear the face.
**Use when:** opening line, topic word, any new section. **Avoid when:** the face top is above 0.15 H and cannot move.
**Text (✎):** word = one meaning word from the user's line (UPPERCASE, ≤ 8 letters, ideally the topic word); tagline = 2–3 short lines made of the user's own nearby words (UPPERCASE, ≤ 11 characters per line).
**Geometry / Graphics:** cloud header (1.2), word centre y 0.165 H, tagline top-left, HEADER doodles (plane under the tagline, two hearts right, zigzag top-right, squiggle top).
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| t0 | header | y offset | hidden → −90 px for 2 f | hard |
| t0+2 f | header | y offset | −90 → 0 px | hard (measured: 0.19 H then 0.30 H, 2 f apart) |
| t0..t0+2 f | footage | move down | 0 → 0.07 H, then 0.12 H | follows header: shift = 154 px × (1 + offset/215) |
**Footage behaviour:** live footage, moved down only.
**Captions during it:** HEADER line y 0.70 H.
**Exit:** Z05 or Z03 (header slides up 0.25 s ease-in while the footage returns).
**Build notes:** pre-render each header (word + tagline) as an RGBA layer once; paste at y offset.
**Flow prompt text:** "At {{TIME}} a pale powder-blue paper shape with a scalloped cloud-like lower edge snaps onto the top of the frame in two quick steps, pushing the picture slightly down. On it, in the middle, the huge heavy black word {{WORD}}; in the top-left corner three tiny handwritten lines {{TAGLINE}}; small thin doodles of a paper plane, two hearts and a zigzag. The person and scene stay exactly as they are."
**Still-image state:** header settled over the top, photo shifted down.

### Z02 · WORD SWAP — H ●● (extension in the same grammar, serves cuts)
**What it is:** on a footage cut, the header's word and tagline change in one frame; the paper stays.
**Use when:** a cut happens while a header is up (person → B-roll, B-roll → B-roll), or a new topic word is spoken.
**Text (✎):** new word + tagline from the user's words.
**Motion:** hard swap on the cut frame; no transition.
**Footage behaviour:** the cut itself; header stays.
**Exit:** Z03 or Z01 end.
**Flow prompt text:** "At {{TIME}}, as the shot changes, the huge black word on the paper shape changes to {{WORD}} and the small handwritten note changes to {{TAGLINE}}; the paper shape itself does not move."

### Z03 · PHOTO CARDS — C ●●● (signature, middle)
**What it is:** two tilted photo cards with pale blue borders slide in from opposite corners over the live footage; the header slides out.
**Use when:** a cut to B-roll, a list step, "previous step beside the current step".
**Content (✎):** card A and card B each show the user's own footage: a calm still (frame at the end of a neighbouring shot), a ≤ 1.5 s silent loop, or another crop. Never empty, never unrelated.
**Geometry:** 1.2 cards; sides swapped by the face box (1.7).
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| t0 | card A | position | from (−0.65 W, −0.35 H) offset → place, 0.33 s | ease-out |
| t0+2 f | card B | position | from (+0.65 W, +0.40 H) offset → place, 0.33 s | ease-out |
| t0 | header (if up) | y offset | 0 → −400 px, 0.25 s | ease-in |
**Footage behaviour:** live footage full-frame behind the cards, in place (shift returns to 0 while the header leaves).
**Captions during it:** CARDS line y 0.875 H.
**Exit:** Z05, or slide out (ease-in, 0.25 s, reverse path).
**Build notes:** pre-rotate cards with `expand=True`, paste by centre; cover-fit with a clamped crop box.
**Flow prompt text:** "At {{TIME}} two photo prints with thin pale blue borders slide in from opposite corners and settle slightly tilted, one at the top-left showing {{CARD_A_CONTENT}}, one at the right-middle showing {{CARD_B_CONTENT}}. The video keeps playing full-screen behind them."
**Still-image state:** both cards settled.

### Z04 · CARD RE-POP — C ●● (extension, serves cuts while cards are up)
**What it is:** on a footage cut the cards keep their places, take the next content and pop from 88 % to 100 % in 5 f.
**Use when:** a cut while Z03 is up. **Content (✎):** previous shot's still in A, the shot before in B.
**Motion:** scale 0.88 → 1.0, 5 f, ease-out; contents swap on the cut frame.
**Flow prompt text:** "At {{TIME}}, as the shot changes, the two photo prints swap to {{CARD_A_CONTENT}} and {{CARD_B_CONTENT}} with a small quick pop, staying in the same tilted places."

### Z05 · HEADER RETURN — H ●● (extension)
**What it is:** the cards slide out on a cut and a new header drops from the top.
**Motion:** cards exit 0.25 s ease-in from the cut; header offset −400 → 0, 0.25 s ease-out starting 2 f after the cut; footage shift follows.
**Text (✎):** word + tagline.
**Flow prompt text:** "At {{TIME}} the photo prints slide away and the pale blue paper shape drops down from the top with the huge black word {{WORD}} and the handwritten note {{TAGLINE}}."

### Z06 · SLANTED CAPTIONS — T ●● (signature, caption system)
**What it is:** small white handwritten uppercase words, slanted and spaced out, fade in place one by one; the chunk is centred as a whole.
**Text (✎):** the user's words in order, UPPERCASE, chunks of 1–3 words (≤ 20 characters), split at punctuation, never end on an article/preposition.
**Geometry:** 1.4 caption; y by layout (1.3), x centred, word gap 26 px; each word keeps its final position (so earlier words do not shift).
**Motion:** word fade 2 f from its spoken time, 6 px rise; chunk end = min(next start − 0.05 s, last word start + 0.75 s); minimum 0.4 s. Line moves between layouts over 0.3 s ease-in-out.
**Exit:** whole chunk disappears on its end (hard).
**Flow prompt text:** "Small white handwritten capital letters, slanted and widely spaced with a soft shadow, appear word by word in the lower part of the screen exactly as the words are spoken: {{LINES}}."

### Z07 · DOODLE SPRINKLE — D ● (extension)
**What it is:** thin hand-drawn icons fade in (3 f) one after another on empty areas.
**Use when:** quiet holds > 1.5 s. **Content (✎):** pick from plane, heart, star, spiral, zigzag, squiggle, bulb, floppy; 2–3 at a time, positions in margins (never over faces).
**Flow prompt text:** "A few thin hand-drawn line icons, a small star and a spiral, fade in at the edges of the picture."

### Z08 · CLOUD WINDOW PAGE — P ●●● (signature, closer)
**What it is:** on the last cut the footage becomes a cloud-shaped window on the paper page: the cloud shrinks in from outside the frame over 0.5 s while the footage settles into it.
**Use when:** payoff / CTA, the last shot (any shot with the subject in the upper two thirds).
**Geometry:** 1.2 cloud window; footage cover-fit with anchor (0.5, 0.0) so the face sits upper-middle; PAGE doodles from t0+0.30 s (5 f fade).
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| t0 | cloud mask | box | (−0.55,−0.35,1.55,1.35) → (0.11,0.055,0.91,0.775) | ease-in-out, 0.5 s |
| t0 | footage | cover box | full frame → window box | ease-in-out, 0.5 s |
**Footage behaviour:** live, in sync; paper shows only outside the cloud.
**Captions during it:** PAGE line y 0.915 H.
**Exit:** none (holds to the end).
**Flow prompt text:** "At {{TIME}} the picture shrinks into a cloud-shaped window with a bumpy outline, centred on a pale powder-blue paper page decorated with thin hand-drawn doodles; the person keeps speaking inside the window."
**Still-image state:** the default poster: page, cloud window with the photo, big word, one caption line.

### Z09 · BIG WHITE WORD — P ●●● (signature, part of the closer)
**What it is:** a fat white word with a soft dark shadow pops under the cloud window.
**Text (✎):** the payoff word from the user's last line, UPPERCASE, ≤ 9 letters.
**Motion:** at t1 (≥ 0.3 s after Z08 starts, may precede the spoken word): fade 0 → 1 in 0.2 s ease-out and scale 1.18 → 1.0 in 0.25 s ease-out. Centre y 0.835 H.
**Flow prompt text:** "Below the window the huge heavy white word {{WORD}} with a soft shadow pops in."

### Z10 · SINGLE CARD — C ●● (extension, for short or B-roll-only inputs)
**What it is:** Z03 with only card B (the user's own related shot) over a live shot.
**Use when:** only one other shot exists. Same motion as card B in Z03.
**Flow prompt text:** "At {{TIME}} one tilted photo print with a pale blue border slides in from the lower right showing {{CARD_CONTENT}}."

### Z11 · HEADER ONLY CLOSER — P ●● (extension, when the last shot has the face too high or low for a window)
**What it is:** Z01 with the closing word and no cloud window; the footage stays full-frame and moved down.
**Flow prompt text:** "The pale blue cloud-edged paper shape stays on top with the huge black word {{WORD}}; the picture stays full-screen below."

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| talking head → B-roll → talking head | Z01 + Z06 (+ Z07) | Z02 on the first cut, Z03 + Z04 over the B-roll, Z05 for a new topic | Z08 + Z09 |
| single talking head | Z01 | Z02 on a new topic word, Z07 on holds | Z08 + Z09 |
| B-roll only | Z01 | Z03 or Z10 (cards from other shots), Z04 on cuts | Z11 or Z08 |
| still image | Z08 settled (poster) | – | – |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
