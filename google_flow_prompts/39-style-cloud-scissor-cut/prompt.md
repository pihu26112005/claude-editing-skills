# Google Flow prompt · Cloud Scissor Cut
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Cloud Scissor Cut" motion style to it.

The look in one sentence: A powder-blue doodled paper cloud with a heavy black title, hand-lettered captions, then a frosted paper band with a scissors-in-hand snip and bold white captions.

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
| Cloud paper | #C6D9E7 | Top cloud, scalloped edge, floating dots |
| Cover paper | #BACDDC at 86 % opacity | Frosted band; over footage it reads about #A3AFBA |
| Title ink | #261409 | Heavy title |
| Pencil | #4A5058 at 85 % | All line doodles, 3 px strokes at 720 wide |
| Caption white | #FFFFFF | Both caption faces |
| Caption shadow | #0A0A0E at 40–55 % | Soft shadow under white captions |
| Scissors | #1A181C blades and rings, #787A82 pivot and edge highlight | Hand-held scissors |
| Skin | #E4B296 with outline #AA765E | Hand |
| Grain | gaussian noise, sigma 6–7 | Both paper layers |

Brand-swap rule: a brand colour replaces the paper blue (cloud and cover, same lightness) and nothing else. Title ink, white captions, pencil and scissors never change. No other colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Full frame, always. No cards, borders, masks, blur or grade. It is only ever covered by the paper layers below. |
| Cloud top | Full-width paper band: flat body 0–0.100H [0–192] plus scalloped bottom edge of overlapping circles (radius 0.047–0.081W, fringe depth 0.03H), total height 0.144H [276]; soft shadow (0, +6 px, blur 5 px, 27 % black). Floating small dots may trail below the edge. Never taller than 0.14H when a face sits at y ≥ 0.15H. |
| Cover paper | A frosted BAND, never a full-frame sheet: it covers at most the lower 40 % of the frame (top of the flat body at 0.62H, scallops reaching up to about 0.57H) or, for a side layout, a side band of at most 0.40W. Scalloped top edge of circles (radius 0.055–0.11W) with 3–4 detached circles above it. 86 % opaque (footage ghosts through the band). The footage above the band stays unfrosted and fully visible. Pencil doodles only inside the band, in its lower part (1.3). |
| Scissors + hand | Black scissors in a flat-colour hand, appearing ONLY for the snip beat (0.6–0.85 s: enter, 4 blade snaps, leave). Scale 0.34: hand + scissors fit within 0.35H, bottom-right (x from 0.65W), forearm leaving through the bottom edge. Never held on screen. |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor = the face or main subject. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Cloud top | 0, 0, 1, 0.144 [0,0,1080,276] | T1, E1 |
| Title line | centre x 0.50W, centre y 0.092H, max width 0.82W | Title text on the cloud |
| Script lane | line 1 baseline centre y ≈ 0.645H, line pitch 58 px [0.045H], left edge x = 0.185W [200], max line width 0.64W | C1 hand-lettered captions |
| Bold lane | top-left of the paper band; first line top y = 0.655H [1257], left edge 0.17W, max line width 0.66W, line pitch 72 px [0.056H] | C2, C3 |
| Paper doodles (band-local, y from the flat body top 0.62H) | cube 0.04W, +0.26H · mug with steam 0.46W, +0.28H · stars 0.85W, +0.23H · scribble 0.24W, +0.36H · spiral 0.78W, +0.35H · paper plane 0.32W, +0.23H | Inside the band only, below the caption area; never over the visible footage |
| Cloud doodles | plane 0.05W · spiral 0.14W · star 0.03W · lightning and two hearts at the right end | Fixed to the cloud |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Ultra-heavy grotesque, UPPERCASE, tight spacing, warm black | Archivo Black (Archivo variable, wght 900, wdth 100) | Anton, Montserrat Black | Fit one line to ≤ 0.82W; 9 characters ≈ 0.14W font, 12 characters ≈ 0.09W. Reference cap height 0.060H |
| Script caption | Thin slanted marker handwriting, UPPERCASE, wide tracking, white | Gaegu Bold | Gaegu Regular, Gochi Hand, Caveat Brush | 58 px [0.08W]; tracking 8 px [0.11em]; synthetic shear 0.18 |
| Bold caption | Heavy condensed grotesque, UPPERCASE, white, left aligned | Archivo (wght 900, wdth 78) | Barlow Black, Anton | 66 px [0.092W]; tracking 0 |
| Solo word (C3) | Bold caption style, enlarged | same | same | 1.6× the bold size, one line |

Rules: all captions UPPERCASE (the style dictates it; the audit compares case-insensitively). Characters keep the user's punctuation. No outline-only text. Nothing rotated. Text sits on top of the hand and scissors but under the cloud top.

Shadows: script caption (0, +3, blur 3 px, 55 %) plus (0, +2, blur 1.3 px, 50 %); bold caption (0, +3, blur 4 px, 40 %).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Cloud drop | ease-out cubic (1−(1−t)³), slides from above the frame | 0.34 s (8 f) |
| Cloud lift | ease-in cubic, leaves upward | 0.34 s (8 f) |
| Title pop | alpha 0 → 1 with scale 0.88 → 1, ease-out | 0.20 s (5 f) |
| Blob rise | ease-out, circles grow from 0 and rise, staggered 0.10 s | 0.34 s each |
| Paper rise | ease-out cubic, bottom to top | 0.60 s (14 f) |
| Hand pop-in | enters 0.25 s before the snip from 0.34H below, ease-out; leaves 0.2 s after, ease-in | 0.25 s in, 0.2 s out |
| Scissor snap | open-close cycle (blade angle 3° → 22° → 3°), 14 steps per second, only during the 0.4 s snip beat | beat 0.6–0.85 s |
| Paper drop-away | ease-in cubic, the band falls out through the bottom | 0.36 s (9 f) |
| Caption word | ease-out alpha ramp, no movement | 0.125 s (3 f) |
| Caption chunk exit | hard cut, same frame as the next chunk | 1 f |

Never: bounce, overshoot, spring, rotation, shake, flashes, colour grading, letter-by-letter typing, wipes other than the paper, glitch, scale pops on captions.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Full-frame display, untouched | Always |
| Frosted paper band at 86 % opacity (footage ghosts through) | Covers at most the lower 40 % of the frame; the rest of the footage stays clear. Never over a speaking face. Band on screen ≤ 45 % of the video, one hold ≤ 3.5 s. Hand + scissors only for the snip beat, ≤ 0.85 s, ≤ 0.35H tall. No doodles outside the band. |
| Cloud top overlay | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; blur, glitch, warp, zoom or colour grading; adding footage the user did not supply. The primary footage plays live and in sync with the audio under every overlay.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by the cloud, paper, hand or captions while speaking. The cloud may touch hair only. If the face top is above 0.17H, shrink the cloud (body 0.07H) or skip T1 and use the script lane only. |
| Cover paper | Band only (lower 40 %). On a speaker shot keep the band top ≥ 0.04H under the chin; if the chin is below 0.56H, skip the band on that shot. If a key subject (hands, product, screen) sits in the band zone for > 1 s, raise the band top by ≤ 0.05H or accept the ghosting for ≤ 1.5 s. |
| Script lane | Default 0.628H. If the face bottom edge is below 0.58H, move the lane to 0.03H under the chin; if that pushes line 2 below 0.88H, drop the lane to 0.76H. |
| Bold lane | Top-left of the paper; if a doodle collides with the text it is fine (doodles sit under text). Keep every glyph ≥ 0.04W from the edges. |
| Footage text (signs, UI) | If readable footage text sits in the script lane for > 1 s, shift the lane up or down by 0.07H. |

---

## 7. MOMENT LIBRARY
Family codes: **T** title · **C** caption · **X** cut or transition treatment · **E** ending.

### MOMENT T1 · CLOUD TITLE DROP
**What it is:** a powder-blue torn-paper cloud with pencil doodles drops from the top edge; the topic words pop in on it in heavy black type.
**Use when:** the opening line names the topic; the video opens on a speaker or calm shot. **Avoid when:** the face top is above 0.15H and cannot be cleared (1.7), or a cut falls within 0.3 s of the drop.
**Text:** 1–2 words, the topic words from the user's own opening, UPPERCASE. These words move out of the caption chunks (caption audit counts them). Max 14 characters per line; if longer, shrink to fit 0.82W.
**Geometry / Graphics:** Cloud top (1.2), Title line (1.3), title ink, doodles per 1.3.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.04–0.38 [1–9] | cloud | y | −0.144H → 0 | ease-out cubic |
| 0.10–0.30 [2–7] | title | alpha, scale | 0, 0.88 → 1, 1 | ease-out |
| 0.38–1.44 [9–35] | cloud, title | hold | final state | — |
| 1.44–1.78 [35–43] | cloud, title | y | 0 → −0.153H | ease-in cubic |

Start: 0.04–0.2 s (at the first spoken word at the latest; reference: cloud arrived 0.17–0.5 s, title 0.25 s). Hold: 1.2–2.2 s. Lift must finish ≥ 3 frames before the next footage cut.
**Footage / plate behaviour:** untouched; only hair or background sits under the cloud.
**Captions during it:** C1 starts at its own word times underneath, in the script lane.
**Exit:** the lift above, in the same motion family as the entrance.
**Build notes:** pre-render the cloud (circles at 2×, grain sigma 6, doodles drawn with jittered 3 px strokes) and its shadow once; shrink the title font in 2 px steps until it fits 0.82W; title and cloud share the same y offset.
**Flow prompt text:** "A powder-blue torn-paper cloud with tiny pencil doodles slides down from the top edge of the frame and a heavy black uppercase title reading {{TOPIC WORDS}} pops onto it. It holds for about a second, then slides back up out of frame before the next shot."
**Still-image state:** cloud at the top, title on it, script lane caption below the face.

### MOMENT C1 · SCRIPT WHISPER
**What it is:** small slanted hand-lettered white capitals with wide tracking, left-aligned in two or three short lines near the chest. Words fade in one by one; the whole chunk is laid out first so no word moves.
**Use when:** the shot is a speaker or calm footage. **Avoid when:** the lane is bright (use X2/C2 or shift lane).
**Text:** 3–5 words per chunk, UPPERCASE, split at punctuation, never ending on an article, preposition or conjunction; max 3 lines of ≤ 0.64W.
**Geometry / Graphics:** Script lane (1.3), script caption font (1.4), shadows (1.4).
**Motion:**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | word | alpha | 0 → 1 over 0.125 s | ease-out |
| next chunk's first word | chunk | exit | hard cut | — |

Chunk start = first word start; end = min(last word end + 0.15, next chunk start − 0.05); min 0.8 s. Reference rhythm: one word per 0.2–0.3 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption. It may stay on top of the rising paper (X2) until the next chunk, which switches to C2.
**Exit:** hard cut.
**Build notes:** Gaegu Bold at 2×, shear 0.18 via affine transform, tracking 8 px; shadow pair per 1.4; pre-render each word once.
**Flow prompt text:** "Small thin white hand-lettered capitals, slanted, widely spaced, in two short lines at chest height, appearing word by word and reading {{CHUNK TEXT}}."
**Still-image state:** the full chunk visible.

### MOMENT X1 · BLOB RISE
**What it is:** three paper circles of different sizes grow and rise from the bottom edge, announcing the paper.
**Use when:** a shot change or a new idea is 0.6–1.0 s away and the band fits under any face. **Avoid when:** a speaking chin is below 0.56H.
**Text:** none.
**Geometry / Graphics:** circles in cover paper colour at 92 % opacity: radii 0.13W, 0.04W, 0.065W at x 0.22W, 0.72W, 0.46W.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.40–2.74 (+0, +0.10, +0.18 stagger) | circle | radius, y | 0 → full, rising 0.09H from 0.02H above the bottom | ease-out |
| 2.70 | — | X2 takes over | — | — |

Start: 0.3 s before X2. **Footage:** untouched. **Captions:** continue.
**Exit:** covered by the paper in X2.
**Flow prompt text:** "Three round powder-blue paper circles of different sizes grow and float up from the bottom edge of the frame."
**Still-image state:** not used.

### MOMENT X2 · SCISSOR PAPER COVER
**What it is:** a scalloped frosted paper band rises from the bottom over the lower 40 % of the frame (footage ghosting through it, the rest of the frame clear). During the rise a small hand with black scissors pops in at the bottom right, snips, and leaves.
**Use when:** a new section starts, a person → B-roll cut, a list or steps begin, or the shot is B-roll without a face. Time the snip around a footage cut. **Avoid when:** the chin is below 0.56H on a speaker shot, or the hold would exceed 3.5 s.
**Text:** none; C2 captions sit on it.
**Geometry / Graphics:** Cover paper band, Scissors + hand (1.2), band doodles (1.3).
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.70–3.30 (14 f) | paper band | y | off-screen below → final (flat body top 0.62H) | ease-out cubic |
| 2.95–3.20 | hand + scissors | y | +0.34H → 0 | ease-out cubic |
| 3.20–3.60 | scissors | blade angle cycle | 3° → 22° → 3° (about 5 snaps) | 14 steps/s |
| 3.60–3.80 | hand + scissors | y | 0 → +0.34H | ease-in cubic |
| 3.30–6.24 | paper band | hold | final state | — |

Hold: 2.0–3.5 s. The snip beat is 0.6–0.85 s in total and does not repeat during the hold. Reference: a full sheet rose 2.83–3.5 s; this skill limits it to a band.
**Footage / plate behaviour:** footage plays live, fully visible above the band and ghosted through it.
**Captions during it:** C1 until its chunk ends, then C2 (or C3) on the band.
**Exit:** X3.
**Build notes:** band layer is 0.38H + 150 px tall with the scallops in its top 150 px; alpha 0.86; pre-render 5 scissor states (3, 8, 13, 18, 22°) at 2× with ring holes punched through the alpha, scaled to 0.34; hand drawn over the rings; doodles drawn only into the band layer.
**Flow prompt text:** "A band of frosted powder-blue paper with a bumpy cloud-shaped top edge rises over the bottom part of the frame only, the shot staying clearly visible above it and faintly through it, with light pencil doodles of a cube, a mug, stars and a spiral inside the band. A small hand holding black scissors pops in at the bottom right, snips the blades open and shut a few times, and leaves."
**Still-image state:** the held band with doodles and one bold caption (no hand).

### MOMENT C2 · BOLD PAPER CAPTION
**What it is:** heavy condensed white capitals, top-left inside the paper band, two or three lines, word by word.
**Use when:** the paper band is holding. **Avoid when:** no band is on screen. Max 3 lines so the text stays inside the band.
**Text:** 2–6 words per chunk, UPPERCASE, split at punctuation, ≤ 3 lines of ≤ 0.66W.
**Geometry / Graphics:** Bold lane (1.3), bold caption font (1.4), shadow (1.4).
**Motion:** word alpha 0 → 1 over 0.125 s ease-out at each word start; chunk exit hard cut. Chunk end = min(last word end + 0.15, next start − 0.05); stop 0.2 s before X3 begins.
**Footage / plate behaviour:** under the paper.
**Captions during it:** this is the caption.
**Exit:** hard cut, or with the paper in X3.
**Build notes:** Archivo wght 900, wdth 78, size 66 px at 2×; the caption is drawn over the band and above the doodles.
**Flow prompt text:** "Heavy condensed white capitals, left aligned in the top left, appearing word by word on the paper and reading {{CHUNK TEXT}}."
**Still-image state:** full chunk.

### MOMENT C3 · SOLO WORD
**What it is:** one keyword alone in the bold lane at 1.6× size on the paper.
**Use when:** a number, amount, time phrase or payoff word needs weight while X2 is holding. **Avoid when:** no paper, or more than 2× per video.
**Text:** 1 word (≤ 10 characters), UPPERCASE.
**Geometry / Graphics:** bold lane, one line, 106 px. Motion as C2. Exit hard cut. Flow prompt text: "One huge heavy white capital word, {{WORD}}, appears at the top left of the paper."

### MOMENT X3 · PAPER DROP-AWAY
**What it is:** the paper band falls out through the bottom edge, revealing the full clean footage.
**Use when:** X2 has held its time; a footage cut is 0.0–0.1 s away so the next shot appears already clean. **Avoid when:** the next shot is not yet playing (never reveal an empty frame).
**Text:** none.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 6.24–6.60 (9 f) | paper band | y | final → fully below the frame | ease-in cubic |

End: on or 1–2 frames before a footage cut. Last bold chunk ends 0.2 s earlier.
**Footage / plate behaviour:** untouched underneath.
**Captions during it:** none (silence gap) or C1 resuming ≥ 0.3 s later.
**Exit:** itself.
**Flow prompt text:** "The paper band falls straight down out of the bottom of the frame, revealing the clean shot."

### MOMENT E1 · CLOUD RETURN
**What it is:** the cloud drops again with a time phrase, number or payoff words as the title, ending the video on a clean speaker.
**Use when:** the last third has a time phrase, amount or payoff word; the video ends on a face or calm shot. **Avoid when:** fewer than 2.5 s remain (shorten the hold), or the face is too high (1.7).
**Text:** 1–2 words from the user's own text, UPPERCASE, moved out of the captions.
**Geometry / Graphics:** as T1. **Motion:** as T1: drop 7.30–7.64, title pop 7.45–7.65, hold, lift 9.40–9.74 (times). C1 chunks continue in the script lane beneath it.
**Footage:** untouched. **Exit:** lift, or hold to the last frame if under 1.0 s remain.
**Flow prompt text:** "The powder-blue paper cloud slides down from the top again and a heavy black uppercase title reading {{WORDS}} pops onto it, staying while the person finishes speaking."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 + C1 | X1 → X2 on the B-roll section with C2 (C3 on a key word), X3 on the cut back | E1 + C1 |
| Single talking head | T1 + C1 | X2 band under the chin on a list or contrast, C2 | E1 |
| B-roll only | X2 early (band rises on the first shot), C2 | X3 → C1 on a clean shot → X1/X2 again | E1 on the last shot |
| Still image | T1 settled | C1 or C2 on the paper | — |

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
