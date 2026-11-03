# Google Flow prompt · Ornate Frame
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Ornate Frame" motion style to it.

The look in one sentence: Footage in a pointed-arch window on ivory paper inside an engraved gold frame with beaded lines, vine corners and oxblood rosettes, lacquer caption plates in ivory serif, gold glints on cuts.

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
### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Paper | #E9E2D0 | Page background (fibre noise, faint diamond lattice at 7 %, vignette to #B9A883 at the edges) |
| Gold ramp | #5E3F10 · #B9882E · #F6DE8C · #D2A445 · #7A5517 | All metal: rules, beads, scroll vines, medallion rings; banded diagonal gradient, period 240 px |
| Gold text ramp | #FFF4C0 → #E6BD58 → #A87822 | Title and emphasis words (vertical gradient) |
| Oxblood | #4A0810 · #9C1E2A · #C23A44 | Rosettes, jewels, numeral discs, ribbon |
| Leaf green | #223A2E · #4A6C56 · #6F8F72 | Vine leaves only |
| Lacquer plate | #332417 → #1B110B (top to bottom) | Title and caption plates |
| Ivory ink | #F3EAD2 | Caption text, numerals, ribbon text |
| Engraving dark | 40–60 % black multiply | Edge line, hatch lines, drop shadow #1E1206 at 45 % |

Brand-swap rule: replace Oxblood with the user's brand colour only if it is dark and saturated. Never change gold, ivory or the paper.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Window | Pointed-arch window, x 81–639, y 150–1126 [121–959, 225–1689]. Arch: cubic bezier from (81,340) via (81,232) and (236,214) to the apex (360,150), mirrored. Bottom corners rounded 16. Footage scale 0.775 of the full frame, centre (360,639). |
| Frame | Outer rectangle x 52–668, y 100–1156: 7 px gold rule, 2.2 px thin rule at 11 px inset. Beaded rule (2.5 px beads, pitch 10.5) 11.5 px outside the window outline. 5.5 px gold ring hugging the window. |
| Corner pieces | Four medallions at (84,132), (636,132), (84,1124), (636,1124): gold ring r 19–27 with 14 scallops, oxblood disc r 19.5 with engraved concentric arcs, gold 8-petal rosette boss. Top corners add two scroll arms and a vine that follows the arch 26 px outside it (curls every ~0.16 of its length, leaves in green, oxblood-and-gold buds). Bottom corners add one short arm. |
| Finial | Gold fleur-de-lis (46 px high) on the arch apex with two small curls. Gold lozenge jewels at the side centres (66,640), (654,640) and bottom centre (360,1141). |
| Plates | Notched-corner lacquer plates with a 2.4 px and a 1.1 px gold rule. Title plate 300x64 at (210,20). Caption plate 612x92 at (48,1160) (inner 600x80). |
| Header | Gold double rule with diamond caps, y 52, x 38–205 and 515–682. Centre piece (x 205–515): title plate, idle medallion or numeral medallion (r 31). |
| Crop | Never crop the footage except by the window. Non-9:16 sources: cover-fit into the 558x992 window, crop anchor = face box or main subject. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Header | 0.05, 0.015, 0.95, 0.075 | Title plate, medallions |
| Window | 0.113, 0.117, 0.887, 0.880 | Live footage |
| Caption plate | 0.083, 0.906, 0.917, 0.984 | Captions (text baseline centre y = 0.947H [1212]) |
| Ribbon lane | centre (0.50W, 0.81H) | K1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Small caps, gold gradient, 1x2 px dark engraved shadow | Cormorant SC SemiBold | Playfair Display SC, IM Fell English SC | 40 px [60], fits plate width 300 |
| Caption | Mixed case, ivory, dark shadow (1,2) at 70 % | Cormorant Garamond SemiBold (wght 600) | EB Garamond, Playfair Display | auto-fit 54 → 34 px so the chunk is ≤ 540 px wide |
| Emphasis word | Same as caption in the gold text ramp | Cormorant Garamond SemiBold | — | same |
| Ribbon / numeral | Small caps, ivory on oxblood | Cormorant SC SemiBold | as title | 46 px / 32 px |

Case: title and ribbon text render in small caps (the font does it), numerals are Roman (I, II, III) only for list counters. No uppercase conversion of the user's words in captions.

### 1.5 Motion language
- Easing: ease-out cubic for entrances (0.3–0.55 s), smoothstep for travel, no overshoot except the 14 % corner swell.
- Typical durations: word fade 0.14 s with 8 px rise; plate fade 0.35 s; frame draw-on 0.9 s.
- Footage motion: only the settle (F1) and a slow push (B1).
- Never: bounce, shake, glitch, spin of the footage, wipes over the footage, flashes, filters, tilt.

### 1.6 What may happen to the user's footage
Allowed: scale to 0.775 and clip to the window (F1); slow push-in up to 1.035 per shot, 1.06 on the last shot, reset at each cut (B1, E1); frame and plates drawn around and below it. Forbidden: any change inside the window (no grading, glow, glint or blur on the footage), speed changes, trimming, reordering, replacement, extra windows. The primary window always plays live footage in sync with the audio.

### 1.7 Safe zones
- Face box stays inside the window and away from the header and the caption plate. Nothing is ever placed over the window except the ribbon (K1), the glint (on gold only) and corner medallions.
- The arch clips the top corners of the footage (about 45 px at the shoulders); at F1 start the footage is full frame so the face is visible from frame 0.
- Footage text near the top corners may be clipped by the arch: prefer a lower crop anchor when the user's footage has titles there.

---

## 7. MOMENT LIBRARY
Families: **F** frame · **T** title · **M** medallion · **C** caption · **K** keyword · **X** transition accent · **B** background/ambient · **E** end · **P** poster. Energy: low / mid / high. Signature moments are mandatory.

### F1 · FRAME SETTLE — F high
**What it is:** the footage starts full frame, shrinks into the arch window while the ivory page appears and the gold frame is drawn around it.
**Use when:** always, at the start. **Avoid when:** never.
**Text:** none.
**Geometry / Graphics:** window and frame per 1.2.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–1.0 | Footage | scale about (360,639) | 1.0 → 0.775 | ease-out cubic |
| 0.55–1.0 | Footage clip | rectangle → arch mask | 0 → 1 | smoothstep |
| 0.12–1.05 | Frame ring | drawn by an angle sweep from top centre both ways (0 → 1.12π) | hidden → drawn | smoothstep |
| 0.35–0.9 (+0.1 per corner) | Corner pieces | scale about the medallion, alpha | 0.55 → 1, 0 → 1 | ease-out cubic |
| 0.15–0.6 | Header rules | alpha | 0 → 1 | ease-out |
| 0.25–0.6 | Caption plate | alpha | 0 → 1 | ease-out |

**Footage / plate behaviour:** live, in sync, face visible from frame 0.
**Captions during it:** first chunk may start at 0.55 s (plate already ≥ 80 %).
**Exit:** none; the frame stays to the end.
**Flow prompt text:** "The video starts full screen, then smoothly shrinks into a tall pointed-arch window on warm ivory paper while a fine engraved gold frame with a dotted line, vine corners and deep red rosettes draws itself around it."
**Still-image state:** frame fully drawn, photo in the window.

### T1 · ENGRAVED TITLE — T mid
**What it is:** a black-lacquer plate in the header unfolds and the title words appear in small-caps gold.
**Use when:** opening line, topic words. **Avoid when:** the first words are a long phrase (> 3 words).
**Text:** the first 1–3 user words, exact case; they leave the caption stream (audit).
**Geometry:** plate 300x64 at (210,20); text 40 px centred.
**Motion:** plate scaleX 0.6 → 1 and alpha 0 → 1 over 0–0.4 s; each word fades in over 0.25 s at its speech start with a 7 px rise; whole title fades 1.62–1.86 s (before the first cut, never across a cut).
**Footage:** untouched. **Captions during it:** caption plate runs normally.
**Exit:** plate and words fade; the idle medallion fades in (T2).
**Build notes:** gold text = glyph mask filled with a vertical gradient + 1x2 px shadow.
**Flow prompt text:** "A small dark lacquered plate with a gold border opens at the top of the screen and the words {{TITLE}} appear on it in engraved golden small capitals."
**Still-image state:** plate with the title.

### T2 · HEADER CREST — T low (extension in the same grammar)
**What it is:** the resting header: gold double rules with diamond caps and a round medallion with a gold fleur-de-lis on a dark disc.
**Use when:** whenever no title or numeral is shown. **Text:** none.
**Motion:** idle medallion alpha 0 → 1 over 0.24 s after the title leaves. **Exit:** flips out for numerals (M1).
**Flow prompt text:** "A gold double rule with small diamond ends runs across the top, with a round gold medallion holding a lily flower in the centre."

### M1 · NUMERAL MEDALLION — M mid
**What it is:** the header medallion flips (scaleX 0 → 1, 0.3 s, ease-out) into an oxblood disc with an ivory Roman numeral and stays for the item.
**Use when:** list items, steps, numbered tips. **Avoid when:** fewer than 2 items.
**Text:** I, II, III… (counters only), max 3 characters.
**Geometry:** ring r 31 with 16 scallops, disc r 25.5, numeral 32 px.
**Timing:** start at max(item start, previous cut + 0.12 s); hold until the item ends; the next numeral replaces it directly.
**Exit:** returns to the idle medallion (T2) with the same flip.
**Flow prompt text:** "The round medallion at the top turns over like a coin and shows a deep red disc with the numeral {{NUMERAL}} in ivory."

### C1 · PLATE CAPTION — C mid
**What it is:** word-by-word captions on the lacquer plate under the window, ivory serif, one chunk at a time.
**Use when:** every spoken line. **Text:** user words only, chunks of 1–4 words, one line, never ending on an article or preposition.
**Geometry:** centred at x = 0.5W, baseline centre y = 1212; max width 540 px; font auto-fit 54 → 34 px.
**Motion:** the chunk is laid out at its final position from the start; each word fades 0 → 1 over 0.14 s at its start with an 8 px rise (ease-out); chunk fades out over the last 0.1 s; the plate stays.
**Timing:** start = first word start; end = min(last word end + 0.1, next start − 0.05); min 0.4 s.
**Footage:** untouched. **Exit:** fade.
**Flow prompt text:** "The spoken words appear one by one in a soft ivory serif on a dark lacquered plate under the window, always centred."

### C2 · GILT EMPHASIS — C low
**What it is:** one word of a chunk is set in the gold text ramp instead of ivory.
**Use when:** a contrast word, a payoff word, a key action. **Limits:** ≤ 1 word per chunk, ≤ 3 per video. **Text:** one user word.
**Flow prompt text:** "One word in the line shines in engraved gold while the others stay ivory."

### K1 · SCROLL RIBBON — K mid
**What it is:** an oxblood ribbon with folded swallow tails and gold edges unfurls across the lower window carrying a keyword or time phrase.
**Use when:** numbers, durations, amounts, one standout noun. **Avoid when:** a face sits low in the shot. **Text:** 1–3 user words (they leave the caption stream), small caps.
**Geometry:** body 70 px high, width = text + 80, tails 70 px, folded tails darker with a 35 % shadow; centre (0.5W, 1040), gold 2.6 px outline and 1 px inner rule.
**Motion:** 0.3 s: scaleX 0.6 → 1, scaleY 0.5 → 1, alpha 0 → 1 (ease-out); hold; fade 0.2 s.
**Footage:** ribbon is the only element over the window.
**Flow prompt text:** "A deep red ribbon with gold edges and folded swallow tails unfurls across the lower part of the window and shows the words {{KEYWORD}} in ivory small capitals."

### X1 · GILT GLINT — X mid
**What it is:** a soft diagonal light sweep that runs over the gold only (frame, corners, rules), 0.75 s, on a cut.
**Use when:** person to B-roll and B-roll to person cuts, and once near the end. **Limits:** ≤ 4 per video.
**Motion:** gaussian band (σ ≈ 70 px along x + 0.55y) travels from −150 to 1550 with smoothstep; adds warm white (255,236,170) at 90 % through the gold alpha only. The footage is never lit.
**Flow prompt text:** "A soft glint of light slides across the gold frame from the top left to the bottom right."

### X2 · CORNER BLOOM — X mid
**What it is:** on a cut, the four corner pieces swell 1.0 → 1.14 → 1.0 around their medallions (0.55 s, sin curve) and a thin gold ring expands from the top medallions (r 30 → 64, alpha 200 → 0).
**Use when:** cuts between two B-roll shots. **Limits:** alternate with X1; ≤ 3 per video.
**Flow prompt text:** "The four vine corners gently swell for a moment and a thin gold ring spreads out from the top corners."

### B1 · WINDOW BREATHE — B low
**What it is:** a slow push-in of the footage inside the window.
**Motion:** scale 1.0 → 1.035 over each shot (smoothstep), reset at each cut; centre fixed at the window centre. **Use when:** every shot longer than 1.2 s.
**Flow prompt text:** "Inside the window the picture drifts very slowly closer."

### E1 · SEAL CLOSER — E mid
**What it is:** the last line: the header medallion pulses 1.0 → 1.2 → 1.0 (0.7 s), the footage push rises to 1.06, a final glint runs over the frame, and the last chunk uses C2.
**Use when:** payoff or call to action. **Text:** last chunk, one emphasis word.
**Flow prompt text:** "For the last line the round medallion at the top swells once, a last glint runs over the frame and the final word glows gold."

### F2 · WIDE WINDOW — F low (extension in the same grammar)
**What it is:** for landscape or very busy footage, the window widens to x 40–680 (scale 0.89) with the arch flattened to a gentle ogee, plates unchanged.
**Use when:** 16:9 or 1:1 sources. **Avoid when:** 9:16 talking heads. Build: scale both mask and frame; keep the face box inside the clip.

### P1 · POSTER — P low (extension in the same grammar)
**What it is:** still mode. Photo in the window (cover-fit, anchor), title plate with the user's headline, caption plate with a subline, all ornaments settled, no glint.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | F1 + T1 | C1 + B1, M1 on lists, X1/X2 on cuts, K1 on a number | E1 |
| Single talking head | F1 + T1 | C1, C2, one K1, one X1 every ~3 s | E1 |
| B-roll only | F1 + T2 | C1, X2 on cuts, B1 | E1 |
| Still image | P1 | none | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

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
