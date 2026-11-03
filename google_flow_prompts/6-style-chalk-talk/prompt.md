# Google Flow prompt · Chalk Talk
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Chalk Talk" motion style to it.

The look in one sentence: White chalk circles drawn around the speaker, yellow sketchy titles written then filled, handwritten captions with a dark tag on the spoken word, charcoal brush-stroke wipes over the cuts, footage in a yellow chalk-bordered card, a cream paper quote card to close.

Re-edit the uploaded video in this style: it may use the layouts, containers, graphics, transitions and captions of the style bible below, but the footage itself (people, scenes, voices, sound, order and timing of shots) is never replaced, recoloured, retimed or reordered.

## 2. INPUTS (fill in before pasting)
VIDEO: the short video uploaded in Flow. This is the only footage you may use; never generate new footage, people or scenes.
SCRIPT (optional): <paste the exact words you want shown as captions, or write NONE>
EXTRA NOTES (optional): <words to emphasise, parts to skip, an accent colour as a hex value, or NONE>

## 3. HOW TO USE THE INPUTS
3.1 SCRIPT is provided (anything other than NONE)
- Use exactly those words, in exactly that order, as the on-screen words. Do not paraphrase, correct, translate, add or drop words (apart from splitting them into caption chunks as the style bible says).
- Ignore all text that is already in the video as a source of words (old captions, subtitles, titles): the script wins.
- Time the words to the speech you hear in the video: each caption chunk appears when its first word is spoken and leaves when its last word ends. If the script and the speech differ, follow the speech's timing and keep the script's words.

3.2 SCRIPT is NONE
- Listen to the audio of the uploaded video and transcribe the speech word for word (same language, same spelling style, keep the speaker's own words, numbers and names). That transcript is the script.
- If the video already shows captions you may read them only as a spelling aid for names and unusual words; never copy their look or position.
- Mark pauses and sentence ends from the audio; they decide where chunks break.

3.3 Existing captions and text from another style (do this BEFORE adding anything)
- Scan the whole uploaded video for burned-in captions, subtitles, karaoke words, titles, lower thirds, emoji or word stickers, progress bars, watermarks and any other text or graphics that a previous edit added on top of the footage.
- Remove all of them completely in every frame where they appear: reconstruct the footage behind them cleanly (no ghost outlines, no smeared or blurred patches, no colour shifts). Original footage must look as if the old text had never been there.
- Keep text that belongs to the scene itself (street signs, shop names, product labels, phone or laptop screens, book covers, clothing prints), unless it is clearly an old caption.
- The reason: this style brings its own captions and graphics. If the old ones stay, the same words appear twice on screen, one in the old look and one in the new look. That must never happen.
- Only after the video is clean, add this style's text and graphics from the script.

3.4 EXTRA NOTES
- Apply them if given (emphasis words, parts to skip, accent colour as a hex value). They never override the hard rules in section 4. If an accent colour is given, swap this style's accent colour for it everywhere; keep neutral colours as they are.

3.5 Audio
- The soundtrack of the uploaded video stays exactly as it is, in sync. Do not generate or add any voice, music or sound of your own.

3.6 Language
- Captions are written in the language that is spoken (or that the script is written in). Keep punctuation as written in the script; for a transcript, add natural punctuation.

## 4. HARD RULES (never break these)
- Footage fidelity: same people, same scenes, same shot order, same timing, same sound. Output length equals input length (within one frame).
- The speaking face is never covered, blurred or distorted while the person speaks.
- Every word on screen comes from the script (or the transcript). Spell it exactly. No extra words, no filler, no lorem ipsum.
- Captions are in sync with the speech: a chunk starts when its first word is spoken.
- Only one caption system is ever visible: old captions are removed first (3.3), then this style's captions are added.
- Use only the fonts, colours, shapes and motion described in the style bible below. Do not mix in other looks.
- Keep everything inside the frame with the style's safe margins.

## 5. HOW TO BUILD THE EDIT (work in this order, silently)
1. WATCH the whole video: list its shots with start and end times (every cut), note who speaks, where the face is in each shot and where the quiet or busy areas of the frame are.
2. PREPARE THE WORDS (section 3): remove old captions, then get the script (given or transcribed) and split it into caption chunks the way the style bible's caption section says (chunk size, line breaks, emphasis words).
3. TIME THE WORDS to the audio: for every chunk, its start and end second.
4. PLACE THE MOMENTS: choose from the moment library below. Use each signature moment where the video gives it a reason (openers on the first words, cut moments on real shot cuts, closers after the last spoken word); use the recommended combinations as starting points, not as a fixed template. Do not use more variety than a short video can carry.
5. CHECK THE SAFE ZONES (style bible): the speaking face is never covered; text stays inside the safe margins; if footage content (a sign, a screen) sits where the caption lane is, move the lane as the style bible says.
6. RENDER the video: every graphic and word appears and disappears exactly as the moments describe (timing, easing and entrance), cut to cut, and stays in sync with the audio.

## 6. STYLE BIBLE
### 1.1 Palette (sampled from the reference)

| Role | Hex | Used for |
|---|---|---|
| CHALK | `#F4F1E8` | chalk circles, caption words over footage |
| YELLOW | `#F3D10A` | titles over footage, card border, list numerals, quote marks, doodles, key caption words |
| BOARD | `#2F2F2D` | charcoal board and brush strokes (with fine horizontal grain) |
| PAPER | `#F7F2E8` | the cream end page and cream brush strokes (with faint horizontal fibres) |
| INK | `#312F2C` | quote text and captions on the paper page |
| TAG | `#221F1D` at 90 % | the dark rounded tag behind the word being spoken (over footage) |
| HIGHLIGHT | `#EDD860` | the highlighter box behind the word being spoken (on paper) |

Brand variant: YELLOW may become one brand accent; BOARD and PAPER stay.

### 1.2 Materials
- **Chalk line:** solid CHALK or YELLOW stroke 0.007 W [8 px] wide, round caps, with a chalky texture (stroke opacity modulated by fine noise between 75 % and 100 %). Lines are slightly imperfect: radius or position wobble of ±0.002 W.
- **Charcoal board:** BOARD plus 3 % luminance noise and faint horizontal streaks (dry-brush grain).
- **Paper:** PAPER plus 2 % noise and faint horizontal fibres.
- **Dry-brush stroke (the transition material):** a horizontal band of BOARD or PAPER, 0.13–0.17 H tall, tilted −4° (rising to the right), whose leading edge is ragged: dozens of thin bristle streaks of random length (0–0.09 W) and thickness (1–4 px) poke ahead of the band, with gaps between them.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Titles, quotes, numerals | sketchy chalk capitals (double-stroke hatched letters) | Cabin Sketch Bold | Cabin Sketch Regular, Rubik Dirt, any chalk/sketch display | title: fit ≤ 0.80 W, cap height ≤ 0.07 H; quote lines: cap height 0.065 H [125 px] |
| Captions | rounded casual handwriting | Gochi Hand | Patrick Hand, Kalam, Comic Neue | 0.050 H [96 px] |

All words on screen are the user's words (or list numerals). Captions keep the user's casing; titles and quotes are UPPERCASE.

### 1.4 Motion language
- **Draw-on:** chalk lines and borders are drawn along their path (arcs grow from the top outward in both directions; rectangles trace around) over 0.3–0.8 s, ease-out-cubic.
- **Write-then-fill:** titles first appear as a chalk outline revealed left to right (0.3 s), then fill solid (0.2 s).
- **Brush wipe:** bands enter one after another (stagger 0.05 s) from alternating sides, each crossing the frame in 0.3 s with ease-in-quad, until the frame is covered. The same strokes run in reverse ("erase") to reveal what's underneath.
- **Words:** each caption word appears at its spoken time (fade 3 f). The active word sits in a TAG (over footage) or a HIGHLIGHT box (on paper) that jumps word to word.
- No sliding panels, no bounce, no zoom punches. The only camera move is a slow drift inside cards (100 → 104 %).

### 1.5 What may happen to the user's footage (style-specific rules)
- Allowed: full-frame footage with chalk drawn over it; footage inside a chalk card (cover fit, crop anchor) on the board or paper; slow drift inside a card; covering the frame with brush strokes during a wipe.
- A brush wipe may fully cover the footage for **at most 0.25 s**, ideally around a footage cut (so it hides the cut). The paper page without footage (K08) is allowed only for the last ≤ 1.5 s or ≤ 15 % of the video; otherwise close with K09 (quote + live footage card).
- The **card always plays the current footage in real time**, in sync with the audio. Never put foreign imagery in a card.
- Never recolour, filter, blur or retime the footage.

### 1.6 Safe zones
- **Face box:** never covered by captions, titles or numerals. Chalk circles may pass around and behind-looking over hair and shoulders but never across the eyes or mouth.
- Captions sit in the chest band (0.58–0.80 H) or the top/bottom band of a card, wherever the shot is calm.

---

## 7. MOMENT LIBRARY
Family codes: **CHALK** (drawn elements), **TYPE**, **CAP**, **WIPE**, **CARD**. Energy:  low ·  medium ·  high.

---

### K01 · CHALK HALO — CHALK  (signature opener)

**What it is:** Three concentric white chalk circles draw themselves around the speaker's head, like a teacher circling the important thing on the board.

**Use when:** the opening line on a talking head (default opener); any key statement on a face.

**Geometry:** centre = the head's centre (face box centre, raised by 0.15 × face height, so the inner circle passes under the chin, not across the mouth). Radii **0.26 W, 0.35 W, 0.46 W**. CHALK line, 0.007 W.

**Motion:** each arc grows from the top (12 o'clock) in both directions: outer starts at 0.17 s, middle +2 f, inner +4 f; each reaches a full circle in 0.75 s (ease-out-cubic). Stays until a wipe covers it.

**Flow prompt text:** "Three white chalk circles draw themselves around the speaker's head, one inside the other, growing from the top in both directions until they are complete, with a dusty hand-drawn texture."

---

### K02 · CHALK TITLE — TYPE  (signature)

**What it is:** One big word in sketchy yellow chalk capitals at the top: first written as an outline left to right, then filled solid.

**Text:** one user word: the key word of the opening line (or of a new section). UPPERCASE, ≤ 10 letters.

**Graphics:** YELLOW, sketch font, cap top 0.02 H, centred on the subject's x (or left-aligned at 0.05 W), largest size that fits 0.80 W with cap height ≤ 0.07 H. Over light backgrounds add a 0.004 W BOARD outline under it.

**Motion:** outline revealed left → right over 0.3 s (the reference shows the outline at 0.47 s), then fill fades in over 0.2 s. Stays until a wipe covers it.

**Flow prompt text:** "At the top, the word \"{{TITLE}}\" is written in sketchy yellow chalk capitals: first as an outline traced left to right, then filled in solid yellow."

---

### K03 · HAND CAPTIONS — CAP (always on)

**What it is:** Captions in casual handwriting. Over footage, words are chalk-white with a soft shadow; the word being spoken sits on a small dark rounded tag; the key word of a chunk is yellow. On paper, words are INK and the spoken word gets a yellow highlighter box.

**Text:** the user's caption text **verbatim** (original casing), chunks of 1–4 words, ≤ 24 characters; at most one yellow key word per chunk (meaning words only; the payoff is always one).

**Graphics:** caption font 0.050 H. Over footage: CHALK words, shadow (0/+2 px, blur 4 px, black 45 %); TAG = rounded rectangle from baseline − 0.040 H to baseline + 0.012 H, 0.012 W wider than the word on each side, radius 0.012 W, behind the active word. On paper: INK words, HIGHLIGHT box (radius 0.008 W) behind the active word. Left-aligned at x 0.08 W (inside a card: card x0 + 0.06 W). Baseline: chest band 0.64 H on a talking head; card top band card y0 + 0.12 H or bottom band card y1 − 0.08 H; paper page 0.925 H.

**Motion:** words appear at their spoken time (fade 3 f, no reflow: the chunk is laid out in advance). The tag/highlight jumps to each new word (1 f). Chunk change: hard swap.

**Flow prompt text:** "Captions are in casual handwriting, white with a soft shadow, appearing word by word as spoken; the word being said sits on a small dark rounded tag, and the key word \"{{KEY}}\" is yellow. The ONLY caption lines, in order, are: [a-b s] \"{{CHUNK_1}}\", … No other text."

---

### K04 · CHARCOAL BRUSH WIPE — WIPE  (signature transition)

**What it is:** Dry charcoal brush strokes slash across the screen in bands, one after another, until the whole frame is a chalkboard.

**Use when:** leaving the opening talking head; any big section change. Time it so the frame is fully covered **on a footage cut** (it hides the cut).

**Geometry:** 7 bands, each 0.15 H tall, overlapping by 0.01 H, tilted −4°; bands alternate entering from the left and the right; bristle edge per Part 1.2.

**Motion:** band k starts at k × 0.05 s, crosses in 0.3 s, ease-in-quad. Total ≈ 0.45–0.65 s. Elements under it (halo, title, captions) stay until covered.

**Flow prompt text:** "Thick dry charcoal brush strokes slash across the screen one after another, slightly tilted, with ragged bristle edges, until the whole frame becomes a dark chalkboard."

---

### K05 · CHALK CARD — CARD  (signature middle)

**What it is:** On the charcoal board, the footage appears inside a tall card with a wobbly yellow chalk border, revealed by brush strokes erasing the charcoal.

**Use when:** right after K04 (B-roll, examples, lists); keep it through several cuts (the footage cuts inside the card).

**Geometry:** card x 0.09–0.91 W, y 0.085–0.91 H (shorten the bottom to 0.84 H when a caption needs the board below). Border: YELLOW chalk line 0.0065 W along the card edge with a small wave (amplitude 0.003 W, wavelength 0.02 W). Footage: cover fit, anchor.

**Motion:** reveal = K04 bands running in erase mode, only inside the card, over 0.45 s; border traced around the card (clockwise from top-left) over 0.3 s, starting when the reveal is half done. Drift (K12) inside.

**Flow prompt text:** "On the dark chalkboard, the video appears inside a tall rectangle with a wobbly yellow chalk border, uncovered by brush strokes wiping away the charcoal."

---

### K06 · OUTLINE PRE-WRITE — TYPE

**What it is:** The closing quote is sketched as a thin dark outline over the card a moment before the paper page arrives, like a teacher pre-writing on the board.

**Text:** the quote lines of K08/K09. **Graphics:** INK outline only (no fill), quote layout of K08. **Motion:** revealed left → right, line by line, 0.3 s, then stays until K07 covers it.

**Flow prompt text:** "Over the card, the closing words are sketched as thin dark outlines, ready to be filled in."

---

### K07 · PAPER WIPE — WIPE

**What it is:** Like K04, but the strokes are cream paper: the board is brushed over with cream until the paper page is revealed. The quote fills in solid as the paper passes behind it.

**Motion:** same band rules as K04, slower: each band 0.4 s, stagger 0.07 s. The frame is fully paper ≤ 0.3 s after a footage cut, or the strokes stop around the K09 card area.

**Flow prompt text:** "Cream paper brush strokes sweep across the dark board, band by band, revealing a clean cream page."

---

### K08 · QUOTE PAGE — TYPE  (closer, footage hidden)

**What it is:** A cream paper page with a big quote in sketchy capitals, two yellow quote marks above it, a yellow doodle after the last line, and handwritten captions with a highlighter.

**Use only** for the last ≤ 1.5 s or ≤ 15 % of the video (Part 1.5). Otherwise use K09.

**Geometry:** quote marks YELLOW (sketch font “ glyph at 0.22 H font size, or two drawn comma shapes) at x 0.04–0.14 W, y 0.02–0.10 H. Quote: INK, sketch font drawn with a 0.004 W same-colour stroke so the hatched letters read solid, cap height 0.065 H, line pitch 0.072 H, left-aligned at 0.05 W, first line top 0.16 H, ≤ 4 lines, ≤ 12 characters per line. Doodle: YELLOW chalk loop/squiggle (≈ 0.12 W × 0.10 H, line 0.0065 W) 0.07 W right of the last line. Captions K03 paper mode at 0.925 H.

**Motion:** quote fills as the paper wipe passes (or writes on line by line, 0.25 s each); quote marks draw on (0.2 s); doodle draws along its path (0.4 s), 0.3 s after the quote.

**Text:** 2–6 user words: the final line or its payoff phrase, UPPERCASE, keeping its punctuation.

**Flow prompt text:** "A clean cream paper page. Two yellow chalk quote marks at the top left, then the words \"{{QUOTE}}\" in big sketchy dark capitals over a few lines, and a small yellow chalk squiggle after the last word."

---

### K09 · QUOTE CARD — TYPE + CARD  (default closer, keeps the footage)

**What it is:** K08's quote, quote marks and doodle on the upper part of the cream page, and the live footage in a yellow-bordered chalk card below.

**Geometry:** quote block as K08 but lines start at 0.12 H (3 lines max); card x 0.09–0.91 W, y 0.40–0.87 H (anchor on the face); captions paper mode at 0.935 H.

**Motion:** the paper wipe (K07) covers the frame around the cut; the card is then revealed by erase strokes (0.4 s) and its border traced (0.3 s); quote marks and doodle draw on.

**Flow prompt text:** "On a cream paper page, the words \"{{QUOTE}}\" are written in big sketchy dark capitals at the top with yellow chalk quote marks, and below them the speaker keeps talking inside a card with a wobbly yellow chalk border."

**Still-image state:** default poster.

---

### K10 · CHALK DOODLE — CHALK

**What it is:** A small yellow chalk loop/squiggle drawn next to a word or title to punctuate it.

**Motion:** drawn along its path in 0.4 s. **Use:** after a title or quote, max 2 per video. **Flow prompt text:** "A small yellow chalk squiggle draws itself next to the words."

---

### K11 · CHALK NUMERAL — TYPE  (extension in the same grammar)

**What it is:** For lists and steps, a yellow sketchy numeral ("1", "2", "3") written in the board margin above the card's top-left corner as each item is spoken; the old numeral is smudged away (fade + 0.01 W horizontal smear, 0.15 s).

**Graphics:** YELLOW sketch font, cap height 0.055 H, left edge at the card's x0, baseline 0.01 H above the card. **Motion:** write-then-fill (0.2 s + 0.1 s).

**Flow prompt text:** "As each step is spoken, a yellow chalk number is written in the dark margin above the card, replacing the previous one."

---

### K12 · CARD DRIFT — CARD

**What it is:** Inside a card, the footage slowly pushes in (100 → 104 %, linear) over each shot. **Flow prompt text:** "Inside the card the shot drifts in very slowly."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll montage → talking head | K01 + K02 + K03 | K04 ending on the first cut → K05 card through the montage; K11 numerals for lists; K02 title inside the card for a new key phrase; K12 | K06 → K07 around the last cut → K09 (or K08 for the last ≤ 1.5 s) + K10 |
| Single talking-head shot | K01 + K02 + K03 | K04 → K05 with the same live shot in the card | K07 → K09 |
| B-roll only | K04 from the start (board) → K05 + K02 | K11; K12 | K07 → K09 |
| Still image (poster) | K09 settled (quote + image card + caption) | — | — |

Never paste a row blindly.

## 9. OUTPUT
- One video, vertical 9:16, same duration, frame rate and resolution as the upload (at least 720 x 1280), original audio track unchanged.
- No watermark, no end card, no title card that is not part of the style.

## 10. NEGATIVE PROMPT (avoid all of these)
- Do not change, replace, recolour, retime or reorder the uploaded footage; do not alter anyone's face, body, outfit or voice.
- Do not add any word that is not in the script / transcript; no misspellings, no random gibberish text, no watermarks, no logos, no stock overlays.
- Never show the same words twice (one copy in an old style and one in the new style); never leave remnants, ghosts or blur patches of removed captions.
- Do not cover the speaker's face while they are speaking; do not let any text run outside the frame or sit on the very edge.
- No black bars, no letterboxing, no extra intro or outro, no end card, no added music or voice-over, no sound effects the style does not ask for.
- No glitches, flicker or warping outside what the style bible describes; no 3D lens flares, no cartoon filters, no beauty filters.

## 11. FINAL CHECK (verify before you finish)
- [ ] Old captions and old on-screen text are gone; nothing is ever shown twice.
- [ ] Every word matches the script or transcript, spelled correctly, and starts with the speech.
- [ ] The face is clear while speaking; no text is cut off or outside the margins.
- [ ] The look matches the style bible (colours, type, shapes, motion), and each moment appears the way its description says.
- [ ] Footage, order, timing and audio are unchanged; length matches the upload.
