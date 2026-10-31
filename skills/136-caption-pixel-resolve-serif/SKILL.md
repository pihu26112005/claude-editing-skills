---
name: 136-caption-pixel-resolve-serif
description: Applies the "Pixel Resolve Serif" caption style (untouched full-frame footage; tiny white serif whisper words that build word by word beside towering stretched high-contrast capitals that resolve out of a pixel mosaic, bend into arches, waves and slants, slip behind the speaker's head, and end on one giant mixed-case word) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants Didone, fashion-editorial, tall serif keyword, mosaic-reveal or behind-the-head title captions.
---

# 136-caption-pixel-resolve-serif — Pixel Resolve Serif

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
- Allowed transforms (moments.md 1.6): none. Footage is full frame and untouched; the only additions are text and its soft shadow. T6 uses a person mask only to put the footage's own head pixels back in front of a word.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, B-roll frames, background swaps, graphic transitions; blur, glitch, warp or zoom of the footage; colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Display words are shown in UPPERCASE (the style's rule); whisper words and the giant finisher T7 keep the user's written case. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all items of all chunks in reading order reproduces the user's text word for word. Run it before building (`assert " ".join(words) == TEXT`).

3.3 **Smooth, no breakdowns.**
- Whisper words fade in with a small rise; display words resolve from a mosaic (T1); every chunk ends with a hard cut (E1).
- **No two chunks on the same frame:** assert chunk[i].end ≤ chunk[i+1].start − 1/fps. No two items overlap inside a chunk (assert disjoint bounding boxes).
- **All text fully inside the frame:** every glyph and warped bbox inside x 0.05–0.95W and y 0.025–0.96H (assert in the build).
- **Face box clear:** no front text inside the speaker's face box; only T6 may sit behind the head, and it must stay ≥ 85 % visible (assert per frame).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: outlines, glows, gradients, boxes, extra colours (white plus one accent only), bounce, overshoot, letter-by-letter typing, slides, wipes, glitch, shake, flashes, scale pops, effects on cuts, rotation of the whole title.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Head top y | Free zones (top, chest) | Brightness | Behind-head OK? |
|---|---|---|---|---|---|---|---|---|

- Behind-head OK only for a talking head whose head top is at y 0.12–0.20 and who does not lean far.
- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Per scene decide: top stack and chest stack positions, whether T6 fits, how far the display word can go without touching the face box. A text may sit over B-roll subjects but never over a speaking face.

**Step 3 — Caption chunks.**
- A chunk is 1.0–1.7 s and 3–7 words: 1–3 whisper items (1–4 words each) and 1–2 display words (T1) plus at most one T7. Split at punctuation and at cuts, never end on an article or preposition, chunk start = first word, chunk end = last word end + 0.3 s but before the next chunk and before the next cut.
- Pick display words: the 1–2 most meaningful nouns, verbs or numbers per chunk. Short words (< 3 letters) stay whispers.
- Output a caption table: `# | Start–End | Reading order (whisper / DISPLAY) | Warp | Colour | Behind head?`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T6 or T3 on the topic word |
| Theme or topic word | The noun the whole video is about | T1 + T3 |
| Contrast or turn | "but", "isn't", "instead", "never" | T5 or whisper + T1 |
| Person → B-roll cut | Scene table | new chunk on the cut, no T6 |
| B-roll → person cut | Scene table | new chunk, T6 allowed |
| List or steps | 3+ parallel phrases | T2 or T1 with alternating K1 |
| Numbers, amounts, names | Digits, proper nouns | T1 accent |
| Long static shot (> 2 s) | Scene table | a second chunk with a different warp |
| Payoff or call to action | Last line | T7 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **C1** (all chunks), **T1** (every display word), **T7** (the closing word), **T6** (at least once when a talking head qualifies; otherwise say why it is skipped).
- A visible change every ~1.5–3 s. Variety: do not repeat the same warp more than twice in a row; K1 alternation; T2 only for real two-word phrases.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, text inside the frame, no overlap, T6 visibility.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with NumPy/OpenCV, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every display word once (draw at 2× on a padded canvas, stretch ×1.5 vertically, warp with `cv2.remap`, downscale with INTER_AREA, crop to bbox); pre-render each whisper word. Lay out every stack before the first word appears.
- Display font: Bodoni Moda variable (wght 820, opsz 14); whisper font: Newsreader (wght 500, opsz 16). Download from the Google Fonts GitHub repo if missing, else use the fallbacks.
- T6 needs the person segmentation model (MediaPipe selfie segmenter, VIDEO mode); run it only on frames where a behind-head word is visible; if unavailable, make the word a front word above the head.
- Assert in render.py: caption audit, no chunk overlap, glyph bbox margins ≥ 0.05W, face box clear, T6 visibility ≥ 0.85.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every chunk and every T6. Look at them.
- Checklist: captions correct and in order; display words uppercase and crisp after the mosaic; hairlines not vanishing; whisper words readable on the footage; no two chunks at once; nothing outside the frame; face box clear; T6 words readable; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_pixel_resolve_serif.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed (accent colour, how many display words).

## 5. STILL MODE (C4)

- Use the moments in their settled state: one chunk, whisper lead-in, one or two display words (T2 or T3), accent colour from the user.
- Default poster layout: photo full frame, top stack at y 0.04–0.28H, T7 finisher in the lower third if the text has a payoff word.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (tiny white serif words beside huge tall elegant capitals that sharpen out of a pixel mosaic, some bending like arches or waves, some tucked behind the head, a giant lowercase-mixed closing word, plain cuts).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every chunk with its time range, whisper words and big words.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled letters; boxes, outlines, glows, transition effects, glitches, blurs, flashes, bouncing or spinning text, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (plain dark plate or the user's palette, chunks with T1/T3/T4, T7 closer, hard cuts between plates). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face; never put front text inside the face box.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never show two chunks at once or let text leave the frame.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
