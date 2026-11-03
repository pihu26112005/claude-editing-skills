# Google Flow prompt · Amber Widget Pipes
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Amber Widget Pipes" motion style to it.

The look in one sentence: Frosted pills resolving from pixel blocks behind the speaker, white widget cards with growing charts and flipping switches, a gradient page the footage shrinks into as a rounded window, a glowing tube that forks in two and a glowing giant-word title.

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
Measured on the reference: periwinkle accent (about #5B5BF5), page gradient #B1AEFC at the top to #F4F3FA at the bottom, white cards, near-white chips. The accent is a **parameter** (ACCENT); the table lists the measured default and the value used on the public demo.

| Role | Reference default | Demo value | Used for |
|---|---|---|---|
| ACCENT | `#5B5BF5` | amber `#FF9F0A` | top pill fill, caption key word, chart line/area, switch on-state, tick badges, pipe tube, big title word |
| ACCENT-LIGHT | `#B9B8FF` | `#FFCD78` | pipe inner highlight |
| ACCENT-INK | `#3F3FC0` | `#8A4000` | text inside frosted pills and card icons (deep, readable on white) |
| ACCENT-DEEP | `#4A4AD0` | `#D67000` | chart stroke |
| PAGE-TOP / PAGE-BOTTOM | `#B1AEFC` / `#F4F3FA` | `#FFC48A` / `#FFF8EE` | gradient page, vertical, with faint vertical streaks (sine banding, 2.5 % luminance) |
| CARD | `#FFFFFF` | `#FFFFFF` | widget cards, end pills |
| FROST | white 55–62 % over a 14 px blur of the footage | same | pills and tiles over footage |
| SKELETON | `#EBEBF9` | `#ECE2D4` | placeholder bars, chips, switch off-state |
| CAPTION | `#FFFFFF` + soft dark shadow | same | lane captions |
| TITLE-STROKE | n/a | `#381B00` | 5 px outline under the big accent title word |

No other accent colour. Brand variant: ACCENT and its four tints may become one brand hue; everything else stays neutral.

### 1.2 Containers
- **Pill:** fully rounded rectangle, height 0.055–0.08 H [70–80 px at 720]. Top pill is solid ACCENT; the others are FROST. Soft shadow 0 / +6 px, blur 12, 12–20 %.
- **Widget card:** white, radius 28–30 px, shadow +10 px, blur 18, 22–25 %. Width 0.65–0.73 W, height 0.21–0.33 H. UI chrome that would need invented words is drawn as skeleton bars, icons, charts and switches, never as fake text or numbers.
- **Tile:** 96x96 px frosted rounded square, radius 22, five in a row, gap 18.
- **Window (L1):** the footage as a rounded rectangle x 0.05–0.95 W, bottom flush with the frame (y 0.62 H to 1.0 H), radius 30 on the top corners only, soft shadow upward. It always plays the live shot, cropped by cover-fit (4:3 crop, vertical anchor on the subject).

### 1.3 Layouts (fractions of W, H)
| Name | Geometry |
|---|---|
| Top lane | y 0.035–0.275 H, used by the pill stack and tile row |
| Under-chin title | y 0.44–0.68 H, centred |
| Bottom caption lane | text centre y 0.76 H (B-roll shots) |
| Page, widget zone | y 0.06–0.55 H |
| Page, caption pill | centre y 0.47 H (card page) or 0.09 H (pipe page) |
| Page window | x 0.05–0.95 W, y 0.62–1.0 H |

### 1.4 Typography
| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Pill text | sentence case, semibold, ACCENT-INK | Poppins SemiBold | Inter SemiBold | 34–38 px (0.028 H) |
| Lane caption | sentence case, semibold, white, shadow 75 % | Poppins SemiBold | Inter SemiBold | 52 px (0.041 H) |
| Caption key word | same, ACCENT | same | same | same |
| Title small line | UPPERCASE, tracking 0.07 em, white | Poppins SemiBold | Montserrat SemiBold | 58 px |
| Title big word | UPPERCASE, heavy, ACCENT, glow + dark stroke | Poppins ExtraBold | Montserrat ExtraBold | 112 px, fits 0.86 W per line |

All text sits at least 0.05 W from the side edges. Every word is the user's word.

### 1.5 Motion language
- Arrive: fade plus 8–10 px rise (cards 30 px rise), ease-out-cubic, 5–9 f.
- Pixel resolve (T1): content drawn blocky (16, 11, 8, 5, 3, 2, 1 px blocks) over 8 f while fading in.
- Draw-on: chart lines and pipes grow along their path, ease-in-out, 1.0–1.1 s.
- Page entry and exit: the footage scales into or out of the window over 10 or 9 f, ease-in-out-cubic, while the page fades in over the same time.
- Never: bounce, tilt, spin, shake, flashes, hue-shifted footage.

### 1.6 What may happen to the user's footage
Allowed: full-frame; moved and scaled into the L1 window (a cover-fit crop of the live shot); a frosted blur used only as the backdrop of a pill or card; the speaker placed in front of pills (person mask, T1 only). The primary shot always plays live and in sync. Forbidden: replacing a shot, recolouring, speed changes, hiding the whole shot for more than the 10 f transition, blur on the face.

### 1.7 Safe zones
- Face box never covered while speaking. T1 pills sit behind the head: pill text is placed in the side zones and asserted to be at least 85 % visible against the person mask on every frame after it has appeared.
- Title and cards stay out of the face box; the under-chin title starts below the chin (0.44 H on a speaker with the face at 0.15–0.40 H).
- Bottom lane avoids on-footage text; the footage's own corner watermark is not covered.

---

## 7. MOMENT LIBRARY
Families: T title, C caption, W widget, P pipe, L layout, X transition, M movement. Energy: low / mid / high.

### T1 · PILL STACK RESOLVE — T mid (signature, opener)
**What it is:** three pills stacked behind the speaker's head, carrying the opening phrase. They fade in on the spoken words, resolving from pixel blocks to sharp.
**Use when:** the video opens on a speaker (talking head). **Avoid when:** no person or the head fills the top of the frame (use W1 + C1 instead).
**Text:** the first 3–6 words split in 2–3 pill phrases, 2–3 words each; case as written.
**Geometry:** pill 1 solid ACCENT, centred, y 0.035–0.105 H, width text + 70 px, text ACCENT-INK on accent (dark `#381B00` on amber). Pill 2 FROST, x 0.05–0.95 W, y 0.125–0.19 H, text right-aligned, 34 px from the right inner edge, 34 px font. Pill 3 FROST, y 0.21–0.275 H, text left-aligned at the left inner edge 26 px, 30 px font. Pills 2–3 run behind the head (person mask on top). Text stays in the side zones.
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word time | pill n | alpha, pixel block | 0 → 1, 16 px → 1 px over 8 f | ease-out-cubic (alpha over 6 f) |
**Footage:** full frame, untouched; person mask EMA 0.6/0.4 plus 1.2 px blur. **Captions during it:** none, the pills are the captions. **Exit:** hard cut on the footage cut.
**Flow prompt text:** "Behind the speaker, a stack of {{3}} rounded pills appears one by one on the spoken words: a solid {{ACCENT}} pill on top and two frosted white pills behind the head, saying exactly {{PHRASES}}. Each pill sharpens from blocky pixels into crisp text."
**Still-image state:** all pills sharp.

### C1 · LANE CAPTION — C low (signature)
**What it is:** one to three words per line, sentence case, white with a soft shadow, words fading in as spoken, with one ACCENT key word.
**Use when:** any speech on full-frame shots, especially B-roll. **Avoid when:** a page scene is up (use C2).
**Text:** 3–5 words, ≤ 26 characters, one key word (≤ 1 per chunk, ≤ 3 per video).
**Geometry:** centred, text centre y 0.76 H on B-roll; under the chin (y 0.44 H) on speakers; 52 px; max width 0.86 W.
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word time | word | alpha, y | 0 → 1, +10 px → 0 over 5 f | ease-out-cubic |
**Exit:** hard cut at chunk end. **Flow prompt text:** "A short white caption, {{WORDS}}, with the word {{KEY}} in {{ACCENT}}, fades in word by word near the bottom."

### C2 · PILL CAPTION — C low (signature on pages)
**What it is:** the chunk sits in a frosted white pill (height 80, radius full) with ACCENT-INK text 36 px, words fading in as spoken.
**Use when:** L1 pages. **Text:** one chunk, ≤ 28 characters, may wrap to two lines (height 132, radius 40).
**Geometry:** width = text + 76 px, ≤ 0.9 W, centred x; centre y (0.47 H under a card, 0.09 H over a pipe). Pill fades in over 6 f; words as C1.
**Exit:** hard cut with the footage, or 4 f fade when a page hands over. **Flow prompt text:** "A rounded frosted pill saying {{WORDS}} appears, words one by one."

### W1 · TICK TILES — W mid
**What it is:** five frosted tiles drop in a row with a person icon; ACCENT tick badges pop on one after another.
**Use when:** lists, steps, "people", progress. **Geometry:** row centred, y 0.065 H, tiles 96 px, gap 18. Tiles stagger 2 f from time, rise 26 px over 7 f; badge r = 15 px at +10 f, +4 f per tile, scale 1 → 1.25 → 1 over 6 f.
**Exit:** hard cut. **Flow prompt text:** "A row of five frosted square tiles with person icons drops in; small {{ACCENT}} tick badges appear on them one at a time."

### W2 · STAT CARD — W mid
**What it is:** a white card (x 0.175–0.825 W, 468x270 px) fades up from frost, with an icon, two skeleton bars, a rising line chart with area fill and a dot, and six chips (the last in ACCENT).
**Geometry:** y 0.047 H (top lane). Card rises 34 px over 9 f; chart draws over 24 f starting at +8 f. **Use when:** growth, results, over-time phrases. **Exit:** hard cut. **Flow prompt text:** "A clean white dashboard card appears at the top with a line chart that draws upward and ends in a dot."

### W3 · TOGGLE CARD — W mid
**What it is:** a white card (x 0.133–0.867 W, y 0.067–0.40 H) with a header and three rows; a switch in each row flips to ACCENT in turn (6 f each, +8 f apart, first at +14 f).
**Use when:** automation, settings, "set it once". **Exit:** 4 f fade at the next cut. **Flow prompt text:** "A white settings card with three rows; the switches turn on one after another in {{ACCENT}}."

### P1 · PIPE FORK — P high (signature)
**What it is:** a pill label with a glowing tube that runs down and forks into two branches ending in two white pills (icon dot plus skeleton bar).
**Geometry:** label pill centre (0.5 W, 0.09 H); stem from y 0.125 H to 0.205 H; branch left to x 0.27 W ending y 0.336 H; branch right to x 0.73 W ending y 0.4375 H; end pills 300x64 px.
**Motion:** tube draws 26 f, ease-in-out, starting 10 f after the label; end pills rise 10 px and fade in during the last 22 % of the draw. **Use when:** a split, a choice, "from one, two". **Exit:** 4 f fade at the cut. **Flow prompt text:** "A glowing {{ACCENT}} tube grows down from a label and splits into two branches that end in white pills."

### L1 · PAGE WINDOW SETTLE — L high (signature layout)
**What it is:** after a cut, the new shot stays full frame for 3 f, then scales over 10 f into the bottom window while a tinted gradient page fades in behind it.
**Use when:** a B-roll shot that carries a UI moment. **Geometry:** see 1.2. Crop anchor: vertical centre of the subject (0.43 H on a phone close-up, 0.27 H on a man at a counter). Page cards enter 11 f after the settle.
**Footage:** live, in sync. **Exit:** X1. **Flow prompt text:** "The shot shrinks smoothly into a rounded window at the bottom while a soft {{PAGE COLOUR}} gradient page fills the rest."

### X1 · WINDOW EXPAND — X mid
**What it is:** on the cut after a page scene the new shot appears in the window, holds 3 f, expands to full frame over 9 f as the page fades out; page widgets fade out over 4 f at the cut.
**Flow prompt text:** "The window grows smoothly back to the full frame as the page fades away."

### T2 · GLOW WORD TITLE — T high (signature, closer)
**What it is:** an under-chin title: a small white uppercase line and one or two giant ACCENT lines with glow and a dark stroke, words popping on their beats.
**Text:** the last 3–4 words; small line = connector words, big lines = payoff word(s).
**Geometry:** small line 58 px at y 0.44 H, big lines 112 px at +78 px and +182 px, centred; ≤ 0.86 W each. Words fade and rise 12 px over 5 f; glow blur 12 at 55 %. **Exit:** none, holds to the end.
**Flow prompt text:** "Under the speaker's chin: {{SMALL WORDS}} in small white capitals, then {{BIG WORDS}} huge in glowing {{ACCENT}} capitals."

### M1 · WINDOW DRIFT — M low
**What it is:** in a page scene longer than 2 s, the crop inside the window drifts up to 1.05x over the shot. Reset at every cut.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | W1 / W3 / P1 on B-roll, L1 for a UI shot, W2 on a growth line | T2 |
| Single talking head | T1 | C1 under the chin, W2 and W1 on a split top lane | T2 |
| B-roll only | L1 + C2 | W3, P1, W2 | C1 with key word |
| Still image | C1 + W2 on the poster | none | none |

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
