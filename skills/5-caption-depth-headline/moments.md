# moments.md — Depth Headline: Style Bible + Moment Library

This file defines the **Depth Headline** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*.

**The look in one line:** the footage stays full-frame and untouched while one giant, ultra-condensed white word stands **behind the speaker** (their head and hair overlap it, like it's painted on the wall), flashing **yellow inside a translucent yellow box the instant that word is spoken**, while small bold captions below light up word by word in yellow. The headline word is *not* repeated in the captions: the giant word says it. Hard, punchy cuts; no slides, no fades.

How to use it:
1. Pick moments by ID (SKILL.md, steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, word, placement rung). Everything else (fonts, sizes, colours, timing behaviour, layer order) is the style and stays as written.
4. For a **final video**, build from the spec. For a **Google Flow master prompt**, use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W` = frame width, `H` = frame height, `f` = frames at 30 fps (at other frame rates keep the **seconds**). Reference values in brackets are for 1080×1920. All numbers were measured on the reference video.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| HEAD-WHITE | `#FFFFFF` | the headline word while waiting |
| SIGNAL-YELLOW | `#FEE401` | the headline word while spoken; the active caption word |
| BOX-YELLOW | `#FEE401` at ≈ 35 % | translucent box behind the spoken headline (soft edge) |
| CHIP-YELLOW | `#FEE401` at ≈ 30 % | translucent chip behind the active caption word |
| CAPTION-WHITE | `#FFFFFF` | caption words |
| SHADOW | black 25–40 %, soft | under headline and captions, for legibility |

Two colours only (white and one signal yellow). Brand variant ✎: SIGNAL-YELLOW may become one saturated brand colour; keep white.

### 1.2 Depth (the signature)
- The headline sits **between the background and the person**: composite it over the footage, then cut it away wherever a **person matte** says "person". The speaker's head, hair and shoulders occlude the letters.
- Matte: a person-segmentation model (MediaPipe selfie segmenter, rembg/u2net human seg, SAM). Feather the matte edge ~1.5 px; smooth it over time (blend 60 % new + 40 % previous frame, reset on cuts) so the cut-out edge doesn't shimmer.
- **Legibility rule:** at least **65 % of the glyph area must stay visible**. If the person would hide more, use the next placement rung (1.4). The face is never covered: the word is always *behind* the person.
- Shots with no person (B-roll, products, screens): the headline sits **in front** of the footage in the same position; nothing else changes.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Headline | ultra-condensed heavy grotesk, UPPERCASE, one word | Anton | Bebas Neue, Oswald Bold, League Gothic, Impact | the largest size that fits **0.86 W**, cap height ≤ rung max (≈ 0.21 H) |
| Caption | geometric sans, extra-bold, sentence case as written | Montserrat ExtraBold (wght 800) | Poppins ExtraBold, Inter ExtraBold | 0.036 H [69 px] |

### 1.4 Headline placement rungs (top of the cap height, max cap height)
| Rung | Top | Max cap height | When |
|---|---|---|---|
| A (reference) | 0.11 H | 0.21 H | default |
| B | 0.07 H | 0.17 H | person hides > 35 % at rung A |
| C | 0.045 H | 0.13 H | still > 35 % at rung B |
Measured: "IDEA" 0.144–0.852 W × 0.108–0.321 H; "HIDING" 0.065–0.930 W × 0.128–0.303 H. Centred on W.

### 1.5 Motion language
- **Everything is a hard cut.** Headline words, colour changes, boxes and caption lines switch on a single frame. No slides, fades, scales or bounces.
- **Rhythm (measured):** each headline word is on screen ≈ 1.3–1.5 s: white for 0.5–0.9 s (while the words before it are spoken), then yellow + box for exactly the time the word is spoken (≈ 0.45 s), then the next word replaces it on the frame its group starts.
- The camera/footage never moves.

### 1.6 What may happen to the user's footage
- Nothing moves: the footage stays full-frame, original scale, in sync, untouched. Only overlays are added (headline, boxes, captions) and the headline is cut by the person matte.
- No crop, zoom, blur, recolour, retime or reordering.

### 1.7 Safe zones
- Headline zone: top 0.04–0.33 H. Caption zone: centred on 0.78 H (baseline 0.795 H); if hands/products sit there and matter, raise to 0.70 H.
- Captions never cross a face. The headline never sits in front of a face (it's behind the person, or in front only when there is no person).

---

## PART 2 — MOMENT LIBRARY

Family codes: **HEAD** (headline), **CAP** (captions). Energy: ● low · ●● medium · ●●● high.

---

### D01 · DEPTH HEADLINE — HEAD ●●● (signature, always on)

**What it is:** One giant ultra-condensed white word behind the speaker, centred at the top of the frame.

**Word (✎):** the key word of the current phrase, taken from the user's text (noun, verb, number or payoff), UPPERCASE, punctuation dropped. One word only (≤ 10 letters reads best; longer words shrink to fit 0.86 W).

**Timing (✎):** appears on the first frame of its **group** (the phrase it belongs to), hard cut; it is shown *before* it is spoken (the reference shows "IDEA" 0.9 s early). It is replaced, hard cut, on the first frame of the next group. Groups never cross a footage cut (switch the word on the cut).

**Graphics:** HEAD-WHITE, Anton, size and position per 1.3/1.4 rung; soft shadow (0/+3 px, blur 5 px, 28 %). Matte cut-out per 1.2.

**Flow prompt text:** "Behind the person, as if painted on the wall, the single word \"{{WORD}}\" stands in huge, tall, ultra-condensed white capitals across the top of the frame; the person's head and hair overlap the letters. It appears instantly, no animation."

**Still-image state:** the word in white behind the person.

---

### D02 · YELLOW HIT — HEAD ●●● (signature)

**What it is:** The instant the headline word is spoken, it turns SIGNAL-YELLOW and a translucent yellow rounded box appears behind it (also behind the person). When the word ends, it snaps back to white (or the next group starts).

**Timing (✎):** from the word's spoken start to its end (≈ 0.4–0.5 s). Measured on the reference: "IDEA" yellow 1.50–1.97 s, "HIDING" 2.47–2.90 s, "SIGHT" 3.90–4.33 s.

**Graphics:** text SIGNAL-YELLOW; box BOX-YELLOW, rounded (radius 0.035 W), padded 0.06 W left/right and 0.03 H top/bottom around the glyphs, edge softened 0.006 W. Both cut by the person matte like the word.

**Flow prompt text:** "The moment the word \"{{WORD}}\" is spoken, the big headline snaps to bright yellow with a soft see-through yellow box behind it, then snaps back to white when the word ends."

---

### D03 · KARAOKE CAPTION — CAP (signature, always on)

**What it is:** A short line (1–3 words) of small extra-bold white captions centred low in the frame. The word being spoken turns yellow with a translucent yellow chip behind it. **The headline word is not in the captions**: during the yellow hit the caption line is all white (nothing active), because the giant word is the one being said.

**Text (✎):** the user's words verbatim, minus the headline words, 1–3 words per line, ≤ 22 characters. A group may have two caption lines in sequence (switch on the first word of the second line).

**Graphics:** CAPTION-WHITE Montserrat ExtraBold 0.036 H, centred, baseline 0.795 H; soft shadow (0/+2 px, blur 3 px, 40 %). Active word: SIGNAL-YELLOW text + CHIP-YELLOW rounded chip (radius 0.010 W, padding 0.010 W) behind it.

**Timing:** the line appears (hard) with its group or with its first word; each word is active from its spoken start to its end; lines switch hard.

**Flow prompt text:** "Small bold white captions centred low in the frame show only these lines, in order: [a-b s] \"{{LINE_1}}\", … The word being spoken turns yellow with a faint yellow highlight behind it. The big headline word never appears in the captions."

---

### D04 · HEADLINE SWAP ON CUT — HEAD ●●

**What it is:** When the footage cuts, the headline switches to the next group's word on the cut frame (hard), so cuts and words land together. If a group would cross a cut, end it on the cut.

**Flow prompt text:** "On every cut, the big headline word changes instantly to \"{{NEXT_WORD}}\"."

---

### D05 · RUNG STEP — HEAD ● (adaptive placement)

**What it is:** For a group where the person (e.g. a close-up or a person standing high in frame) would hide more than 35 % of the letters, the headline uses rung B or C: higher and smaller. Chosen once per group (never changes mid-group).

**Flow prompt text:** "The headline sits a little higher and smaller here so the person's head doesn't hide most of it."

---

### D06 · CLEAN TAIL — CAP ● (ending)

**What it is:** After the last word, headline and captions disappear together (hard) and the footage plays clean for its remaining frames. The reference ends with 0.6 s clean. If the video ends right after the last word, keep the last group to the end instead.

**Flow prompt text:** "After the last word, all text disappears and the video plays clean to the end."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Plan |
|---|---|
| Talking head (single shot) | D01 + D02 + D03 throughout, one headline word every 1.2–2 s; D05 when they lean in; D06 at the end |
| Talking head ↔ B-roll | same, plus D04 on every cut; on B-roll shots the headline is in front (no person) |
| Lists | one headline per item (the item's key word), captions carry the rest |
| Still image (poster) | D01 behind the person + one D03 line; or D02's yellow state for extra punch |

Each video gets its own grouping based on its own hook points (SKILL.md step 4). Never paste a row blindly.
