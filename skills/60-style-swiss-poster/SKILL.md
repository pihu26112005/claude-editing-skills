---
name: 60-style-swiss-poster
description: Applies the "Swiss Poster" motion-graphics style (strict six-column grid with hairlines and dots, footage locked into grid modules on a Swiss-red or warm-paper field, huge tight flush-left bold grotesk captions, giant step numerals, one red circle, and a left-to-right column swap on every cut) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a Swiss, International Typographic, poster, red grid, Helvetica-style or minimal bold-type look.
---

# 60-style-swiss-poster — Swiss Poster

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
- Allowed transforms (moments.md 1.6): cover-fit crop into a grid module with the crop anchor on the subject; the red or paper field rising over the lower part of the frame (T1); hairline grid, dots and the red circle drawn over the footage.
- The primary module always plays the current footage in real time, in sync with the audio. There are no secondary footage windows.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, zoom punches, flashes, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote. The only numerals are step digits for real list items and the "01 / 06" shot counter.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks reproduces the user's text word for word and in order. Run it before building.

3.3 **Smooth, no breakdowns.**
- Continuous curves from moments.md; hard switches only on footage cuts, and for caption words and chunks (hard cuts by design).
- Every element enters with its moment's motion; nothing blinks; no black or empty areas.
- No big move within 3 frames after a cut except X1 itself; X1 is the only thing that starts on a cut.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md. Never: bounce, overshoot, rotation, shadows, blur, glow, flashes, letter-by-letter typing, gradients, uppercase conversion, a second accent colour, rounded corners, cards with borders, more than one circle per layout.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and cuts as a thin black line sweeping left to right.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each visually.
- Look at 2–4 frames per scene.
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h fractions) | Subject bounds | Best layout (P1/P2/P3/E1) | Crop anchor |
|---|---|---|---|---|---|---|---|

- Speech timing: speech-to-text word timestamps only to time the user's own words; otherwise `silencedetect=n=-30dB:d=0.12` plus syllable-weighted spreading (0.15 s pause at commas, 0.3 s at full stops). No speech: spread phrases across each shot (1.0–2.5 s each).

**Step 2 — Layout plan per scene.** Pick the layout whose module keeps the face and subject whole (moments.md 1.7). Talking head → P1 (or E1 last). List steps → P2 and P3 alternating, each with N1. Other B-roll → P2, P3 or P1 so that no two neighbouring shots share a layout.

**Step 3 — Caption chunks.**
- 3–5 words, ≤ 3 lines at the layout size, split at punctuation, never end on an article, preposition or conjunction, prefer starting a chunk at a cut; start = first word start, end = min(last word end + 0.1, next start − 0.05), minimum 0.4 s.
- One keyword per chunk at most, ≤ 5 per 10 s.
- Output the caption table `# | Start–End | Text | Keyword`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1, P1, C1 |
| Theme or topic word | The noun the video is about | keyword in C1 |
| Contrast or turn | "but", "isn't", "instead", "never" | keyword, X1 |
| Person → B-roll cut | Scene table | X1 into P2 or P3 |
| B-roll → person cut | Scene table | X1 into P1 or E1 |
| Any later cut | Scene table | X1 with a new layout |
| List or steps | "first", "second", 3+ parallel phrases | N1 per step on P2/P3 |
| Numbers, amounts, time phrases | Digits, "one year" | keyword |
| Long static shot (> 2.5 s) | Scene table | K1 re-pop or layout change at a sentence boundary |
| Section change without a cut | Pause, new topic | X1 at the sentence boundary (the footage module re-lays) |
| Payoff or call to action | Last line | E1 |

**Step 5 — Choose moments.**
- Mandatory in every output: **T1** (opener), **C1** (captions), **X1** (every cut), **K1** (one circle per layout), **M1**; **N1** when the video has a list; **E1** for the last line when it is ≤ 5 words.
- A visible change every ~1.5–3 s. Never two layout changes within 0.6 s.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each spec; change only ✎ fields. Check every frame of the plan: faces inside the module, captions inside the field and ≥ 48 px from the edges, circle not on a face, numeral not touching the caption.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Draw grid, dots and circles at 2× or 4× and downscale; cache the finished grid overlay. Pre-lay-out every chunk per layout before its first word. Measure text with per-character advances plus tracking.
- Fonts: Inter variable (weight 800 captions, 900 numerals, optical size 32); download from the Google Fonts GitHub repo if missing, else the fallbacks.
- Cover-fit module crops, anchor clamped inside the scaled frame.
- X1: render old and new layout for the same frame and paste the new columns up to the edge.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Contact sheet at 1–1.5 fps, plus frames around T1 and every cut. Look at them.
- Checklist: captions correct, in order and readable on their field; keyword colours right per field; no word moves after it appears; numerals match the list order; faces inside modules; grid and dots visible but quiet; footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** `<original name>_swiss_poster.mp4` (claude.ai: `/mnt/user-data/outputs/`); a brief reply with the compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

Use P1: image cover-fit into the top 60 %, red field below with the text as a C1 stack (all words visible), grid overlay, circle, rail. Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s, split at cuts; add a CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio exactly as they are. Only add…") · 2 INPUT VIDEO MAP (scene by scene with timestamps) · 3 STYLE (plain-words paragraph of the look) · 4 TEXT INVENTORY (every allowed word, tricky words spelled letter by letter, the step digits) · 5 TIMELINE (each moment's Flow prompt text with its time and words) · 6 CAPTION TABLE with times · 7 AVOID (new footage, other fonts or colours, bounce, shadows, extra words) · 8 SRT backup. Plain words only: no px, %, hex codes or font names.

## 7. GENERATE MODE (C1)

Plan scenes from the story, time the captions, choose moments. Master prompt → section 6 with story scenes. Final video → a typography-and-grid-only piece rendered in code (red and paper pages with numerals, circle, captions; no fake footage). Image → a typography poster in code.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim; never desync the primary module.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen or let an AI model draw captions in edit or still mode.
- Never break the style's "never" items (3.4) or invent moments.
- Never ask beyond missing inputs plus the one output question.
- Never deliver without looking at the rendered frames.
