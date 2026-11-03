# Google Flow prompt · App World
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "App World" motion style to it.

The look in one sentence: A phone mock-up beside the speaker, a frosted checklist that ticks off steps, a white app dialog that types your line, and a dark app screen with a live progress timer behind the cut-out speaker; bold white captions with one pink word.

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
| GLASS | `#2A2624` at 68 % over a blur of the footage (lighter washes out on bright shots) | frosted cards (checklist, phone body tint) |
| PAPER-UI | `#FFFFFF` | app dialogs, input fields |
| UI-INK | `#1C1A19` | text inside white UI |
| UI-MUTED | `#8E8A86` | secondary UI text, empty checkboxes, skeleton lines |
| PINK | `#F4A7B9` | the one accent: checked boxes, buttons, progress fill, the caption key word |
| PINK-DEEP | `#E8708F` | pressed button, progress bar end |
| NIGHT | `#1D1517` | the dark app screen of A4 |
| CAPTION | `#FFFFFF` | captions, with a soft dark shadow |

No other accent colour. Brand variant: PINK may become one brand colour; everything else stays neutral.

### 1.2 Containers
- **Card:** rounded rectangle, radius 0.035 W [38 px], 1 px inner hairline `#FFFFFF` at 14 % on glass / `#E8E6E1` on white, soft shadow 0 / +0.012 H, blur 0.03 W, black 28 %.
- **Frosted glass:** the footage behind the card, Gaussian-blurred (radius 0.025 W) and darkened with GLASS. Never a flat grey.
- **Phone:** rounded rectangle 9:19.5, radius 0.045 W, black bezel 0.008 W, a small notch pill; the screen is a white or NIGHT app page.
- **Skeleton lines:** UI chrome that would need invented words is drawn as rounded grey bars (UI-MUTED at 35 %), never as fake text.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Caption | bold geometric sans, sentence case, two lines max | Inter Bold (wght 700) | Plus Jakarta Sans Bold, Arial Bold | 0.042 H [81 px] |
| Caption key word | same, PINK | same | same | same |
| Card title | small caps label, letter-spaced 0.12 em | Inter SemiBold | same | 0.016 H [31 px] |
| Card item / UI text | medium sans | Inter SemiBold (wght 600) | same | 0.022 H [42 px] (smaller reads poorly in shared GIFs and phone feeds) |
| Timer / counters | tabular monospace digits | JetBrains Mono SemiBold | IBM Plex Mono | 0.024 H [46 px] |
| Label caption (A6) | uppercase, letter-spaced 0.08 em, white→PINK gradient | Inter ExtraBold | same | 0.026 H [50 px] |

All words are the user's words. UI chrome without user words uses icons, numbers or skeleton bars.

### 1.4 Motion language
- **Arrive:** slide 0.04 H + fade, ease-out-cubic, 8–10 f; tiny overshoot allowed only on the phone (A1), 3 %.
- **Fill:** checkboxes pop PINK with a 6 f scale 70 → 110 → 100 %; progress bars fill linearly; typed text appears 2 letters per frame.
- **Leave:** fade + 0.02 H drift up, ease-in-quad, 6 f.
- **Dark-screen fade (A4):** background darkens over 10 f; the person stays.
- UI pieces never rotate, never bounce more than 3 %, never cover a face.

### 1.5 What may happen to the user's footage
- Default: footage stays full-frame and untouched; UI floats over it.
- A1 phone and A3 dialog may show **the user's own footage** (a still or a live inset of the current frame) inside their screens.
- A4 replaces the **background behind the person** with NIGHT, only with a clean person matte, max 2.5 s per use and 25 % of the video. Without a clean matte, use A4-CARD: shrink the footage into a rounded card on NIGHT instead.

### 1.6 Safe zones
- Face box: never covered by any card, caption or phone.
- Top zone (0.06–0.30 H): checklist and dialogs. Side zone (outer 0.30 W at chest height): phone. Bottom zone (0.72–0.86 H): captions.
- If the face is in the top zone, cards go in the bottom zone and captions move to 0.62 H.

---

## 7. MOMENT LIBRARY
Family codes: **UI** (interface pieces), **CAP** (captions), **CUT** (scene treatment). Energy:  low ·  medium ·  high.

### A1 · PHONE MOCK-UP — UI  (signature)
**What it is:** A phone slides in beside the speaker at chest height showing an app page made from the user's own footage.
**Use when:** a person shot where the line names a result, a profile, a product, "all you need is…".
**Text:** title on the screen = 1–3 user words. Other rows = skeleton bars or numerals.
**Geometry:** phone 0.25 W wide, centred x 0.80 W (side away from the face), centre y 0.52 H. Screen: white page; top a round avatar (still of the speaker), the title in UI-INK bold, a PINK pill button (no text, or one user word), a 3×2 grid of thumbnails from the user's other shots.
**Motion:** slide in from +0.08 W with 3 % overshoot, 10 f; gentle float ±0.004 H (sine, 2 s period) while on screen; leave 6 f.
**Flow prompt text:** "A small smartphone slides in beside the person at chest height, showing a clean white app page with a round photo of them, the words \"{{TITLE}}\", a soft pink button and a grid of small thumbnails from the video. It floats gently and never covers the face."

### A2 · GLASS CHECKLIST — UI  (signature for lists)
**What it is:** A frosted-glass card at the top with a small letter-spaced title and 2–4 items; each item's circle fills PINK with a check as it is spoken.
**Use when:** the captions list steps, rules or tips.
**Text:** title = 1–3 user words (UPPERCASE); items = each item's user words, ≤ 22 characters; a counter "1 of 3" in numerals.
**Geometry:** card x 0.06–0.94 W, top 0.07 H; row height 0.05 H; checkbox circle 0.026 H; PINK fill + white tick when done; done items stay full white, pending items UI-MUTED.
**Motion:** card arrives 10 f; the counter updates on each tick; card stays across cuts until the list ends, then leaves 6 f.
**Flow prompt text:** "A frosted glass card floats at the top of the frame with a small spaced title \"{{TITLE}}\" and a short checklist: {{ITEMS}}. As each item is said, its circle fills soft pink with a tick."

### A3 · APP DIALOG — UI  (signature middle)
**What it is:** A white app window drops from the top: first an empty drop zone, then a confirmation line with thumbnail clips of the user's footage, then the user's words typing into an input with a PINK send button.
**Use when:** a B-roll shot or a line describing an action ("do it", "add", "send", "start").
**Text:** confirmation = 1–4 user words with a ✓; typed input = the spoken line (≤ 30 characters).
**Geometry:** card x 0.06–0.94 W, top 0.06 H, height 0.21 H; thumbnails 0.13 W wide, 4:3; input bar with PINK round send button at its right.
**Motion:** drop in 10 f; drop zone (dashed outline) 0.4 s → swap to the confirmation row with thumbnails sliding in 3 f apart → typing 2 letters/frame → send button pulses PINK-DEEP on the last word; leave 6 f.
**Flow prompt text:** "A clean white app window drops in at the top. Small thumbnails of the video slide into it, then the words \"{{TYPED}}\" type into a text box and a soft pink send button pulses."

### A4 · DARK APP SCREEN — CUT  (signature closer)
**What it is:** The room fades to a deep plum-black app screen; the speaker stays cut out in front. A glass card at the top shows a running task with a countdown timer and a PINK progress bar.
**Use when:** the payoff / CTA / the line where "the work happens".
**Text:** task title = 2–5 user words; timer = numerals counting down to 00:00.
**Geometry:** NIGHT fills the background with a soft vignette; card x 0.06–0.94 W, top 0.03–0.07 H (as high as needed to clear the head), height 0.105 H; timer right-aligned; progress bar 0.006 H tall at the card bottom.
**Motion:** background fade 10 f; card arrives 8 f later; timer counts down and the bar fills linearly over the card's life; at the end the bar flashes PINK-DEEP once.
**Fallback A4-CARD:** if the matte is poor, the footage shrinks (12 f, ease-in-out) into a rounded card 0.80 W wide centred at 0.58 H on NIGHT, card on top as above.
**Flow prompt text:** "The room behind the person fades to a deep dark plum app screen while they stay in front. At the top a frosted card shows \"{{TASK}}\" with a timer counting down and a soft pink progress bar filling."

### A5 · BOLD CAPTIONS — CAP (always on)
**What it is:** Two-line bold white captions in the lower third; one meaning word per chunk is PINK.
**Text:** user's words verbatim, chunks of 2–6 words split over max 2 lines (≤ 18 characters per line).
**Geometry:** centred x; baseline of line 2 at 0.835 H (0.62 H if the face is low, or just above a bottom card); shadow 0 / +0.003 H, blur 0.01 W, black 65 % with a 2 px dark stroke so pink stays readable on bright footage.
**Motion:** each chunk fades in over 4 f with a 0.01 H rise; swaps instantly on the next chunk.
**Flow prompt text:** "Bold white captions in two short lines near the bottom, one key word in soft pink. The ONLY caption lines, in order, are: [a-b s] \"{{CHUNK_1}}\", …"

### A6 · LABEL CAPTION — CAP  (accent)
**What it is:** A single uppercase letter-spaced line with a white-to-pink gradient, used once for a punchy 2–4-word phrase (e.g. "SPEND → SAVE").
**Text:** 2–4 user words; an arrow "→" allowed between them.
**Geometry / motion:** baseline 0.86 H; letters reveal left to right over 8 f.
**Flow prompt text:** "One short line \"{{LABEL}}\" in spaced-out bold capitals fading from white to soft pink appears near the bottom."

### A7 · SLOW PUSH — CUT  (extension)
Footage scale 100 → 104 % linear over a shot longer than 1.5 s with no other UI arrival. Never during A4.
**Flow prompt text:** "The shot drifts in very slowly."

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll list → talking head | A1 phone on the first line | A2 checklist ticking through the list across cuts; A3 dialog on an action line over B-roll | A4 dark app screen on the payoff |
| Single talking head | A1 phone | A2 checklist, A6 label | A4 |
| B-roll / product only | A3 dialog | A2 checklist, A7 push | A4-CARD |
| Still image | A1 phone beside the subject + one A5 caption | — | — |

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
