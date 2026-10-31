# moments.md — Aqua Glass Stage: Style Bible + Moment Library

This file is the single source of truth for the Aqua Glass Stage style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, with specs measured on a 304x540, 30 fps, 10.0 s reference reel and converted to fractions of W and H. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage lives inside frosted-glass rounded cards that float on a sky-blue gradient or a white stage with pink and blue diagonal slabs, the cards glide between layouts on every cut, small frosted chips carry the captions (one bold italic keyword over light words), and a gradient outline grows around the speaker at the end.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (the reference ran at 30 fps; the demo at 24 fps; at another fps keep the seconds). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Sky gradient top | #B6D0F1 | Top of the blue backdrop (measured) |
| Sky gradient bottom | #0B62D1 | Bottom of the blue backdrop (measured) |
| Stage white | #FDFDFD | White stage backdrop (measured) |
| Pink slab | #F6B7C8 → #EC86AD | Diagonal slabs bottom right, and the glass ring of the lower card |
| Blue slab | #6298E0 → #1467D0 | Diagonal slabs top left, and the glass ring of the upper card |
| Glass ring | white at 35 % with a 2 px bright white edge at 80 % | Border of every card |
| Chip frost | footage blurred, 14 % #DCE6FA + 24 % #141E3C | Light caption chip (on the blue backdrop) |
| Chip slate | footage blurred at 32 % + 68 % #2C2422 | Dark caption chip (stage and full frame) |
| Caption text | #FFFFFF with a soft shadow | All caption and title text |
| Outline gradient | #2A6FE0 (top) → #B07BE0 (bottom), bottom fading to 25 % | Face outline (F1) |

Brand-swap rule: replace the blue family (sky, blue slab, outline top) with the user's brand colour and the pink family with its partner colour; keep white text and the neutral stage white.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Card (footage window) | Rounded rectangle, radius 0.06–0.08W [65–86]. Footage inside is cover-fit; crop anchor ✎ = face or subject. |
| Glass ring | Border 0.035W [38] wide around the card, radius = card radius + ring width, translucent white with a gradient tint (blue for the upper card on the stage, pink for the lower card) and a thin bright edge. Cards may bleed off one screen edge (upper card off the right, lower card off the left). |
| Pointer | Small downward triangle under the upper card, 0.10W wide, 0.045H tall, centred on x = 0.32W, blue gradient. Only in the stage layout. |
| Chip | Rounded rectangle, radius 0.033W [36], padding 0.036W horizontal and 0.012H vertical; the footage behind it is blurred (radius 0.014W) and tinted. Fits the whole chunk. |
| Footage in full-frame layout | 100 % of W and H, no ring. |

### 1.3 Layouts / grid

| Layout | Card rects (x0,y0,x1,y1 as fractions) | Backdrop | Chip centre y |
|---|---|---|---|
| FULL | P 0,0,1,1 | none | 0.58 (slate) |
| BLUE | P 0.09,0.10,0.91,0.90, radius 0.08W; ring on | sky gradient | 0.54 (frost), or 0.80 when the face is low |
| STACK | P (upper) 0.09,0.035,1.03,0.445; S (lower) −0.03,0.555,0.91,0.965; radius 0.06W; pointer on | white stage with slabs | 0.50 (slate) |

P is the primary window (live footage in sync with audio). S is the secondary window (a still or short silent loop of the user's own footage).

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | Bold italic, mixed case as written | Inter Tight Bold/ExtraBold Italic (wght 800) | Inter Bold Italic, Montserrat Bold Italic | 0.081W [87] |
| Light word | Upright regular, mixed case | Inter (wght 450) | Manrope Regular, Plus Jakarta Sans | 0.053W [57] |
| Title | Bold italic CAPITALS, two lines, centred | Inter Tight ExtraBold Italic | Inter ExtraBold Italic | 0.112W [121] per line, line pitch 0.118W |
| Solo keyword | Keyword style at 1.3× | same | same | 0.105W |

Line height of a chip line = 1.22 × keyword size. Word gap = 0.30 × light size. Text colour white; soft shadow (0, +3 px, blur 3 px, black 35 %). Titles are the only uppercase text (design decision measured on the reference).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Layout morph (cards, ring, backdrop move together) | ease-in-out cubic | 0.35–0.45 s |
| Backdrop cross-fade during a morph | follows the morph curve | same |
| Caption word entrance | linear alpha ramp, no movement | 0.125 s (3 f at 24) |
| Chip entrance | alpha 0 → 1 | 0.12 s |
| Chunk change | hard replace in one frame | 1 f |
| Title entrance | ease-out cubic, rise 0.02H + fade | 0.30 s |
| Outline growth | ease-out cubic | 0.8 s |

Never: bounce, overshoot, spring, rotation of cards, shake, glitch, flashes, letter-by-letter typing, colour grading of footage.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Scale and move the primary footage into a card (cover-fit crop around the anchor) | Always live, in sync with the audio; the card never covers the speaking face with anything but the glass ring edge |
| Rounded-corner masks, glass ring, shadow | Per 1.2 |
| Secondary window | Only the user's own footage: a still of a neighbouring shot, a silent loop ≤ 1.5 s, or another crop |
| Blur only inside caption chips | Never on the face |
| Slow push inside a card (M1) | ≤ 1.06 per shot |

Forbidden: replacing or regenerating footage, recolouring, retiming, trimming, reordering, grading, blurring or hiding a face, adding footage the user did not supply.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by a chip, title, outline stroke or ring. Chips go below the chin; titles go in the bottom 0.25 of the card. |
| Chip lane | Default centre y per layout (1.3). Move it so the chip top is ≥ 0.03H under the chin. |
| Title | Bottom of the card (title block centre ≈ 0.80H in BLUE); never when the speaker's hands or chest carry the same words. |
| Edges | Chip and title text stay ≥ 0.04W from the screen edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **G** glass card · **T** title · **C** caption · **P** stage · **X** cut treatment · **F** frame graphic · **M** footage motion · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### G1 · GLASS CARD INSET — G ●● (signature opener)
**What it is:** the full-frame footage shrinks into a rounded glass card while a sky-blue gradient fades in around it.
**Use when:** the video opens on a speaker or a calm shot. **Avoid when:** the first 0.3 s contains a cut.
**Text (✎):** none.
**Geometry / Graphics:** layout BLUE (1.3), ring on, sky gradient behind. Crop anchor ✎ = face box centre.
**Motion (measured on the reference at 30 fps; demo at 24 fps):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.10–0.45 ✎ | primary card | rect and radius | FULL → BLUE | ease-in-out cubic |
| 0.10–0.45 ✎ | backdrop and ring | alpha | 0 → 1 | follows card |

Start ✎: 0.10 s (after at most 3 frames of untouched full frame). Speech may already be running.
**Footage / plate behaviour:** live footage, scaled and rounded only; the face stays inside the card the whole time.
**Captions during it:** C1 (frost chip) below the chin.
**Exit:** X1 morph to the next layout.
**Build notes:** interpolate the 16-value layout vector (rect, radius, ring alpha, backdrop weights, secondary rect, chip y, chip tint); re-do the cover-fit crop every frame.
**Flow prompt text:** "Right at the start the full-screen video smoothly shrinks into a rounded frosted-glass card with a soft sky-blue gradient fading in around it. The person stays centred in the card and keeps speaking."
**Still-image state:** card on blue.

### T1 · CAPS TITLE STRIP — T ●● (signature)
**What it is:** the topic words appear in bold italic capitals near the bottom of the first card, over a soft dark gradient, then fade.
**Use when:** the opening line names the topic. **Avoid when:** the face is low in the card (bottom 0.25 is occupied).
**Text (✎):** 1–3 of the user's words, as written but uppercase, split over two lines (≤ 14 characters per line).
**Geometry / Graphics:** two lines centred on x = 0.50W, baseline of the second line ≈ 0.88H in BLUE; font 0.112W; black gradient over the bottom 0.24 of the card, 0 → 55 %.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.35–0.65 ✎ | title and gradient | alpha, y | 0 → 1, +0.02H → 0 | ease-out |
| hold ✎ | title | — | — | — |
| 1.45–1.75 ✎ | title and gradient | alpha | 1 → 0 | linear |

The fade finishes ≥ 0.08 s before a cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** chips sit above the title (centre y 0.54).
**Exit:** linear fade.
**Build notes:** draw at 2× with a blurred shadow, downscale; the moved words are excluded from the caption chunks (audit).
**Flow prompt text:** "Near the bottom of the card, the title {{TITLE}} appears in bold slanted white capital letters over a soft dark fade, rising a little, then fades away. It never covers the speaker's face."
**Still-image state:** final state.

### C1 · FROST CHIP CAPTION — C ●● (signature, the caption system)
**What it is:** the phrase builds word by word inside a small frosted chip: one keyword in bold italic on its own line, light upright words around it.
**Use when:** always on the BLUE layout and on calm footage. **Avoid when:** the chip would sit on the face.
**Text (✎):** the user's exact words, case as written. Chunk: 2–5 words, 1–2 lines; line 1 usually holds the keyword (with at most one light word before it), line 2 the light words. One keyword per chunk, meaning-carrying noun or verb, never an article or preposition. Never end a chunk on an article, preposition or conjunction.
**Geometry / Graphics:** chip per 1.2, frost tint, centre x = 0.50W, centre y ✎ per layout (1.3), laid out completely before the first word so nothing moves; lines centred in the chip.
**Motion (measured on the reference; chunk changes about every 0.7 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| chunk start ✎ | chip | alpha | 0 → 1 over 0.12 s | linear |
| word start ✎ | word | alpha | 0 → 1 over 0.125 s | linear |
| chunk end ✎ | chip and words | — | replaced by the next chunk in the same frame, or alpha → 0 over 0.08 s if there is a gap | hard |

Chunk end = next chunk's first word, or min(last word end + 0.3 s, next cut).
**Footage / plate behaviour:** untouched; the chip blurs only the pixels behind it.
**Captions during it:** this is the caption system.
**Exit:** per table.
**Build notes:** crop the region under the chip from the composed frame, Gaussian blur 10 px at 720 wide, mix with the frost tint, mask with a rounded rectangle; render text at 2× on a transparent layer, shadow first.
**Flow prompt text:** "In a small frosted-glass label near the middle of the frame, captions build word by word: the key word is bold, slanted and larger, the other words are light and small. Each word fades in softly. When a phrase is done it is replaced at once by the next. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### C2 · SLATE CHIP CAPTION — C ●● (signature)
**What it is:** the same chip and type as C1 with a dark smoky tint, used on the stage and on full-frame shots.
**Use when:** the layout is STACK or FULL, or the footage behind the chip is bright. **Avoid when:** never needed on the blue backdrop.
**Text (✎):** as C1.
**Geometry / Graphics:** chip tint slate (1.1); centre y 0.50 (STACK, between the cards) or 0.58 (FULL), moved to stay ≥ 0.03H under the chin.
**Motion:** as C1. The tint cross-fades with the layout morph (frost ↔ slate) over the morph duration.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** as C1.
**Build notes:** as C1.
**Flow prompt text:** "In a small dark smoky-glass label, captions build word by word: the key word bold, slanted and larger, the other words light and small. The label sits just below the speaker's chin, or between the two cards. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### P1 · STAGE STACK — P ●●● (signature)
**What it is:** the white stage with pink and blue diagonal slabs shows two glass cards: the live footage in the upper card, a still of a neighbouring shot in the lower card, with the caption chip between them.
**Use when:** the shot is B-roll, a product, a screen or any shot where the speaker is not the main subject; a person → B-roll cut. **Avoid when:** the shot is a wide or vertical scene that cannot be cropped to a 1.3:1 window.
**Text (✎):** none (captions per C2).
**Geometry / Graphics:** layout STACK (1.3); slabs drift 0.004W per second towards the top left; slabs fly in from the corners during the morph. Upper ring blue-tinted, lower ring pink-tinted, pointer on. Secondary content ✎: the last speaker frame, or the previous B-roll shot (still), cover-fit around its anchor; change it with a 0.2 s cross-dissolve on the cut.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut ✎ → +0.40 | cards, ring, backdrop, slabs | layout | previous → STACK | ease-in-out cubic |
| during the stay | slabs | position | drift | linear |

**Footage / plate behaviour:** primary live; secondary a still only.
**Captions during it:** C2 chip at centre y 0.50.
**Exit:** X1 morph.
**Build notes:** crop anchors ✎: speaker (0.5, 0.30); hands/objects (0.5, 0.40–0.55).
**Flow prompt text:** "The picture moves onto a bright white stage with soft pink and blue diagonal bars in the corners. The current shot plays in a frosted-glass card at the top with a small blue pointer under it, and a still of {{OTHER_SHOT}} sits in a pink-edged glass card below it."
**Still-image state:** stack with a still on both cards.

### B1 · BLUE CARD RETURN — G ●● (extension in the same grammar)
**What it is:** after a stage section the footage returns to the single glass card on the sky gradient for a new beat.
**Use when:** a shot that fills a vertical frame (a person, a full-height scene) after one or more stage shots. **Avoid when:** twice in a row.
**Text (✎):** none.
**Geometry / Graphics:** BLUE layout; chip centre y ✎ 0.54, or 0.80 when the face is high (face bottom < 0.45H) and the lower area is free.
**Motion:** X1 morph into BLUE (0.40 s).
**Footage / plate behaviour:** live footage, scaled.
**Captions during it:** C1.
**Exit:** X1 morph.
**Build notes:** same as G1.
**Flow prompt text:** "The picture glides back into a single rounded frosted-glass card over a soft sky-blue gradient."
**Still-image state:** card on blue.

### X1 · CARD MORPH — X ●●● (signature treatment of every cut)
**What it is:** the footage changes with its own hard cut while the cards, rings, backdrop and chip glide together to the next layout. There is no flash and no wipe over the footage.
**Use when:** every footage cut. **Avoid when:** never.
**Text (✎):** none.
**Geometry / Graphics:** the two layouts involved (1.3); duration ✎ 0.35–0.45 s.
**Motion (measured on the reference: 2.85–3.4 s full → stage, 7.0–7.5 s stage → full):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut ✎ → +0.40 | all layout values | interpolate | layout A → layout B | ease-in-out cubic |
| cut | primary footage | content | old shot → new shot | hard cut, same frame |

**Footage / plate behaviour:** the new shot appears inside the moving card on the cut frame.
**Captions during it:** the chip glides to its new y with the tint; no chunk starts inside the first 3 frames.
**Exit:** none.
**Build notes:** layouts as a vector; layout sequence list `(time, layout, duration)`.
**Flow prompt text:** "At each cut the new shot appears inside the card while the card, its glass border, the backdrop and the caption label glide smoothly to their new positions. No flash, no wipe, no shake."
**Still-image state:** none.

### F1 · FACE OUTLINE GROW — F ●●● (signature closer)
**What it is:** a thin rounded outline with a blue-to-violet gradient starts tight around the speaker's head and grows outwards to frame the upper body, fading towards the bottom.
**Use when:** the last speaker shot in full frame (payoff, call to action). **Avoid when:** the speaker's head is cropped by the frame edge.
**Text (✎):** none.
**Geometry / Graphics:** stroke 0.012W [13]; start rect ✎ = face box + 0.06W margin (reference: 0.28,0.10,0.72,0.46), end rect 0.04,0.03,0.96,0.72; radius 0.09W → 0.07W; gradient 1.1; alpha 1 at the top to 0.25 at the bottom.
**Motion (reference: 7.8–9.2 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| start ✎ → +0.8 | outline | rect | start → end | ease-out cubic |
| start ✎ → +0.2 | outline | alpha | 0 → 1 | linear |

**Footage / plate behaviour:** untouched, full frame.
**Captions during it:** C2 chip, lower.
**Exit:** holds to the end.
**Build notes:** stroke drawn at 2× on a mask, vertical gradient and alpha ramp multiplied in.
**Flow prompt text:** "Around the speaker a thin rounded outline, blue at the top and violet lower down and fading towards the bottom, starts close around the head and slowly grows to frame the upper body."
**Still-image state:** outline at its end rect.

### C3 · SOLO KEYWORD CHIP — C ●●● (extension in the same grammar)
**What it is:** one payoff word alone, larger, in a one-line chip.
**Use when:** a turn or payoff word, a number or a name. **Avoid when:** longer than 12 characters; max 2 per video, ≥ 3 s apart.
**Text (✎):** one user word.
**Geometry / Graphics:** keyword style at 0.105W in a chip of C1/C2 tint per layout.
**Motion:** C1 entrance; hold 0.5–0.9 s; hard replace.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the chunk.
**Exit:** hard.
**Build notes:** same renderer, bigger font.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in large bold slanted white lettering inside a small frosted-glass label, then is replaced by the next caption."
**Still-image state:** the word.

### M1 · CARD DRIFT — M ● (extension in the same grammar)
**What it is:** a slow push inside the card on a long static shot.
**Use when:** a shot > 2 s without a cut. **Avoid when:** the footage already moves.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** crop zoom ×1.00 → ×1.06, linear, about the anchor ✎; reset at the next cut.
**Footage / plate behaviour:** live, scaled only.
**Captions during it:** unaffected.
**Exit:** reset by the cut.
**Build notes:** `cover(..., zoom=)` with box floats; clamp.
**Flow prompt text:** "Inside the card the shot slowly pushes in by a few percent."
**Still-image state:** none.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last chip holds until just before the end; the outline stays; the picture finishes clean.
**Use when:** every video.
**Text (✎):** the last chunk.
**Geometry / Graphics:** C2 chip, F1 outline.
**Motion:** chip holds to min(last word end + 0.3 s, end − 0.25 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | G1 + T1 + C1 | X1 on every cut; P1 on B-roll, B1 once on a full-height shot, C2 on the stage | F1 + C2 + E1 |
| Single talking head, no cuts | G1 + T1 + C1 | C3 on one payoff word; M1 on a long shot | F1 + E1 |
| B-roll only, no speech | P1 (still of the neighbouring shot) + C2 | X1 on every cut; B1 for full-height shots | E1 |
| Still image + text | G1 settled + C1 chunk | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Layout sequence used: FULL 0–0.10 → BLUE (0.10, 0.35 s) → STACK (cut 1.833, 0.40 s) → BLUE with chip y 0.80 on the grocery shot (cut 4.917, 0.40 s) → STACK (cut 6.625, 0.40 s) → FULL (cut 8.375, 0.45 s).
- Title "SAVING MONEY" (words moved out of the chunks, caption audit counts them): rise 0.35–0.65 s, fade 1.45–1.75 s, cut at 1.833 s.
- Sizes at W 720: keyword 58 px, light 38 px, chip padding 26 × 16 px, chip radius 24 px, title 81 px, ring 25 px, stroke 9 px.
- Secondary stills: last speaker frame (1.75 s) during the cash and phone shots' first part, cash still (3.2 s) during the phone shot, grocery still (6.54 s) during the plant shot.
- Chip tint: frost on BLUE, slate on STACK and FULL. Slate was needed on the stage because white text on a light frost chip is unreadable over white.
- M1 skipped: no shot long enough without a cut except the opener.
