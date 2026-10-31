# moments.md — Gradient Stack: Style Bible + Moment Library

This file is the single source of truth for the Gradient Stack caption style. Part 1 is the style bible (palette, type, lanes, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, measured on a 720x1280, 30 fps, 10.0 s reference reel of a speaker walking toward the camera in a bright room. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: the footage always stays full frame and untouched.

**The look in one line:** small tight white bold sans words build a short line with a soft shadow, and one giant extra-bold keyword with a colour gradient (bright on the left, dark on the right) blurs in right under it; each phrase sits in the top lane or the middle lane, alternating, and fades out as the next one in its lane arrives.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, lane…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 30 fps, so "f" values are 30 fps frames; at another fps keep the seconds. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Small-word white | #FFFFFF | Small caption words |
| Small-word shadow | #000000 at 60 % | Soft shadow under small words (0, +3 px, blur 3.5 px at 720 wide) |
| Keyword colour 1 indigo | #2E1A86 | Keyword fill at its left edge (measured L 31,18,82 after the gradient started) |
| Keyword colour 2 azure | #1F86B0 | Keyword fill, left edge (measured 31,101,131) |
| Keyword colour 3 green | #2A923E | Keyword fill, left edge (measured 33,95,44) |
| Keyword colour 4 violet | #862CAA | Keyword fill, left edge |
| Keyword colour 5 royal blue | #2436A8 | Keyword fill, left edge (measured 27,37,108) |
| Keyword colour 6 olive | #8EA32C | Keyword fill, left edge (measured 104,109,56 in shade) |
| Keyword colour 7 teal | #1F9480 | Keyword fill, left edge (measured 31,132,113) |
| Keyword colour 8 rose | #C04A55 | Keyword fill, left edge (measured 146,74,63 in shade) |
| Gradient end | colour × 0.35 | The keyword's right edge (measured ratio 0.30–0.40) |

Each keyword takes the next colour of the cycle in order (K2). Brand-swap rule: if the user gives a brand colour, use it as keyword colour for every keyword (keep it saturated, mid-dark, readable on footage); white stays white. No other colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, boxes, borders, masks, blur plates, dimming or colour overlays. |
| Caption chunk | Two stacked parts, both centred on x = 0.50W: the small line (pre-keyword words) and the keyword directly under it. No box, no underline, no outline. |
| Keyword gradient | Horizontal, left edge = keyword colour, right edge = colour × 0.35, linear. |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor ✎ = the speaker's face box (or the main subject). |

### 1.3 Layouts / grid

Lanes are defined by the small line's centre y. The keyword baseline sits 0.94 × keyword size below it.

| Lane | Small-line centre y | Keyword region (reference size) | Use |
|---|---|---|---|
| A — top | 0.104H [200] in the reference; 0.034H [65] when the face top is at 0.15H | y 0.13–0.20H (reference) | Phrases 1, 3, 5… |
| B — middle | 0.46H [883] (measured 0.44–0.46H) | y 0.49–0.56H | Phrases 2, 4, 6… |
| C — lower (extension) | 0.70H [1344] | y 0.73–0.80H | When lanes A and B collide with a face or the subject |

Edge rule: every glyph stays ≥ 0.04W from the left and right edges (the reference keyword reached x 0.01W–0.95W while sliding in; the settled state stays inside).

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Small word | Geometric sans, semibold, mixed case as written, tight tracking | Poppins SemiBold | Montserrat SemiBold, Outfit SemiBold | 0.07W [76]; letter-spacing −0.03em; word gap 0.22 em. Measured: "Some homes get" = 0.57W wide |
| Keyword | Same family, extra bold, lowercase or as written, very tight tracking, gradient fill, no outline, no shadow | Poppins ExtraBold | Poppins Black, Montserrat ExtraBold | 0.16W [173] by default (reference ran 0.16–0.18W); letter-spacing −0.04em; auto-shrink so the width ≤ 0.84W |

Rules: text case exactly as the user wrote it (no forced case). Keyword keeps its trailing punctuation as written. Never rotated, never outlined. Small words carry the shadow; keywords carry none.

### 1.5 Motion language

| Family | Easing | Typical duration (reference at 30 fps) |
|---|---|---|
| Small word entrance | ease-out cubic: alpha 0 → 1 in place (no slide) | 0.27 s (8 f) |
| Keyword entrance | ease-out cubic: alpha 0 → 1, blur radius 14 px → 0 (at 720 wide), slide in from the left by 0.04W | 0.30 s (9 f) |
| Chunk exit | linear alpha 1 → 0 for the whole chunk (small words and keyword together) | 0.30 s (9 f) |
| Cuts | caption is not touched by cuts; no mode change | 0 f |

Never: bounce, overshoot, letter-by-letter typing, scale pops, colour flashing, rotation, wipes, glitch, shake.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text overlays with their shadow | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; blur, glitch, warp, zoom, flashes or colour grading of any kind; cards, splits, B-roll frames, background swaps. Footage is never hidden or darkened. The primary footage plays live, in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | The keyword may touch hair or the top of the head by its descenders only; it never covers the forehead, eyes, nose or mouth. Check lane A: keyword baseline + 0.3 × keyword size must be ≤ face top + 0.02H, else lower the face-top margin by shifting lane A up (min small-line centre 0.03H) or shrink the keyword. |
| Lane B | Valid when the face bottom edge ≤ 0.43H; otherwise use lane C. |
| Lane C | Valid when the face box does not reach below 0.66H; else use lane A. |
| Overlap | A chunk may sit over the speaker's body, clothes or B-roll objects (as the reference does), but not over readable footage text for more than 1 s. |
| Edges | Glyphs ≥ 0.04W from the left and right edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **K** keyword · **T** title/opener · **E** end.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · OPENER PHRASE — T ●● (signature opener)
**What it is:** the first chunk of the video starts in lane A on the first spoken word, so the screen is never bare while the speaker starts talking.
**Use when:** every video. **Avoid when:** the first 0.3 s contains a cut (then start the chunk after the cut).
**Text (✎):** the user's first 1–3 words as the small line, then the first meaning-carrying word as keyword.
**Geometry / Graphics:** lane A, per C1 and K1. In the reference the opener was "Some homes get" + keyword at 0.20–1.10 s.
**Motion:** C1 words from the first word's start, K1 at the keyword's start; lifetime per C3.
**Footage / plate behaviour:** untouched; the face box is visible from frame 0.
**Captions during it:** this is the first caption.
**Exit:** C3 fade.
**Build notes:** lane A margin per 1.7 when the face top is high (demo: small-line centre 0.034H, keyword 0.16W).
**Flow prompt text:** "Right at the start, a short line of small white words appears word by word near the top of the frame, and one large bold word in {{COLOUR}} fades in sharply from a blur right under it. It never covers the speaker's face."
**Still-image state:** the chunk, settled.

### C1 · SMALL WORD LINE — C ●● (signature, the caption system)
**What it is:** the words before the keyword build left to right as one small bold white line with a soft shadow; each word fades in exactly in place (no slide, so spacing never changes); earlier words never move.
**Use when:** always. **Avoid when:** never.
**Text (✎):** the user's exact words, case as written; 1–4 words before the keyword (0 words = K4). A chunk never crosses a sentence boundary: a word ending in . ! or ? is the last word of its chunk (if it is the only word left, it becomes a solo keyword, K4). One phrase at a time: the previous phrase (small line and keyword together) must be gone by ≤ 0.15 s after the next phrase's first word; never two phrases on screen longer than that cross-fade.
**Geometry / Graphics:** small line per 1.4, centred on x = 0.50W at the lane's centre y. The whole line is laid out once at its final width, spaces included, before the first word appears; each word has fixed final x and is only revealed there. Word gap 0.22 em.
**Motion (measured on the reference, 30 fps; words started 0.20, 0.50, 0.73 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha | 0 → 1 | ease-out cubic, 8 f |
| word start ✎ | earlier words | — | unchanged | — |

Word start = the word's spoken start time.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** C3.
**Build notes:** render each word separately at 2× with its shadow baked in (blurred copy of the glyph mask, offset down), downscale, then composite per frame with alpha and x offset.
**Flow prompt text:** "Small white bold words appear one after another in a tight line, each fading in softly in place, with a soft dark shadow under the letters. The only words are {{SMALL_WORDS}}."
**Still-image state:** the full small line.

### K1 · GIANT GRADIENT KEYWORD — K ●●● (signature)
**What it is:** one meaning-carrying word, huge and extra bold, directly under the small line. It comes in out of a blur, sliding a few pixels from the left, and its colour runs from bright on the left edge to dark on the right.
**Use when:** every chunk has one. **Avoid when:** never; at most one per chunk.
**Text (✎):** one user word, as written (with its trailing punctuation). Choose a noun, verb or number that carries the meaning; never an article, preposition or conjunction. Make it the last word of its chunk.
**Geometry / Graphics:** Keyword type per 1.4, centred on x = 0.50W. Baseline = lane small-line centre y + 0.94 × keyword size. Colour from the cycle (K2) with the gradient per 1.2. Font size 0.16W, shrunk until the width ≤ 0.84W (K3). No shadow.
**Contrast (generic rule):** before building, measure the mean luma of the footage under the keyword's box at keyword start + 0.35 s. Luma ≥ 0.50: dark gradient (as 1.1) with a soft white halo (glyph mask blurred 9 px at 2×, 60 %). Luma < 0.50: light gradient (left = colour + 62 % toward white, right = colour + 28 % toward white) with a soft dark halo (45–55 %). Keywords must stay clearly readable on mid-tone shots such as beige clothing.
**Motion (measured on the reference, 30 fps; keyword at 1.10 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| keyword start ✎ | keyword | alpha | 0 → 1 | ease-out cubic, 9 f |
| keyword start ✎ | keyword | blur radius | 14 px → 0 | ease-out cubic, 9 f |
| keyword start ✎ | keyword | x offset | −0.04W → 0 | ease-out cubic, 9 f |

Keyword start = the keyword's spoken start time.
**Footage / plate behaviour:** untouched; the keyword may overlap hair, shoulders or objects but never a speaking face (1.7).
**Captions during it:** sits under the small line of its own chunk.
**Exit:** C3.
**Build notes:** draw the glyph mask at 2× with per-letter tracking, fill with a numpy horizontal gradient, downscale; per frame apply `GaussianBlur(14·(1−e))` and alpha on the pre-rendered patch.
**Flow prompt text:** "Directly under the small line, one very large, heavy, rounded word, {{KEYWORD}}, comes into focus out of a blur while sliding in a little from the left. Its colour is {{COLOUR}}, bright at the left edge and darkening to the right."
**Still-image state:** the keyword, settled.

### K2 · KEYWORD COLOUR CYCLE — K ● (signature detail)
**What it is:** every keyword gets a different deep colour, taken in order from the palette, so consecutive keywords never match.
**Use when:** always. **Avoid when:** the user gave a brand colour (use it for every keyword).
**Text (✎):** none. **Geometry / Graphics:** colours 1–8 of 1.1 in order, then repeat from 1; never the same colour twice in a row.
**Motion:** none. **Footage / plate behaviour:** untouched. **Captions during it:** per K1. **Exit:** none.
**Build notes:** `PAL[chunk_index % 8]`.
**Flow prompt text:** "Each large word has its own deep colour, different from the one before it: {{COLOUR_LIST}}."
**Still-image state:** the chosen colour.

### C2 · ZIGZAG LANES — C ●● (signature)
**What it is:** chunks alternate between the top lane and the middle lane, so the eye zigzags down and up the frame; only one phrase is on screen at a time.
**Use when:** every video with 2+ chunks. **Avoid when:** lane A or B fails the face rule (use lane C, or the other lane).
**Text (✎):** none. **Geometry / Graphics:** chunk 1 lane A, chunk 2 lane B, chunk 3 lane A, … Lane geometry per 1.3.
**Motion:** none of its own; a lane is free as soon as its previous chunk ends (C3).
**Footage / plate behaviour:** untouched.
**Captions during it:** one chunk at a time (a ≤ 0.15 s cross-fade at each change).
**Exit:** C3.
**Build notes:** assign lanes per chunk, then validate against the scene table (1.7) and switch the failing chunk to lane C.
**Flow prompt text:** "The caption phrases alternate between the upper part of the frame and the middle of the frame, one after the other, so a new phrase appears in the other position while the previous one is still fading."
**Still-image state:** two chunks, one per lane (optional).

### C3 · CHUNK LIFETIME AND FADE — C ●● (signature timing)
**What it is:** a chunk stays after its keyword lands, then fades out as one block.
**Use when:** every chunk. **Avoid when:** it is the last chunk (E1).
**Text (✎):** none. **Geometry / Graphics:** none.
**Motion (measured on the reference, 30 fps: keyword landed 1.10 s, gone at 3.2 s; the next keyword in its lane landed at 3.5 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| end − 0.30 s ✎ | whole chunk | alpha | 1 → 0 | linear, 9 f |

Chunk end ✎ = the next chunk's first word + 0.12 s, with a linear 0.12 s cross-fade starting at that first word (≤ 0.15 s); if the gap to the next chunk is longer than 2.6 s after the keyword, fade out over 0.25 s at keyword start + 2.6 s. Only one chunk is ever on screen apart from that cross-fade.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** this is the exit.
**Build notes:** multiply the chunk layer's alpha by `(end − t) / 0.30` in the last 0.30 s.
**Flow prompt text:** "After about two seconds a caption phrase fades away smoothly as one block, just before the next phrase in the same position arrives."
**Still-image state:** none.

### K3 · LONG KEYWORD FIT — K ●● (extension in the same grammar)
**What it is:** a long keyword shrinks (never wraps) until it fits.
**Use when:** the keyword is longer than 8 characters. **Avoid when:** never; a keyword over 14 characters is not chosen (pick another word).
**Text (✎):** the keyword. **Geometry / Graphics:** reduce the font size in 2 px steps from 0.16W until width ≤ 0.84W. Lane baseline uses the shrunk size.
**Motion:** as K1. **Footage / plate behaviour:** untouched. **Captions during it:** per K1. **Exit:** C3.
**Build notes:** `while width(size) > 0.84*W: size -= 4` (at 2×). Demo: "investments," (12 characters) fitted at about 0.14W.
**Flow prompt text:** "A long keyword, {{KEYWORD}}, is sized smaller so it fits across the frame in one line."
**Still-image state:** the fitted keyword.

### K4 · SOLO KEYWORD — K ●●● (extension in the same grammar)
**What it is:** a payoff word alone, with no small line, at the lane position.
**Use when:** a strong turn or number with nothing before it in its phrase. **Avoid when:** more than 2 per video, or within 3 s of another solo.
**Text (✎):** one user word. **Geometry / Graphics:** K1 spec; the keyword baseline = lane centre y + 0.94 × size as if the small line existed (keeps the lane grid).
**Motion:** as K1. **Footage / plate behaviour:** untouched. **Captions during it:** none besides the keyword. **Exit:** C3.
**Build notes:** chunk with an empty pre-word list.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in large heavy lettering, coming into focus from a blur."
**Still-image state:** the keyword.

### C4 · LOWER LANE — C ●● (extension in the same grammar)
**What it is:** a chunk placed lower (small-line centre 0.70H) when lanes A and B are blocked by a face or the subject.
**Use when:** the shot's face sits in lane A's width or reaches below 0.43H (check against the face of any shot the chunk lives in); a close-up on a face high in the frame. **Avoid when:** the subject sits low (then use lane A).
**Text (✎):** none. **Geometry / Graphics:** lane C per 1.3; same type, same motion.
**Motion:** as C1/K1. **Footage / plate behaviour:** untouched. **Captions during it:** a chunk keeps its lane for its whole life. **Exit:** C3 (ends at the next cut if the lane then conflicts).
**Build notes:** demo used lane C on the grocery shot to keep the checkout customer's face clear.
**Flow prompt text:** "On this shot the phrase sits lower in the frame so it stays clear of the person's face."
**Still-image state:** a chunk at 0.70H.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last chunk stays up to the final frame, with no exit fade (the reference kept its last chunk to the end of the clip).
**Use when:** every video. **Avoid when:** the video continues into another clip.
**Text (✎):** the last chunk's words. **Geometry / Graphics:** lane per C2.
**Motion:** hold; no exit.
**Footage / plate behaviour:** untouched. **Captions during it:** per above. **Exit:** video ends.
**Build notes:** set the last chunk's end to infinity.
**Flow prompt text:** "The last phrase stays on screen until the very end of the video."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 | C1 + K1 + K2 per chunk, C2 lanes, C4 where B-roll or a face blocks, C3 fades | E1 |
| Single talking head, no cuts | T1 | C1 + K1 + K2, C2 lanes, K4 for one payoff word | E1 |
| B-roll only, no speech | T1 (user's words spread over the shots, 1.2–2.5 s per chunk) | C1 + K1 + K2, C2 lanes, C4 on busy shots | E1 |
| Still image + text | T1 settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Face top at 0.15H: lane A small-line centre 0.034H and keyword size 0.16W kept the keyword clear of the head (descenders touch the top of the hair only). At 0.18W and 0.04H the keyword covered hair.
- Chunks used (small words + keyword, lane): Saving + money (A); isn't about + earning (B); solo more. (A); Pay + yourself (B); first, + automate (A); your + investments, (A); and + spend (B); only what's + left. (C); Do it for one + year (B); and watch what + happens. (A, held to the end). Measured luma: dark gradient on 7 of 10 keywords (0.51–0.69), light gradient on "left." (0.40) and "year" (0.47).
- Lane C was needed only on the grocery shot (customer's face at 0.10–0.37H, x 0.50–0.75W blocks lane A's width).
- Keyword start fades the whole keyword in 0.30 s; all keywords read on beige, wood, white and dark shots without outlines.
- M-type moves skipped: this is a caption-only style.
