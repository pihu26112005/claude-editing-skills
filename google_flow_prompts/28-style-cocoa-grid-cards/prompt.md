# Google Flow prompt · Cocoa Grid Cards
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Cocoa Grid Cards" motion style to it.

The look in one sentence: Footage as a rounded card on a cream-then-cocoa graph-paper page that rises, swells to full frame and slides aside for a dark text page with a typed white chip, phrases typed into brown label bars.

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
| Cream page | #EDE2DB | Page behind the card at the start |
| Cream grid line | #E0D5CE | Graph-paper lines on the cream page |
| Cocoa page | #4B3B37 | Dark text page, caption bars |
| Cocoa grid line | #5C4C48 | Graph-paper lines on the cocoa page |
| Ink | #4D3D37 | Italic title on the cream page |
| Tick | #6F645D | Thin guide lines above and below the card |
| Cream text | #F2E9E4 | Caption text on bars and on the cocoa page |
| Chip white | #FFFFFF | Topic chip box |
| Chip ink | #221A18 | Chip text and icon |

Brand-swap rule: if the user gives a brand colour, replace Cocoa page (and the bar) with a dark shade of it and Cream page with a pale tint of it. Keep text contrast high. No accent colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Page | Full frame. Graph-paper grid: line pitch 0.0835W [90], line width 0.003W [3], first vertical line at x ≈ 0, first horizontal line at y = 0.032H [61]. Same grid on both pages. |
| Card (settled) | Live footage in a rounded rectangle. Corner radius 0.045W [48]. No border, no shadow. Card 1 (opener): x 0.167–0.831W, y 0.315–0.829H [180–896, 604–1592]. Card 2 (return): x 0.10–0.90W, y 0.1875–0.81H [108–968, 360–1556]. Both are ≈ 0.72 wide-to-tall. |
| Card crop | Cover-fit: scale = card width / source width (so the source keeps its full width), vertical window anchored on the face (face centre at 0.30 of the card height). Crop anchor . While the card grows or moves, the crop window interpolates continuously. |
| Tick lines | Two 0.002W [3] wide vertical lines at x = 0.50W: top one from y = 0 to 0.104H [200], bottom one from the card's bottom edge to the page bottom. Cream page only. |
| Caption bar | Rectangle, #4B3B37 at 95 %, sharp corners, height 0.0615H [118], centred on x = 0.50W, centre y = 0.70H [1344]. Width = full chunk text width + 2 × 0.028W [30] padding; text left-aligned at the left padding. Fixed on the page: it does not move with the card. |
| Topic chip | White rectangle, sharp corners, height 0.047H [91], centre x = 0.50W, centre y = 0.228H. Contents: small asterisk icon (0.033W) then uppercase text. Width = padding 0.03W + icon + gap + text + padding 0.03W. |
| Inset card | Small rounded card (radius 0.03W) of the user's own footage on the cocoa page, 0.40W × 0.30H, x 0.50–0.90W, y 0.58–0.88H, with an italic label under its bottom-right corner. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Title line | centre x 0.50W, centre y 0.218H [419] | Italic title word between the top tick and the card |
| Bar lane | x 0.04–0.96W, y 0.669–0.731H | Bar captions (all states: card, full frame) |
| Staircase | first line centre y 0.46H [884]; line pitch 0.93 × font size; first line starts at x = 0.15W; each next line starts at (previous start + 0.5 × previous line width), kept right edge ≤ 0.92W | Bare staircase caption on the cocoa page or over footage |
| Serif line | centre x 0.50W, centre y 0.60H | Serif words on full-frame footage |
| Topic chip | centre y 0.228H | Cocoa page |
| Inset card | x 0.50–0.90W, y 0.58–0.88H | Cocoa page, under the staircase |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Italic transitional serif, semibold, mixed case as written, cocoa ink | Newsreader Italic (wght 600) | Lora Italic, Playfair Display Italic | 0.088W [95]; 6-letter word ≈ 0.24W wide |
| Bar caption | Humanist grotesque sans, medium, lower-case as written, cream, letter-spacing 0 | Work Sans Medium (wght 500) | Manrope Medium, Inter Medium | 0.085W [91]; shrink to ≥ 0.07W if width + padding > 0.92W |
| Bare staircase | Same sans, cream, soft shadow on footage | Work Sans Medium | Manrope, Inter | 0.085W [91]; line pitch 0.93 em |
| Serif line | Roman serif, medium, white, soft shadow | Newsreader Medium (wght 500) | Lora, Playfair Display | 0.115W |
| Chip text | Uppercase sans, medium, tracked, near-black | Work Sans Medium | Manrope, Inter | 0.053W; letter-spacing 0.06 em |
| Inset label | Small italic serif, cream | Newsreader Italic | Lora Italic | 0.036W |

Font note: Work Sans and Newsreader were identified by letterform and match the reference closely. Download Work Sans from the Google Fonts GitHub repo (ofl/worksans) if missing.

Rules: case exactly as the user wrote it, except the chip, which is uppercase by style. No outline-only text. Nothing is rotated. Text on footage gets a soft shadow (0, +3 px, blur 6 px, #000000 at 42 % at 61 px type); text on a bar or the page has none.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Card rise | exponential ease-out (1 − 2^(−10u)) from below the page | 0.45 s (opener), most of the move in the first 0.2 s |
| Card expand to full frame | smoother-step in-out (slow start, fast middle) | 0.8 s |
| Card settle (full frame to card) | cubic ease-out | 0.7–1.6 s |
| Slide aside | cubic ease-in, footage moves right off frame | 0.5 s |
| Slide return | exponential ease-out, footage enters from the right | 0.5 s |
| Caption word | ease-out alpha ramp, no movement | 0.08–0.1 s |
| Caption chunk change | hard cut, bar resizes in the same frame | 1 f |
| Title / chip | alpha + 0.012H rise (title); letter-by-letter type-on at 0.065 s per letter (chip) | 0.3 s / 0.5 s |
| Cuts | hard cut inside the card or full frame, no effect | 0 f |

Never: bounce, overshoot, spring, rotation, tilt, glitch, shake, blur, flashes, colour accents, wipes other than the slide, scale pops on captions, effects on cuts.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Cover-fit crop into a rounded card (scale ≥ 0.66, full width kept) | Primary footage plays live in the card, in sync with the audio |
| Growing, shrinking and sliding the footage window | Per the moments; continuous curves only |
| Rising in from the bottom edge at the opener | The speaking face is clear of the page edge by 0.2 s |
| Covering the footage with the cocoa page (D1) | Only on a shot without a speaking face, ≤ 1.2 s per cover, once or twice per video, ≤ 15 % of total duration; the audio keeps playing |
| Inset card of the user's own footage (S1) | A still of the current shot (≤ 1.5 s); never a different person or scene than the user supplied |
| Text, bar, chip, page and tick overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; freezing the primary window; blur, glitch, warp, colour grading or filters of any kind; adding footage the user did not supply.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by the bar, staircase, serif line, chip or inset card; never cut by a card edge. If a face sits at y 0.62–0.78H, move the bar lane to y 0.88H (bar centre) for that shot. |
| Card crop | Keep the whole face box inside the card with ≥ 0.03H margin; shift the vertical window, not the scale. |
| Bar lane | y 0.669–0.731H by default. Never over a face. |
| Serif line | y 0.60H; use y 0.82H if a face sits at 0.50–0.70H. |
| Footage text (signs, UI) | If readable footage text sits in the bar or serif lane for more than 1 s, switch the lane (bar to 0.88H, serif to 0.82H). |
| Edges | Every glyph and bar stays ≥ 0.04W from the left and right edges. |

---

## 7. MOMENT LIBRARY
Family codes: **P** page · **C** caption · **K** card move · **D** dark page · **T** tag · **S** secondary · **X** cut · **E** ending.

### MOMENT P1 · GRID PAGE OPEN
**What it is:** the video opens on an empty cream graph-paper page; the caption bar starts typing first, the italic title fades in above, and the footage rises into a rounded card from the bottom edge.
**Use when:** every video, at the start; the first shot has a person or a main subject. **Avoid when:** the first shot is a face that is already speaking and the page would hide it beyond 0.2 s (then start the rise at t = 0 as in the Motion table).
**Text:** title = one word from the user's own words (the topic word), as written, ≤ 12 characters; omit the title if none fits.
**Geometry / Graphics:** cream page + grid (1.2), Card 1, tick lines, title line (1.3), title in Ink.
**Motion (reference at 30 fps; demo values at 24 fps in brackets):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.5–1.0 [0.0–0.45] | card | y offset | card top 0.67H → 0.315H (card clipped by the page bottom) | exponential ease-out |
| 0.5–1.0 [0.45–0.7] | tick lines | alpha | 0 → 1 | linear |
| 0.6–0.9 [0.35–0.65] | title | alpha, y | 0 → 1, +0.012H → 0 | cubic ease-out |
| hold | card, title, ticks | — | final state | — |

**Footage / plate behaviour:** live footage inside the card; first shot visible from the first frame (the demo started the rise at t = 0 so the face is in view by 0.2 s).
**Captions during it:** C1 bars run from the first spoken word; the first bar may appear before the card.
**Exit:** K1 expands the card over the page.
**Flow prompt text:** "The video opens on a warm cream graph-paper page. The footage rises from the bottom edge into a rounded card in the middle of the page, while a short italic serif title, {{TITLE}}, fades in above it and two thin vertical guide lines appear above and below the card."
**Still-image state:** card settled, title visible.

### MOMENT C1 · LABEL BAR CAPTION
**What it is:** each phrase sits in a cocoa label bar near the lower third; the bar is sized to the whole phrase at once and the words type in from the left, one by one.
**Use when:** always while the footage is in a card or full frame. **Avoid when:** the cocoa page is showing alone (use C2).
**Text:** the user's exact words, case as written. Chunk rules: 2–3 words, ≤ 20 characters at the base size; split at punctuation; never end a chunk on an article, preposition or conjunction; a chunk lasts 0.6–1.4 s; a single long word may stand alone for up to 1.2 s; prefer chunk changes at cuts.
**Geometry / Graphics:** bar per 1.2, text per 1.4, bar width fixed to the full chunk before the first word appears. If the phrase is too wide, shrink the font down to 0.07W, else split.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | new word | alpha | 0 → 1 (0.08 s) | ease-out |
| word start | earlier words | — | unchanged | — |
| chunk end | bar + words | — | replaced by the next bar in the same frame | hard cut |

Word start = the word's spoken start time. Chunk end = next chunk's first word start, or min(last word end + 0.4 s, next mode change).
**Footage / plate behaviour:** untouched; the bar overlays the card or the full frame, centred on x = 0.50W regardless of the card.
**Captions during it:** this is the caption system.
**Exit:** hard cut.
**Build notes:** one sprite per word (2× then downscale); bar pasted at integer pixel positions; measure with `font.getlength` of the whole chunk first.
**Flow prompt text:** "Near the lower third, each short phrase appears inside a dark brown label bar that already fits the whole phrase, and the words appear one by one from the left in clean cream lettering. When a phrase is complete the next phrase replaces it at once. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk in the bar.

### MOMENT K1 · CARD EXPAND
**What it is:** the rounded card swells to the full frame, its corners squaring off, and the page disappears behind it.
**Use when:** the story moves from the setup to the main body; a sentence boundary or a cut ≥ 0.3 s earlier; footage that benefits from full frame (B-roll, products, a face that must be larger). **Avoid when:** within 0.1–0.25 s after a cut; once only per card state.
**Text:** none.
**Geometry / Graphics:** rect interpolates from Card 1 (or Card 2) to the full frame; radius 0.045W → 0.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.6–5.4 [2.35–3.15] | card rect | all four edges | card → (0,0,W,H) | smoother-step |
| same | card | radius | 0.045W → 0 | same |

**Footage / plate behaviour:** live; the crop window opens to the whole frame as the rect grows.
**Captions during it:** bars stay in place.
**Exit:** none (ends in full frame).
**Build notes:** compute scale = max(rect w / W, rect h / H); vertical window offset = clamp(anchor − 0.30 × window height).
**Flow prompt text:** "The rounded video card smoothly grows until it fills the whole frame, its corners straightening, and the cream page disappears behind it."
**Still-image state:** none.

### MOMENT D1 · SLIDE-ASIDE TEXT PAGE
**What it is:** the full-frame footage slides off to the right and a dark cocoa graph-paper page takes over; a white topic chip types in at the top and the phrase appears as a bare staircase of cream words.
**Use when:** a topic word, number or time phrase deserves a beat; a B-roll or object shot without a speaking face (0.8–1.2 s cover). **Avoid when:** a face is speaking in the shot (do not cover it); never twice within 3 s.
**Text:** chip = 1–2 of the user's words in uppercase (≤ 14 characters); staircase = the user's words of the current phrase (C2).
**Geometry / Graphics:** cocoa page + grid, chip (1.2), staircase (1.3).
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 7.05–7.55 | footage | x offset | 0 → +W | cubic ease-in |
| 7.58–8.10 | chip | letters | one by one, 0.065 s per letter | linear |
| word starts | staircase words | alpha | 0 → 1 (0.1 s) | ease-out |

**Footage / plate behaviour:** footage slides out live; the shot keeps playing under the page (audio continues). Cover ≤ 1.2 s.
**Captions during it:** C2 only; no bar on the bare page.
**Exit:** D2.
**Build notes:** the chip box grows with the typed text but its final width is centred on 0.50W; the staircase words are already on screen over the footage when the slide starts and stay fixed while the footage leaves.
**Flow prompt text:** "The picture slides off to the right and reveals a dark brown graph-paper page. A small white tag typing {{CHIP_TEXT}} in capital letters appears near the top, and the words {{CAPTION_WORDS}} appear in cream lettering as a staircase, each line starting a little further right."
**Still-image state:** dark page, chip and staircase.

### MOMENT D2 · SLIDE RETURN
**What it is:** the footage glides back in from the right edge and fills the frame.
**Use when:** ends a D1 cover; the cut to the next shot may happen under the page. **Avoid when:** without a preceding D1.
**Text:** none.
**Geometry / Graphics:** full-frame footage.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 8.42–8.92 | footage | x offset | +W → 0 | exponential ease-out |

**Footage / plate behaviour:** live. If a footage cut falls under the page, the new shot slides in; start the slide ≥ 3 f after the cut.
**Captions during it:** C1 may start on the first word after the slide begins.
**Exit:** settles in full frame; K2 may follow.
**Build notes:** same renderer as D1 with the sign reversed.
**Flow prompt text:** "The picture glides back in from the right edge until it fills the frame again."
**Still-image state:** none.

### MOMENT K2 · CARD SETTLE
**What it is:** the full-frame footage shrinks back into a rounded card on the cocoa page.
**Use when:** after D2 or at the closing line, to finish on the card look. **Avoid when:** a face would be cut by the card crop.
**Text:** none.
**Geometry / Graphics:** full frame → Card 2; radius 0 → 0.045W.
**Motion:**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 8.95–9.65 | rect | all edges | full → Card 2 | cubic ease-out |

**Footage / plate behaviour:** live.
**Captions during it:** C1 bar stays fixed on the page.
**Exit:** holds as a card.
**Build notes:** window offset uses the face anchor (0.30 of the card height).
**Flow prompt text:** "The picture shrinks smoothly into a rounded card sitting on a dark brown graph-paper page."
**Still-image state:** Card 2 on the cocoa page.

### MOMENT T1 · TOPIC CHIP
**What it is:** a small white tag that types a topic word in capitals, with a tiny asterisk icon.
**Use when:** a topic, step name or number is introduced on the cocoa page. **Avoid when:** more than 14 characters; it never appears over footage.
**Text:** user's word(s), uppercase.
**Geometry / Graphics:** chip per 1.2.
**Motion:** letters appear one by one, 0.065 s per letter; hold until the page ends.
**Footage / plate behaviour:** none (cocoa page only).
**Captions during it:** C2 below.
**Exit:** covered by D2.
**Build notes:** pre-render one sprite per letter count; draw the icon as four crossing lines.
**Flow prompt text:** "A small white rectangular tag near the top types out {{CHIP_TEXT}} in capital letters, with a tiny asterisk before it."
**Still-image state:** the full tag.

### MOMENT C2 · BARE STAIRCASE
**What it is:** the phrase appears word by word as cream lettering with no bar, each line starting further right than the one before.
**Use when:** during D1, or over full-frame B-roll for a short phrase. **Avoid when:** on a speaking face shot, or over bright footage (use C1).
**Text:** user's words; 1–2 words per line, ≤ 3 lines.
**Geometry / Graphics:** Staircase (1.3), font per 1.4; shadow on footage.
**Motion:** word alpha 0 → 1 over 0.1 s at each word start; the whole phrase stays until the page ends; no movement.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut with the next phrase or D2.
**Build notes:** lay out all lines before the first word; line k start = start(k−1) + 0.5 × width(k−1), right edge clamped to 0.92W.
**Flow prompt text:** "The words {{CAPTION_WORDS}} appear one by one in cream lettering without any box, stepping down and to the right line by line."
**Still-image state:** whole phrase.

### MOMENT C3 · SERIF LINE
**What it is:** a short phrase in white roman serif, one word after another, centred below the middle of the frame.
**Use when:** a payoff or contrast phrase of 1–3 words deserves a quieter, editorial beat on full-frame footage; max 2 per video. **Avoid when:** over bright footage or a face at 0.50–0.70H.
**Text:** user's words, ≤ 18 characters.
**Geometry / Graphics:** Serif line (1.3), font per 1.4, soft shadow.
**Motion:** each word alpha 0 → 1 and +0.012H → 0 over 0.2 s (cubic ease-out); phrase holds; hard cut at the end.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the bar for its duration.
**Exit:** hard cut.
**Build notes:** same sprite method as C1.
**Flow prompt text:** "Near the middle of the frame, the words {{CAPTION_WORDS}} fade up one by one in a refined white serif, then are replaced by the next caption."
**Still-image state:** the phrase.

### MOMENT S1 · INSET CARD
**What it is:** a small rounded card of the user's own footage slides up beside the staircase on the cocoa page, with a tiny italic label.
**Use when:** during D1, to show what the line is about. **Avoid when:** the user has no related shot (skip it).
**Text:** label = one of the user's words, as written.
**Geometry / Graphics:** inset card and label (1.2); the card shows a still of the current shot, cover-fit.
**Motion (demo 7.66–8.02 s):** card rises 0.6 × (H − y) → rest position, cubic ease-out, 0.36 s; label alpha with it; covered by D2.
**Footage / plate behaviour:** still of the shot (≤ 1.5 s).
**Captions during it:** C2 above it.
**Exit:** covered by D2.
**Build notes:** grab the still from the frame at the middle of the cover.
**Flow prompt text:** "A small rounded card showing a still from the footage slides up on the right of the dark page, with the word {{LABEL}} written under it in tiny italic letters."
**Still-image state:** the card with its label.

### MOMENT X1 · CUT IN CARD
**What it is:** the footage changes with a plain hard cut while the card, page, title and bar stay exactly where they are.
**Use when:** every cut while the footage is in a card or full frame. **Avoid when:** never add an effect.
**Text:** none.
**Motion:** hard cut; crop anchor switches to the new shot's subject on the same frame; a chunk change is preferred on the cut frame.
**Footage / plate behaviour:** untouched; no big move starts within 3 f of the cut; a cut under the cocoa page (D1) is hidden by it.
**Captions during it:** per C1.
**Exit:** none.
**Build notes:** anchor table per shot (face y and frac).
**Flow prompt text:** "At each cut the picture inside the card simply changes to the next shot with no effect; the page and the captions stay where they are."
**Still-image state:** none.

### MOMENT E1 · END HOLD
**What it is:** the closing card or full frame holds with the last bar until just before the end.
**Use when:** every video. **Avoid when:** never.
**Text:** last chunk.
**Motion:** the bar holds to min(last word end + 0.4 s, end − 0.08 s); the page and card stay still.
**Footage / plate behaviour:** live to the last frame.
**Captions during it:** per C1.
**Exit:** video ends.
**Build notes:** none.
**Flow prompt text:** "The last caption stays in its bar until the very end while the card holds still on the page."
**Still-image state:** final card.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | P1 + C1 | X1 on every cut; K1 at the first sentence boundary; C3 on a payoff; D1 on a B-roll shot with a topic phrase | D2 + K2 + E1 |
| Single talking head, no cuts | P1 + C1 | K1 after the first sentence; D1 only if the shot has no speaking face (skip otherwise); C3 on one phrase | K2 + E1 |
| B-roll only, no speech | P1 (user's title words, if any) + C1 | X1 on every cut; D1 with S1 on one shot; C2 phrases | D2 + E1 |
| Still image + text | P1 settled (card of the image), bar with the text | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

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
