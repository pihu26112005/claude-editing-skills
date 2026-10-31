---
name: 38-style-aqua-glass-stage
description: Applies the "Aqua Glass Stage" motion-graphics style (footage in rounded frosted-glass cards on a sky-blue gradient or a white stage with pink and blue diagonal slabs, cards that glide between layouts on every cut, small frosted caption chips with one bold italic keyword, and a gradient outline that grows around the speaker) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a glassmorphism, frosted glass, blue gradient, app-like or soft pastel stage look.
---

# 38-style-aqua-glass-stage — Aqua Glass Stage

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
- Allowed transforms (from moments.md 1.6): scale, move and cover-fit crop of the primary footage into a rounded card; glass ring, shadow and rounded mask; a secondary card holding a still of a neighbouring shot, a silent loop ≤ 1.5 s or another crop of the user's own footage; blur only inside caption chips; M1 push ≤ 1.06 per shot.
- The primary card always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; colour grading or filters on the footage; blurring or covering a face; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote, except titles (uppercase by design). Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining the title words and all caption chunks reproduces the user's text word for word and in order. Run it before building.

3.3 **Smooth, no breakdowns.**
- Layout changes are continuous morphs (ease-in-out, 0.35–0.45 s); the footage itself changes only on its own cuts, on the first frame of a morph.
- Caption chunks replace each other in one frame; every other element enters and exits with its moment's motion; nothing blinks; no empty or black areas.
- Never start a caption chunk inside the first 3 frames of a morph, and never start a title within 0.3 s after a cut.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, spring, tilted or rotated cards, shake, glitch, flashes, wipes over the footage, letter-by-letter typing, extra colours, a face behind a chip or title.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Best layout (BLUE / STACK / FULL) | Crop anchor | Chip centre y |
|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: layout, crop anchor, chip y (≥ 0.03H under the chin), title position, what the secondary card shows.

**Step 3 — Caption chunks.**
- 2–5 words, 1–2 lines, one keyword per chunk (bold italic), split at punctuation, never end on an article, preposition or conjunction, 0.6–1.6 s per chunk. Prefer chunk changes at cuts.
- Move 1–3 opening topic words into the title (T1) if the video opens on a calm shot; keep them out of the chunks.
- Output a caption table: `# | Start–End | Layout | Lines | Keyword`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | G1, T1 |
| Theme or topic word | The noun the whole video is about | T1, keyword in C1 |
| Contrast or turn | "but", "isn't", "instead", "never" | keyword, C3 |
| Person → B-roll cut | Scene table | X1 into P1 |
| B-roll → person cut | Scene table | X1 into FULL or B1 |
| Any later cut | Scene table | X1 |
| List or steps | "first", numbered items, 3+ parallel phrases | P1 with the previous step in the lower card |
| Numbers, amounts, names | Digits, proper nouns | keyword or C3 |
| Long static shot (> 2 s) | Scene table | M1 |
| Payoff or call to action | Last line on a speaker | F1, C2, E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **G1** (opener), **C1/C2** (captions), **X1** (every cut), **P1** (on at least one B-roll shot; if there is no B-roll, show a still of another part of the user's own footage in the lower card for one section), **F1** (closer on the last speaker shot; if there is no speaker, skip it). Unless physically impossible: for a video shorter than 3 s, shorten the morphs, never drop G1.
- A visible change every ~1.5–3 s (new chunk, morph, title). Never two morphs closer than 1.2 s. Never use the same layout twice in a row without a different secondary still or anchor.
- Variety: B1 at most once in a row; C3 at most 2× and ≥ 3 s apart; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, chips and titles readable and inside the frame (≥ 0.04W from the edges), secondary stills meaningful.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render the sky gradient, the stage with slabs and the title once. Hold the layout as a numeric vector and interpolate it per frame; redo the cover-fit crop every frame.
- Sub-pixel crops via `Image.resize(..., box=floats)`; clamp boxes (`box offset can't be negative`). Draw rounded shapes and text at 2× or 3× and downscale. Download fonts from the Google Fonts GitHub repo if missing, else use the fallbacks. Measure text before drawing; lay out each chunk completely before its first word appears.
- Style-specific notes: blur the region behind a chip from the already composed frame; cards may bleed off the screen edge, so clip when pasting; the caption tint is frost on the blue backdrop and slate elsewhere.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every moment. Look at them.
- Checklist: captions correct, in order and readable; one bold italic keyword per chunk; no word moves after it appears; chips never over a face; morphs smooth; stills are the user's footage; primary in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_aqua_glass_stage.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: G1 card on the blue gradient with the photo inside, T1 title strip or one C1 chunk.
- Default poster layout: photo in the BLUE card, chip at y 0.54 or title at the bottom.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (rounded frosted-glass cards on a soft sky-blue gradient or a white stage with pink and blue diagonal bars, cards gliding smoothly between layouts on each cut, small frosted caption labels with one bold slanted word, a thin gradient outline growing around the speaker at the end).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range and keyword.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; flashes, glitches, bouncing or spinning cards, tilted cards, blur over a face, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (blue gradient or white stage with slabs, empty glass cards, T1 title, C1 chips, X1 morphs between layouts). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary card.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
