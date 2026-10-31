# moments.md — Water Fill Caps: Style Bible + Moment Library

This file is the single source of truth for the Water Fill Caps caption style. Part 1 is the style bible (palette, type, motion, footage rules, safe zones). Part 2 is the moment library with specs measured on a 540x960, 30 fps, 8.1 s reference reel and tuned on a 720x1280, 24 fps render. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: the footage stays full frame and untouched. (The reference also showed a black title wall and a slow zoom; only its type system is used here.)

**The look in one line:** small heavy white lead-in words pop up under the speaker's chin, and the phrase lands on one giant keyword in chunky type that is filled with a pale-to-deep blue water texture and spans almost the full width.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Lead white | #FFFFFF | Small lead-in words |
| Water deep | #163045 | Darkest patches inside the keyword fill (measured 5th percentile 22,48,69) |
| Water mid-dark | #376881 | Fill gradient stop (55,104,129) |
| Water mid | #7BA0BE | Fill gradient stop, median of the reference fill (123,160,190) |
| Water light | #BED5E8 | Fill gradient stop (190,213,232) |
| Water pale | #D5E9FA | Lightest streaks (213,233,250) |
| Text shadow | #000000 at 55 % | Soft shadow under every caption glyph (design decision, needed on bright footage) |

Brand-swap rule: if the user gives a brand colour, rebuild the water fill as a 5-stop ramp from a very dark to a very light tint of that colour. White stays white. No other colours exist.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, boxes, plates, borders, masks, blur or colour overlays. |
| Caption block | Text only, centred on x = 0.50W. Lead-in lane and keyword lane per 1.3. |
| Water fill | A single texture, 4 soft cloud-like blobs of dark and light blue across the full frame (noise scales 0.22W, 0.10W, 0.04W; weights 0.5, 0.35, 0.15; contrast stretched ×1.8), mapped through the 5 palette stops. Fixed in screen space, never animated, so each keyword shows a different slice of it. Render it once. |

### 1.3 Layouts / grid

| Layout | Region | Use |
|---|---|---|
| Lead-in lane | last baseline 0.545H [1046]; line pitch 0.056H [108]; max 2 lines; max line width 0.84W | Small white words, stacked upward from the last baseline |
| Keyword lane | baseline 0.685H [1315]; x-height top ≈ 0.58H; width up to 0.92W; centred on x = 0.50W | Giant keyword |
| Reference values | lead-in last baseline ≈ 0.50–0.53H, keyword baseline ≈ 0.65H, keyword width 0.88–0.93W | Measured on the reference |

Both lanes sit in the lower middle, below the chin of a centred speaker.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Lead-in | Ultra-heavy grotesque, mixed case as written, tight spacing, white, soft shadow | Archivo (variable) weight 900, width 100 | Archivo Black, Montserrat Black, Inter ExtraBold | 0.095W [103]; line height 0.056H |
| Giant keyword | Same family, wider and heavier, filled with the water texture, soft shadow | Archivo weight 900, width 108 | Archivo Black, Montserrat Black | fit to 0.92W, capped at 0.34W [367]; shrink font until the word fits |
| Title (T1) | Giant keyword style, stacked | as above | as above | each line fit to 0.86W, cap 0.30W |

Rules: case exactly as the user wrote it (no forced uppercase). Punctuation stays attached to its word and is filled too. No outlines, no italics, no rotation.

Text shadow: (0, +3 px, blur 7 px, #000000 at 55 %), drawn at 2× then downscaled.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Lead-in word entrance | alpha ramp, ease-out (1−(1−t)³), no movement | 0.10 s (reference 2–3 f at 30 fps) |
| Keyword entrance | same ramp, 0.10 s, no movement | 0.10 s |
| Chunk exit | hard cut, whole chunk gone in one frame | 1 f |
| Cuts | hard cut; the new chunk starts on the cut | 0 f |
| Footage push (M1) | linear scale | across the shot |

Words appear one by one at their spoken time and never move once placed (the full chunk is laid out first). Never: bounce, overshoot, slides, typewriter letters, rotation, outlines, flashes, wipes, colour changes of a word after it appears.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Slow push-in about the face or subject (M1) | Total scale ≤ 1.15 per shot; reset at the next cut |
| Text and shadow overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; black or colour walls that hide the footage; text-shaped windows that replace the picture; speed ramps; freezing; blur, glitch, warp, colour grading; adding footage the user did not supply. The primary footage plays live, in sync with the audio.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. The first lead-in line top (last baseline − (lines−1) × 0.056H − 0.07H) must sit ≥ 0.01H below the chin. If it does not, move both lanes down by up to 0.06H; if still blocked, drop the lead-in to one line. |
| Keyword lane | Keep the baseline ≤ 0.90H. If a face sits low (chin below 0.58H), put the lead-in above the face only if it clears the hair line; otherwise skip the lead-in and use K1 in the free lane. |
| Footage text (UI, signs) | If readable text sits in a lane for more than 1 s, shift both lanes by up to 0.10H. |
| Edges | Every glyph stays ≥ 0.04W from the left and right edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **K** keyword · **T** title · **X** cut treatment · **M** footage motion · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### C1 · LEAD-IN + GIANT KEYWORD — C ●●● (signature, the caption system)
**What it is:** a phrase builds in two layers. Small white heavy words pop in one by one under the face, then the last meaning word lands below them as a giant water-filled word. The whole chunk is replaced at once by the next.
**Use when:** always, on any shot with speech or phrases. **Avoid when:** the keyword is longer than 14 characters and would shrink under 0.12W (use C2).
**Text (✎):** the user's exact words, case as written. Chunk = 1–4 lead-in words + 1 keyword (a keyword may carry trailing punctuation). Split at punctuation and natural phrases; never end the lead-in on an article, preposition or conjunction when the keyword could not follow it; the keyword is the strongest noun, verb or number of the chunk and is usually the last word. Chunk length 0.8–2.0 s.
**Geometry / Graphics:** lead-in lane and keyword lane (1.3). Lead-in wraps balanced into at most 2 lines if the single line exceeds 0.84W; lines are centred on x = 0.50W and stack upward from the last baseline. Keyword fits 0.92W, cap 0.34W.
**Motion (measured on the reference, 30 fps; chunk "at the payoff / can": words at 1.9, 2.2, 2.3 s, keyword at 2.6 s, chunk gone at 2.83 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | lead-in word | alpha | 0 → 1 | ease-out, 0.10 s |
| keyword start ✎ | keyword | alpha | 0 → 1 | ease-out, 0.10 s |
| chunk end ✎ | all words | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Word start = the word's spoken start time. Chunk end = the next chunk's start, or min(last word end + 0.4 s, next cut), or end − 0.25 s for the last chunk.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system.
**Exit:** hard cut.
**Build notes:** render each state (chunk, words visible) once at 2×, quantise alpha to 1/8 steps for caching; lead-in in white with shadow, keyword as a glyph mask filled from the pre-rendered water texture (same screen position every time); measure with `font.getlength`; Archivo variable axes order in Pillow is [weight, width].
**Flow prompt text:** "In the lower middle of the frame, captions build up in two layers. Small, very bold white words appear one by one under the speaker's chin, and then the key word, {{KEYWORD}}, appears below them very large in chunky lettering filled with a blue water texture of pale and deep blue, almost as wide as the frame. When the phrase is done it is replaced at once by the next one. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### K1 · SOLO GIANT KEYWORD — K ●●● (signature)
**What it is:** one payoff word alone in the keyword lane, no lead-in.
**Use when:** a strong turn or payoff word, a number, or a one- or two-word sentence ("more.", "never", "free"); also when a chunk's lead-in was spoken before a cut and only the keyword remains. **Avoid when:** more than 2 per 5 s.
**Text (✎):** one user word (with its punctuation), case as written.
**Geometry / Graphics:** keyword lane; font fit 0.92W, cap 0.34W; same fill and shadow.
**Motion:** C1 keyword entrance (0.10 s alpha ramp); hold 0.4–1.5 s; hard cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the normal chunk.
**Exit:** hard cut.
**Build notes:** C1 renderer with an empty lead-in.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in the lower middle of the frame, very large, in chunky lettering filled with a blue water texture, fading in quickly, then is replaced by the next caption."
**Still-image state:** the word.

### C2 · PLAIN WHITE STACK — C ●● (extension in the same grammar)
**What it is:** a chunk with only small white lead-in words, for phrases with no strong keyword or a keyword too long for the giant lane.
**Use when:** connective phrases, long words (> 14 characters), or when C1 would repeat more than 3 times in a row. **Avoid when:** it is the only mode used in a video.
**Text (✎):** 2–6 user words, ≤ 2 lines.
**Geometry / Graphics:** lead-in lane (1.3), font 0.095W, last baseline 0.545H ✎ (shift per 1.7).
**Motion:** word-by-word ease-out ramps (0.10 s), hard cut out.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut.
**Build notes:** C1 renderer with no keyword.
**Flow prompt text:** "In the lower middle of the frame, a short phrase, {{PHRASE}}, builds word by word in small, very bold white lettering, then is replaced at once by the next phrase."
**Still-image state:** the phrase.

### T1 · STACKED WATER TITLE — T ●●● (extension in the same grammar)
**What it is:** a one- to three-word title stacked on separate lines, every word in the giant water-fill type, popping in line by line.
**Use when:** the opening line names the topic and the first 1.0 s has room (a speaker with the face high, or B-roll). **Avoid when:** the face box would be covered (use C1 instead), or within 0.3 s after a cut.
**Text (✎):** 1–3 of the user's own words, as written, max 20 characters in total.
**Geometry / Graphics:** lines fit 0.86W (cap 0.30W), line pitch 0.14H, last baseline 0.685H, centred; water fill and shadow as 1.1/1.4. It replaces the C1 chunk for its duration.
**Motion:** each line alpha 0 → 1 over 0.10 s, lines 0.15–0.25 s apart; hold 0.8–1.4 s; hard cut.
**Footage / plate behaviour:** untouched.
**Captions during it:** none; the title is the caption for those words (they are removed from the next chunk, caption audit counts them).
**Exit:** hard cut.
**Build notes:** one layer per line count; reuse the keyword mask code.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, appears in the lower middle of the frame with each word on its own line, in very large chunky lettering filled with a blue water texture, each line fading in quickly one after another, then it is replaced by the captions."
**Still-image state:** full title.

### X1 · CUT RESET — X ● (signature treatment of every cut)
**What it is:** the shot changes with a plain hard cut and the caption chunk changes on the same frame.
**Use when:** every footage cut. **Avoid when:** never; add no effect.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** at the cut frame ✎ the running chunk ends and the next chunk starts; if speech continues over the cut, the new chunk starts with the next unspoken word. If only the keyword of the old chunk remains unspoken, use K1.

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut ✎ | caption chunk | old chunk → new chunk | same frame | hard cut |

**Footage / plate behaviour:** untouched; no flash, blur or zoom.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** split chunks at cut times and set the chunk start to max(first word start, cut time).
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the caption on screen is replaced in the same moment by the next caption."
**Still-image state:** none.

### M1 · SLOW PUSH — M ● (extension in the same grammar)
**What it is:** a gentle push-in on a long static shot (the reference slowly zooms into the speaker during its last seconds).
**Use when:** a shot longer than 2 s with little motion, or the last shot. **Avoid when:** the footage already moves a lot.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** scale ×1.00 → ×1.10 across the shot (linear, max 1.15), about the face box centre ✎; reset at the next cut. Captions do not scale.
**Footage / plate behaviour:** live footage, scaled only.
**Captions during it:** unaffected.
**Exit:** reset by the cut.
**Build notes:** `Image.resize(..., box=floats)` about the anchor; clamp the crop box.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last chunk stays until just before the end, then the picture finishes clean.
**Use when:** every video.
**Text (✎):** the last chunk's words.
**Geometry / Graphics:** C1 or K1.
**Motion:** hold to min(last word end + 0.4 s, end − 0.25 s); the final 0.25 s has no caption.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | C1 (or T1 if the face is high and the first line names the topic) | X1 on every cut; C1 per phrase; K1 on a payoff or one-word sentence; C2 for connective phrases | C1 + E1 |
| Single talking head, no cuts | C1 | K1 on one payoff word; C2 between; M1 on a shot > 2 s | E1 |
| B-roll only, no speech | T1 (user's own words) | X1 on every cut; C1 or K1 phrases of 1.0–2.0 s | E1 |
| Still image + text | C1 in its settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Lead-in 0.095W (68 px), last baseline 0.545H, pitch 0.056H; keyword baseline 0.685H. The speaker's chin sat at about 0.40H, so lane positions were clear of the face with no shift.
- Keyword fit: "earning" and "more." fill 0.92W; "investments," (12 characters) shrinks to about 0.15W and reads thin on the bright phone screen (acceptable, shadow 55 % keeps it legible); a keyword with 8–9 characters lands near 0.20–0.23W.
- Keyword fill texture first built with 0.5/0.3/0.2 noise at scales 0.12/0.055/0.02 looked speckled; the 0.5/0.35/0.15 mix at 0.22/0.10/0.04 with contrast ×1.8 matches the reference's smooth ice-water look.
- Two keywords in one chunk ("earning more.") shrank the type too much; split it: lead-in + "earning", then K1 "more." at 1.45 s.
- Chunk plan used: "Saving money isn't about / earning" (0.10), K1 "more." (1.45), "Pay yourself / first," (2.10), "automate your / investments," (3.25, on the cut), "and spend only what's / left." (4.95), "Do it for one / year" (6.90), "and watch what / happens." (8.45 to 9.75).
- M1 skipped: no shot needed it.
