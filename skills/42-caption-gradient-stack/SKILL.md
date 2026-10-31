---
name: 42-caption-gradient-stack
description: Applies the "Gradient Stack" motion-graphics caption style (untouched full-frame footage, small tight white bold words building a line with a soft shadow, and one giant extra-bold keyword per phrase with a bright-to-dark colour gradient that blurs in right under it, phrases zigzagging between the top and middle of the frame) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants big colourful keyword captions, bold sans captions, gradient words or a stacked caption look.
---

# 42-caption-gradient-stack — Gradient Stack

Style data lives in [moments.md](moments.md). Read it fully before planning.

## 1. YOUR JOB

You are a motion designer who knows one style. Steps: collect inputs (section 2) → analyse the footage scene by scene and line up the captions → find hook points and choose moments → copy each moment's spec verbatim and adapt only the ✎ fields → deliver the final video/image (build and check) or a Flow master prompt.

The value you add is choosing the keywords, placing the lanes and timing the chunks. You never invent a new look, and you never alter the user's footage.

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
- Allowed: full-frame display, untouched; text overlays with shadow (moments.md 1.6).
- The primary footage always plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, B-roll frames, background swaps, zooms, blur, glitch, flashes, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case and punctuation the user wrote. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all chunks (small words in order, then the keyword) reproduces the user's text word for word and in order. Run it before building. This is why the keyword must be the last word of its chunk.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; nothing blinks; every chunk enters with its entrance and leaves with the C3 fade (except the last chunk, E1).
- The face box is visible from frame 0; the keyword never covers a speaking face (moments.md 1.7).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md, with their exact look and motion. Never: outlines, boxes, bounce, overshoot, letter-by-letter typing, scale pops, rotation, a second font, a keyword with a shadow, two keywords in one chunk, the same keyword colour twice in a row, effects on cuts.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Lane A free? | Lane B free? | Lane C free? |
|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the words across each shot (1.2–2.5 s per chunk).

**Step 2 — Safe zones and lane plan per scene.** Apply moments.md 1.7: lane A needs the keyword to clear the face top; lane B needs the face bottom ≤ 0.43H; otherwise lane C. Set the lane A margin from the highest face top in the video.

**Step 3 — Caption chunks.**
- Each chunk = 0–4 small words + 1 keyword that is the last word. Split at punctuation and natural phrases; never end a chunk's small line on an article or preposition unless the keyword follows; one chunk per ~1.0–1.5 s of speech; the keyword is a noun, verb or number.
- Chunk start = first word start; keyword start = its spoken start.
- Lanes alternate A, B, A, B (C2); apply overrides (C4). Compute lifetimes (C3).
- Output a caption table: `# | Start–keyword–End | Lane | Small words | Keyword | Colour`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First words, first 0.5 s | T1 |
| Theme or topic word | The noun the whole video is about | K1 keyword |
| Contrast or turn | "but", "isn't", "instead", "never" | K1 keyword on the turn word |
| Person → B-roll cut | Scene table | C2 lane check, C4 if needed |
| B-roll → person cut | Scene table | C2 lane check |
| List or steps | 3+ parallel phrases | one chunk per item |
| Numbers, amounts, names | Digits, proper nouns | K1 or K4 |
| Section change | Pause, new topic word | new chunk after the pause |
| Payoff or call to action | Last line | K1 on the payoff word, E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1** (opener), **C1** (small line), **K1** (gradient keyword in every chunk), **K2** (colour cycle), **C2** (zigzag lanes), **C3** (fade), **E1** (end hold). Unless physically impossible: for a video shorter than 3 s use one chunk, never drop K1.
- Extensions as needed: K3 (long words), K4 (at most 2 solo words), C4 (face conflicts).
- Variety: different videos pick different keywords and different chunk splits.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text | ✎ Lane | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame: face safe, text inside the frame (≥ 0.04W from the edges), no two chunks in one lane.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every small word (with baked shadow) and every keyword (gradient fill) once at 2× and downscale.
- Fonts: Poppins SemiBold and ExtraBold (download from the Google Fonts GitHub repo if missing); fallbacks per moments.md 1.4. Measure text with per-character advances plus tracking before drawing; lay the whole small line out before its first word appears.
- Keyword blur: `GaussianBlur(14·(1−e))` on the pre-rendered patch each frame.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 1–3 fps plus frames around every cut and every keyword entrance. Look at them.
- Checklist: captions correct, in order and readable; keyword colours differ in sequence; no word moves after it appears; faces safe; lanes alternate; fades clean; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_gradient_stack.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: one chunk in lane A (or lane B if the subject is at the top), keyword in colour 1.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph (small white bold words line by line, one very large heavy rounded keyword per phrase in a deep colour that darkens from left to right and comes into focus from a blur, phrases alternating between the upper and middle part of the frame).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every chunk with its time range, lane, small words, keyword and colour name.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed audio or music; extra or misspelled text; garbled captions; outlines, boxes, bouncing or spinning text, camera shake, transition effects.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a typography-only piece rendered in code (plain light plate in the user's palette if given, T1, C1, K1, C2, E1). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary footage.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add cards, effects or any other element not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
