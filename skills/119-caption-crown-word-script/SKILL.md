---
name: 119-caption-crown-word-script
description: Applies the "Crown Word Script" motion-graphics caption style (one heavy condensed uppercase keyword with a thick black outline popping in above the speaker's head, plus flowing white script captions with a thin black outline that build word by word at lower left, footage untouched and full-frame) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants bold keyword headlines over the head, handwritten-style white captions, creator or vlog caption looks.
---

# 119-caption-crown-word-script — Crown Word Script

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

Ask missing inputs in one message (max 3 short questions), stop and wait. Keep asking until every required input is in hand.

### 2.2 The one output question

Only after all inputs are in, ask exactly one question unless already answered: **"Do you want me to make the final video for you, or give you a master prompt for Google Flow (you paste it into Flow with your video)?"** For an image: "final image or Flow master prompt". If inputs and the output choice come in one message, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

3.1 **Footage is sacred.**
- Allowed transforms (moments.md 1.6): full-frame display, untouched; text, outline and shadow overlays only.
- The primary footage plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, frames, blur, glitch, zoom, flashes, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Crown words are shown in UPPERCASE (the one case change this style makes); script captions keep the user's case. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all script chunks reproduces the user's text word for word and in order. Crown words are repeats of words already in the script chunks, never new words. Run the audit before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only for chunk changes and crown-to-crown swaps (hard by design).
- Footage cuts get no effect: the style adds nothing on a cut. A crown word and a script chunk may run across a cut unchanged.
- Never start a crown pop within 0.1 s after a cut if the shot changes the head position; keep a crown word off the head (1.7).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md. Never: boxes or plates behind text, typing letter by letter, slides, bounce or overshoot beyond the 1.00 settle, rotation, glitch, shake, flashes, lowercase crown words, more than one crown word at a time, centred script captions, extra colours.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect cuts with `select='gt(scene,0.3)'`; retry 0.12–0.2 if none; confirm visually.
- View 2–4 frames per scene. Build the scene table:

| Scene | Start–End | Shot type | Subject | Head top y and head x range | Face bottom edge | Lane (0.74–0.86H) luminance and detail |
|---|---|---|---|---|---|---|

- Speech timing: speech-to-text word timestamps only to time the user's words, else `silencedetect=n=-30dB:d=0.12` plus syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones per scene.** Crown band must end ≥ 0.02H above the head top (1.7); decide per shot the crown centre x (centre, or the side away from the head). Caption lane: default baseline 0.805H; shift up only if it would cover a speaking mouth.

**Step 3 — Caption chunks.** 3–5 words per chunk, one line, width ≤ 0.84W; split at punctuation; never end on an article, preposition or conjunction; chunk starts at its first word, ends at the next chunk's first word (or last word end + 0.4 s). Output `# | Start–End | Text | x anchor`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence | T1 on the topic word, C1 |
| Theme or topic word | The noun the video is about | T1 |
| Contrast or turn | "but", "isn't", "never", "instead" | T1 on the turn word |
| Steps or list | 3+ parallel phrases | T1 relay (T3), one crown word each |
| Numbers, amounts, time phrases | Digits, "one year" | T1 on the number or time word |
| Cut person ↔ B-roll | Scene table | T4 side crown if the head moves, otherwise nothing |
| Payoff or call to action | Last line | T1 on the payoff word, E1 |
| Long pause or calm shot | > 1.5 s without a crown word | C3 or T1 on a quiet keyword |

**Step 5 — Choose moments.**
- Mandatory in every output: **T1** (crown words, at least 4 per 10 s of speech), **C1** (script build on every spoken phrase), **T2** (soft crown exit). Unless physically impossible.
- A visible change every ~1.5–3 s. One crown word at a time; gap between crown words 0.1–0.25 s; each crown word holds 0.7–1.6 s.
- Choose crown words: the meaning-carrying noun or verb of each phrase; never articles, prepositions or fillers.
- Output the plan table `# | Moment ID | Start–End | ✎ Text | ✎ Position | Reason`.

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: crown clear of the head, script inside the frame (≥ 0.06W from the edges), nothing over a speaking mouth.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Draw text at 2× and downscale. Measure with `font.getlength` before laying out a chunk; lay out the whole chunk first so no word moves after it appears.
- Download fonts from the Google Fonts GitHub repo if missing, else use the fallbacks.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.** Contact sheet at 3–4 fps plus frames around every crown pop and chunk change. Look at them. Checklist: captions correct and in order; crown words uppercase with outline; only one crown word at once; head and mouth clear; no word moves after it appears; footage in sync; duration, fps, resolution and audio match; signature moments present. Fix and re-render.

**Step 9 — Deliver.** Save as `<original name>_crown_word_script.mp4`. Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

Use the settled states: one crown word above the head (T1 final), one script chunk in the lower-left lane (C1 complete). Never alter the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP · 3 STYLE (plain words) · 4 TEXT INVENTORY (every allowed word, ending "Nothing else is written anywhere.") · 5 TIMELINE (`[start–end s] MOMENT NAME. <Flow prompt text, filled>`) · 6 CAPTIONS (every line with its time range) · 7 NEGATIVE (changing the person, face, outfit or background; new scenes; reordered shots; changed audio; extra or misspelled text; boxes behind text, glitches, flashes, bouncing or spinning text, camera shake). Plain words only. Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

Plan scenes from the story, time the captions, choose moments. Final video: a typography-only piece on a plain plate in the user's palette (crown words and script chunks, hard cuts). Image: a typography poster, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never cover, cut or blur a speaking face with a crown word or caption.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects on cuts or any effect not in moments.md.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
