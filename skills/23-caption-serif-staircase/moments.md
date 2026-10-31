# moments.md — Serif Staircase: Style Bible + Moment Library

This file is the single source of truth for the Serif Staircase style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, with exact specs measured on a 1080x1920, 24 fps, 6.0 s reference reel (one hard cut). Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays clean and untouched while a slightly tilted white italic serif title rises in over the top, and soft serif captions build up word by word in a staircase of white roman words and yellow italic keywords, switching to black text on a white label box when the shot is bright or busy.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 24 fps, so "f" values are 24 fps frames; at another fps keep the seconds. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Text white | #FFFFFF | Title, roman caption words |
| Keyword yellow | #F4F10E | Italic emphasis words (measured median 243,240,14) |
| Label box | #FFFFFF at 95 % | Box behind caption text in box mode (design decision: the reference box sat on white cloth, so its opacity could not be read; it reads as solid white) |
| Label text | #111111 | Caption text inside the box (measured near-black) |
| Text shadow | #000000 at 40 % | Soft shadow under white and yellow text on footage |
| Box shadow | #000000 at 12 % | Faint edge shadow on the box (design decision) |

Brand-swap rule: if the user gives a brand colour, replace Keyword yellow with it (keep it bright enough to read on footage). Never change the white or the black. No other colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H. No cards, borders, masks, rounded corners, blur plates or colour overlays. |
| Label box (box mode only) | Sharp-cornered rectangle, white, fits the text: width = text width + 2 × 0.035W [38] padding; height 0.058H [112]; centred on x = 0.50W. Measured on the reference: x 0.089–0.898W, y 0.204–0.262H for a 23-character line. |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor ✎ = the speaker's face box (or the main subject). |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Title block | 0.13, 0.08, 0.86, 0.18 [140,156,929,346]; centre x = 0.49W, centre y = 0.13H [250] | Tilted title |
| Staircase lane | 0.18, 0.60, 0.82, 0.74 [194,1152,885,1421] | Caption mode "build" on a speaker or calm footage |
| Staircase line 1 | text centred on x = 0.50W; baseline ≈ 0.645H [1238] | First line |
| Staircase line 2 | line pitch 0.064H [123] below line 1; single emphasis word centred on x = 0.41W [443]; two or more words centred on x = 0.50W | Second line |
| Box lane (top) | box centre y = 0.233H [447] | Caption mode "box" (default) |
| Box lane (bottom) | box centre y = 0.80H [1536] | Box mode when the subject or a face sits in the top lane |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Italic serif with calligraphic shapes, semibold, mixed case (as the user wrote it), rotated −4.5° (rising to the right) | Newsreader Display SemiBold Italic | Lora SemiBold Italic, Source Serif 4 SemiBold Italic | Font size ≈ 0.20W [215]; width of the line ≈ 0.72W [780] for a 9-letter word; max width 0.80W |
| Caption roman word | Soft old-style serif, medium weight, mixed case as written, tight word spacing | Newsreader Medium | Lora Medium, Source Serif 4 | Font size ≈ 0.10W [108]; letter-spacing −0.02em |
| Caption keyword | Same family, italic, yellow | Newsreader Medium Italic | Lora Italic, Source Serif 4 Italic | same size as roman words |
| Box text | Same roman face, near-black | Newsreader Medium | Lora Medium | Font size ≈ 0.09W [97]; letter-spacing −0.02em |
| Solo keyword (C3) | Keyword style, enlarged | Newsreader Medium Italic | Lora Italic | 1.5× the caption size |

Font note: the family was identified by letterform only (soft calligraphic italic, ink-trap-free old-style roman). Check the render against the reference crops and fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Rules: text case exactly as the user wrote it (no forced uppercase). No outline-only text. Only the title is rotated; captions and boxes are never rotated.

Text on footage gets a soft shadow (0, +3 px, blur 6 px, #000000 at 40 %). The title shadow is stronger: (0, +6 px, blur 10 px, #000000 at 45 %).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Title entrance | ease-out (cubic: 1−(1−t)³), rise from below + alpha | 0.25 s (6 f) |
| Title exit | linear alpha fade, no movement | 0.38 s (9 f) |
| Caption word entrance | ease-out alpha ramp, no movement | 0.125 s (3 f) |
| Caption chunk exit | hard cut, replaced in the same frame | 1 f |
| Box caption entrance and exit | hard cut | 1 f |
| Cuts | hard cut (no transition effect), caption mode switches on the same frame | 0 f |

Never: bounce, overshoot, spring, slides, typewriter letter-by-letter, wipes, glitch, shake, scale pops on captions, flashes, transitions between shots, rotation of anything except the title.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Slow push-in about the face or subject anchor (M1) | Total scale ≤ 1.08 per shot; reset at the next cut |
| Text, shadow and label box overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; freezing; blur, glitch, warp, zoom-punch or colour grading of any kind; adding footage the user did not supply. The primary footage plays live, in sync with the audio, at all times. Footage is never hidden or darkened.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by captions or the box. The title may overlap hair or background but never the forehead, eyes, nose or mouth. |
| Staircase lane | Default region 1.3. If the face box bottom edge is below 0.58H, move the whole lane down so line 1 sits ≥ 0.03H under the chin; if that pushes line 2 below 0.88H, switch the chunk to box mode in the bottom lane. |
| Title block | If the face box top is above 0.20H, shift the title up (min centre y 0.07H) or shrink it; if that fails, drop it to the bottom of the video's first calm shot or skip to T2 later. |
| Box lane | Pick the top or bottom lane with less subject overlap; never over a face. |
| Footage text (signs, UI) | If readable footage text sits in the chosen lane for more than 1 s, use the other lane. |
| Edges | Every glyph and the box stay ≥ 0.04W from the left and right edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **C** caption · **X** cut treatment · **M** footage motion · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · TILTED TITLE RISE — T ●● (signature opener)
**What it is:** a one- or two-word white italic serif title, tilted slightly upwards to the right, fades in while rising a few pixels, holds, then fades out in place.
**Use when:** the opening line states the topic; the video starts on a speaker or a calm shot. **Avoid when:** the first 0.3 s contains a cut, or the face box cannot be cleared (use the 1.7 fallback).
**Text (✎):** 1–2 words from the user's own words (or a title the user supplied), as written. Max 16 characters in total. If two words do not fit on one line at ≤ 0.80W, stack them in two lines (line pitch 0.9 em, both centred).
**Geometry / Graphics:** Title block, centre x = 0.49W, centre y = 0.13H, rotation −4.5° about its centre, white fill, title shadow. Font size scaled so the widest line ≈ 0.72W (9 letters ≈ 0.2W font size); cap at 0.22W.
**Motion (measured on the reference, 24 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.04–0.29 [1–7] ✎ | title | alpha | 0 → 1 | ease-out |
| 0.04–0.29 [1–7] ✎ | title | y offset | +0.03H [58] → 0 | ease-out (cubic) |
| 0.29–1.54 [7–37] ✎ | title | hold | final state | — |
| 1.54–1.92 [37–46] ✎ | title | alpha | 1 → 0 | linear |

Start ✎: 0.04–0.3 s into the video (at the first spoken word at the latest). Hold ✎: 1.1–1.5 s; the fade-out starts when the first caption chunk ends or 1.5 s after the start, whichever is later, and finishes ≥ 0.3 s before a cut.
**Footage / plate behaviour:** footage untouched.
**Captions during it:** C1 runs underneath in the staircase lane; the title never shares a region with it.
**Exit:** 0.38 s linear fade.
**Build notes:** render the title once at 2× with Pillow (font size per above, shadow baked in), rotate with `Image.rotate(4.5, expand=True, resample=BICUBIC)` (positive angle = counter-clockwise in Pillow), then composite per frame with alpha and y offset.
**Flow prompt text:** "Near the start, a short title, {{TITLE}}, written in a graceful white italic serif and tilted slightly upwards to the right, fades in near the top of the frame while rising a little, stays for about a second and a half, then fades away. It never covers the speaker's face."
**Still-image state:** final state.

### C1 · STAIRCASE CAPTION — C ●● (signature, the caption system)
**What it is:** a phrase builds word by word in the lower middle of the frame. Plain words are white roman serif; keywords are yellow italic and each keyword drops to a new line, so the phrase steps down like a staircase. When the phrase is complete the whole block is replaced by the next one.
**Use when:** always on speaker shots and calm footage. **Avoid when:** the lane's background is bright or busy (use C2).
**Text (✎):** the user's exact words, case as written. Chunk rules: 3–5 words per chunk; split at punctuation and natural phrases; never end a chunk on an article, preposition or conjunction ("a", "the", "of", "and", "to"); a chunk lasts 0.8–1.5 s; prefer chunk changes at cuts. Keywords ✎: 1–2 per chunk, ≤ 3 per 5 s; choose the meaning-carrying nouns and verbs (the topic word, the person, the action); never an article or preposition. The first word of a chunk may be a keyword.
**Geometry / Graphics:** Staircase lane. The whole chunk is laid out before it starts so that no word ever moves: the first word of the chunk is always on line 1, centred on x = 0.50W at baseline 0.645H. Line break rule: a keyword that follows a roman word or another keyword starts a new line; roman words that follow a keyword join that keyword's line to its right; roman words that follow roman words stay on the same line. Max 3 lines. Line 2+ pitch 0.064H. A line with a single keyword is centred on x = 0.41W; any other line is centred on x = 0.50W. Words are separated by 0.25 em.
**Motion (measured on the reference, 24 fps; words at 0.42, 0.83, 1.25 s, then a new chunk at 1.5, 1.75, 2.08, 2.46 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha | 0 → 1 (starts as a dim olive-grey ghost, reaches full colour) | ease-out, 3 f |
| word start ✎ | earlier words | — | unchanged (no colour change, no movement) | — |
| chunk end ✎ | all words of the chunk | alpha | 1 → 0 | hard cut, same frame as the next chunk's first word |

Word start = the word's spoken start time. Chunk end = the next chunk's first word start (no empty gap), or min(last word end + 0.4 s, next cut) for the last chunk of a shot.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system. At a cut, the chunk in progress is replaced in the same frame by the next chunk (in C1 or C2 mode, chosen for the new shot).
**Exit:** hard cut per the table.
**Build notes:** render each word separately with Pillow at 2×; measure with `font.getlength` before laying out the chunk; build one RGBA layer per (chunk, word-count) state; fade a word by multiplying its alpha.
**Flow prompt text:** "In the lower middle of the frame, captions appear word by word in a soft serif typeface. Ordinary words are white; important words, {{KEYWORDS}}, are yellow and slanted, and each one starts a new line slightly to the left, so the caption steps downwards. Each new word fades in softly in place. When a phrase is complete it is replaced at once by the next phrase. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk.

### C2 · LABEL BOX CAPTION — C ●● (signature, for bright or busy shots)
**What it is:** the whole phrase appears at once as black serif text on a plain white label box near the top of the frame.
**Use when:** the footage under the staircase lane is bright (mean luminance > 0.6) or detailed (flat objects, text, patterns); B-roll with a main subject in the middle; any shot where white and yellow text would not read. **Avoid when:** the shot is a calm speaker shot with a dark or mid-tone lane (use C1).
**Text (✎):** the user's exact words, case as written; one line, 2–6 words, ≤ 28 characters (≤ 0.82W wide); same chunk rules as C1; no keyword colours (all text near-black).
**Geometry / Graphics:** Label box and Box text per 1.2 and 1.4. Box lane (top) by default; bottom lane per 1.7. The box fits the text exactly each time the phrase changes.
**Motion (measured on the reference, 24 fps; phrases switched at 2.83 s and 5.0 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| phrase start ✎ | box + text | alpha | 0 → 1 | hard cut (1 f) |
| phrase end ✎ | box + text | alpha | 1 → 0, replaced in the same frame by the next phrase | hard cut (1 f) |

Phrase length ✎: 1.0–2.5 s (the reference held phrases for 2.2 s and 1.0 s).
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption. The whole phrase is visible at once, so the viewer reads while the speaker or narration continues; for speech, start the box at the phrase's first word.
**Exit:** hard cut.
**Build notes:** draw the box with `ImageDraw.rectangle` at 2× then downscale; add the faint box shadow as a blurred rectangle at 12 % alpha.
**Flow prompt text:** "At the top of the frame, a short line of text, {{PHRASE}}, appears all at once in black serif lettering on a plain white rectangular label that fits the text, and is replaced at once by the next line. The label never covers the main subject."
**Still-image state:** the phrase in the box.

### X1 · CUT RESTYLE — X ● (signature treatment of every cut)
**What it is:** the shot changes with a plain hard cut, and the caption mode switches in the same frame to suit the new shot. There is no transition effect.
**Use when:** every footage cut. **Avoid when:** never; do not add effects.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion (measured on the reference, 24 fps; one cut at 2.83 s):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut ✎ (the footage's own cut time) | caption | mode and chunk | C1 chunk → C2 phrase (or the reverse), same frame as the cut | hard cut |

The caption in progress is not allowed to straddle a cut in a different mode: end the old chunk on the cut frame and start the new one on that frame. If the speech continues across the cut, the new chunk starts with the next word that is still unspoken at the cut.
**Footage / plate behaviour:** untouched; no flash, blur or zoom on the cut.
**Captions during it:** per above.
**Exit:** none.
**Build notes:** compute the caption mode per shot from the scene table (luminance of the lane region, subject overlap); keep the mode constant within a shot.
**Flow prompt text:** "At each cut the picture simply cuts to the next shot with no effect, and the captions change their style in the same moment to suit the new shot: {{CAPTION_STYLE_BEFORE}} before the cut and {{CAPTION_STYLE_AFTER}} after it."
**Still-image state:** none.

### T2 · SECTION TITLE — T ●● (extension in the same grammar)
**What it is:** a second tilted title, smaller, for a new topic word later in the video.
**Use when:** the story moves to a new topic, step or name (≥ 3 s after T1 ended, ≥ 0.5 s after a cut). **Avoid when:** a caption chunk occupies the title block region (it never does by default) or the video is shorter than 6 s.
**Text (✎):** 1–2 of the user's words, as written, max 16 characters.
**Geometry / Graphics:** same as T1 at 0.75× size; centre x ✎ = 0.50W (or 0.30W / 0.70W to avoid the face), centre y = 0.11H, rotation −4.5°.
**Motion:** same as T1 (0.25 s rise + fade-in, hold 1.0–1.3 s, 0.38 s fade-out).
**Footage / plate behaviour:** untouched.
**Captions during it:** unchanged.
**Exit:** 0.38 s linear fade, ≥ 0.3 s before a cut.
**Build notes:** reuse the T1 renderer.
**Flow prompt text:** "Later in the video, a smaller tilted title, {{TITLE}}, in the same white italic serif fades in near the top while rising a little, stays for about a second, and fades out."
**Still-image state:** final state.

### C3 · SOLO KEYWORD — C ●●● (extension in the same grammar)
**What it is:** one payoff word alone at 1.5× size in yellow italic.
**Use when:** a strong turn or payoff word ("never", a number, a name) that deserves a beat. **Avoid when:** the word is longer than 12 characters; max 2 per video, ≥ 3 s apart.
**Text (✎):** one user word, case as written.
**Geometry / Graphics:** Keyword style at 1.5× size, centred on x = 0.50W, baseline 0.66H (staircase lane), text shadow.
**Motion:** C1's word entrance (3 f alpha ramp); hold 0.4–0.8 s; hard cut to the next chunk.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the normal chunk for its duration.
**Exit:** hard cut.
**Build notes:** same renderer as C1; scale the font size, not the bitmap.
**Flow prompt text:** "One important word, {{WORD}}, appears alone in the lower middle of the frame in large yellow slanted lettering, fading in softly, then is replaced by the next caption."
**Still-image state:** the word.

### M1 · SLOW PUSH — M ● (extension in the same grammar)
**What it is:** a barely visible push-in on a long static shot so it never looks frozen.
**Use when:** a shot longer than 2 s with no cut and little motion. **Avoid when:** the footage already moves a lot.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** scale ×1.00 → ×1.06 across the shot (linear), about the subject anchor ✎ (face box centre); reset to 1.00 at the next cut.
**Footage / plate behaviour:** live footage, scaled only; no blur.
**Captions during it:** unaffected (captions do not scale).
**Exit:** reset by the cut.
**Build notes:** `Image.resize(..., box=floats)` about the anchor; clamp the crop box inside the frame.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last caption stays until just before the end, then the picture finishes clean.
**Use when:** every video. **Avoid when:** the last line is a payoff that needs C3.
**Text (✎):** the last chunk's words.
**Geometry / Graphics:** C1 or C2 as chosen for the last shot.
**Motion:** the last chunk or phrase holds to min(last word end + 0.4 s, end − 0.25 s); the final 0.25 s [6 f] has no caption.
**Footage / plate behaviour:** untouched (M1 optional).
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1/C2.
**Flow prompt text:** "The last caption stays until just before the end, then disappears and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | T1 + C1 | X1 on every cut; C1 on speaker shots, C2 on bright or busy B-roll; M1 on a long B-roll shot | E1 |
| Single talking head, no cuts | T1 + C1 | C3 on one payoff word; T2 at a new topic; M1 on a shot > 2 s | E1 |
| B-roll only, no speech | T1 (user's own title words, if any) + C2 | X1 on every cut; C2 phrases of 1.0–2.5 s; M1 on long shots | E1 |
| Still image + text | T1 final state, C2 phrase in the settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- T1 title with a face box top at 0.15H (< 0.20H): centre y 0.08H, 12-character title as one line at font ≈ 0.114W (82 px at W 720) so the line is ≤ 0.72W; rotated bbox bottom stayed ≤ 0.113H, clear of the face. Timing used: rise 0.08–0.33 s, fade 1.10–1.48 s (shorter hold than 1.1 s because the cut was at 1.83 s and the fade must finish ≥ 0.3 s before it).
- C2 box text: when a phrase is wider than the box limit at 0.09W, shrink the font until text width + 2 × 0.035W ≤ 0.92W (used 0.069W for "automate your investments,", 0.073W for "and spend only what's left."). Phrases up to 27 characters work this way; otherwise split.
- C2 lane choice that worked: top lane on the cash/hands shot and the plant shot; bottom lane (0.80H) on the phone shot and on the grocery shot (face in the top lane).
- C1 on a beige sweater (mid-tone, bright) stays readable with the 40 % shadow; no change needed.
- M1 was skipped: every shot was shorter than 2 s.
