# moments.md — Editorial Grid: Style Bible + Moment Library

This file defines the **Editorial Grid** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*.

**The look in one line:** a quiet, gallery-white page where the footage lives inside sharp-cornered cards that settle, swell, split into an asymmetric grid and slide on clean ease-out curves, with monospaced uppercase captions typed word by word, a widely letter-spaced keyword above the card, and a bold black title word to close. No colour except the footage, no bounce, no shadows on cards. Precision is the decoration.

How to use it:
1. Pick moments by ID (SKILL.md, steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, text, which footage goes in which card, crop anchor, side). Everything else (sizes, margins, fonts, motion curves, durations, layer order) is the style and stays as written.
4. For a **final video**, build from the spec. For a **Google Flow master prompt**, use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W` = frame width, `H` = frame height, `f` = frames at 30 fps (at other frame rates keep the **seconds**). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| PAGE | `#FFFFFF` | the canvas behind everything (pure white, no texture, no vignette) |
| INK | `#111111` | all text, caption words once spoken |
| GHOST | `#B9B9B9` | a caption word while it is fading in; never a resting colour |
| BAR | `#FFFFFF` | caption bars and caption tabs |

The footage is the only colour in the frame. No accent colours, no gradients, no tints. (Brand variant ✎: PAGE may become an off-white `#F6F5F1` or a brand neutral; INK stays near-black.)

### 1.2 Cards (the footage containers)
- A **card** is a sharp-cornered rectangle (radius 0) that shows the footage with **cover** fit: the footage is scaled uniformly to fill the card and cropped by the card edges. No border, no shadow, no rounded corners, no frame.
- **Crop anchor (✎):** the point of the footage kept centred inside the card. Default = face box centre for people, subject centre for B-roll. The face must never be cut by a card edge.
- Inside a card the footage may also drift (E15) between 100 % and 106 % cover scale.
- **Primary card** = the card that shows the *current* moment of the timeline, in real time, with the audio. There is always exactly one.
- **Secondary card** = an extra card that shows **the user's own footage only**: a held still (or a short silent loop ≤ 1.5 s) from a neighbouring scene, or a second crop of the current frame. Never external or generated imagery.

### 1.3 Grid
- Side margins **0.074 W** [80 px], top margin **0.085 H** [163 px], gutter **0.028 H** [54 px].
- Layouts (all positions as fractions of W/H; x0, y0, x1, y1):

| Layout | Card | Box | Aspect |
|---|---|---|---|
| **SOLO** (centred) | primary | 0.074, 0.200, 0.920, 0.795 | ≈ 0.80 |
| **SPLIT-A** (reference) | top-left portrait | 0.059, 0.085, 0.587, 0.520 | ≈ 0.68 |
| | bottom-right landscape, bleeds off the right edge | 0.181, 0.548, 1.000, 0.882 | ≈ 1.37 |
| **SPLIT-B** (mirror) | top-right portrait | 0.413, 0.085, 0.941, 0.520 | ≈ 0.68 |
| | bottom-left landscape, bleeds off the left edge | 0.000, 0.548, 0.819, 0.882 | ≈ 1.37 |
| **STACK** | top landscape, bleeds left | 0.000, 0.110, 0.860, 0.440 | ≈ 1.46 |
| | bottom landscape, bleeds right | 0.140, 0.470, 1.000, 0.800 | ≈ 1.46 |
| **TITLE-CARD** (outro with footage) | primary, upper | 0.160, 0.085, 0.840, 0.560 | ≈ 0.81 |

Either card of a split may be the primary. Default: the card whose shape fits the current shot (people → portrait, B-roll → landscape).

### 1.4 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Captions | monospaced, medium, UPPERCASE | IBM Plex Mono Medium | JetBrains Mono Medium, Noto Sans Mono, DejaVu Sans Mono | 0.035 H [67 px] |
| Keyword header | monospaced, regular, UPPERCASE, letter-spaced ≈ 2.9 em (gap ≈ 5 letter widths) | IBM Plex Mono Regular | same | 0.016 H [31 px] |
| Title word | grotesk, bold/extra-bold, UPPERCASE, tight tracking −2 % | Inter Bold / ExtraBold | Helvetica Neue Bold, Arial Bold, Liberation Sans Bold | cap height 0.040 H [77 px] |
| Tagline / list index | monospaced, regular, UPPERCASE, letter-spaced 0.15 em | IBM Plex Mono Regular | same | 0.017 H [33 px] |

All on-screen words are the user's words (or list numerals). Nothing is italic. Nothing is centred-justified across two lines; captions are always one line.

### 1.5 Motion language
- **Settle / slide in:** ease-out-quart, 7–8 f. Fast start, long soft landing. **No overshoot, no bounce, ever.**
- **Swell (build-up):** ease-in-quad, 12–14 f. Slow start, accelerating into the cut.
- **Exit:** ease-in-quad, 4–5 f, then a **hard cut** (the element is gone on the next frame).
- **Type-on:** letters appear left to right, 2 letters per frame; type-off removes them right to left, 3 letters per frame.
- **Word reveal (captions):** each word fades from 0 to 100 % in 3 f (passing through GHOST grey) at its spoken time.
- **Layout changes happen on a cut** (a cut in the footage, or a hard cut the style makes at the end of a swell). Between cuts, layouts are still except for E15 drift.
- Everything aligns to the grid in 1.3. Nothing is tilted.

### 1.6 What may happen to the user's footage (style-specific rules)
- Allowed: uniform scale and position of the footage inside cards (cover fit + crop anchor), card size and position animation, and a white page around the cards. In this style, **white page around the footage is the design**, not an empty bar.
- The **primary card always plays the current footage in real time**, in sync with the audio. The timeline is never paused, reordered, sped up or trimmed.
- Secondary cards show only the user's own footage (held still, ≤ 1.5 s silent loop, or another crop).
- Full-page white without footage (E11) is allowed only for the **last ≤ 1.5 s** or **≤ 15 %** of the video, whichever is shorter, and only if the final line is already being spoken. Otherwise use E13 (title with the footage still visible).
- Never recolour, filter, blur or retime the footage.

### 1.7 Safe zones
- **Face box:** never covered by a caption bar, tab or text; never cut by a card edge.
- **Caption zone inside a card:** the lower 22 % of the card, unless the face sits there. Then the bar moves **outside** the card as a tab under its bottom edge (E04).
- Footage text (screens, signs) may be covered by a caption bar only if it isn't the point of the shot.

---

## PART 2 — MOMENT LIBRARY

Family codes: **CARD** (footage containers), **TYPE** (typography), **CAP** (captions), **CUT** (transitions). Energy: ● low · ●● medium · ●●● high.

---

### E01 · CARD SETTLE — CARD ●● (signature opener)

**What it is:** The video opens almost full-frame, then tightens into the centred SOLO card on a white page, like a photo being placed on a gallery wall.

**Use when:** the first frames of the video (default opener), and after an E11/E10 return to footage.

**Motion:**

| t (f @30) | Property | From → To | Ease |
|---|---|---|---|
| 0 → 7 | card box | (0.044, 0.124, 0.950, 0.873) → SOLO box | ease-out-quart |
| 0 → 7 | footage cover scale inside card | 107 % → 100 % | same curve |
| 8 → | — | still | — |

Measured on the reference: the card loses about 70 % of its excess size in the first 4 frames.

**Crop anchor (✎):** the face/subject centre of the first shot.

**Flow prompt text:** "The video opens nearly full screen and in a quarter of a second smoothly shrinks into a clean, sharp-cornered rectangle centred on a pure white page, with even white margins around it. No border, no shadow, no bounce."

**Still-image state:** footage in the SOLO card on white.

---

### E02 · KEYWORD TYPE-ON — TYPE ● (signature)

**What it is:** One keyword, typed letter by letter in tiny, widely spaced monospaced capitals ("V I S U A L"), centred above the card. It types off again before the layout changes.

**Use when:** the opening line's key noun, or the theme word of a new section. One per section, max 3 per video.

**Text (✎):** one user word from the line it introduces (or the line just after), UPPERCASE, ≤ 10 letters.

**Graphics:** INK, keyword font, letter-spacing ≈ 2.9 em (each letter followed by a gap about 5 letter widths wide; measured on the reference: 6 letters span 0.44 W). Centred on the card's centre-line; baseline at card top − 0.035 H (SOLO: y ≈ 0.160 H).

**Motion:** type-on starts **0.3–0.5 s before** the word is spoken (on the reference it appears at 0.40 s, while the word comes at 1.6 s, so it can lead the line), 2 letters per frame. Stays still. Type-off 3 letters per frame, finishing **≥ 0.1 s before** any swell (E06) or layout change.

**Flow prompt text:** "Above the card, the single word \"{{WORD}}\" types on letter by letter in very small, widely spaced black typewriter capitals, centred. It stays still, then types off letter by letter before the next change."

---

### E03 · CAPTION BAR (in card) — CAP (always on, SOLO layout)

**What it is:** A white rectangular bar sitting on the lower part of the card, holding the current caption chunk in monospaced capitals. The bar is pre-sized to the whole chunk; words appear one at a time as they're spoken.

**Text (✎):** the user's caption text **verbatim**, UPPERCASE, split into chunks of 1–3 words, ≤ 18 characters (monospace is wide: 18 characters ≈ 0.68 W). Punctuation kept (commas, full stops, apostrophes).

**Graphics:** BAR white, corner radius 0.006 W, height 0.042 H, inner padding 0.020 W left/right. Text INK, caption font, left-aligned, vertically centred. Bar left edge at card x0 + 0.095 × card width; bar bottom at card y1 − 0.10 × card height (✎ move up if the subject's hands/product sit there; if the face is in the lower 25 % of the card, switch to E04).

**Motion:** new chunk: the bar appears instantly at its full chunk width with all words invisible; each word fades in over 3 f at its spoken time (GHOST → INK). Chunk change: the bar resizes to the next chunk in 1 frame and its words are cleared (a hard swap is the style; no slide). If the gap before the next chunk is > 0.4 s, the bar disappears and comes back with the next chunk.

**Flow prompt text:** "Captions sit in a plain white rectangular bar near the bottom of the card, black monospaced capitals, left-aligned. The bar is already sized for the whole line and the words appear one by one exactly as they are spoken. The ONLY caption lines, in order, are: [a-b s] \"{{CHUNK_1}}\", [c-d s] \"{{CHUNK_2}}\", … No other text, no repeated lines."

---

### E04 · CAPTION TAB (on a card edge) — CAP (always on, grid layouts)

**What it is:** In SPLIT/STACK layouts the caption bar becomes a white tab glued to the **bottom edge of the primary card** (half on the card, half over the gutter), like a museum label.

**Graphics:** BAR white, square corners, height 0.040 H, padding 0.018 W. If the tab is wider than its card, it right-aligns to the card's right edge and the overhang simply sits on the white page (the text stays readable thanks to its shadow). Position: tab top at card y1 − 0.034 H; left edge at the card's horizontal centre − 0.04 W (portrait card) or at x0 + 0.06 W (landscape card). If the tab would run past the frame edge, right-align it to the card's right edge instead. Text INK, caption font, with a very soft text shadow (0 / +1 px, blur 3 px, black 12 %) because it sits over footage and white.

**Motion:** as E03. When the layout changes (E07/E08), the tab moves with its card (same curve, same frames).

---

### E05 · FLOATING CAPTION — CAP (on white)

**What it is:** With no card under it (E11 end page, or while a card is off-screen), the caption is set directly on the white page: monospaced capitals with no bar, centred horizontally, with the same word-by-word reveal.

**Graphics:** INK, caption font, no bar, soft text shadow (0 / +2 px, blur 6 px, black 10 %). Baseline at 0.80 H. Laid out for the whole chunk first (so words don't shift as they appear), chunk centred on W.

**Flow prompt text:** "With no card behind them, the captions sit directly on the white page in black monospaced capitals, centred low in the frame, words appearing one by one as spoken."

---

### E06 · SWELL — CARD ●● (build-up before a change)

**What it is:** Just before a cut, the primary card slowly grows, accelerating, like an inhale. Then the layout changes on the cut.

**Use when:** 0.40–0.50 s before a footage cut or a sentence boundary that will trigger E07/E08/E10. Max once per 3 s.

**Motion:** card box scales about its centre to **105 % width / 112 % height** over 13 f, ease-in-quad. The footage cover scale follows so nothing letterboxes. The keyword (E02) must already be gone. The caption bar rides with the card.

**Measured on the reference:** card 457×571 → 479×670 px between 2.07 s and 2.53 s, then a hard switch at 2.57 s.

**Flow prompt text:** "The card slowly grows a little, faster and faster, for about half a second, like it's about to burst, and then the layout changes on the cut."

---

### E07 · GRID SPLIT — CARD ●●● (signature middle)

**What it is:** On a cut, the single card becomes two: a portrait card top-left and a landscape card bottom-right that bleeds off the right edge. Both slide in from the right and settle together.

**Use when:** the footage cuts from a person to B-roll (or vice versa), or the script moves from statement to example/explanation. ✎ mirror to SPLIT-B when the face would be cut, or for variety.

**Content (✎):** which card is primary (live) and what the secondary shows (still/loop/crop of the user's own footage, Part 1.2).

**Motion (starts on the cut frame):**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 → 8 | portrait card | x offset | +0.070 W → 0 | ease-out-quart |
| 0 → 8 | landscape card | x offset | +0.070 W → 0 (start 1 f later) | ease-out-quart |
| 0 → 8 | both | opacity | 100 % from frame 0 (no fade) | — |

The caption switches from E03 to E04 on the same frame, attached to the primary card.

**Flow prompt text:** "On the cut, the layout splits into two sharp-cornered cards on the white page: a tall card in the upper left showing {{CARD_A_CONTENT}}, and a wide card in the lower right, running off the right edge, showing {{CARD_B_CONTENT}}. Both slide in a short distance from the right and settle smoothly with no bounce. A narrow white gap separates them."

**Still-image state:** SPLIT-A with both cards in place.

---

### E08 · GRID SHIFT — CARD ●● (re-layout on a later cut)

**What it is:** On the next cut, the cards re-arrange into another layout (SPLIT-A ↔ SPLIT-B, SPLIT → STACK, or back to SOLO). Every card slides straight to its new box in 8 f, ease-out-quart. Content changes happen on the cut frame.

**Use when:** each new footage cut in the middle of the video, so every cut gets a layout beat. Don't repeat the same layout twice in a row.

**Rules:** the primary card's live footage never pauses during the move. A secondary card whose content changes swaps on the cut frame (hard), never cross-fades.

**Flow prompt text:** "On the cut, the cards glide to new positions on the white grid: {{NEW_LAYOUT_WORDS}}. They move in straight lines and settle smoothly, no bounce."

---

### E09 · CUT NUDGE — CARD ● (accent for cuts inside a card)

**What it is:** When the footage cuts *inside* the primary card and no layout change is planned, the card makes a tiny settle: it is 2 % larger on the cut frame and settles to 100 % in 5 f (ease-out-quart). It marks the cut without moving the grid.

**Flow prompt text:** "When the shot inside the card changes, the card makes a tiny, quick settle, barely noticeable."

---

### E10 · EXIT DRIFT — CUT ●●

**What it is:** All cards accelerate to the right for 4–5 frames, then a hard cut to the next state (E11 white page, or a new SOLO card via E01).

**Motion:** every card x offset 0 → +0.05 W (portrait) / +0.06 W (landscape) over 4 f, ease-in-quad; frame 5 = next state. Measured on the reference: 3.97–4.10 s, then the white page at 4.13 s.

**Flow prompt text:** "The cards slip quickly to the right for a split second and the scene cuts cleanly to {{NEXT_STATE}}."

---

### E11 · TITLE PAGE — TYPE ●●● (signature closer, full white)

**What it is:** A pure white page with one huge bold black word centred, and the captions floating below (E05). Only for the last ≤ 1.5 s / ≤ 15 % of the video (Part 1.6).

**Text (✎):** one user word: the payoff, verb or call to action of the final line ("WATCH", "SAVE", "START"). UPPERCASE, ≤ 9 letters.

**Graphics:** INK, title font, cap height 0.040 H, tracking −2 %, centred at (0.5 W, 0.440 H). Appears on the cut frame, fully formed (no animation, no fade).

**Flow prompt text:** "The scene cuts to a pure white page with the single word \"{{WORD}}\" in huge, bold, black capitals in the centre. Nothing else moves."

---

### E12 · TAGLINE — TYPE ●

**What it is:** A small, letter-spaced monospaced line under the title word, typed on 0.5–0.8 s after the title appears and held to the end.

**Text (✎):** ≤ 4 user words from the final line (e.g. "WHAT HAPPENS"), UPPERCASE, ≤ 24 characters.

**Graphics:** INK, tagline font, centred, baseline 0.030 H below the title's baseline. Type-on 2 letters per frame.

**Flow prompt text:** "Under the big word, a short line \"{{TAGLINE}}\" types on in tiny, spaced-out black typewriter capitals."

---

### E13 · TITLE CARD — CARD + TYPE ●●● (closer that keeps the footage)

**What it is:** The primary card glides up into the TITLE-CARD box (upper part of the page, footage still playing), and the title word appears below it on white, followed by the tagline. Default closer for user videos.

**Motion:** card box → TITLE-CARD box over 8 f, ease-out-quart (or on a cut via E10 → E01-style settle into TITLE-CARD). Title word at (0.5 W, 0.665 H), appearing on the frame the card lands; tagline under it (E12) 0.5 s later; the caption floats at 0.86 H (E05).

**Flow prompt text:** "The card glides up into the top half of the white page and keeps playing; below it the word \"{{WORD}}\" appears in huge bold black capitals, then a tiny spaced-out line \"{{TAGLINE}}\" types on under it."

**Still-image state:** this is the default poster layout.

---

### E14 · LIST INDEX — TYPE ● (extension in the same grammar)

**What it is:** For lists and steps, a tiny monospaced counter ("01", "02", "03") typed in the top-left corner of the primary card's outside margin, updating as each item is spoken.

**Graphics:** INK, tagline font, baseline 0.008 H above the primary card's top-left corner, left-aligned to it (inset 0.04 W if the card bleeds off the left edge). Type-on 2 letters per frame; the old number types off in 2 f before the new one types on.

**Use when:** the captions list 2–5 items. Numerals only, no other words.

**Flow prompt text:** "As each item of the list is spoken, a tiny black monospaced number (01, 02, 03) types on just above the top-left corner of the card."

---

### E15 · CARD DRIFT — CARD ● (keeps long shots alive)

**What it is:** Inside a card, the footage slowly pushes in (cover scale 100 % → 104 %, linear) over the shot, anchored on the subject. The card itself doesn't move.

**Use when:** any shot longer than 1.5 s with no other card motion. Never during E06.

**Flow prompt text:** "Inside the card the shot drifts in very slowly."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll montage → talking head | E01 + E02 + E03 | E06 → E07 at the first cut; E08 on each later cut, alternating layouts; E14 for lists; E15 on long shots | E13 (or E10 → E11 if the last shot is ≤ 1.5 s) + E12 |
| Single talking-head shot | E01 + E02 + E03 | E06 at sentence ends → E07 with a second crop of the same shot (wide + close); E15 | E13 + E12 |
| B-roll only (no face) | E01 + E02 | E08 on every cut through SPLIT-A/B and STACK; E09 for cuts kept inside a card | E10 → E11 + E12 |
| Still image (poster) | E01 settled | E02 keyword + E03 caption | E13 title + E12 tagline |

Each video gets its own selection based on its own hook points (SKILL.md step 4). Never paste a row blindly.
