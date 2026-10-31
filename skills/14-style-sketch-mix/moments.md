# moments.md — Sketch Mix: Style Bible + Moment Library

This file defines the **Sketch Mix** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*. Measured on a 540x960, 30 fps reference reel (8 s, three beats: talking head, B-roll with the speaker in a circle, cream paper page), then tuned on a 720x1280, 24 fps render.

**The look in one line:** a sketchbook mixed into a reel. A fat white keyword sits inside a loose double-stroke pencil ellipse, handwritten and bold captions arrive one word at a time, the speaker keeps talking from a round bubble over B-roll, and a cream paper page holds a hand-circled phrase.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, text, side, anchor, content). Everything else is the style.
4. Final video: build from the spec. Google Flow master prompt: use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W`, `H`, `f` (frames at 30 fps; at other frame rates keep the **seconds**). Reference values in brackets are for 1080x1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| PAPER | `#FAF4ED` | the cream page (SK05) |
| PENCIL | `#E2DACD` at 88 % (second pass 70 %) | scribble ellipse over footage |
| INK | `#3A3935` | page ink: circle, handwriting, bold caption on paper |
| WHITE | `#FFFFFF` | keyword, captions over footage |
| SHADOW | `#000000` at 30–50 %, blur 0.007 W | soft shadow under white text |

No other colour is added. Brand variant ✎: PAPER may become another warm neutral; ink stays near-black.

### 1.2 Containers / shapes
- **Full frame:** all footage plays full frame, untouched. There are no cards or borders.
- **Speaker bubble:** a circle, diameter **0.50 W** [540], centred at x = 0.75 W (or 0.25 W) and y = 0.235 H [450]; flush with the frame edge. No border, no shadow.
- **Scribble ellipse:** two loose hand-drawn passes (1.9 and 1.6 turns) with a wobble of ±1.2 %, rotated −4° (left end lower), stroke 0.0065 W [7] and 0.0045 W [5].
- **Paper page:** full-frame flat PAPER colour, no texture.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | ultra-heavy sans, UPPERCASE, white, tight | Archivo (wght 900, wdth 100) | Montserrat Black, Inter Black, Anton | widest allowed 0.52 W; start 0.075 H [144] and shrink |
| Hand caption | round handwriting, bold, white | Gaegu Bold | Patrick Hand, Caveat, Gochi Hand | 0.058 H [111] |
| Bold caption | geometric heavy sans, sentence case | Montserrat (wght 800) | Inter ExtraBold, Poppins Bold | 0.049 H [94] |
| Page phrase | handwriting, dark ink, 2–3 short lines | Gaegu Bold | same as hand caption | 0.080 H [154], line pitch 0.080 H |
| Page caption | as bold caption, INK colour, no shadow | Montserrat 800 | same | 0.049 H |

### 1.4 Motion language
- **Draw-on:** strokes are revealed along their path in 7 f (0.23 s), ease-out-cubic; a second pass follows 1 f later.
- **Wipe:** text appears or leaves by a left-to-right crop of its own width (6 f in, 5 f out), ease-out-cubic.
- **Word fade:** each caption word fades in over 4 f (0.17 s), ease-out-cubic, at its spoken time, in its final position. Words never move.
- **Bubble pop:** diameter 0.14 W to 0.50 W over 8 f with a tiny overshoot (ease-out-back, 1.2), starting 5 f after a cut.
- **Page fade:** the paper fades in over 5 f.
- Nothing bounces except the bubble pop, nothing rotates while moving, nothing slides.

### 1.5 What may happen to the user's footage
- Allowed: overlays (keyword, ellipse, captions); a **bubble** showing the speaker (live footage if the speaker is on screen in the current shot, otherwise a still of the speaker or a ≤ 1.5 s silent loop); a cream page that covers a **B-roll shot with no person** for at most 1.5 s (≤ 15 % of the video).
- The primary footage plays full frame, in sync with the audio, except under the page.
- Forbidden: colour grading, speed changes, trimming, reordering, replacing anything, blurring, cutting a face out, and covering any face that is speaking.

### 1.6 Safe zones
- Keyword + ellipse sit below the chin: centre y = the lower of 0.50 H and (face bottom + 0.09 H). Keep the ellipse top at least 0.02 H under the chin. Recheck on shots that zoom in.
- Hand and bold captions sit at y = 0.665 H and 0.675 H (baseline); when a face reaches below 0.55 H, move the caption to 0.775 H.
- The bubble sits in the top corner opposite any visible face (check the B-roll's face box).
- Never put the bubble over a speaking face.

---

## PART 2 — MOMENT LIBRARY

Families: **K** keyword, **C** caption, **B** bubble, **P** page, **X** extension. Energy: ● calm, ●● medium, ●●● punchy.

### SK01 · SCRIBBLE WORD — K ●●● (signature)
**What it is:** a fat white UPPERCASE word inside a hand-drawn double ellipse that draws on, then wipes away before the next cut.
**Use when:** a talking-head shot has a theme word or contrast word; the opener; the payoff. **Avoid when:** the word would sit on the face, or the shot is shorter than 1 s.
**Text (✎):** one user word (the topic or payoff word), UPPERCASE, up to 7 letters at full size.
**Geometry / Graphics:** word centred at x = 0.50 W, y per safe zone (default 0.50 H). Ellipse centre x 0.47 W, half-width = min(0.47 W, (word width + 0.32 W) / 2), half-height 0.066 H, rotated −4°. Colours PENCIL; word WHITE with SHADOW 30 %.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 | ellipse pass 1 | drawn length | 0 → 100 % over 7 f | out-cubic |
| +1 f | ellipse pass 2 | drawn length | 0 → 100 % over 7 f | out-cubic |
| +2 f | word | left-to-right wipe | 0 → 100 % over 6 f | out-cubic |
| end − 5 f | ellipse + word | erase from the left | 0 → 100 % over 5 f | out-cubic |
**Footage:** untouched. **Captions during it:** hand captions below (SK02).
**Exit:** erased by the end of the shot (at least 0.2 s before a cut); on the last shot it stays to the end.
**Build notes:** draw polylines at 2x and downscale; wipe by cropping the text layer; erase by trimming the start of the path.
**Flow prompt text:** "A thick white capital word, {{WORD}}, is encircled by a loose pencil-style double ellipse that is drawn on in a quarter of a second while the word wipes in from left to right, sits below the speaker's chin for {{DURATION}} seconds, then is erased from left to right. The speaker is never covered."
**Still-image state:** word and both ellipse passes complete.

### SK02 · HAND CAPTION — C ●● (signature caption on talking heads)
**What it is:** white handwritten words appear one at a time, laid out at their final place as a short centred chunk.
**Use when:** any shot where the speaker is the main footage. **Avoid when:** B-roll (use SK03).
**Text (✎):** user words in their own case, 2–3 words, max 20 characters per chunk; split at punctuation and at cuts; never end a chunk on an article or preposition.
**Geometry:** centred at x = 0.50 W, baseline y 0.665 H (0.775 H if the face is low); word gap 1.1 spaces; WHITE with SHADOW 30 %.
**Motion:** each word fades in over 4 f at its spoken time (out-cubic). A chunk shows from its first word to min(next chunk start − 0.05 s, last word start + 0.6 s).
**Footage:** untouched. **Exit:** the whole chunk disappears when the next begins.
**Build notes:** lay out the full chunk first, draw only the words whose time has come.
**Flow prompt text:** "Handwritten white words appear one at a time near the lower middle of the frame, each fading in as it is spoken, in short groups of two or three words, then the group is replaced by the next. They stay clear of the face."

### SK03 · BOLD CAPTION — C ●● (signature caption on B-roll)
**What it is:** the same word-by-word system in a heavy white sans with a soft shadow, for B-roll.
**Use when:** a shot without the speaker as main footage. **Avoid when:** a face sits at y 0.58–0.72 H.
**Text (✎):** as SK02, max 18 characters per chunk.
**Geometry:** centred at x 0.50 W, baseline y 0.675 H; WHITE with SHADOW 50 %.
**Motion:** as SK02. **Footage:** untouched. **Exit:** replaced by the next chunk; hard cut with the shot.
**Flow prompt text:** "Bold white words with a soft shadow appear one at a time in the lower middle of the frame, each fading in as it is spoken, then are replaced by the next short group."

### SK04 · SPEAKER BUBBLE — B ●●● (signature)
**What it is:** when the shot cuts to B-roll, the speaker shrinks into a round window in the top corner and keeps talking.
**Use when:** every cut from the speaker to B-roll and between B-roll shots while the speech goes on. **Avoid when:** a face or key subject sits in that corner (flip the side, SK08); the speaker never appears in the video (skip).
**Content (✎):** the speaker from the nearest talking-head shot: cover-fit crop centred on the face, about 0.46 W wide. Live if the speaker is on screen; otherwise a still (a calm frame with the mouth nearly closed) or a ≤ 1.5 s silent loop.
**Geometry:** circle 0.50 W, centre y 0.235 H, centre x 0.75 W or 0.25 W (✎ side). Anti-aliased edge, no border.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut + 5 f | bubble | diameter | 0.14 W → 0.50 W over 8 f | out-back 1.2 |
**Footage:** B-roll full frame, untouched. **Captions during it:** SK03 at the lower middle.
**Exit:** disappears with the shot at the next cut and pops again on the next B-roll if still needed.
**Build notes:** cache the circular crop per diameter; mask drawn at 3x.
**Flow prompt text:** "Right after the cut, a small round window of the speaker pops open in the {{SIDE}} top corner and grows to about half the frame width, then stays there while the full-frame shot plays."

### SK05 · PAPER PAGE — P ●● (signature closer)
**What it is:** a flat cream page with a hand-circled short phrase and a bold dark caption below it, written word by word.
**Use when:** a B-roll shot with no person near the end (a list, a number, a time phrase, a payoff). Hidden footage ≤ 1.5 s. **Avoid when:** a face is speaking on screen.
**Text (✎):** the phrase (1–3 words, user's case) inside the circle; the spoken chunks as bold captions below.
**Geometry:** PAPER fill. Ellipse centre (0.50 W, 0.295 H), half-width 0.34 W, half-height 0.135 H, two INK passes (0.0065 W, 0.0045 W), rotated −3°. Phrase lines centred in it, pitch 0.080 H. Caption baseline y 0.655 H.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0 | page | opacity | 0 → 100 % over 5 f | out-cubic |
| +5 f + 0.05 s | circle | drawn length | 0 → 100 % over 9 f | out-cubic |
| +3 f later | phrase lines | wipe | 0 → 100 % over 7 f | out-cubic |
**Footage:** covered; the audio goes on. **Exit:** hard cut on the next footage cut (the page must end on a cut).
**Flow prompt text:** "A plain warm cream page fades in over the shot. A loose dark pencil circle is drawn on, with {{PHRASE}} handwritten inside it, and bold dark words appear one at a time below it as they are spoken. On the next shot the page is gone."
**Still-image state:** page, circle, phrase and the full caption.

### SK06 · PENCIL UNDERLINE — X ●● (extension in the same grammar)
**What it is:** a hand-drawn PENCIL underline under one bold caption word over B-roll. **Use when:** an emphasis word on B-roll (a number, "first", "only"). **Avoid when:** more than 3 per video.
**Geometry:** one pass 0.004 W, 6° wobble, 0.01 H under the baseline, spanning the word + 4 %. **Motion:** draws on in 6 f, out-cubic, at the word's time; leaves with the chunk.
**Flow prompt text:** "A loose pencil underline is drawn under the word {{WORD}} as it is spoken."

### SK07 · NUMBER CIRCLE — X ●●● (extension)
**What it is:** a numeral or amount in handwriting inside a small scribble circle (diameter 0.22 W) at the top corner, for lists and amounts. **Use when:** steps (1, 2, 3), amounts, durations. **Text (✎):** the numeral from the user's words only.
**Motion:** circle draws on 7 f, numeral wipes 5 f; replaced by the next numeral with a 3 f erase. Opposite corner to the bubble.
**Flow prompt text:** "A small pencil circle with the handwritten {{NUMBER}} inside it is drawn on in the {{SIDE}} top corner."

### SK08 · BUBBLE FLIP — X ●● (extension)
**What it is:** the bubble pops on the other side (x 0.25 W) when a visible face or key subject occupies the usual corner. **Use when:** the B-roll has a person at the top right (or left). Same spec as SK04 with x mirrored. **Flow prompt text:** as SK04 with the other side.

### SK09 · SCRIBBLE POSTER — X ●● (extension, still image)
**What it is:** the still state for images: SK01 word and ellipse over the photo, SK02 caption below. **Use when:** C4/C5. Everything settled, no animation. **Flow prompt text:** "A thick white capital word inside a loose pencil ellipse sits under the subject's chin, with handwritten white words below."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| talking head → B-roll → talking head | SK01 + SK02 | SK04 on each B-roll cut + SK03; SK05 on a person-free shot | SK01 on the payoff word + SK02 |
| single talking head | SK01 + SK02 | SK01 on a second theme word | SK01 payoff |
| B-roll only | SK03 + SK07 | SK06, SK05 | SK05 |
| still image | SK09 | – | – |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
