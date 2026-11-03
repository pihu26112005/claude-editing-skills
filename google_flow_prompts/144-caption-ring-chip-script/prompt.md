# Google Flow prompt · Ring Chip Script
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Ring Chip Script" caption style to it.

The look in one sentence: One low line of small hand-lettered white words per phrase, the key word on a solid rounded cyan chip in marker lettering and one other word circled by a loose violet hand-drawn ring.

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
| Chip fill | #F3D946 | Rounded chip behind the key word |
| Chip text | #111111 | Key word on the chip |
| Ring stroke | #DF5C74 | Hand-drawn ring around the echo word |
| Small words | #FFFFFF | All other words |
| Shadow | #000000 at 95 % blur 4 px, offset 3 px down, plus 3 px dark stroke | Keeps white words readable on bright footage |

Brand-swap rule: chip fill and ring stroke are parameters (two different hues; chip text stays dark and the ring must read on both light and dark footage). White words and shadow never change. The demo uses a sky-cyan chip (#4CD3F2, text #082236) and a violet ring (#A06BFF).

### 1.2 Containers / shapes

- Footage: always full frame, 100 % of W and H, untouched. No cards, bars, borders, blur plates or colour overlays.
- Chip: rounded rectangle, corner radius 0.36 × chip height, solid fill, no border, no shadow. Chip height 0.039H measured [75 px]; demo 112 px at 720 wide (0.0875H) because the demo words are larger. Horizontal padding 22 px each side.
- Ring: open hand-drawn ellipse, 1.1 turns, a little wobbly, stroke 8 px (demo) [measured ≈ 2.5 px at 360 wide], extra soft dark shadow under the stroke. Encloses one word with ≈ 22 px horizontal and 10 px vertical air; sits slightly low so its tail loops under the word. The ring never touches the chip.

### 1.3 Layouts / lanes

One line per chunk, centred on x = 0.50W. Baseline y of the line:

| Lane | Baseline y | Use |
|---|---|---|
| Chest | 0.60H | Speaker shots: line stays below the face box (y > 0.40H) |
| Low | 0.80–0.90H  | B-roll with a clear lower area; pick the cleanest strip |
| Top | 0.14H  | B-roll with calm top area (wall, sky) |

Side margin ≥ 0.05W on every box including the ring. The whole line is shrunk uniformly if wider than 0.82W (demo: scale 0.64–1.0).

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Small words | Slanted brush handwriting, mixed case as written, white | Gaegu Bold | Caveat, Gochi Hand | 70 px at 720 wide (≈ 0.097W); reference small caps height ≈ 0.025H |
| Key word | Bold marker handwriting, dark on the chip | Caveat Brush | Gochi Hand, Kalam Bold | 100 px at 720 wide (≈ 1.4 × small) |

Word gap 26 px. Line = small words and the chip word in reading order.

### 1.5 Motion language

| Element | Motion |
|---|---|
| Small word | fade 0 → 100 % over 0.12 s, ease-out cubic, rise 0.008H, at its spoken time; the whole line is laid out first so no word moves |
| Chip + key word | chip fades in and scales 0.85 → 1.0 over 0.18 s, ease-out cubic (no overshoot), at the key word's spoken time; word fades over 0.2 s |
| Ring | starts 0.18 s after the echo word appears; the stroke draws along its path over 0.32 s, ease-out cubic |
| Exit | whole chunk (chip, words, ring) fades out over 0.12 s |
| Never | bounce, overshoot, letter-by-letter typing, slides, wipes, glitch, shake, flashes, effects on cuts, rings around two words at once |

### 1.6 What may happen to the user's footage

Allowed: text, chip and ring overlays with their soft shadows. Nothing else: no mask, no cut-out, no zoom, crop change, blur, colour change, background swap or retime. The footage plays live and in sync.

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head) never receives visible text, chip or ring.
- All boxes (words, chip, ring) inside 0.05W side margins and 0.02H top.
- Ring and chip are never on the same word and the ring never overlaps the chip.

---

## 7. MOMENT LIBRARY
Family codes: C caption, K keyword, R ring, E end. Energy: low / medium / high.

### C1 · CHEST LINE — C low
**What it is:** the base line: 2–6 small hand-lettered white words building word by word in one centred line below the speaker's face.
**Use when:** speaker shot, phrase with no strong word. **Avoid when:** hands or a phone sit exactly on the lane and a cleaner strip exists (use C2).
**Text:** 2–6 words, as written. **Geometry:** lane Chest (1.3), small words (1.4). **Motion:** 1.5 small word. **Exit:** fade 0.12 s.
**Footage behaviour:** untouched. **Captions during it:** this is the caption.
**Build notes:** pre-render each word as a sprite with shadow; lay the whole line out first.
**Flow prompt text:** "A small white handwritten line '{{LINE}}' fades in word by word below the speaker's face, with a soft dark shadow."
**Still-image state:** all words in.

### C2 · LOW LINE — C low
**What it is:** C1 on B-roll, in the lower lane.
**Use when:** any B-roll shot. **Geometry:** lane Low, y 0.80–0.90H chosen from the shot's cleanest strip. **Motion/Exit:** as C1.
**Flow prompt text:** "Near the bottom of the frame, a small white handwritten line '{{LINE}}' fades in word by word."

### C3 · TOP LINE — C low
**What it is:** C1 near the top on calm backgrounds. **Use when:** subject fills the lower half. **Geometry:** lane Top (0.14H). **Motion/Exit:** as C1.
**Flow prompt text:** "Near the top of the frame, a small white handwritten line '{{LINE}}' fades in word by word."

### K1 · CHIP KEYWORD — K medium
**What it is:** one word of the line sits on a solid rounded chip in bold dark marker lettering while the rest stays small white handwriting.
**Use when:** the phrase has one strong word (noun, verb, number). **Avoid when:** two strong words compete (chip one, ring the other, see K2).
**Text:** 1 key word, ≤ 12 characters ideal, as written; 1–5 small words before and after it.
**Geometry:** chip fill accent (1.1), height and padding 1.2; word 1.4.
**Motion:** chip 1.5 at the key word's spoken time; small words per 1.5. Chunk visible 0.65–1.7 s.
**Footage behaviour:** untouched. **Exit:** fade.
**Build notes:** draw the chip at 3× and downscale; chip text sits on the same baseline as the small words, the chip is centred on the key word's x-height.
**Flow prompt text:** "In the same line, the word '{{KEYWORD}}' appears on a solid {{ACCENT}} rounded label in bold dark handwriting, while '{{OTHER WORDS}}' stay small and white."

### R1 · RING ECHO — R medium
**What it is:** a loose hand-drawn ring is drawn around one small word of the line.
**Use when:** a contrast, number, or the word that qualifies the chip word. **Avoid when:** the line is already crowded (more than 6 words) or the word is next to the line end with no margin.
**Text:** the ringed word is one of the line's small words, never the chip word. ≤ 1 ring per chunk.
**Geometry:** ring 1.2, colour ring accent. **Motion:** ring 1.5; if the word's window leaves less than 0.5 s after the ring starts, pick an earlier word.
**Exit:** fades with the chunk.
**Flow prompt text:** "A loose hand-drawn {{RING COLOUR}} ring draws itself around the word '{{WORD}}'."

### K2 · CHIP AND RING — K high
**What it is:** K1 plus R1 in the same chunk: one chip word and one ringed word, usually the chip after the ring or two words apart.
**Use when:** the phrase has a pair (action and object, first and last). **Limit:** ≤ 3 per 10 s.
**Flow prompt text:** "The word '{{KEYWORD}}' sits on a solid {{ACCENT}} label while a hand-drawn ring draws around '{{WORD}}' in the same line."

### K3 · SOLO CHIP — K high
**What it is:** a one-word or two-word chunk where the chip word is the whole punchline. **Use when:** payoff, number, name. **Limit:** ≤ 1 per 6 s.
**Geometry:** lane any; chip as 1.2 at scale 1.0. **Motion/Exit:** as K1.
**Flow prompt text:** "One word '{{KEYWORD}}' pops onto a solid {{ACCENT}} label in bold handwriting and fades out."

### E1 · CLOSING CHIP — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 (or K2), held to 0.1 s before the speech ends and never past the end of the shot or a head leaning into the lane.
**Flow prompt text:** "For the last line, the word '{{KEYWORD}}' sits on a solid {{ACCENT}} label and stays until the speech ends."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 + K1 | K2 on lists, C2 / K1 on B-roll, C3 on busy lower areas | E1 |
| Single talking head | K1 | K2, C1, K1 | E1 |
| B-roll only | C2 + K1 | C3, K3 | E1 |
| Still image | K1 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Chip #4CD3F2 (text #082236), ring #A06BFF stroke 8 px, small words Gaegu Bold 70 px, key word Caveat Brush 100 px, chip height 112 px at scale 1, word gap 26 px, line cap 0.82W, shadows as 1.1, fade-in 0.12 s, chip 0.18 s, ring starts +0.18 s and draws 0.32 s, fade-out 0.12 s. Chunks (start–end, lane, chip word, ring word): 0.10–0.76 C1/K2 Chest (money, Saving); 1.10–1.80 K1 Chest (more.); 2.10–3.20 K2 Low 0.80H (yourself, first,); 3.25–4.85 K2 Low 0.84H (automate, investments,; scale 0.64); 4.95–6.55 K2 Low 0.90H (left., spend); 6.90–8.30 K2 Top 0.14H (year, one); 8.45–9.55 E1/K2 Chest (happens., watch; ended early because the speaker leans toward the camera at 9.6 s).

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
