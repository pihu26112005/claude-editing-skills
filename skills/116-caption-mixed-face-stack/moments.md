# moments.md — Mixed Face Stack: Style Bible + Moment Library

This file is the single source of truth for the Mixed Face Stack caption style. Part 1 is the style bible (palette, type roles, layout, motion, footage rules, safe zones). Part 2 is the moment library: every caption move the style knows. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel (one locked talking-head shot); everything marked "(design, not measured)" is a design decision in the same grammar. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** untouched full-frame footage with a tight stack of two to four lines of words in four different typefaces at once (heavy white capitals, bright accent capitals, a big high-contrast italic serif, and tiny plain connector words), each word popping in on its own beat and the whole stack hard-cutting away when the chunk ends.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, role per word, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s). The reference ran at 32 fps; keep seconds at other frame rates. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Text white | #FFFFFF | Heavy capitals, serif italic words, connector words |
| Accent | #FFD400 (measured: warm saturated yellow) | Accent capitals. **Parameter:** the user may pick any bright, saturated colour. The shipped demo uses hot magenta #FF2E88. |
| Shadow | #000000 at 82 % (design) | 3 px offset, 6 px blur drop shadow plus a 1 px near-black edge (2.5 px under the shadow) on every word (design: the reference sat on a dark plate and used a faint shadow; the edge keeps text readable on bright B-roll) |

Brand-swap rule: replace only the Accent. White stays white. No other colours, no boxes, no gradients.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, plates, blur, tint or masks. |
| Caption stack | No container. Words sit directly on the footage with the shadow only. |
| Crop | None (cover-fit only if the source is not 9:16; anchor ✎ = the speaker's face). |

### 1.3 Layouts / grid

Measured on the reference: stacks sat in the middle-lower third, left-biased, 0.44–0.66H [845–1267], x 0.00–0.78W; the block covered the speaker's chin. This skill moves the block below the face (design decision, because the face must stay clear).

| Layout | Spec |
|---|---|
| Stack block (default) | Left margin 0.07W [76]; right margin 0.07W; first baseline at 0.535H + 1 line pitch (≈ 0.60H) [1152]; max 4 lines |
| Line pitch | 0.066H (84 px at 720x1280 [126]) |
| Line indents (✎ cycle) | line 1: 0; line 2: +0.13W; line 3: +0.04W; line 4: 0. Cycle repeats. Indent is clamped so the line ends inside the right margin. |
| Word gap | 14 px at 720 wide [21] between words on the same line |
| Baseline rule | Words on one line share one baseline, so a small connector sits at the bottom edge of the big word beside it |
| Lane shift ✎ | If the face bottom is lower than 0.46H, move the block down so the first baseline is ≥ face bottom + 0.05H; if the block would pass 0.86H, anchor it above the face instead (first baseline 0.12H). |
| Mirror ✎ | If the subject sits in the left half, set line 1 flush right and indent lines leftward. |

### 1.4 Typography

Four roles. The mix IS the style: every stack uses at least three of the four.

| Role | Look | Preferred free font | Fallbacks | Size (720 wide [1080]) |
|---|---|---|---|---|
| BIG | Heavy geometric sans, UPPERCASE, tight | Poppins ExtraBold | Montserrat ExtraBold, Archivo Black | 78 px [117] (measured cap height ≈ 0.039H) |
| ACC | Bold geometric sans, UPPERCASE, in the accent colour | Josefin Sans Bold | Jost Bold, Poppins SemiBold | 96 px [144] (set larger than BIG: Josefin caps run short) |
| SERIF | High-contrast display serif, italic, lowercase (as written), white | Playfair Display Italic Medium | Newsreader Italic, Bodoni Moda Italic | 96 px [144] |
| SM | Plain humanist or geometric sans, lowercase, regular, white | Poppins Medium | Inter Medium, Open Sans | 46 px [69] (about 0.5 × BIG) |

Role assignment rules (the reference mixes by word weight):

| Word type | Role |
|---|---|
| Connectors: and, but, so, to, for, of, your, our, it, a, the, in, on, at, with, short pronouns | SM (never two stacked lines of only SM) |
| Main noun or verb of the phrase | BIG |
| The single payoff or meaning word of the chunk (≤ 1 per chunk, ≥ 60 % of chunks) | ACC |
| A turn, a feeling or a soft word (not, instead, maybe, adjectives of mood) | SERIF |

Case: BIG and ACC are uppercased by the renderer; SERIF and SM keep the user's case. Punctuation stays attached to its word.

### 1.5 Motion language

| Item | Spec |
|---|---|
| Word entrance | 0.25 s (6 f at 24 fps): rise 18 px [27] from below, scale 0.92 → 1.0, opacity 0 → 1 (reaches full at 60 % of the move). Ease-out cubic. (design, timing consistent with the measured ≈ 0.2 s ramp) |
| Word timing | Each word starts at its spoken start time. Measured: words of a chunk landed 0.19–0.2 s apart. |
| Hold | Stack stays still until the chunk ends. No drift, no breathing. |
| Exit | Hard cut of the whole stack (measured: chunk gone in one frame, 0.1 s empty gap before the next chunk). |
| Never | Overshoot, bounce, spin, tilt, typing letter by letter, karaoke recolouring, glow, outline-only text, boxes, wipes, transitions on cuts, uppercase on SERIF or SM. |

### 1.6 What may happen to the user's footage

Nothing. Footage plays untouched, full frame, in sync with the audio. Allowed: caption overlays and their shadows. Forbidden: zoom, push, blur, grade, speed change, trim, reorder, regenerate, card layouts, background swaps, graphic transitions. Footage cuts are left as plain cuts; captions may change on a cut.

### 1.7 Safe zones

- The speaking face is never covered: keep the whole stack outside the face box (add 0.03H of air).
- Stay ≥ 0.07W from left and right edges and ≤ 0.86H at the bottom (platform UI).
- Burnt-in footage text: if the block collides with it, use lane shift or mirror.
- Bright shots: the shadow and edge (1.1) already keep white readable; raise the shadow opacity to 95 % before changing any colour.

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption stack, **K** keyword treatment, **T** title/opening text, **E** end. Energy: low / medium / high.

### C1 · Triple Stack — C medium (signature)
**What it is:** the core caption. Three words to six words, three lines, every line a different face, each word popping on its spoken time, whole stack hard-cut at the chunk end.
**Use when:** any speech or phrase of 3–6 words. Default chunk. **Avoid when:** a one-word beat (use C3) or a number (use K3).
**Text (✎):** 3–6 consecutive user words, 14–30 characters in total, split at punctuation, never ending on an article, preposition or conjunction.
**Geometry / Graphics:** 1.3 stack block; lines 2–3 words max, ≥ 3 roles used (e.g. SM + BIG, then SERIF, then ACC).
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | each word | y, scale, opacity | +18 px, 0.92, 0 → 0, 1.0, 1 over 0.25 s | ease-out cubic |
| chunk end | whole stack | visibility | 1 → 0 | hard cut (empty ≥ 0.05 s before the next stack) |

**Footage behaviour:** untouched. **Captions during it:** this is the caption. **Exit:** hard cut.
**Build notes:** pre-render each word as a 2x sprite with shadow, downscale with LANCZOS; lay out the complete chunk first so no word moves after landing; fit-shrink a line by 5 % steps until it fits inside the margins.
**Flow prompt text:** "A stack of three short lines of {{WORDS}} appears word by word on the lower middle of the frame, mixing heavy white capitals, one bright {{COLOUR}} capital word, an elegant italic serif word and a tiny plain word; the stack disappears instantly when the phrase ends."
**Still-image state:** full stack settled at the block position.

### C2 · Pair Stack — C medium
**What it is:** two-line version for short phrases (2–3 words): a BIG or SERIF line and an ACC or SERIF line, second line indented.
**Use when:** 2–3 word phrases, quick beats, list items. **Avoid when:** 5+ words.
**Text (✎):** 2–3 user words. **Geometry:** lines 1–2 of 1.3. **Motion:** as C1.
**Footage / captions / exit:** as C1.
**Flow prompt text:** "Two lines of {{WORDS}} pop in one word at a time: the first in heavy white capitals, the second in a bright {{COLOUR}} colour, shifted to the right; both vanish together."
**Still-image state:** two lines settled.

### C3 · Solo Slam — C high (extension, design not measured)
**What it is:** one word, centred on x = 0.50W, 1.35× the BIG size (or SERIF at 1.3×), single line, same entrance.
**Use when:** a one-word hook or a hard stop ("never", a name, a number word). **Avoid when:** more than 2× per video.
**Text (✎):** one user word. **Geometry:** baseline at 0.62H. **Motion:** entrance 0.2 s, hold, hard cut.
**Flow prompt text:** "One large word {{WORD}} pops in at the lower middle of the frame in heavy white capitals, then vanishes."
**Still-image state:** the word centred at the lower middle.

### C4 · Flip Side Stack — C medium (extension, design not measured)
**What it is:** C1 mirrored: line 1 flush right at 0.93W, later lines indented leftward. Used when the subject sits on the left.
**Use when:** the subject or a face is in the left half or burnt-in text sits on the left. **Avoid when:** it would hit the right-hand subject.
**Text (✎):** as C1. **Motion:** as C1, rise stays vertical.
**Flow prompt text:** "The same word-by-word stack of {{WORDS}} is aligned to the right side of the frame."
**Still-image state:** stack on the right.

### K1 · Accent Capital — K medium (signature)
**What it is:** the chunk's meaning word in the accent colour, uppercase Josefin-style bold, one per chunk, set 1.23× BIG for visual parity.
**Use when:** payoff words, nouns that carry the topic, verbs of action. **Avoid when:** a connector; > 3 accent words in a row of chunks without a white-only chunk (measured: nearly every chunk had one, so skip at most every third).
**Text (✎):** one word per chunk. **Motion:** as C1 word entrance. **Exit:** with its stack.
**Flow prompt text:** "The key word {{WORD}} is written in bright {{COLOUR}} capitals while the other words stay white."
**Still-image state:** accent word on its own line.

### K2 · Serif Turn — K medium (signature)
**What it is:** a soft or contrasting word set in white italic serif, lowercase, larger than the sans words; it gives each stack its elegant counterpoint.
**Use when:** contrast words ("but", "not", "instead"), feelings, verbs of motion, the word after a pause. **Avoid when:** a number or an all-caps abbreviation.
**Text (✎):** one word per chunk (two in a 4-line stack). **Motion:** as C1.
**Flow prompt text:** "The word {{WORD}} appears in a large, elegant white italic serif with lowercase letters."
**Still-image state:** serif word on its own line.

### K3 · Connector Whisper — K low (signature)
**What it is:** small plain lowercase words sitting on the baseline of the line's big word, about half its height, white.
**Use when:** every connector (1.4). **Avoid when:** it would be the only word on a line.
**Text (✎):** the connector words. **Motion:** as C1 word entrance, shifted to arrive just before its neighbour (its own time).
**Flow prompt text:** "Tiny plain white words such as {{WORDS}} sit next to the big words, at their bottom edge."
**Still-image state:** a small word left of a big one.

### K4 · Number Stack — K high (extension, design not measured)
**What it is:** a numeral or amount as BIG (or ACC when it is the payoff) with its unit or noun as SM on the same baseline.
**Use when:** numbers, prices, durations, percentages. **Avoid when:** the user wrote the number as a word (keep their writing).
**Text (✎):** numeral + unit exactly as written. **Geometry:** BIG at 1.25×, SM at 1×, baseline shared.
**Flow prompt text:** "The figure {{NUMBER}} appears large in heavy capitals with the small word {{UNIT}} beside it."
**Still-image state:** figure + unit on one line.

### T1 · Opening Stack — T high (signature)
**What it is:** the first chunk of the video, starting with the first spoken word (measured: first stack landed 0.5 s after the start, with the first word a BIG white line). Uses C1 or C2 with line 1 as BIG and line 2 as ACC.
**Use when:** always on the opening line. **Avoid when:** none (short videos: shorten the hold, never drop it).
**Text (✎):** the first 2–4 user words. **Motion:** as C1, but the first word enters at the spoken time exactly.
**Flow prompt text:** "As the speaker begins, the opening words {{WORDS}} pop in stacked, the first in heavy white capitals and the next in a bright {{COLOUR}} colour."
**Still-image state:** opening stack.

### T2 · Topic Callout — T medium (extension, design not measured)
**What it is:** a section or topic word held as a solo ACC line with an SM word above it, for list items or new topics.
**Use when:** a new step, a section change without a cut. **Avoid when:** within 0.5 s of a footage cut.
**Text (✎):** the user's topic words. **Motion:** as C1. **Flow prompt text:** "A small word {{WORD}} sits above one bright {{COLOUR}} capital word {{TOPIC}} for the length of the section."
**Still-image state:** SM + ACC pair.

### E1 · Payoff Stack — E high (signature)
**What it is:** the last chunk, with the last word as ACC (or the strongest word), held until at most 0.1 s after the last spoken word, then cut away. Measured: the final stack was a short two-word SM + BIG pair that cut out when speech ended.
**Use when:** the last line, a call to action. **Avoid when:** none.
**Text (✎):** last 2–4 user words. **Motion:** as C1. **Exit:** hard cut at speech end + 0.1 s (clamped to video end).
**Flow prompt text:** "The final words {{WORDS}} pop in stacked with the last word in bright {{COLOUR}} capitals and vanish when the speaker finishes."
**Still-image state:** closing stack.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 (BIG + ACC) | C1/C2 with K1 + K2 per chunk; C4 when the B-roll subject is on the left; chunk changes on the cuts | E1 |
| Single talking head | T1 | C1, C2 alternating, K3 on every connector, one C3 on a turn word | E1 |
| B-roll only (voice-over) | T1 on the first phrase | C2, C1 with lane shift per shot, K4 for numbers | E1 |
| Still image + text | C1 settled | none | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
