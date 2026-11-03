# Google Flow prompt · Mosaic Gloss
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Mosaic Gloss" motion style to it.

The look in one sentence: A rounded footage card on a pastel gradient page, pixel-mosaic wipes on every cut, glowing typed keywords over whisper words, a glossy pill slot with a ball knob and a speech-bubble caption.

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
Measured defaults (reference: light blue family). The accent family is a parameter {{ACCENT}}; swap the whole family together.
| Role | Measured default | Used for |
|---|---|---|
| Page top / bottom | #81C2FC / #B9DFFB | page behind the card, pill page |
| Bottom fade | deep navy ~#0A1E3C, alpha 0 to 0.93 over the lowest 22% | icons sit on it |
| Keyword | cyan #17C8F0 to azure #3A9AED gradient, same-hue glow | big keyword |
| Whisper | white, soft darker shadow | small words |
| Bubble / pill | cyan-azure gradient, white text | bubble, pill |
| Mosaic tiles | 6-7 shades of the page hue, 0.95 alpha | cut wipe |
| Clouds / glass icons | white / frosted white | decoration |
Demo accent family (warm sunset, rule: different hue from reference): page #FFB28E to #FFDAC0, plum fade #280A30, keyword amber #FFC93C to hot pink #FF3D8B, bubble #FF4E8C to #FF8A5A, knob amber, tiles peach/coral/pink/amber.

### 1.2 Containers / Shapes
- Card: x 0.09W-0.905W, y 0.03H-0.83H (587x1024 at 720), radius 38 [57], footage cover-fit, soft shadow (blur 20, offset y 14), bottom 22% of the frame carries the dark fade over card and page.
- Pill page card: same x, y 0.03H-0.60H, radius 38, crop anchor (0.5,0.5).
- Full-bleed: footage untouched, clouds on top.
- Pill: dashed capsule halo 576x126 at y 0.755H, inner gradient pill inset 16 with a white gloss line, ball knob r 33 overlapping the bottom edge.
- Bubble: rounded rect radius 36, gradient, top gloss band, tail bottom-right, text Poppins SemiBold 36.
- Glass icon tile 112x112, radius 26, white 0.92 alpha, glyph inside (calendar, coin, spark; any generic glyph).
- Mosaic: 9x16 grid of 80 px tiles.

### 1.3 Layouts
| Name | Footage rect | Extras |
|---|---|---|
| FULL | 0,0,1,1 | clouds at top |
| CARD | 0.09,0.03,0.905,0.83 | page, fade, icon bottom-left |
| PILL PAGE | 0.09,0.03,0.905,0.60 | whisper line y 0.715H, pill y 0.755-0.855H |

### 1.4 Typography
| Use | Look | Font | Fallbacks | Size |
|---|---|---|---|---|
| Keyword | weight 800, gradient fill, 2 px dark outline, glow, typed per letter | Montserrat | Poppins ExtraBold | auto-fit to max width 0.80W, start 104 |
| Whisper | white regular-medium, words fade 0.28 to 1 alpha over 0.18 s | Poppins Medium | Inter | 32 |
| Pill label top | UPPERCASE bold tracked +4 | Montserrat 700 | Poppins | 26 |
| Pill keyword | white heavy, typed | Montserrat 800 | Poppins | 50 |
| Bubble | white semibold, last word soft yellow | Poppins SemiBold | Inter | 36 |

### 1.5 Motion language
Ease-out cubic for settles and slides; back-ease overshoot (1.2-1.8) for pops (icons, pill, bubble); caption keyword types one letter every 0.05 s (max 0.32 s total); caption chunks hard-cut out; no bounce on the card itself; mosaic is stepwise (pixel-like, one frame steps).

### 1.6 What may happen to the footage
Allowed: scale and crop into the card, full-bleed with overlays, rounded mask, shadow, dark bottom fade, clouds and tiles on top for at most 0.45 s per cut. Primary footage always plays live, in sync. Forbidden: recolour, blur, speed change, replacing the shot with a blank page (the reference shows a text-only pill page for 2 s; here the shot stays in a card above the pill).

### 1.7 Safe zones
Face box never covered while speaking. Tiles over a speaking face: at most 3 frames (face tiles go last out of an outgoing speaker shot and first out of an incoming one). Keyword at y 0.56-0.64H on card/low shots, y 0.2H on top-zone B-roll; bubble inside the top 0.14H of the card. All text at least 0.05W from the side edges.

## 7. MOMENT LIBRARY
Families: L layout, T transition, K keyword caption, C caption, G graphic. Energy: low, mid, high.

### L1 · FULL-BLEED OPEN — L low (signature)
**What it is:** first shot plays full frame, untouched, for 0.40 s while the first caption starts.
**Use when:** every video start. **Avoid when:** never.
**Motion:** none. Footage live.
**Flow prompt text:** "The video starts full frame exactly as shot."

### L2 · CARD SETTLE — L mid (signature)
**What it is:** the full frame shrinks into the big rounded card while the gradient page, streaks and fade grow in behind.
**Use when:** after the opening line, speaker shots, calm shots. **Avoid when:** footage with text near the edges.
**Geometry:** CARD (1.3); fade starts at 0.78H.
**Motion:** | t | Element | Property | From to To | Ease | 0.40-0.95 s | rect | full to CARD | ease-out cubic |; radius 0 to 38; fade alpha 0 to 1.
**Footage:** live, scaled cover (0.82x).
**Exit:** mosaic wipe.
**Build notes:** `Image.resize(box=...)` for cover crop; rounded mask at 2x.
**Flow prompt text:** "The shot smoothly shrinks into a large rounded card floating on a soft {{ACCENT}} gradient page with faint grid lines and light streaks."

### L3 · CLOUD FULL-BLEED — L mid (signature)
**What it is:** B-roll full frame with 3 soft cream clouds sliding down from the top and drifting.
**Geometry:** clouds y 4-100 at x 150, -40, 570; keep below y 0.08H over faces.
**Motion:** | 0.20-0.65 s after the cut | cloud | y -70 to 0, alpha 0 to 1 | ease-out |; then +-10 px sine drift, 1.1 s period.
**Captions during it:** top zone (whisper y 0.115H, keyword y 0.205H) or low zone (keyword y 0.64H) when a face is in the upper area.
**Flow prompt text:** "Soft white clouds drift in along the top edge of the shot."

### L4 · PILL PAGE — L mid (signature)
**What it is:** the shot sits in a shorter card, with a glossy capsule slot below that fills with the keyword while a ball knob slides right.
**Geometry:** PILL PAGE (1.3), pill 1.2.
**Motion:** | 0-0.3 s | pill | scale 0.9 to 1 and fade | back-ease |; knob left to right 0.6 s starting 0.1 s before the keyword; keyword typed 0.055 s per letter.
**Text:** 1-2 whisper words in uppercase above, one keyword (max 14 characters) inside.
**Flow prompt text:** "Below the shot a glossy rounded slot with a dashed outline fills with the word {{KEYWORD}} while a round knob slides to the right."

### T1 · MOSAIC WIPE — T high (signature)
**What it is:** a grid of 9x16 pixel tiles in page colours builds over the last 6 frames before a cut, fully covers the cut frame, then clears in random order over 10 frames.
**Use when:** every footage cut (5 cuts in a 10 s clip). **Avoid when:** a cut within 0.5 s of another.
**Motion:** tile appear frame = cut-6+rand(0..5), clear frame = cut+1+rand(0..10), alpha 0.95, nearest-neighbour. Face rule: face tiles appear at cut-1 on a speaker going out, and clear within 3 frames on a speaker coming in.
**Flow prompt text:** "At the cut, a grid of small pixel squares in {{ACCENT}} shades builds over the picture and then dissolves square by square to reveal the next shot."

### K1 · GLOW KEYWORD — K high (signature)
**What it is:** one big keyword typed in letter by letter with a gradient fill, dark outline and glow.
**Text:** 1-2 spoken words, never more; the chunk's most meaningful word(s).
**Geometry:** 1.4; centre y per zone; rises 10 px while typing.
**Flow prompt text:** "One large glowing {{ACCENT}} word types onto the screen letter by letter."

### C1 · WHISPER LINE — C low (signature)
**What it is:** the rest of the chunk as one small white line directly above (words before the keyword) or below (words after) the keyword; words fade from ghost to solid as spoken.
**Text:** 1-4 words, at most 26 characters, never ending on an article.
**Flow prompt text:** "Small white words appear one by one in a single line next to the big word."

### C2 · BUBBLE CAPTION — C mid (signature)
**What it is:** the chunk's words type word by word inside a gradient speech bubble with a tail, last word in soft yellow.
**Geometry:** 1.2, top of card y 0.052H, width at most 0.74W of text; tail ends above the face box.
**Motion:** pop 0.6 to 1 scale over 0.24 s, back-ease, anchored at the tail.
**Flow prompt text:** "A rounded speech bubble pops in near the top and its words appear one at a time."

### G1 · GLASS ICON TILE — G mid
**What it is:** a frosted white tile with a simple glyph pops in bottom-left on the dark fade. **Text:** none; glyph chosen from the chunk's meaning.
**Motion:** pop 0 to 1 over 0.3 s, back-ease 1.8; leaves with the shot.
**Flow prompt text:** "A small frosted icon tile pops in at the bottom left."

### G2 · PAGE STREAK — G low
**What it is:** diagonal soft light bands slide slowly across the page (60 px/s). Always on with CARD and PILL PAGE.

### L5 · CARD SWELL — L mid
Card grows back to full frame over 0.5 s (inverse of L2) before a cut, instead of the mosaic, when the next shot should be full-bleed.

### E1 · BUBBLE CLOSER — C mid
Final line as C2 on the last card shot, held until 0.02 s before the end.

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| talking head, B-roll, talking head | L1, L2, K1+C1 | L3, L4, T1 on every cut | L2 card, C2 bubble |
| single talking head | L1, L2 | K1+C1 chunks, G1 icons, C2 for questions | C2 |
| B-roll only | L1 full, K1 | L3, L4, L2 alternating | K1 on last line |
| still image | CARD with K1+C1 | - | - |
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
