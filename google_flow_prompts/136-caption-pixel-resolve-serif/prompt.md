# Google Flow prompt · Pixel Resolve Serif
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Pixel Resolve Serif" caption style to it.

The look in one sentence: Tiny white serif whispers beside tall stretched Didone capitals that resolve from a pixel mosaic, bend into arches and waves, slip behind the head and end on one giant mixed-case word.

The footage stays FULL FRAME and UNTOUCHED: no cards, split screens, layouts, backgrounds, wipes or graphic transitions. This style only adds its caption system (and title/headline text if the style bible below lists it) on top of the original picture.

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
4. PLACE THE CAPTION MOMENTS: choose from the moment library below. Captions always follow the speech; title or headline moments go at the start or on the strongest words; keep the same grammar for the whole video.
5. CHECK THE SAFE ZONES (style bible): the speaking face is never covered; text stays inside the safe margins; if footage content (a sign, a screen) sits where the caption lane is, move the lane as the style bible says.
6. RENDER the video: every graphic and word appears and disappears exactly as the moments describe (timing, easing and entrance), cut to cut, and stays in sync with the audio.

## 6. STYLE BIBLE
### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Whisper white | #FFFFFF | All whisper words; white display words |
| Display accent (default) | #E4B562 | Accent display words. This is a parameter: the user's brand colour replaces it; any saturated colour that reads on the footage works |
| Shadow | #000000 at 45–80 % | Soft drop shadow under every glyph (display 45 % blur 6, whisper 80 % blur 3) |

Rule: only white plus one accent colour. Display words alternate white and accent (K1). Never outlines, gradients, boxes or glows.

### 1.2 Containers / shapes

None. Footage is always 100 % of W and H, untouched. There are no cards, plates, bars, blurs, colour overlays or masks, except the person cut-out used by T6 (text goes behind the head, the footage itself is never altered).

### 1.3 Layouts / grid

Text is built as stacks: a vertical flow of items read top to bottom (reading order = spoken order). A chunk has one to three stacks.

| Zone | Region (y0–y1 as fractions of H) | Use |
|---|---|---|
| Top stack | 0.03–0.30 | Whisper lead-in plus display word(s); the reference put them above the head |
| Chest stack | 0.44–0.75 | Whisper tails and the giant finisher over the torso (T7) |
| Side margin | x 0.05–0.95 W | Hard limit for every glyph and every warped bbox (items left-aligned start at 0.07W) |

Stack gap between items: 0.014H [reference 0.012H]. Items in one stack never overlap (bounding boxes disjoint). A display item is centred (x centre 0.50W) unless marked left (starts at 0.07W). Face box (speaker): x 0.34–0.66, y 0.15–0.40: no front text inside it. Only T6 may cover head pixels, via the cut-out.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Whisper word | Tiny roman serif, lowercase as written, white, soft shadow | Newsreader (wght 500, opsz 16) | EB Garamond, Gelasio | 44 px at 720x1280 [0.034H]; reference ≈ 0.030H |
| Display word | Bold Didone, thick stems with hairlines, UPPERCASE, stretched vertically ×1.5 | Bodoni Moda (wght 820, opsz 14) | Playfair Display Black, Abril Fatface | cap height 0.075–0.10H after ×1.15 gain; width ≤ 0.86W (shrink uniformly if wider) |
| Giant finisher (T7) | Same Didone, MIXED case exactly as written, stretched ×1.5 | Bodoni Moda | Playfair Display | cap height 0.115H [reference 0.12H], width ≤ 0.86W |

Use a low optical size for display words (opsz 14 on Bodoni Moda): at high optical sizes the hairlines vanish at 720 px and letters like E read as C.

### 1.5 Motion language

| Element | Motion |
|---|---|
| Whisper word | Appears on its spoken beat: fade in over 3 f with a 6 px rise, ease-out quad. Never moves after. |
| Display word | Mosaic resolve (T1): 7 f at 24 fps. Block sizes 34, 22, 14, 9, 5, 3 px then clean; alpha 0.55, 0.75, 0.9, then 1. Then static. |
| Chunk end | Hard cut: every element of the chunk disappears on the same frame. |
| Between chunks | Never two chunks on one frame; at least 1 frame gap. |
| Never | Bounce, overshoot, letter-by-letter typing, scale pops, slides, wipes, glitch, shake, flashes, outlines, glows, rotation of the whole title. |

### 1.6 What may happen to the user's footage

Allowed: nothing but text overlays and shadows. Full-frame untouched footage; no zoom, crop, colour change or speed change. Forbidden: everything else (cards, splits, B-roll frames, background swaps, transitions). T6 uses a person mask only to draw the footage's own head pixels back over the text; the footage is never replaced.

### 1.7 Safe zones

- Face box stays clear of all front text (T6 text sits behind, never in front of, the face).
- No two chunks visible on the same frame; no two items overlapping inside a chunk.
- Whisper words need a soft shadow because they are small and white: on bright footage keep the shadow at 80 %.
- Behind-head words must stay ≥ 85 % visible (area of letter pixels not hidden by the head), measured per frame while the word is settled. Place them so only the bottom edge meets the hair; if the speaker leans up and visibility drops, lift the word or make it a front word above the head.

---

## 7. MOMENT LIBRARY
Family codes: C caption, T title/display word, K keyword rule, E end. Energy: low, mid, high.

### C1 · WHISPER LINE — C low
**What it is:** one to four tiny white serif words that appear one by one on their spoken beats, left aligned, placed above or below a display word.
**Use when:** every chunk; carries all the small connector words. **Avoid when:** never skip it, a chunk with only display words loses the contrast the style depends on.
**Text:** the user's words, written case, 1–4 words per whisper item.
**Geometry:** left x = 0.07W; size 44 px; word gap 0.30 × size; line sits inside a stack with gap 0.014H.
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | each word | alpha, y | 0 → 1, +6 px → 0 over 3 f | ease-out quad |

**Captions during it:** this is the caption.
**Exit:** hard cut with the chunk.
**Build notes:** lay the whole line out first (measure every word) so no word moves; shadow black 80 %, blur 3, offset 2 px.
**Flow prompt text:** "Tiny elegant white serif words fade in one by one on the beat of the speech, small and quiet, sitting beside a much larger word: {{WORDS}}."
**Still-image state:** all words visible.

### T1 · MOSAIC RESOLVE WORD — T high
**What it is:** a tall stretched display word that appears as a coarse pixel mosaic and sharpens into crisp letters in about a quarter of a second.
**Use when:** the keyword of every chunk (noun, verb, number). **Avoid when:** more than one per chunk is entering at the same time, or on a word under 3 letters.
**Text:** one spoken word, UPPERCASE; colour white or accent (K1).
**Geometry:** see 1.4; warp from T3/T4/T5 or none; shadow 45 %, blur 6–7, offset 5 px.
**Motion:**

| f | Property | Value |
|---|---|---|
| 0–5 | block size px | 34, 22, 14, 9, 5, 3 |
| 0–2 | alpha | 0.55, 0.75, 0.9 |
| 6 | clean | alpha 1, no mosaic |

**Footage behaviour:** untouched. **Exit:** hard cut.
**Build notes:** render the word, downscale to blocks (area average), upscale nearest-neighbour, multiply alpha by 1.7 and clip so blocks look solid; shadow from the mosaic alpha.
**Flow prompt text:** "The big word {{WORD}} first appears as a chunky blocky pixel mosaic and snaps into sharp tall elegant serif capital letters within a quarter of a second, then stays still."
**Still-image state:** crisp word.

### T2 · STACKED PAIR — T high
**What it is:** two display words one under the other with the bounding boxes just touching (gap 0.014H), one white and one accent, optionally under a whisper lead-in.
**Use when:** two-word keyword phrases ("one year"); lists. **Avoid when:** the words differ greatly in length (more than 2:1); use T1 twice in separate stacks.
**Text:** two words, UPPERCASE, each resolves on its own beat (T1).
**Geometry:** same cap height for both (0.095H); centred.
**Flow prompt text:** "Two large tall serif words stacked tightly, {{WORD1}} in white and {{WORD2}} in {{ACCENT}}, each appearing on its own beat."
**Still-image state:** both visible.

### T3 · ARCH WORD — T mid
**What it is:** a display word bent into a gentle arch: the middle is higher and taller, the ends lower and shorter.
**Use when:** the headline word of a chunk, a payoff. **Avoid when:** under 4 letters (looks lopsided).
**Warp:** per-column vertical shift = −a × 0.55h × 3 × (1 − u²), per-column height scale = 1 + 0.20 × (1 − u²), u = 2x/w − 1, a 0.07–0.10.
**Build notes:** use `cv2.remap` on the stretched 2× alpha mask, then downscale.
**Flow prompt text:** "The word {{WORD}} curves slightly upward in the middle like a small arch, tall serif capitals, tallest in the centre."
**Still-image state:** settled arch.

### T4 · WAVE WORD — T mid
**What it is:** a display word riding a soft sine wave (1.25 cycles).
**Use when:** casual, flowing words. **Avoid when:** next to T3 in the same chunk.
**Warp:** vertical shift = a × 0.55h × 2.2 × sin(2π × 1.25 × x/w), a 0.03–0.035; no scale change. Larger a breaks readability.
**Flow prompt text:** "The word {{WORD}} ripples gently up and down like a slow wave, tall serif capitals."
**Still-image state:** settled wave.

### T5 · SLANT RISE WORD — T mid
**What it is:** a display word on a rising diagonal; letters grow taller toward the right, like a perspective lean.
**Use when:** momentum words ("more", "left", "next"). **Avoid when:** for the last word of a sentence that needs weight (use T7).
**Warp:** shift = −a × 0.55h × 3 × u, scale = 1 + 0.22 × u, a 0.05.
**Flow prompt text:** "The word {{WORD}} rises on a diagonal, taller on the right than the left, tall serif capitals."
**Still-image state:** settled slant.

### T6 · BEHIND-HEAD WORD — T high
**What it is:** a display word placed so the speaker's head overlaps its lower edge: the head is in front of the letters, which gives depth.
**Use when:** a talking-head shot with head top at y 0.12–0.20 and a keyword; use once or twice per video. **Avoid when:** no clean person cut-out, a speaker who leans or moves so visibility falls under 85 %, B-roll shots.
**Text:** one keyword.
**Geometry:** word top y = 0.055–0.08H so only its bottom 10–15 % meets the hair; centred.
**Footage behaviour:** footage untouched; draw the word, then restore the original pixels where the person mask is 1.
**Flow prompt text:** "The big word {{WORD}} sits just above the speaker's head and the top of their hair slightly overlaps its bottom edge, so the word appears to be behind the person."
**Still-image state:** word behind head.

### T7 · GIANT MIXED-CASE FINISHER — T high
**What it is:** one huge word in mixed case (as written), stretched, over the chest/lower third, closing the chunk.
**Use when:** the last word of the video or a section, the payoff or call to action. **Avoid when:** more than once per video.
**Text:** the user's final word, mixed case exactly as written.
**Geometry:** cap height 0.115H, width ≤ 0.86W, centred in the chest stack (top y 0.69H after a whisper lead-in); white or accent.
**Motion:** T1 mosaic resolve. **Exit:** hard cut at the end of the video.
**Flow prompt text:** "A very large tall serif word {{WORD}} in the lower part of the frame over the speaker's chest, sharpening out of a pixel mosaic."
**Still-image state:** word settled.

### C2 · ARC WHISPER — C low
**What it is:** a whisper line whose words sit on a very slight arc (centre words 18 px higher than the ends).
**Use when:** a whisper tail of 2–4 words under or beside a display word, for a hand-set feel. **Avoid when:** one-word lines.
**Build notes:** dy = −18 × (1 − (2(j + 0.5)/n − 1)²) per word; otherwise C1.
**Flow prompt text:** "The small white words {{WORDS}} follow a very slight upward curve."
**Still-image state:** settled arc.

### K1 · COLOUR ALTERNATION — K low (rule)
**What it is:** display words alternate white and accent in reading order; at most one accent word per stack; at least 3 accent words per 10 s is plenty.
**Use when:** always. **Build notes:** if the user gives a brand colour it replaces the accent.
**Flow prompt text:** "Big words alternate between white and {{ACCENT}}."

### E1 · HARD CLEAR — E low (rule)
**What it is:** at the chunk end every element vanishes on one frame, and the next chunk starts at least 1 frame later. There is never a fade-out, slide or overlap.
**Flow prompt text:** "All the words disappear together in one instant, and a fresh set appears for the next phrase."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 + T6 on the first keyword | T1 with T3/T4/T5 per chunk, T2 for a two-word phrase | T7 on the last word |
| Single talking head | C1 + T6 | alternate T3, T5, T6, one T2 | T7 |
| B-roll only | C1 + T3 | T1/T4/T5, T2 for lists (no T6) | T7 |
| Still image | C1 + T1 settled | one T2 | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the demo (720x1280, 24 fps, 10 s)

| Chunk | Time (s) | Content | Moments |
|---|---|---|---|
| A | 0.10–1.05 | whisper top, MONEY behind head (accent, arch), whisper tail low | C1, T6, T3 |
| B | 1.10–1.80 | EARNING behind head (white, slant), whisper tail | T6, T5, C1 |
| C | 2.00–3.15 | whisper, YOURSELF (accent, wave), whisper | C1, T4 |
| D | 3.20–4.88 | AUTOMATE (white, arch), whisper, INVESTMENTS, (accent, wave) | T3, T4, C1 |
| E | 4.95–6.58 | whisper, SPEND (white, arch), arc whisper, LEFT. (accent, slant) | C1, C2, T3, T5 |
| F | 6.90–8.30 | whisper, ONE (white, arch) over YEAR (accent, wave) | C1, T2 |
| G | 8.45–9.85 | whisper, WATCH (accent, arch), whisper, happens. (white, mixed case, giant) | C1, T3, T7 |

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
