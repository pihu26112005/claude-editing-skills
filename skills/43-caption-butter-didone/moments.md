# moments.md — Butter Didone: Style Bible + Moment Library

This file is the single source of truth for the Butter Didone caption style. Part 1 is the style bible (palette, type, motion, footage rules, safe zones). Part 2 is the moment library: every caption and title move the style knows, with specs measured on a 540x960, 30 fps, 7.9 s reference reel (one talking-head shot, no cuts) and tuned on a 720x1280, 24 fps render. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: the footage is never touched.

**The look in one line:** pale butter-yellow high-contrast Didone type on untouched footage: a small lowercase caption block that pops in word by word near the bottom with one CAPITAL keyword, and a giant edge-to-edge capital version of the key spoken word slamming in across the top.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 30 fps; the demo render at 24 fps. Keep seconds at other rates. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Butter yellow | #FEF08F | Every glyph: giant words, caption words, caps keywords (measured median 254,240,143) |
| Text shadow | #000000 | Soft drop shadow under all text so the pale yellow reads on bright footage |

Brand-swap rule: if the user gives a brand colour, replace Butter yellow with it (keep it light and warm enough to read on footage). There is one text colour; never add a second, no outlines, no boxes, no highlights.

### 1.2 Containers / shapes

None. Footage is always full frame, 100 % of W and H, untouched. No cards, borders, masks, label boxes, blur plates, tints or darkening overlays. Crop only when the source is not 9:16 (cover-fit, anchor ✎ = the speaker's face).

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Giant band, free | x 0.04–0.97, centre y 0.20H [384]; cap height 0.13–0.17H [250–326] | Giant word where no face sits in the top 0.30H (measured on the reference: caps spanned y 0.11–0.28H) |
| Giant band, face-safe | x 0.04–0.97, y 0.025–0.14H (cap height ≤ 0.115H) | Giant word over a speaker whose face top is below 0.15H (used on demo2) |
| Giant band, low face | x 0.04–0.97, y 0.025–0.095H (cap height ≤ 0.07H) | Face top near 0.10H (a person standing close to the top edge) |
| Caption lane | centred on x = 0.50W, lines 0.095H [182] apart; the last line baseline ≈ 0.79H [1517] for one line, 0.79H + 0.043H per extra line | Caption block, 1–3 lines (reference: baselines 0.79H for 1 line; 0.74/0.84H for 2; 0.69/0.78/0.875H for 3) |
| Max line width | 0.80W [864] | Wrap point |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Giant word | High-contrast Didone capitals, heavy stems, hairline serifs, letters nearly touching, uppercase always | Bodoni Moda, weight 900, optical size 14 (low), plus a 1.5 px same-colour stroke | Playfair Display Black, Libre Bodoni Bold | Fit the word to 0.93W wide; cap height capped by the band (1.3). Letter-spacing −0.02em |
| Caption word | Same family, bold, lowercase as written; first letter capital only if the user wrote it so | Bodoni Moda, weight 800, optical size 14 (low), plus a 0.6 px same-colour stroke | Playfair Display Bold, Libre Bodoni Bold | ≈ 0.143W [154] so that two words "xxxxx xxxxxx" of 12 characters span ≈ 0.79W; letter-spacing −0.005em; word space 0.22em |
| Caps keyword | Caption face, converted to UPPERCASE, same size and colour | Bodoni Moda 800 / opsz 14 + 0.6 px stroke | as above | same as caption words |

**Hairline rule:** every stroke must stay visible on bright and mid-tone footage. Never use a high optical size (it thins the hairlines of H, W, M, A until words read broken, e.g. "H APPENS"). Use the LOW optical-size axis (≈14, the sturdy text cut), weight ≥ 800, a same-colour stroke (giant 1.5 px, caption 0.6 px at W = 720, drawn at 2×) and the soft shadow below. Check a full-size crop of one giant word before delivering. Punctuation on caption words is exactly the user's ("first," stays "FIRST,").

Rules: one family, one colour. Giant words are always uppercase and drop trailing punctuation. Caption words keep the user's case and punctuation; only the keyword is uppercased. Draw letter by letter with the font's own advances (tracking via an offset). Font note: identified by letterform only (ball-terminal Didone with extreme stroke contrast); check against a reference crop, then fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Shadow: caption (0, +3 px, blur 6 px, #000000 at 60 %) plus a tight edge shadow (0, +1 px, blur 1.5 px, 55 %); giant (0, +5 px, blur 12 px, 55 %) plus the same tight edge shadow. Values at W = 720. Without them the yellow disappears on cream walls and wood.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Caption word entrance | hard pop, 1 f, no fade, no movement, at the word's spoken start | 0 s |
| Caption chunk exit | hard cut; all words of the chunk vanish in one frame | 0 s |
| Giant word entrance | hard pop at the word's spoken start, full size, no scale | 0 s |
| Giant word exit | hard cut, on the same frame as the chunk end or later by ≤ 0.15 s | 0 s |
| Gaps | between chunks nothing is on screen (the reference had a 1.3 s clean gap) | — |

Never: fades, slides, bounce, scale pops, typewriter letter-by-letter, rotation, wipes, glitch, shake, flashes, or any effect on cuts. The style is all hard pops.

### 1.6 What may happen to the user's footage

Nothing. Allowed: full-frame display, untouched, with text and shadow overlays on top. Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed changes; blur, tint, darken, colour grading or filters; cards, splits, zooms, graphic transitions, B-roll frames, background swaps; adding footage the user did not supply. The primary footage plays live, in sync with the audio, at all times.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by a giant word or a caption. Pick the giant band (1.3) from the face top: face top ≥ 0.15H → face-safe band; ≈ 0.10H → low-face band; face top < 0.09H or a face fills the top → no giant on that shot (use a caption-only moment, or place the giant only on a face-free shot) |
| Giant over hair | The reference giant overlapped the top of the hair; allowed only when the face top is below 0.25H |
| Caption lane | Default 1.3. If the face bottom edge is below 0.62H, move the block down so the first line sits ≥ 0.03H under the chin; if that pushes the last baseline below 0.93H, use a 1–2 line chunk |
| Footage text (signs, UI) | If readable footage text sits in the lane for more than 1 s, shift the lane up by 0.08H |
| Edges | Every glyph stays ≥ 0.03W from the left and right edges (giants ≥ 0.03W; captions ≥ 0.07W) |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title (giant word) · **C** caption · **K** keyword · **E** end.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · GIANT KEYWORD SLAM — T ●●● (signature)
**What it is:** the most important spoken word of a phrase appears in giant capitals across the top of the frame at the moment it is spoken, holds under the speaker's face, and disappears with its caption chunk. The word is removed from the small caption so it is not shown twice.
**Use when:** a topic, verb or contrast word carries the sentence (reference: one verb or noun per phrase); 1 per phrase, every 2–3 s. **Avoid when:** two giants would be < 1.5 s apart, or the face leaves no band (1.7).
**Text (✎):** 1 word from the user's own text, uppercase, no trailing punctuation, 3–9 letters ideal (longer words still fit by shrinking), ≤ 1 per chunk.
**Geometry / Graphics:** giant band per 1.3 (free, face-safe or low-face). Word centred on x = 0.505W, width 0.93W unless the cap-height limit binds first (then narrower, still centred). Butter yellow, giant shadow. Cap height measured on the reference: 0.173H BEST, 0.13H FORCE, 0.146H THEY, 0.14H MAKE.
**Motion (measured on the reference, 30 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ (1.43 s [43]) | giant | alpha | 0 → 1, full size | hard pop |
| hold ✎ | giant | — | final state; 0.77–0.97 s | — |
| end ✎ (2.20 s [66]) | giant | alpha | 1 → 0 | hard cut |

Start ✎ = the word's spoken start (within ±0.05 s). Hold ✎: 0.7–1.0 s; end at or just after the chunk end, never across a footage cut (end on the cut frame).
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 keeps building in the lane; the giant word is skipped in the caption line.
**Exit:** hard cut.
**Build notes:** render the word once at 2× (font size from the word width at a test size, then min with the cap-height limit) with Pillow, baked shadow, downscale with LANCZOS, composite per frame by time. Cap-height ratio of the font from `getbbox("H", anchor="ls")`. Baseline = band centre + cap/2.
**Flow prompt text:** "As the word {{WORD}} is spoken, it appears all at once in huge pale yellow capital letters in an elegant high-contrast serif face, stretched almost edge to edge across the top of the frame above the speaker's head. It stays for under a second and then disappears at once. It never covers the speaker's face."
**Still-image state:** the giant word at the top, full size.

### T2 · GIANT STACK — T ●●● (extension in the same grammar)
**What it is:** two short words stacked on two lines as one giant block, for a two-word idea.
**Use when:** a two-word phrase is the whole point (a name, "never again"); the shot has no face in the top 0.45H (B-roll, product, landscape). **Avoid when:** a face is in the top half.
**Text (✎):** two consecutive user words, uppercase, ≤ 14 letters total, no punctuation.
**Geometry / Graphics:** T1 styling; each line fits 0.93W; line pitch 0.95 em; block centred on y = 0.22H; total cap height ≤ 0.32H.
**Motion:** both words pop together at the first word's start, hold 1.0–1.3 s, hard cut. Same table as T1.
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 continues in the lane; both words skipped in the caption.
**Exit:** hard cut.
**Build notes:** draw each line like T1; stack with 0.95 em pitch.
**Flow prompt text:** "As {{WORD_1}} {{WORD_2}} is spoken, both words appear at once, stacked on two lines, in huge pale yellow capital letters in an elegant high-contrast serif face across the upper part of the frame. They stay about a second and disappear at once."
**Still-image state:** stack at the top.

### T3 · GIANT ON BROLL — T ●●● (extension)
**What it is:** T1 at full reference size on a shot with no face in the top 0.30H.
**Use when:** B-roll, product, hands, plants, landscapes: a face-free shot with a strong spoken word. **Avoid when:** any face or head sits in y 0.10–0.35H.
**Text (✎):** as T1.
**Geometry / Graphics:** free band: centre y 0.20H, cap height up to 0.17H [326], width 0.93W (demo2: YEAR at cap 0.14H, AUTOMATE cap 0.07H because the long word was width-limited).
**Motion:** as T1; end ≥ 1 f before a footage cut (on the cut frame).
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 lane as normal.
**Exit:** hard cut.
**Build notes:** as T1.
**Flow prompt text:** "As the word {{WORD}} is spoken, it appears all at once in huge pale yellow capital letters in an elegant high-contrast serif face across the top of the frame, over the scene, stays under a second and disappears at once."
**Still-image state:** the giant word in the free band.

### C1 · BUTTER CAPTION BLOCK — C ●● (signature, the caption system)
**What it is:** a phrase of 2–5 words pops in word by word near the bottom, centred, in small bold lowercase Didone. Words stay put once they appear. The whole block is cut at the end of the phrase. Nothing is on screen between phrases.
**Use when:** always on speech. **Avoid when:** no speech and no on-screen need (use C2 or skip).
**Text (✎):** the user's exact words, case as written; 2–5 words per chunk (reference: 2, 5, 2, 3); split at punctuation and natural phrases; never end on an article, preposition or conjunction; ≤ 1 keyword per chunk (K1); a giant word (T1) is skipped inside the chunk.
**Geometry / Graphics:** caption lane (1.3). Lay the whole chunk out first so no word moves: greedy wrap at 0.80W, lines centred on x = 0.50W, line pitch 0.095H, word space 0.22em. If one word is wider than 0.86W, shrink the whole chunk's font until it fits (demo2: INVESTMENTS, at 0.86 of base).
**Motion (measured on the reference, 30 fps; chunks "your IDEAS", "don't arrive when you THEM", "ARRIVE when", "you finally ROOM"):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha | 0 → 1 at its fixed position | hard pop (1 f) |
| chunk end ✎ | all words | alpha | 1 → 0 | hard cut |

Word start = spoken start. Chunk end = last word start + 0.45–0.7 s hold, or the next chunk's first word, or the footage cut, whichever is first (reference holds: 0.47, 0.40, 0.27 and 0.73 s after the last word). Gaps of 0.5–1.3 s with no caption are allowed in pauses.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system. At a cut, end the chunk on the cut frame if the speech continues; start the next chunk on the next word.
**Exit:** hard cut.
**Build notes:** one RGBA layer per word (baked shadow); at each frame composite the words with start ≤ t. Measure with `font.getlength` before layout. Run the caption audit: all caption words plus giant words, in order, equal the user's text.
**Flow prompt text:** "In the lower middle of the frame, short captions appear word by word in small bold lowercase letters in pale yellow, in an elegant high-contrast serif face. Each word pops into place at the moment it is spoken and never moves. When the phrase is finished, all its words disappear at once. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk in the lane.

### K1 · CAPS KEYWORD — K ●● (signature detail of C1)
**What it is:** one word per chunk is written in capitals at the same size, as a second beat of emphasis inside the small caption.
**Use when:** a chunk has a meaning-carrying noun or verb (the object, the action, the number word). **Avoid when:** the chunk is only fillers; never two caps words in one chunk; never on a word already used as a giant.
**Text (✎):** 1 word per chunk, ≤ 1 per 2.5 s on average, uppercase conversion only (the word stays the user's word). Keep its punctuation.
**Geometry / Graphics:** same face, size, colour and shadow as caption words; it is simply uppercase, so it is wider (a 6-letter caps word ≈ 0.50W).
**Motion:** pops in on its own spoken start like any word (C1 table).
**Footage / plate behaviour:** untouched.
**Captions during it:** inside C1. It may sit anywhere in the chunk (reference: last, first, last).
**Exit:** with the chunk.
**Build notes:** call `.upper()` on the display text only; the audit uses the original word.
**Flow prompt text:** "Inside the small caption, the word {{KEYWORD}} is written in capital letters while the other words stay lowercase, all in the same pale yellow."
**Still-image state:** chunk with the capital word.

### C2 · SOLO WORD CAPTION — C ●● (extension)
**What it is:** a one-word chunk (a punchy single word or an interjection) sits alone on one line in the lane.
**Use when:** a single emphatic word sits between pauses, or a shot has a one-word beat. **Avoid when:** it would be the giant's own word.
**Text (✎):** 1 user word, case as written (uppercase if it is the chunk's keyword).
**Geometry / Graphics:** C1 lane, one line, baseline 0.79H, centred.
**Motion:** pop at the spoken start; hold ≥ 0.4 s after; hard cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** it is the caption.
**Exit:** hard cut.
**Build notes:** same as C1 with one word.
**Flow prompt text:** "Near the bottom of the frame, the single word {{WORD}} pops in by itself in small pale yellow lettering in an elegant serif face and disappears at once."
**Still-image state:** one word in the lane.

### C3 · LANE SHIFT — C ● (extension)
**What it is:** the caption block sits higher or lower so it clears a face, a hand or readable footage text, without any animation.
**Use when:** the face bottom is below 0.62H, a subject stands in the lane, or footage text sits there. **Avoid when:** the default lane is clear.
**Text (✎):** none.
**Geometry / Graphics:** shift the block up by 0.08H (to put the last baseline near 0.71H) or down to a last baseline of 0.90H; never inside the giant band; keep the chunk's line count ≤ 2 when shifted up.
**Motion:** none; the position is fixed for the whole chunk; at a cut it may change on the cut frame.
**Footage / plate behaviour:** untouched.
**Captions during it:** inside C1.
**Exit:** with the chunk.
**Build notes:** add a y offset to the lane baseline per chunk.
**Flow prompt text:** "The captions sit slightly {{higher_or_lower}} than usual so they stay clear of the {{SUBJECT}}."
**Still-image state:** chunk at the shifted lane.

### E1 · CLEAN CLOSE — E ● (extension)
**What it is:** the last chunk (and last giant) hard-cut away just before the clip ends, so the final frames are clean footage.
**Use when:** always at the end of a speech video. **Avoid when:** the audio ends in the last 0.2 s.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** the last caption and giant end at the clip end minus 0.05–0.3 s (reference: last text left 0.07 s before the end; demo2: 0.05 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** none after the cut.
**Exit:** hard cut.
**Build notes:** set the last chunk end and giant end ≤ duration − 0.05 s.
**Flow prompt text:** "The last words disappear at once just before the video ends and the picture finishes clean."
**Still-image state:** footage only.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 + T1 on the first topic word | T3 on face-free B-roll words, T1 on speaker words, K1 per chunk | C1 + T1 on the payoff word, E1 |
| Single talking head, no cuts | C1 + T1 | T1 every 2–3 s, K1 per chunk, C3 if the face is low | T1 on the last word, E1 |
| B-roll only, no speech | C2 phrases timed to the shots + T3 on the title word | T2 on a two-word idea | E1 |
| Still image + text | giant word in the band + C1 chunk in the lane | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Caption font size 98 px (0.137W) at Bodoni Moda 800 / opsz 14 + 0.6 px stroke, tracking −0.005em; giant Bodoni Moda 900 / opsz 14 + 1.5 px stroke, tracking −0.02em. The first version (700/opsz 28 and 800/opsz 72) lost its hairlines on cream walls and wood.
- Giant sizes used: MONEY 181 px (cap 0.107H, face-safe band, bottom 0.14H), AUTOMATE 117 px (width-limited on the phone shot), SPEND 118 px (low-face band, bottom 0.095H, width 0.55W because the shopper's head starts at 0.10H), YEAR 234 px (free band, cap 0.14H), HAPPENS 139 px (face-safe band).
- Giant timing used: MONEY 0.35–1.20, AUTOMATE 3.25–4.10 (starts on the cut, word at 3.20), SPEND 5.15–5.95, YEAR 7.65–8.35 (ends before the 8.375 cut), HAPPENS 9.15–9.95.
- Caption chunks used: "Saving isn't about" 0.10–1.10, "EARNING more." 1.10–1.83, "Pay yourself FIRST," 2.10–3.20, "your INVESTMENTS," 3.55–4.85, "and only what's LEFT." 4.95–6.60, "Do it for ONE" 6.90–8.30, "and WATCH what" 8.45–9.95. INVESTMENTS, needed the 0.86 shrink.
- Shadows were required on every shot; with them the pale yellow read on the cream wall, wood desk and bright shop.
