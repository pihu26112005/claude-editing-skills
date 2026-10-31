# moments.md — Vermilion Cards: Style Bible + Moment Library

This file defines the **Vermilion Cards** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*.

**The look in one line:** a hot vermilion-orange (and later saffron-yellow) page; footage sits in sharp cards with a hard black offset shadow, or runs full-frame between two orange bands that carry a giant ultra-condensed cream title; captions are small cream label boxes with the newest word flashing orange; a black diagonal wedge wipes between layouts.

How to use it:
1. Pick moments by ID (SKILL.md, steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, text, which footage goes in which card, crop anchor). Everything else is the style.
4. For a **final video**, build from the spec. For a **Google Flow master prompt**, use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W` = frame width, `H` = frame height, `f` = frames at 30 fps (at other frame rates keep the **seconds**). Reference values in brackets are for 1080×1920. Measured on a 540×960, 30 fps reference.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| VERMILION | `#FE3B00` | page of the stack layout, title bands, newest-word colour |
| SAFFRON | `#F3AD01` | page of the single-card layout (V08) |
| CREAM | `#E0D1BC` | title letters, caption label boxes, plain captions |
| INK | `#1B1B1B` | card shadows, wedge, caption text |

No other colours; the footage carries everything else. Brand variant ✎: VERMILION and SAFFRON may be swapped for two brand colours of similar strength; CREAM and INK stay.

### 1.2 Containers
- **Full-frame:** footage fills the frame. Two bands overlay it (V01), nothing else changes.
- **Card:** rectangle with 0.007 W radius, cover-fit crop (✎ anchor), **hard offset shadow**: INK, no blur, extruded diagonally down-right by 0.014 W [15 px] at rest.
- **Stack card boxes:** top x 0.09–0.91 W, y 0.055–0.474 H; bottom x 0.09–0.91 W, y 0.551–0.957 H [0.12 W gap between them for a caption].
- **Single card box (V08):** x 0.087–0.92 W, y 0.049–0.963 H.
- Pages are flat colour; no texture, no gradient.

### 1.3 Layouts

| Layout | Page | Content |
|---|---|---|
| FULL + BANDS | footage | top band y 0–0.17 H, bottom band y 0.83–1 H, both VERMILION (reference 0.197 H; 0.17 keeps hair and faces clear) |
| STACK | VERMILION | two cards, plain captions between them |
| SINGLE | SAFFRON | one tall card, label captions |

### 1.4 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Title | ultra-condensed heavy grotesque, UPPERCASE, CREAM, left-aligned from x −0.004 W, repeated in both bands | Anton | Bebas Neue, League Gothic, Oswald Bold | cap height 0.12 H [230 px], shrunk so the word fits 0.96 W |
| Label caption | semibold sans, original case, INK on a CREAM box | Inter SemiBold (wght 600) | Plus Jakarta Sans 600, Manrope 600 | 0.039 H [75 px]; box height 0.052 H, side padding 0.014 W |
| Plain caption | medium sans, CREAM, no box, centred | Inter Medium (wght 500) | Plus Jakarta Sans 500 | 0.034 H [65 px], shrink to fit 0.84 W |

### 1.5 Motion language
- **Hard and punchy:** captions pop with no fade; layouts switch on footage cuts; the only soft curves are ease-out-cubic (arrivals) and ease-in-out-cubic (wedge).
- **Card arrival:** scale up from 62 % with a huge shadow that retracts (V04).
- **Pop:** 6 % overscale and a 0.04 W shadow settle back over 0.2 s (V05).
- No bounce, no rotation, no fades on cards. Letters of a title fade in individually.

### 1.6 What may happen to the user's footage
- Allowed: cover-fit crops into cards; full-frame footage with the two bands laid on top (bands never cover a face); uniform scale during pops and drops.
- The **primary footage always plays live, in sync with the audio**: full-frame, or the bottom card of a stack, or the single card. The top card of a stack shows the user's own previous shot as a **still** (≤ 1 shot old).
- Never recolour or filter footage. Never retime, reorder or trim.
- Exception: **footage is cropped** when it sits in a card (shape change only).

### 1.7 Safe zones
- Faces are never under a band, a label, a wedge or a shadow. In FULL + BANDS captions sit at y 0.64 H, under the chin of a normal talking head; if a face is lower than 0.55 H, move the label to y 0.80 H [✎].
- Cards: set the crop anchor so the face sits inside its card with ≥ 6 % margin.

---

## PART 2 — MOMENT LIBRARY

Families: **BAND**, **CARD**, **CAP**, **CUT**. Energy: ● low · ●● medium · ●●● high.

---

### V01 · BAND OPEN — BAND ●●● (signature opener)

**What it is:** Over full-frame footage, a vermilion block appears top-left and one bottom-right; both sweep across to become full-width bands.

**Use when:** the opening line; any talking-head stretch ≥ 1.5 s (also the closer, V09). **Avoid when:** a face sits in the top 17 % or bottom 17 % of the frame.

**Geometry:** top band x 0–W, y 0–0.17 H; bottom band x 0–W, y 0.83–1 H (✎ height may shrink to 0.14 H for tight framing).

**Motion (measured):**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 3 | both blocks | width | pop to 0.12 W | hard |
| 3 → 9 | top block (anchored left), bottom block (anchored right) | width | 0.12 W → W | ease-out-cubic |

Starts 0.10 s into the video. Bands stay until the layout changes.

**Build notes:** draw plain rectangles on the live frame.

**Flow prompt text:** "Two bold orange-red bars sweep in across the top and the bottom of the frame, the top one from the left and the bottom one from the right, while the video keeps playing between them."

---

### V02 · TITLE REVEAL — BAND ●●● (signature)

**What it is:** A giant condensed word fills both bands; its letters fade in one by one in a scrambled order.

**Text (✎):** one user word (topic or verdict), UPPERCASE, ≤ 9 letters.

**Graphics:** CREAM, repeated identically in both bands, vertically centred in each band, left-aligned, size per 1.4.

**Motion (measured):** after the bands finish (≈ 6 f after V01 starts), each letter goes 0 → 100 % over 5 f (0.17 s); letter start times are spread over 7 f in a scrambled order (not left to right).

**Exit:** leaves with the layout change (hard).

**Flow prompt text:** "The word \"{{TITLE}}\" appears in huge, tall, narrow cream capitals inside both bars, the letters fading in one at a time in a scattered order."

---

### V03 · LABEL CAPTIONS — CAP ●● (signature, always on in FULL and SINGLE layouts)

**What it is:** Small cream boxes with black text that grow word by word; the newest word is orange for 0.4 s, then black.

**Text (✎):** the user's words verbatim, chunks of 2–4 words (≤ 26 characters), original case. Each word pops at its spoken time (no fade). A chunk wider than 0.66 W breaks onto a second box stacked under the first (gap 0.004 H).

**Graphics:** left edge x 0.15 W, top y 0.64 H; box CREAM, text INK, newest word VERMILION; sizes per 1.4.

**Exit:** the chunk disappears at its end (hard).

**Flow prompt text:** "Small cream label boxes with black text appear low on the frame and grow one word at a time; the newest word flashes orange for a moment, then turns black. The line is: \"{{LINE}}\"."

---

### V04 · CARD DROP — CARD ●●● (signature)

**What it is:** On a cut, the page turns vermilion and two cards drop in: the new shot live in the lower card, the previous shot as a still in the upper card. Each card grows from small while its black shadow retracts.

**Use when:** person → B-roll cut, or any cut after FULL + BANDS. **Avoid when:** the new shot has a face that cannot fit a card.

**Content (✎):** bottom = current footage (live); top = previous shot's calm still, or the person if the story needs the speaker.

**Motion (measured):**

| t (f @30) | Property | From → To | Ease |
|---|---|---|---|
| 0 → 10 | card scale (about its centre) | 62 % → 100 % | ease-out-cubic |
| 0 → 10 | shadow offset | 0.17 W → 0.014 W | ease-out-cubic |
| 0 → 10 | cards' centre x | −0.08 W → 0 | ease-out-cubic |

Starts on the cut frame.

**Captions during it:** V06.

**Flow prompt text:** "On the cut, the screen turns bright orange-red and two framed pictures drop in, one above the other, each growing from small with a hard black block shadow that shrinks as it settles: {{TOP}} on top and {{BOTTOM}} below."

---

### V05 · CARD POP — CARD ●● 

**What it is:** A new shot in an existing layout arrives with a quick scale-and-shadow punch.

**Use when:** a cut that stays inside a stack or single card. **Motion:** 0 → 6 f: scale 106 % → 100 %, shadow 0.054 W → 0.014 W, ease-out-cubic; the content changes hard on the first frame. In a stack the top still updates to the previous shot.

**Flow prompt text:** "On the cut the framed picture lands with a small punch: it is slightly larger for an instant and its black block shadow settles back."

---

### V06 · PLAIN CAPTIONS — CAP ●

**What it is:** Cream text without a box, centred in the gap between the two cards; words pop in one by one.

**Text (✎):** same chunks as V03. **Graphics:** centre x 0.5 W, y 0.5125 H, size per 1.4. **Exit:** hard at chunk end.

**Flow prompt text:** "Cream text with no box sits centred between the two pictures and grows one word at a time: \"{{LINE}}\"."

---

### V07 · WEDGE WIPE — CUT ●●● (signature)

**What it is:** A black slanted band sweeps left to right across the whole frame; behind it the layout changes to the single saffron card.

**Use when:** a cut from a stack or bands to a calm hero shot; a section change. **Avoid when:** a face is expected to be on screen mid-sweep (the wedge crosses it for ~0.1 s; accept only on B-roll).

**Geometry:** band width 0.45 W, slant 0.30 W over the full height, INK.

**Motion:** 12 f @ 24 fps (0.5 s), ease-in-out-cubic; centre x from −0.37 W to 1.37 W. Left of the band: new layout; right: old layout (still updating live content).

**Flow prompt text:** "A black slanted band sweeps from left to right across the whole frame; behind it the orange-red page turns saffron yellow and the pictures become one tall framed picture."

---

### V08 · SAFFRON CARD — CARD ●● 

**What it is:** One tall card (box 1.2) on the saffron page with label captions (V03).

**Content (✎):** current footage, live; anchor ✎ on the face. **Hold:** any length; use V05 on cuts.

**Flow prompt text:** "The video plays inside one tall framed picture with a hard black block shadow on a saffron yellow page."

---

### V09 · BAND CLOSE — BAND ●●● (signature closer)

**What it is:** V01 + V02 again on the final section, with the payoff word as title.

**Text (✎):** one user word from the last line. **Motion:** as V01/V02, starting 0.1 s after the layout cut.

**Flow prompt text:** "Two bold orange-red bars sweep in across the top and bottom again and the word \"{{TITLE}}\" fills them in huge cream capitals, letter by letter."

---

### V10 · SOLO CARD — CARD ●● (extension in the same grammar)

**What it is:** B-roll-only videos: one card on vermilion (box 1.2, same shadow) with V04's arrival, plain captions below the card.

**Use when:** no speaker anywhere. **Flow prompt text:** "A single framed picture with a hard black block shadow drops onto an orange-red page; cream text sits beneath it."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | V01 + V02, V03 | V04, V05, V06, V07 + V08 | V09 |
| Single talking head | V01 + V02, V03 | V07 + V08 half way | V09 |
| B-roll only | V10 | V04 / V05, V07 + V08 | V08 |
| Still image | V08 settled (saffron page) | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
