# Google Flow prompt · Depth Headline
**Type:** dynamic caption system (captions and caption-level text only)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Depth Headline" caption style to it.

The look in one sentence: One giant ultra-condensed word standing behind the speaker that snaps yellow in a see-through box the instant it's spoken, small bold karaoke captions that leave that word out, hard punchy cuts.

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
| HEAD-WHITE | `#FFFFFF` | the headline word while waiting |
| SIGNAL-YELLOW | `#FEE401` | the headline word while spoken; the active caption word |
| BOX-YELLOW | `#FEE401` at ≈ 35 % | translucent box behind the spoken headline (soft edge) |
| CHIP-YELLOW | `#FEE401` at ≈ 30 % | translucent chip behind the active caption word |
| CAPTION-WHITE | `#FFFFFF` | caption words |
| SHADOW | black 25–40 %, soft | under headline and captions, for legibility |

Two colours only (white and one signal yellow). Brand variant: SIGNAL-YELLOW may become one saturated brand colour; keep white.

### 1.2 Depth (the signature)
- The headline sits **between the background and the person**: composite it over the footage, then cut it away wherever a **person matte** says "person". The speaker's head, hair and shoulders occlude the letters.
- Matte: a person-segmentation model (MediaPipe selfie segmenter, rembg/u2net human seg, SAM). Feather the matte edge ~1.5 px; smooth it over time (blend 60 % new + 40 % previous frame, reset on cuts) so the cut-out edge doesn't shimmer.
- **Legibility rule:** at least **65 % of the glyph area must stay visible**. If the person would hide more, use the next placement rung (1.4). The face is never covered: the word is always *behind* the person.
- Shots with no person (B-roll, products, screens): the headline sits **in front** of the footage in the same position; nothing else changes.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Headline | ultra-condensed heavy grotesk, UPPERCASE, one word | Anton | Bebas Neue, Oswald Bold, League Gothic, Impact | the largest size that fits **0.86 W**, cap height ≤ rung max (≈ 0.21 H) |
| Caption | geometric sans, extra-bold, sentence case as written | Montserrat ExtraBold (wght 800) | Poppins ExtraBold, Inter ExtraBold | 0.036 H [69 px] |

### 1.4 Headline placement rungs (top of the cap height, max cap height)
| Rung | Top | Max cap height | When |
|---|---|---|---|
| A (reference) | 0.11 H | 0.21 H | default |
| B | 0.07 H | 0.17 H | person hides > 35 % at rung A |
| C | 0.045 H | 0.13 H | still > 35 % at rung B |
Measured: "IDEA" 0.144–0.852 W × 0.108–0.321 H; "HIDING" 0.065–0.930 W × 0.128–0.303 H. Centred on W.

### 1.5 Motion language
- **Everything is a hard cut.** Headline words, colour changes, boxes and caption lines switch on a single frame. No slides, fades, scales or bounces.
- **Rhythm:** each headline word is on screen ≈ 1.3–1.5 s: white for 0.5–0.9 s (while the words before it are spoken), then yellow + box for exactly the time the word is spoken (≈ 0.45 s), then the next word replaces it on the frame its group starts.
- The camera/footage never moves.

### 1.6 What may happen to the user's footage
- Nothing moves: the footage stays full-frame, original scale, in sync, untouched. Only overlays are added (headline, boxes, captions) and the headline is cut by the person matte.
- No crop, zoom, blur, recolour, retime or reordering.

### 1.7 Safe zones
- Headline zone: top 0.04–0.33 H. Caption zone: centred on 0.78 H (baseline 0.795 H); if hands/products sit there and matter, raise to 0.70 H.
- Captions never cross a face. The headline never sits in front of a face (it's behind the person, or in front only when there is no person).

---

## 7. MOMENT LIBRARY
Family codes: **HEAD** (headline), **CAP** (captions). Energy:  low ·  medium ·  high.

---

### D01 · DEPTH HEADLINE — HEAD  (signature, always on)

**What it is:** One giant ultra-condensed white word behind the speaker, centred at the top of the frame.

**Word:** the key word of the current phrase, taken from the user's text (noun, verb, number or payoff), UPPERCASE, punctuation dropped. One word only (≤ 10 letters reads best; longer words shrink to fit 0.86 W).

**Timing:** appears on the first frame of its **group** (the phrase it belongs to), hard cut; it is shown *before* it is spoken (the reference shows "IDEA" 0.9 s early). It is replaced, hard cut, on the first frame of the next group. Groups never cross a footage cut (switch the word on the cut).

**Graphics:** HEAD-WHITE, Anton, size and position per 1.3/1.4 rung; soft shadow (0/+3 px, blur 5 px, 28 %). Matte cut-out per 1.2.

**Flow prompt text:** "Behind the person, as if painted on the wall, the single word \"{{WORD}}\" stands in huge, tall, ultra-condensed white capitals across the top of the frame; the person's head and hair overlap the letters. It appears instantly, no animation."

**Still-image state:** the word in white behind the person.

---

### D02 · YELLOW HIT — HEAD  (signature)

**What it is:** The instant the headline word is spoken, it turns SIGNAL-YELLOW and a translucent yellow rounded box appears behind it (also behind the person). When the word ends, it snaps back to white (or the next group starts).

**Timing:** from the word's spoken start to its end (≈ 0.4–0.5 s). Measured on the reference: "IDEA" yellow 1.50–1.97 s, "HIDING" 2.47–2.90 s, "SIGHT" 3.90–4.33 s.

**Graphics:** text SIGNAL-YELLOW; box BOX-YELLOW, rounded (radius 0.035 W), padded 0.06 W left/right and 0.03 H top/bottom around the glyphs, edge softened 0.006 W. Both cut by the person matte like the word.

**Flow prompt text:** "The moment the word \"{{WORD}}\" is spoken, the big headline snaps to bright yellow with a soft see-through yellow box behind it, then snaps back to white when the word ends."

---

### D03 · KARAOKE CAPTION — CAP (signature, always on)

**What it is:** A short line (1–3 words) of small extra-bold white captions centred low in the frame. The word being spoken turns yellow with a translucent yellow chip behind it. **The headline word is not in the captions**: during the yellow hit the caption line is all white (nothing active), because the giant word is the one being said.

**Text:** the user's words verbatim, minus the headline words, 1–3 words per line, ≤ 22 characters. A group may have two caption lines in sequence (switch on the first word of the second line).

**Graphics:** CAPTION-WHITE Montserrat ExtraBold 0.036 H, centred, baseline 0.795 H; soft shadow (0/+2 px, blur 3 px, 40 %). Active word: SIGNAL-YELLOW text + CHIP-YELLOW rounded chip (radius 0.010 W, padding 0.010 W) behind it.

**Timing:** the line appears (hard) with its group or with its first word; each word is active from its spoken start to its end; lines switch hard.

**Flow prompt text:** "Small bold white captions centred low in the frame show only these lines, in order: [a-b s] \"{{LINE_1}}\", … The word being spoken turns yellow with a faint yellow highlight behind it. The big headline word never appears in the captions."

---

### D04 · HEADLINE SWAP ON CUT — HEAD

**What it is:** When the footage cuts, the headline switches to the next group's word on the cut frame (hard), so cuts and words land together. If a group would cross a cut, end it on the cut.

**Flow prompt text:** "On every cut, the big headline word changes instantly to \"{{NEXT_WORD}}\"."

---

### D05 · RUNG STEP — HEAD  (adaptive placement)

**What it is:** For a group where the person (e.g. a close-up or a person standing high in frame) would hide more than 35 % of the letters, the headline uses rung B or C: higher and smaller. Chosen once per group (never changes mid-group).

**Flow prompt text:** "The headline sits a little higher and smaller here so the person's head doesn't hide most of it."

---

### D06 · CLEAN TAIL — CAP  (ending)

**What it is:** After the last word, headline and captions disappear together (hard) and the footage plays clean for its remaining frames. The reference ends with 0.6 s clean. If the video ends right after the last word, keep the last group to the end instead.

**Flow prompt text:** "After the last word, all text disappears and the video plays clean to the end."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Plan |
|---|---|
| Talking head (single shot) | D01 + D02 + D03 throughout, one headline word every 1.2–2 s; D05 when they lean in; D06 at the end |
| Talking head ↔ B-roll | same, plus D04 on every cut; on B-roll shots the headline is in front (no person) |
| Lists | one headline per item (the item's key word), captions carry the rest |
| Still image (poster) | D01 behind the person + one D03 line; or D02's yellow state for extra punch |

Never paste a row blindly.

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
