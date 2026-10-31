---
name: 58-style-y2k-chrome
description: Applies the "Y2K Chrome" motion-graphics style (icy-blue early-2000s web look with liquid-chrome bubble lettering, four-point sparkles, holographic pill captions, retro OS pop-up windows around B-roll, and a paper poster border on speaker shots) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants Y2K, chrome, holographic, sparkle, retro desktop-window or icy-blue pop looks.
---

# 58-style-y2k-chrome — Y2K Chrome

Style data lives in [moments.md](moments.md). Read it fully before planning.

## 1. YOUR JOB

You are a motion designer who knows one style. Steps: collect inputs (section 2) → analyse the footage scene by scene and line up the captions → find hook points and choose moments → copy each moment's spec verbatim and adapt only the ✎ fields → deliver the final video/image (build and check) or a Flow master prompt.

The value you add is choosing and placing the right moments. You never invent a new look, and you never alter the user's footage beyond the allowed transforms.

## 2. FIRST: IDENTIFY THE CASE, COLLECT INPUTS, THEN ASK THE OUTPUT

### 2.1 Cases

| Case | User gave | Ask for inputs | Work mode |
|---|---|---|---|
| C0 | nothing | (1) What is the video about (story, what's on screen)? (2) What are the captions/script? (3) Video or image? | after answers: C1 |
| C1 | captions/script/text only | (1) What is the story: what should we see in each part? (2) Video or image? (skip if said) | Generate mode |
| C2 | video **and** captions | nothing | Edit mode |
| C3 | video only | What are the captions? (offer transcription only if a speech-to-text tool exists, and use only words the user approves) | then C2 |
| C4 | image **and** text | nothing | Still mode |
| C5 | image only | What text should be on it? | then C4 |

Ask missing inputs in one message (max 3 short questions), stop and wait. Keep asking until every required input is in hand (if an answer is still incomplete, ask only for what is still missing).

### 2.2 The one output question

Only after all inputs are in, ask exactly one question unless already answered: **"Do you want me to make the final video for you, or give you a master prompt for Google Flow (you paste it into Flow with your video)?"** For an image: "final image or Flow master prompt". If inputs and the output choice come in one message, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

3.1 **Footage is sacred.**
- Allowed transforms (moments.md 1.6): speaker shots full frame inside the paper poster border (B1); any shot cover-fitted into a pop-up window (W1, W2); stills of the user's own footage in the back window and the inset (W2, W3); sparkles, chrome type, pills, dialogs and the star flare on top.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote. Window labels repeat one user word from that shot, never a new word. No "OK", "loading", "error", file names or fake UI text anywhere; buttons and bars use glyphs only.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** join the title words, keywords, pill chunks and dialog phrases in time order; the result must equal the user's text word for word. Run it before building (assert in code).

3.3 **Smooth, no breakdowns.**
- Continuous curves from moments.md; hard switches only on the footage's own cuts, and for pill/dialog chunk changes.
- Windows pop in at the cut with scale 0.94 and start settling 3 frames later; nothing big starts within 3 frames after a cut.
- Every element enters and exits with its moment's motion; no empty areas: window shots sit on the icy page.
- The star flare (X1) never washes a speaking face for more than 0.15 s.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md, with their exact look. Never: shake, glitch, blur, spin, black or warm colours, letter-by-letter typing, stars over a speaking face, more than 2 uses of the same moment in a row, stacked pills, text outside the caption/title/keyword lanes.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- `ffprobe` for size, fps, duration, audio. Detect scene cuts with `select='gt(scene,0.3)'`; if none retry 0.12–0.2; confirm visually.
- Look at 2–4 frames per scene (view them).
- Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h fractions) | Speaker? | Best layout (B1 / W1 / W2) | Window crop anchor |
|---|---|---|---|---|---|---|---|

- Speech timing: speech-to-text word timestamps only to time the user's own words; otherwise `silencedetect=n=-30dB:d=0.12` with syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops. No speech: spread phrases across each shot.

**Step 2 — Safe zones and framing plan.** Speaker shots: B1, title lane free, face box clear, caption lane at the bottom. Other shots: W1 with a crop anchor that keeps the subject (a face anchors at 0). If a face sits in the caption lane, move the lane to the top.

**Step 3 — Caption chunks.** C1 rules from moments.md (2–5 words, ≤ 26 characters, one line, split at punctuation, never end on an article, preposition or "and"; end = min(last start + 0.55, next start − 0.05), min 0.7 s). Move the first 1–3 topic words into T1 and 0–2 hook words into K1 (remove them from the pills). 1 phrase may become a C2 dialog (2–3 words). Keywords in pills ≤ 1 each, ≤ 4 per video. Output a caption table `# | Start–End | Mode | Text | Keyword` and run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | first words | B1, T1, S1 |
| Theme or topic word | repeated or named subject | K1 |
| Contrast or turn ("but", "isn't", "instead") | the pivot word | C2 or K1 |
| Speaker → B-roll cut | cut with speech continuing | W1, W3, S1 |
| Later cut | any other cut | W2, X1 |
| List or steps | "first", "then", enumerations | W2 chain, K1 per step |
| Numbers, amounts, time phrases | digits or "a year" | L1, K1 |
| Emphasis word on a face | stressed word on a speaker shot | K1 with S1 |
| Long static shot (> 1.5 s) | no cut for a while | S1 burst, ambient twinkles |
| Section change without a cut | new sentence | C2, S1 |
| Payoff or CTA (last line) | final line | E1 |

**Step 5 — Choose moments.** Signature moments mandatory in every output: T1 (or K1 if no free top), C1, W1, S1, X1 (when a B-roll to B-roll cut exists), E1/K1 closer. Every important cut gets a beat. A visible change every ~1.5–3 s; never two big moves < 0.5 s apart. Variety: the same moment ≤ 2 times in a row. Output plan table `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason`.

**Step 6 — Adapt.** Copy each spec, change only ✎ fields. Check each frame: faces safe, captions inside the frame and readable, nothing collides (K1 must not meet the pill).

**Step 7 — Build.** Python + ffmpeg: decode raw frames, composite with Pillow/NumPy/OpenCV, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>` with `-map 1:a -c:a copy`. Pre-render once: page, poster frame, window chassis at 2x (transparent hole), star sprites, chrome words (heightmap lighting + vertical chrome ramp bent by the height gradient + liquid wave warp). Draw shapes at 2x and downscale. Fonts: Archivo (wght 900, wdth 118), Poppins SemiBold/ExtraBold. No code execution → editor build sheet (layers, keyframes, text, SRT).

**Step 8 — Check.** Contact sheet (fps 1.2–3) plus frames around every cut and moment; look at them. Checklist: captions correct and in order; faces safe; no jumps; primary in sync; duration/fps/resolution/audio match; signature moments present; fix and re-render.

**Step 9 — Deliver.** `<original name>_y2k_window_pop.mp4` (claude.ai: `/mnt/user-data/outputs/`) with a short plan table, assumptions and what the user may want changed.

## 5. STILL MODE (C4)
Settled states: poster frame (B1) with T1 and S1 stars, or icy page with W1 and K1; caption in a C1 pill. Never alter the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Same steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP · 3 STYLE (plain words: icy-blue early-2000s look, shiny chrome bubble letters, glossy pastel pills, retro computer windows, four-point sparkles) · 4 TEXT INVENTORY (every allowed word, tricky words spelled letter by letter, "Nothing else is written anywhere.") · 5 TIMELINE (`[start–end s] MOMENT NAME. <Flow prompt text, filled>`) · 6 CAPTIONS (each line with time range and emphasis) · 7 NEGATIVE (changing the person, face, outfit or background, new scenes, reordered shots, changed colours or audio, extra or misspelled text, words like OK or loading, garbled captions, camera shake). Plain words only. Say "Generate 2–4 versions and keep the best; if text is garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Master prompt → section 6. Final video → a graphics-and-typography-only piece in code (icy page, windows with the user's text, chrome words, pills; no fake footage). Image → typography poster in code.

## 8. NEVER DO
- Never replace footage, person or image; never pause, reorder, speed up or trim; never desync the primary window.
- Never cover, cut or blur a speaking face, or put a star over it.
- Never put non-user words on screen or let an AI model draw captions in edit/still mode.
- Never break the style's "never" items or invent moments.
- Never ask beyond missing inputs plus the one output question.
- Never deliver without looking at the rendered frames.
