# moments.md — Chrome Tier: Style Bible + Moment Library

This file is the single source of truth for the Chrome Tier caption style. Part 1 is the style bible (palette, type, motion, footage rules, safe zones). Part 2 is the moment library measured and tuned from a 1080x1920, 24 fps, 13.6 s reference reel. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. This is a caption system only: the reference also used blur pulls, floating cards and background changes, and none of that is part of this skill.

**The look in one line:** captions are set in two tiers, small light white sans for the connecting words and big heavy italic keywords filled with a glossy teal-silver chrome gradient, stepping down the lower frame in a loose staggered stack over footage that stays full-frame and untouched.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 24 fps, so "f" values are 24 fps frames; at another fps keep the seconds. Reference values in brackets are for 1080×1920. The demo values (720×1280) are in the tuning notes at the end.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Small word | #FFFFFF | Connecting words (tier 1) |
| Chrome dark | #2E4240 | Left and right ends of the keyword gradient, keyword edge ink #18262A |
| Chrome mid | #96B8C0 | Quarter points of the gradient (measured pale teal-grey on the reference) |
| Chrome light | #EEF6F7 | Bright band at 55 % of the keyword width |
| Chrome low | #78A0AA | 80 % point, then back to Chrome dark |
| Shadow | #000000 | Soft shadow under every word |

Brand-swap rule: if the user gives a brand colour, tint the chrome mid and low stops towards it; keep the light band near white and the ends dark. Never change the white small words.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, untouched. No cards, boxes, plates, borders, masks, blur or dimming. |
| Text block | A stack of 1–3 lines, no background shape. Block width ≤ 0.86W. Left, right or centre aligned (✎). |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Lower lane | 0.07, 0.56, 0.93, 0.84; first baseline 0.655H | Default for every chunk |
| Top lane | 0.07, 0.03, 0.93, 0.15; baseline 0.115H | One-line chunks only (T1), when the face box top is ≥ 0.15H |
| Side margin | 0.07W each side | Left edge of a left stack, right edge of a right stack |
| Line indent | odd lines shift 0.05W towards the centre | The staggered "stair" |
| Line pitch | 0.20W if the next line holds a keyword; 0.17W after a line with a keyword; 0.105W for small-only lines | Between baselines |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Small word | Light-to-regular grotesk, mixed case as written, very tight spacing | Inter, weight 380 | Inter Tight Regular, Manrope Medium | 0.092W [99]; letter-spacing −0.035em; word gap 0.22 × size |
| Keyword | Black-weight italic grotesk, mixed case as written, chrome gradient fill, 3 px dark edge at 2× | Inter Tight Black Italic | Archivo ExtraBold Italic, Barlow ExtraBold Italic | 0.21W [227]; letter-spacing −0.02em; shrink ×0.94 steps down to 0.10W until the word fits ≤ 0.86W |
| Keyword gradient | Horizontal: 0 % #2E4240, 38 % #96B8C0, 55 % #EEF6F7, 80 % #78A0AA, 100 % #344A4C; plus a soft horizontal highlight band at 42 % of the height (+30 levels) | — | — | per word |
| Top-lane sizes | small 0.085 × and keyword 0.78 × the lower-lane sizes | — | — | — |

Font note: identified by letterform (tight neo-grotesk light for small words, heavy slanted grotesk with chrome shading for keywords). Check against the reference crops; fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Rules: text case exactly as the user wrote it. No outline-only text. Nothing rotated. Every word keeps the shadow (0, +6 px at 1×, Gaussian blur 7 px at 2×, #000000 at 100 % doubled for small words; keyword shadow 59 %, blur 10 px, offset +4 px).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Small word entrance | ease-out alpha ramp (cubic), no movement | 0.17 s (4 f) |
| Keyword entrance | ease-out alpha ramp + settle from 1.07× to 1.00× about its centre | 0.17 s (4 f) alpha, 0.25 s (6 f) settle |
| Chunk exit when the next chunk starts within 0.1 s | hard cut in the same frame | 1 f |
| Chunk exit otherwise | linear alpha fade | 0.125 s (3 f) |
| Cuts | footage cuts plainly; the caption carries on across the cut unchanged | 0 f |

Words never move once visible: the whole chunk is laid out before its first word appears. Never: bounce, overshoot, slides, typewriter letters, rotation, blur on the text, flashes, colour changes after appearing.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Text and shadow overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; blur, dimming, grading or filters; cards, split screens, background swaps, blur pulls, graphic transitions; adding footage the user did not supply. The footage plays live in sync with the audio at all times.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered. Lower lane is used when the face box bottom edge is ≤ 0.56H. If the face sits lower, mirror to the top lane for one-line chunks, or shift the stack so the first baseline is ≥ 0.03H under the chin and the last baseline ≤ 0.88H. |
| Top lane | Allowed only if the glyph bottoms (including descenders) stay ≥ 0.02H above the face box top and the face box top ≥ 0.15H. |
| Footage text (signs, UI) | If readable footage text sits in the lane for more than 1 s, flip the stack to the other lane, or change the alignment side. |
| Edges | Every glyph ≥ 0.07W from the left and right edges. |
| Bright footage | White small words and a pale chrome fill lose contrast on bright, flat footage. Keep the shadow and the dark edge as written; if still weak, move the stack onto the darker half (C3). |

---

## PART 2 — MOMENT LIBRARY

Family codes: **C** caption · **T** title/headline · **K** keyword · **X** cut treatment · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### C1 · TIERED LINE — C ●● (signature, the caption system)
**What it is:** a phrase builds word by word in the lower lane. Small light white words and heavy chrome keywords share one baseline, each new word fading in where it will stay; the next phrase replaces the block.
**Use when:** always, on every kind of shot. **Avoid when:** never; use C3 to protect a face or footage text.
**Text (✎):** the user's exact words, case as written. Chunks of 2–5 words; split at punctuation and natural phrases; never end a chunk on an article, preposition or conjunction where avoidable; 0.6–1.7 s per chunk. Keywords ✎: exactly one per chunk (a second only in K3), the most meaning-carrying noun, verb or number; never an article or preposition.
**Geometry / Graphics:** Lower lane, first baseline 0.655H. Small words and the keyword share a baseline on a line while the line fits ≤ 0.86W; a small word that follows a keyword starts a new line; a keyword that does not fit starts a new line. Odd lines indent 0.05W. Pitches per 1.3. Alignment ✎ left or right (C2 alternates it).
**Motion (measured on the reference, 24 fps, words about 0.25–0.4 s apart, tuned on demo):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | small word | alpha | 0 → 1 | ease-out, 4 f |
| word start ✎ | keyword | alpha, scale | 0 → 1, 1.07 → 1.00 | ease-out, 4 f / 6 f |
| chunk end ✎ | all words | alpha | 1 → 0 | hard cut at the next chunk's first word, else 3 f fade |

Word start = the word's spoken start time. Chunk end = the next chunk's first word start, or min(last word end + 0.4 s, next cut + 0.2 s, video end − 0.25 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system.
**Exit:** per the table.
**Build notes:** draw each word as a separate RGBA sprite at 2×, per-character tracked drawing (`font.getlength(text[:i]) + i × tracking × size`), downscale ×0.5 with LANCZOS; lay out every chunk once; baseline of each sprite = text origin + `font.getbbox("H")[3]/2`.
**Flow prompt text:** "In the lower part of the frame, captions build up word by word. Ordinary words are small, thin and white. The important word, {{KEYWORD}}, is large, heavy and slanted, filled with a glossy teal and silver metal shine, and sits on the same line or steps down onto its own line. Each word fades in softly in place and the phrase is replaced by the next. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### K1 · CHROME KEYWORD — K ●● (signature, the look of the keyword)
**What it is:** the keyword's material: black italic letters with a teal-silver chrome gradient, a dark edge and a soft shadow, settling in from slightly oversized.
**Use when:** inside every C1 chunk. **Avoid when:** the word is longer than 14 characters (it will shrink; if it falls under 0.10W, set it as a small word).
**Text (✎):** one user word, case as written.
**Geometry / Graphics:** Keyword type per 1.4: gradient stops, 3 px edge in #18262A at 2× (alpha 90 %), shadow offset +8 px at 2×, blur 10 px.
**Motion:** per C1 keyword row.
**Footage / plate behaviour:** untouched.
**Captions during it:** part of the chunk.
**Exit:** with the chunk.
**Build notes:** build the gradient as a NumPy array, mask with the text alpha, paste over the edge layer, composite over the blurred shadow.
**Flow prompt text:** "The keyword {{KEYWORD}} is drawn in large heavy slanted letters with a glossy blue-grey and silver metallic gradient, a thin dark outline and a soft shadow."
**Still-image state:** the finished word.

### T1 · OPENER HEADLINE — T ●● (signature opener)
**What it is:** the first two words of the video as a single compact line in the top lane, small word plus chrome keyword, appearing as the speaker starts.
**Use when:** the video opens on a speaker or calm shot with the face box top ≥ 0.15H. **Avoid when:** the face box top is above 0.15H, or the first words need two lines (use C1 in the lower lane).
**Text (✎):** the user's first 2–3 words, the last one the keyword. Max 16 characters.
**Geometry / Graphics:** Top lane, baseline 0.115H, left aligned at 0.07W; small word 0.085 × and keyword 0.78 × the lower-lane sizes; one line only.
**Motion:** per C1 (word starts at the spoken times, ≥ 0.25 s apart); holds until the next chunk starts.
**Footage / plate behaviour:** untouched.
**Captions during it:** none other.
**Exit:** hard cut to the C1 chunk.
**Build notes:** same renderer as C1 with the lane parameter set to top.
**Flow prompt text:** "At the very start, in the top-left of the frame, a short opening line appears: a small white word followed by {{KEYWORD}} in large glossy metallic slanted lettering. It stays clear of the face."
**Still-image state:** final state.

### C2 · MIRROR STACK — C ●● (signature variation)
**What it is:** consecutive chunks alternate between a left-hand stack and a right-hand stack so the block seems to zigzag down the frame.
**Use when:** two or more chunks in a row in the lower lane. **Avoid when:** a face or footage text sits on the chosen side (use the other side).
**Text (✎):** as C1. **Side ✎:** left or right per chunk, alternating by default.
**Geometry / Graphics:** C1 geometry; right alignment puts each line's right edge on 0.93W (minus the line indent).
**Motion:** as C1; the side flips on chunk boundaries only.
**Footage / plate behaviour:** untouched. **Captions during it:** this is the caption.
**Exit:** as C1.
**Build notes:** the alignment is a per-chunk parameter.
**Flow prompt text:** "Caption blocks alternate sides: one hugs the left side of the lower frame, the next hugs the right side, each built word by word."
**Still-image state:** one chunk.

### K2 · SOLO CHROME WORD — K ●●● (extension in the same grammar)
**What it is:** one payoff word alone, chrome, at 1.3× keyword size.
**Use when:** a strong turn or payoff word, a number or a name. **Avoid when:** the word is longer than 9 characters; max 2 per video, ≥ 3 s apart.
**Text (✎):** one user word, case as written.
**Geometry / Graphics:** Keyword style at 0.27W, left or right aligned per C2, baseline 0.66H, shrink to fit 0.86W.
**Motion:** keyword entrance; hold 0.5–0.9 s; hard cut to the next chunk.
**Footage / plate behaviour:** untouched. **Captions during it:** replaces the normal chunk.
**Exit:** hard cut.
**Build notes:** scale the font size, not the bitmap.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in the lower frame in very large glossy metallic slanted letters, then is replaced by the next caption."
**Still-image state:** the word.

### K3 · KEYWORD PAIR — K ●● (extension in the same grammar)
**What it is:** a chunk with two chrome keywords, each starting its own line, small words in between.
**Use when:** a contrast or a two-part idea ("more … less"). **Avoid when:** more than 2 per video.
**Text (✎):** 4–6 user words, two of them keywords.
**Geometry / Graphics:** C1 geometry, up to 3 lines; the second line indents 0.05W.
**Motion:** as C1. **Footage / plate behaviour:** untouched. **Captions during it:** this is the caption.
**Exit:** as C1. **Build notes:** as C1.
**Flow prompt text:** "A caption with two heavy metallic slanted words, {{KEYWORD_1}} and {{KEYWORD_2}}, each on its own line, with small white words between them."
**Still-image state:** the chunk.

### C3 · LANE GUARD — C ● (extension in the same grammar)
**What it is:** the placement rule that keeps captions off faces and footage text: lane, side and size are adapted per shot.
**Use when:** a face or readable footage text sits in the lower lane, or the footage is bright and flat. **Avoid when:** the default lane is clear.
**Text (✎):** none.
**Geometry / Graphics:** options in order: switch side; move the stack so the first baseline is ≥ 0.03H under the chin; use the top lane for a one-line chunk; shrink keywords to ≥ 0.15W.
**Motion:** none; applied before the chunk starts.
**Footage / plate behaviour:** untouched. **Captions during it:** as chosen.
**Exit:** none. **Build notes:** compute from the scene table's face boxes.
**Flow prompt text:** "The captions sit in whichever part of the frame keeps the speaker's face and any readable text clear."
**Still-image state:** none.

### X1 · CUT CARRY — X ● (signature treatment of every cut)
**What it is:** the footage cuts plainly and the caption carries across the cut without moving, so the text becomes the thread between shots.
**Use when:** every footage cut. **Avoid when:** a chunk is wholly in a lane that the new shot's subject occupies (apply C3 on the cut frame).
**Text (✎):** none. **Geometry / Graphics:** none.
**Motion:** no change at the cut; a chunk boundary within ±0.15 s of a cut is moved onto the cut frame.
**Footage / plate behaviour:** untouched; no flash, blur or zoom.
**Captions during it:** unchanged.
**Exit:** none. **Build notes:** snap chunk starts to cuts when within 0.15 s.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the caption words stay exactly where they are."
**Still-image state:** none.

### T2 · SECTION HEADLINE — T ●● (extension in the same grammar)
**What it is:** a later chunk set as a one-line headline in the top lane for a new topic.
**Use when:** a new topic word, ≥ 3 s after T1 and the face box top ≥ 0.15H. **Avoid when:** the video is shorter than 6 s.
**Text (✎):** 2–3 user words, last one the keyword, max 16 characters.
**Geometry / Graphics:** as T1, side ✎ left or right.
**Motion:** as T1. **Footage / plate behaviour:** untouched. **Captions during it:** none other.
**Exit:** hard cut to the next chunk. **Build notes:** reuse T1.
**Flow prompt text:** "Later, a short headline appears at the top of the frame: a small white word and {{KEYWORD}} in large glossy metallic slanted letters."
**Still-image state:** final state.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last chunk holds to just before the end and the picture finishes clean.
**Use when:** every video. **Avoid when:** never.
**Text (✎):** the last chunk's words.
**Geometry / Graphics:** C1 lower lane.
**Motion:** holds to min(last word end + 0.4 s, end − 0.25 s), then a 3 f fade; the last 0.25 s has no caption.
**Footage / plate behaviour:** untouched. **Captions during it:** per above.
**Exit:** video ends. **Build notes:** none beyond C1.
**Flow prompt text:** "The last caption stays until just before the end, then fades and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 | C1 with C2 side flips, X1 on every cut, K3 on a contrast, C3 where a face or text blocks the lane | E1 |
| Single talking head, no cuts | T1 + C1 | C2 side flips, K2 on one payoff word, T2 at a new topic | E1 |
| B-roll only, no speech | C1 phrases of 1.0–2.5 s | X1, C2, C3 | E1 |
| Still image + text | C1 chunk in its settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Sizes used: small 0.092W (66 px), keyword 0.21W (151 px); top lane small 0.85 ×, keyword 0.78 × of those. First attempt at 0.075W / 0.15W read too small against the reference; the reference keyword reads about 0.17–0.21W.
- Baselines: lower lane 0.655H; top lane 0.115H. The first layout used a fixed ascent guess and put small words above the keyword baseline; the fix is the `getbbox("H")` rule in C1 build notes.
- Pitches 0.20W / 0.17W / 0.105W stopped the small line from overlapping the keyword line below it.
- "Saving money" did not fit one line at lower-lane sizes (keyword 0.21W wide ≈ 0.67W); the top-lane sizes fix it and keep it above the face (face box top 0.15H).
- Chunks used (start–end s, side): Saving money .10–.55 top; isn't about earning more. .55–1.85 L; Pay yourself first, 2.10–3.20 R; automate your investments, 3.20–4.95 L; and spend only 4.95–5.70 R; what's left. 5.70–6.80 L; Do it for one year 6.90–8.45 R; and watch what happens. 8.45–9.75 L.
- Shadows were doubled for small words to keep white readable on the bright wood and phone shots.
- X1 needed no snapping: all chunk starts were already ≥ 0.15 s from the cuts, and chunks 4 and 7 carry across cuts.
