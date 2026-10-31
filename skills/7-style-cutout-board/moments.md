# moments.md — Cutout Board: Style Bible + Moment Library

This file defines the **Cutout Board** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*.

**The look in one line:** a designer's desk. At key beats the subject is cut out like a sticker (thick, slightly wobbly yellow outline) and dropped onto a green self-healing cutting mat with a grid and crop marks. Captions mix three voices: small condensed serif words, one hot-pink highlighter tag in bold sans, and one giant ultra-wide black word on a white label strip. Cuts are hard and snappy, with no easing curves to speak of; graphics pop on and off like paper stuck to a board.

How to use it:
1. Pick moments by ID (SKILL.md, steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, text, which word is pink, which word is giant, placement zone, cutout anchor). Everything else (colours, fonts, sizes, outline, grid, timings) is the style and stays as written.
4. For a **final video**, build from the spec. For a **Google Flow master prompt**, use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W` = frame width, `H` = frame height, `f` = frames at 30 fps (at other frame rates keep the **seconds**). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| MAT | `#50705A` | cutting-mat base (sampled 76,107,81 → 82,113,87) |
| MAT-LINE | MAT + 6 % white | minor grid lines |
| MAT-MAJOR | MAT + 14 % white | major grid lines |
| MARK | `#C9D3C9` | crop marks |
| OUTLINE | `#E5BF06` | sticker outline and the small dots on the mat |
| PINK | `#E371A6` | highlighter tag |
| TAG-INK | `#1A1A1A` | text on the pink tag, giant word |
| PLATE | `#F2F0EA` | white label strip behind the giant word |
| SERIF | `#FFFFFF` | small serif words (soft shadow over footage) |

### 1.2 The cutting mat (board)
- Flat MAT colour, very slight lighter haze towards the top (+4 % luminance at the top edge, fading out by 0.3 H).
- Grid: 1-px lines every **0.05 W** [54 px] both ways (MAT-LINE); every 5th line is MAT-MAJOR (every 0.25 W).
- Crop marks: four L-shaped marks inset 0.02 W from the sides and 0.065 H from top/bottom, arms 0.03 W long, 0.002 W thick, MARK colour, opening towards the corner.
- 5–8 tiny OUTLINE-yellow dots (diameter 0.008 W) at random major/minor grid intersections near the edges, fixed for the whole video.

### 1.3 The sticker cutout
- The subject is separated from its background with a **person/object matte** (rembg u2netp / MediaPipe selfie segmentation / SAM). The **subject's pixels are the live footage**, unchanged; only the background is replaced by the mat.
- **Outline:** the matte dilated by **0.022 W** [24 px], filled OUTLINE yellow, edge slightly rough. It **boils**: the dilation edge is re-randomised (±0.004 W noise) every 0.2 s (6 times a second), like a hand-cut sticker on stop-motion.
- **Bottom edge:** the sticker is cut straight across at its bottom (the outline does not wrap the bottom); default bottom at 0.79 H.
- **Size (measured):** sticker box x 0.20–0.78 W, y 0.30–0.79 H; the subject's head top sits ≈ 0.31 H. Scale ≈ 0.55–0.62 of the original frame for a waist-up talking head (0.62 when the speaker is framed wide), ≈ 0.64 for an object.
- If no matte tool is available or the matte is poor (hands, hair, objects lost), use the **card fallback**: a rectangle crop of the same footage with 0.015 W rounded corners and the same boiling yellow outline.

### 1.4 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Serif words | condensed display serif, regular, sentence case | Instrument Serif | Playfair Display, DejaVu Serif Condensed | 0.042 H [81 px] |
| Pink tag | bold geometric sans, lowercase as written | Inter Bold (wght 700) | Archivo Bold, Liberation Sans Bold | 0.036 H [69 px] |
| Giant word | ultra-wide black grotesk, UPPERCASE | Archivo Expanded Black (wdth 125, wght 900) | Unbounded Black, Dela Gothic One, Archivo Black | largest size that fits 0.90 W, cap height ≤ 0.040 H |

- **Pink tag:** PINK rounded rectangle (radius 0.008 W), padding 0.012 W horizontal, 0.004 H vertical, TAG-INK text.
- **Plate:** PLATE rounded rectangle (radius 0.01 W), 0.966 W wide (x 0.017–0.983 W), height 0.054 H; the giant word is centred, as large as fits.
- All words are the user's words.

### 1.5 The caption composition
Each caption chunk is a small stacked composition:
- **Line A:** 1–4 serif words with **at most one** word in a pink tag (the emphasis word), left-to-right in reading order.
- **Line B (optional):** one giant word on the plate (the key noun/verb of the chunk). Max one giant word per 2 s.
- **Line C (optional):** 1–3 trailing serif words (e.g. "beats", "when you're").
- Lines are centred on a common axis, 0.008 H apart. The whole block sits in a **placement zone** (✎): TOP (block top at 0.075 H), HEAD-SIDE (right of the head, top 0.09 H, right-aligned at 0.94 W), CHEST (block top at 0.60 H), or LOW (block top at 0.80 H). Pick the zone that doesn't touch the face box.

### 1.6 Motion language
- **Hard and snappy.** Board pops and exits are cuts (1–2 frames). No slides, no long eases.
- Serif words fade in over 3 f (grey → white) at their spoken time.
- Pink tag pops in at its word: scale 90 → 100 % in 2 f, no overshoot.
- Giant word + plate "ghost in": opacity 0 → 100 % over 4 f with a slight blur (0.004 W) clearing; ghost out the same way when the chunk ends.
- Sticker outline boils at 6 fps (1.3).

### 1.7 What may happen to the user's footage (style-specific rules)
- Allowed: full-frame footage untouched; **board moments** (K01) where the subject is matted and placed as a sticker on the mat (subject pixels live and in sync, background replaced) for **≤ 2.5 s per use and ≤ 35 % of the video in total**; uniform scale of the subject for the sticker.
- The subject inside the sticker is always the current live footage, in sync with the audio. The board replaces only the background, never the person or object.
- Only use a board moment when the matte is clean (face, hair and hands intact); otherwise use the card fallback (1.3).
- Never recolour, filter, retime, reorder or trim the footage.

### 1.8 Safe zones
- Captions never touch the face box (use HEAD-SIDE only if there's 0.30 W of free space beside the head).
- The pink tag and plate never cover hands doing the action of the shot.
- On the board, the caption block goes in the TOP zone (above the sticker).

---

## PART 2 — MOMENT LIBRARY

Family codes: **BOARD** (cutout/mat), **CAP** (caption compositions), **CUT**. Energy: ● low · ●● medium · ●●● high.

---

### K01 · BOARD POP — BOARD ●●● (signature)

**What it is:** In one snap, the background vanishes: the subject is cut out and the frame becomes a green cutting mat. The cutout flashes at full size for one frame, then jumps to a small sticker with a thick boiling yellow outline in the middle of the mat. The caption composition sits above it.

**Use when:** the hook line or a key statement on a talking-head shot, or a hero object shot with a clean matte. Starts on a word (the first word of the statement). Max 2 per 10 s.

**Motion (measured on the reference, 1.03–1.07 s):**

| t (f @30) | State |
|---|---|
| 0 | mat replaces the background; the matted subject still at full size and position, no outline |
| 1 | sticker at its final size and position (x 0.20–0.78 W, y 0.30–0.79 H), yellow outline on |
| 1 → end | sticker live, outline boils every 6 f (0.2 s) |

**Anchor (✎):** the subject's head-top and centre-x (or object centre) are mapped to (0.49 W, 0.31 H); bottom cut at 0.79 H.

**Flow prompt text:** "In one snap, the background disappears: the person is cut out like a sticker with a thick, slightly wobbly yellow outline and placed, smaller, in the middle of a green self-healing cutting mat with a fine grid, crop marks in the corners and a few tiny yellow dots. The person keeps talking normally inside the sticker."

**Still-image state:** sticker on the mat with a caption composition above it.

---

### K02 · BOARD EXIT — CUT ●●

**What it is:** A hard cut back to the untouched full-frame footage. The sticker lingers on top for exactly one frame, then disappears, so the exit feels like peeling.

**Use when:** at the end of the board statement; preferably exactly on a footage cut (then the lingering frame is skipped).

**Motion:** f0: full-frame footage + sticker (same box); f1: footage only.

**Flow prompt text:** "The scene snaps back to the normal full-frame video; the sticker flickers once and is gone."

---

### K03 · SERIF LINE — CAP (always on)

**What it is:** The base caption: small white condensed serif words appearing one by one as spoken.

**Text (✎):** the user's words **verbatim**, original case, 1–4 per line. **Graphics:** SERIF white, Part 1.4 size; over footage add a dark glow (text stroked 2 px in black at 65 %, offset +1 px, blurred 4 px) so thin serifs stay readable on light clothes and walls. On the mat no glow. **Motion:** each word fades in over 3 f at its start.

**Flow prompt text:** "Captions are small white elegant condensed serif words appearing one by one as spoken."

---

### K04 · PINK TAG — CAP ●

**What it is:** One emphasis word inside a hot-pink highlighter tag with bold dark sans text, inline with the serif words.

**Text (✎):** the chunk's emphasis word (adjective, verb, number), as written. Max one per chunk. **Motion:** pops at its word, scale 90 → 100 % in 2 f.

**Flow prompt text:** "The word \"{{WORD}}\" appears in bold dark letters inside a hot-pink highlighter tag, inline with the serif words."

---

### K05 · GIANT WORD PLATE — CAP ●●● (signature)

**What it is:** The key word of the line, set in huge ultra-wide black capitals on a long white label strip spanning almost the full width, directly under the serif line.

**Text (✎):** one user word (noun/verb/payoff), UPPERCASE, punctuation kept ("DIRECTION."), ≤ 12 characters. **Graphics:** Part 1.4 plate + giant word. **Motion:** ghost in over 4 f at its spoken time (or with the first word of the chunk if it's the chunk's subject); stays until the chunk ends; ghost out 4 f.

**Flow prompt text:** "Under the serif words, the word \"{{WORD}}\" appears in huge, extremely wide, heavy black capitals on a long white label strip that spans almost the whole width."

---

### K06 · PLACEMENT JUMP — CAP ● (keeps the eye moving)

**What it is:** Consecutive caption compositions jump between placement zones (TOP → CHEST → HEAD-SIDE → LOW…), chosen by the shot's empty space. No animation between them: the old block ghosts out, the new one builds in its new zone.

**Rule:** never the same zone three times in a row; never a zone touching the face or the action.

**Flow prompt text:** "Each new caption group appears in a different empty part of the frame (top, beside the head, chest height or low), never over the face."

---

### K07 · OBJECT STICKER — BOARD ●● (extension in the same grammar)

**What it is:** K01 applied to a B-roll object (plant, product, phone): the object is cut out with the boiling yellow outline and placed on the mat, bottom-cut at 0.79 H, slightly larger (object box ≈ 0.62 W wide).

**Use when:** a B-roll shot with a single clear object and a clean matte, on the line that names it or its meaning.

**Flow prompt text:** "The {{OBJECT}} is cut out like a sticker with a thick wobbly yellow outline and placed on the green cutting mat."

---

### K08 · CARD STICKER — BOARD ●● (fallback)

**What it is:** When no clean matte exists, the footage is shown as a rectangular card (0.015 W rounded corners) with the boiling yellow outline on the mat, same box as K01. Same timing and exit.

**Flow prompt text:** "The video shrinks to a rectangular card with a thick wobbly yellow border, placed on a green cutting mat with a grid."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | full frame + K03/K04 composition, then K01 board pop on the hook statement | K02 exit on the first cut; K03/K04/K05 compositions on B-roll with K06 placement jumps; K07 on one clean-object shot | final composition with K05 giant payoff word on the speaker (full frame), or a second K01 if the matte is clean |
| Single talking-head shot | K01 on the hook | K02, K06 jumps, one K05 per sentence | K05 payoff word |
| B-roll / product only | K07 (or K08) on the first shot | K06 jumps | K05 |
| Still image (poster) | K01 sticker on the mat + one full composition (serif + pink + giant) | — | — |

Each video gets its own selection based on its own hook points (SKILL.md step 4). Never paste a row blindly.
