# moments.md — Ghost Underline: Style Bible + Moment Library

This file is the single source of truth for the Ghost Underline caption system. Part 1 is the style bible (palette, type, layout, motion, footage rules, safe zones). Part 2 is the moment library. Values were measured on a 720x640, 24 fps, 8.1 s reference reel that showed captions on a black plate; the plate is not part of this skill, only the caption and title typography. Where the reference did not show something, the value is marked "(design, not measured)". SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays full-frame and untouched while mid-frame captions build word by word, ghost-grey words firming up to white in a heavy bold sans, with the key word of each phrase set in a light serif italic that carries a thin two-colour gradient underline.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (24 in the reference; at another fps keep the seconds). Reference values in brackets are for a 1080-wide frame.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Measured default | Demo accent (parameter) | Used for |
|---|---|---|---|
| Sans word | #FFFFFF | #FFFFFF | Ordinary caption words |
| Keyword | #F3E7CE (warm cream) | #EADFFF (pale lilac) | Serif italic keyword |
| Underline start → end | #C8A840 → #FF9F4A → #E6734D (gold, amber, coral) | #FF4FA3 → #8A5CFF (magenta to violet) | 2-3 px gradient line under keywords |
| Ghost word | #444444 rising to its final colour | same | First frames of every word |
| Shadow | none on black plate; use #000000 at 90 % blurred 6 px on footage (design, not measured) | same | Legibility over footage |

Accent rule: the keyword colour and the underline gradient are parameters. If the user gives a brand colour, use it as the gradient start and a lighter or shifted tint as the end; keep the keyword colour pale. White stays white.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, untouched. No cards, boxes, bars, tints or blur plates behind text. |
| Underline | Height 0.004W [4], full width of the keyword (glyph advance), sits 0.012W [13] under the baseline, horizontal linear gradient, appears with the word. Measured: 2 px at 720 wide, 8 px under the baseline. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions of the frame) | Use |
|---|---|---|
| Caption lane | centre y = 0.665H (measured on the reference at 0.50 of its short frame; moved below the face area for 9:16), block width ≤ 0.76W, centred on x = 0.50W | All C moments |
| Line pitch | 1.22 × sans size [≈ 0.107W] | Two-line chunks |
| Title lane | centre y = 0.075H, centred | T1, T2 |
| Edges | every glyph ≥ 0.05W from left and right | Always |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption word | Heavy geometric grotesque, bold 700, mixed case as written, tight natural spacing | Inter Bold | Inter Tight Bold, Manrope ExtraBold | 0.088W [95] (measured ≈ 0.086W) |
| Keyword | Light calligraphic serif italic, medium 500–560 weight, same text colour treatment, underlined | Newsreader Italic | Lora Italic, Source Serif 4 Italic | 0.098W [106] |
| Solo word | Keyword style enlarged | Newsreader Italic | Lora Italic | 0.17W |
| Title | Keyword style enlarged | Newsreader Italic | Lora Italic | 0.125W |

Word gap = 0.28 × sans size. Baselines of sans and serif words on a line are aligned. Case exactly as the user wrote it. No outline-only text.

### 1.5 Motion language

| Family | Easing | Duration |
|---|---|---|
| Word entrance | colour ramp ghost grey → final colour, linear, with alpha 0 → 1 ease-out cubic 1−(1−p)^3 at 1.7× speed | 0.21 s (5 f) |
| Chunk exit | hard cut, replaced in the same frame by the next chunk or by nothing | 1 f |
| Layout | the whole chunk is laid out before its first word shows; no word ever moves | — |
| Title | rise 0.02H + alpha, ease-out cubic, 0.25 s; fade out linear 0.3 s (design, not measured) | — |

Never: bounce, overshoot, slides, letter-by-letter typing, scale pops, rotation, wipes, glitch, shake, flashes, effects on cuts.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text, soft shadow and underline overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed changes; blur, grading, filters, cards, splits, B-roll frames, background swaps, graphic transitions. The primary footage plays live, in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Default lane centre y = 0.665H keeps a two-line chunk (top ≈ 0.60H) under a face whose bottom is ≤ 0.50H. If the face bottom is lower, move the lane down (min block bottom ≤ 0.90H) or shorten to one line. |
| Title lane | Title bottom (with underline) ≤ 0.14H; skip or shrink if the face top is above 0.15H. |
| Footage text (signs, UI) | If readable footage text sits in the lane for > 1 s, shift the lane up or down by one line pitch. |
| Edges | Glyphs ≥ 0.05W from left and right; assert text boxes in code. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **C** caption · **K** keyword · **X** cut handling · **E** end. Energy legend: ● calm · ●● medium · ●●● high.

### C1 · GHOST WORD BUILD — C ●● (signature, the caption system)
**What it is:** a phrase of 2–6 words is laid out in the caption lane; each word fades in at its spoken time, starting as a dark ghost grey and firming up to white. Earlier words stay put. At the end of the phrase the whole block cuts away.
**Use when:** always, on any footage. **Avoid when:** never.
**Text (✎):** the user's exact words, case as written. Chunk rules: 2–6 words, ≤ 28 characters per line, split at punctuation and natural phrases, never end on an article, preposition or conjunction; chunk lasts 0.6–2.0 s; start = first word start; end = next chunk start − 0.05 s, or last word end + 0.4 s for the last chunk.
**Geometry / Graphics:** caption lane 1.3, sans size 0.088W. Wrap into two balanced lines only when the single line would exceed 0.76W; first word always on line 1. Line pitch 1.22 × size. Lines centred on x = 0.50W.
**Motion (measured, 24 fps; words every 0.4 s):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | word | colour | #444444 → white | linear, 0.21 s |
| word start ✎ | word | alpha | 0 → 1 | ease-out cubic, 0.12 s |
| chunk end ✎ | whole block | alpha | 1 → 0 | hard cut |

**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut; the next chunk starts on the next word, with no gap longer than the speech pause.
**Build notes:** pre-render each word as a glyph mask plus a blurred shadow mask at 2× then downscale; place by measured advance so a word's position never changes; tint per frame.
**Flow prompt text:** "In the middle-lower part of the frame, the caption builds word by word in heavy white sans-serif lettering. Each word first appears as a dim grey ghost and firms up to bright white within a fifth of a second. Nothing moves once placed. When the phrase is done it vanishes at once. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### K1 · UNDERLINED ITALIC KEYWORD — K ●● (signature)
**What it is:** one meaning-carrying word per phrase is set in a light serif italic in a pale tint and carries a thin gradient underline that appears with the word.
**Use when:** every chunk with a noun or verb that carries the idea; the topic word, the action, the number. **Avoid when:** more than 1 per chunk (2 only in a chunk of ≥ 5 words), or an article or preposition.
**Text (✎):** the keyword, as written, including attached punctuation.
**Geometry / Graphics:** Keyword type 0.098W, baseline shared with the line, colour per 1.1; underline per 1.2 under the word's advance width.
**Motion:** same word entrance as C1; the underline fades in with the word (alpha only).
**Footage / plate behaviour:** untouched.
**Captions during it:** the keyword sits in the normal flow of the chunk.
**Exit:** with the chunk.
**Build notes:** align baselines by font ascent; draw the underline as a 3 px gradient strip per frame.
**Flow prompt text:** "One important word in the phrase, {{KEYWORD}}, is written in a slim slanted serif style in a pale tint with a thin colour-fading line under it, while the other words stay bold white."
**Still-image state:** the keyword with its underline.

### C2 · SINGLE-LINE CHUNK — C ●● (extension in the same grammar)
**What it is:** a short phrase (2–3 words) that fits one line, centred in the lane so that its single line sits on the lane's centre.
**Use when:** quick beats, short sentences. **Avoid when:** more than 28 characters.
**Text (✎):** as C1.
**Geometry / Graphics:** as C1, one line centred vertically on y = 0.665H.
**Motion:** as C1.
**Footage / plate behaviour:** untouched. **Captions during it:** this is the caption. **Exit:** hard cut.
**Build notes:** same renderer.
**Flow prompt text:** "A short phrase builds word by word on one line in the lower middle of the frame, in bold white lettering, each word fading up from grey."
**Still-image state:** the phrase.

### C3 · SOLO PAYOFF WORD — C ●●● (extension in the same grammar; used for the final word)
**What it is:** one payoff word alone in the keyword style at 0.17W with its underline.
**Use when:** the last word, a number, a turn. **Avoid when:** longer than 12 characters; max 2 per video, ≥ 3 s apart.
**Text (✎):** one user word.
**Geometry / Graphics:** Solo word type, centred on x = 0.50W, baseline lane centre y = 0.66H.
**Motion:** C1 entrance; hold 0.4–0.8 s; hard cut or end.
**Footage / plate behaviour:** untouched. **Captions during it:** replaces the chunk. **Exit:** hard cut.
**Build notes:** same renderer, bigger size.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in large slanted pale lettering with a colour-fading line underneath, fading up softly."
**Still-image state:** the word.

### T1 · ITALIC TITLE — T ●● (extension in the same grammar, design not measured)
**What it is:** a one- or two-word title in the keyword style at the top of the frame, rising 0.02H while fading in, with the gradient underline, then fading out.
**Use when:** the opening line names the topic. **Avoid when:** the face top is above 0.15H and the title would touch it; a cut within 0.3 s.
**Text (✎):** 1–2 of the user's words, as written, max 16 characters; if moved into the title, remove them from the first caption chunk (caption audit counts them once).
**Geometry / Graphics:** keyword type 0.125W, centred x = 0.50W, centre y = 0.075H; underline per 1.2.
**Motion:** rise and fade-in 0.25 s ease-out cubic; hold 1.0–1.4 s; fade-out 0.3 s linear, finished ≥ 0.3 s before a cut.
**Footage / plate behaviour:** untouched. **Captions during it:** C1 runs lower; they never share a region. **Exit:** fade.
**Build notes:** reuse the keyword renderer.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, in slim slanted serif lettering with a thin colour-fading underline, fades in at the top of the frame while rising slightly, stays about a second, then fades away. It never covers the face."
**Still-image state:** title.

### T2 · SECTION TITLE — T ●● (extension, design not measured)
**What it is:** a second title for a new topic, at 0.85× T1 size.
**Use when:** a real topic change, ≥ 3 s after T1 and ≥ 0.5 s after a cut. **Avoid when:** video shorter than 6 s.
**Text (✎):** 1–2 user words. **Geometry / Graphics:** as T1, 0.85× size, centre x ✎ 0.50W (or 0.30W / 0.70W). **Motion:** as T1. **Footage:** untouched. **Exit:** fade.
**Build notes:** reuse T1.
**Flow prompt text:** "Later, a smaller title, {{TITLE}}, in the same slim slanted lettering fades in near the top, stays about a second, and fades out."
**Still-image state:** title.

### X1 · CUT-SAFE SWAP — X ● (extension)
**What it is:** the footage cuts plainly; captions are not changed by the cut unless a chunk boundary falls within 0.3 s, in which case the boundary is moved to the cut frame.
**Use when:** every footage cut. **Avoid when:** never; add no effect.
**Text (✎):** none. **Geometry:** none.
**Motion:** hard cut only. **Footage:** untouched. **Captions during it:** unchanged, or swapped on the cut frame. **Exit:** none.
**Build notes:** compute chunk boundaries against the scene cut list.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect; the caption keeps building and only changes between phrases."
**Still-image state:** none.

### E1 · END HOLD — E ● (extension)
**What it is:** the last phrase or solo word holds until just before the end.
**Use when:** every video. **Avoid when:** never.
**Text (✎):** the last chunk. **Motion:** holds to min(last word end + 0.4 s, end − 0.25 s); the last 0.25 s has no caption. **Footage:** untouched. **Exit:** end of video.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** the last chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 with K1 | C1 + K1 on every chunk; C2 on short beats; X1 on cuts | C3 + E1 |
| Single talking head | T1 + C1 with K1 | T2 at a topic change; C3 on one payoff word | E1 |
| B-roll only, no speech | C1 with K1 from the first caption | 1.0–2.0 s chunks across the shots | E1 |
| Still image + text | one C1 chunk with K1 in the settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (demo2 render, 720x1280, 24 fps)

- Sizes used: sans 63 px (0.088W), serif italic 70 px (0.098W), solo 122 px, title 90 px. Lane centre y = 0.665H (851 px). Wrap limit 0.76W.
- Italic weight must be ≥ 500; a hairline weight vanished on light footage. Variable-font axis order for Newsreader Italic is [weight, optical size] = [560, 24].
- Baseline alignment between Inter and Newsreader needs per-font ascent offsets.
- Timing used: title 0.10–1.46 s (rise 0.25 s, fade 0.3 s); chunks 0.55–2.05, 2.10–3.15, 3.20–4.90, 4.95–6.85, 6.90–8.40, 8.45–9.12 s; solo word 9.15–9.75 s; word fade 0.21 s.
- "Saving money" was used as the title and removed from the first chunk; the audit joins title + chunks.
