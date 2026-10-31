---
name: 117-caption-tall-serif-stack
description: Applies the "Tall Serif Stack" motion-graphics caption style (untouched full-frame footage, a block of tall narrow high-contrast serif capitals in one saturated colour that cuts in above the speaker with a soft drifting sheen, and a tiny bold white serif caption that builds word by word just under the block) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a magazine-cover, tall serif, stacked headline, red-title or bold editorial caption look.
---

# 117-caption-tall-serif-stack — Tall Serif Stack

Style data lives in [moments.md](moments.md). Read it fully before planning. This is a caption system only: typography, chunking, timing, titles and placement. The footage is never changed.

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
- Allowed transforms (moments.md 1.6): full-frame display, untouched; text and shadow overlays only.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, bars, splits, blurs, zooms, glitches, flashes, tints, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Title words are uppercase copies of words from the user's own text; captions keep the user's case and punctuation. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks reproduces the user's text word for word and in order. Every title word must be a word, or consecutive words, from the user's text. Run both checks before building.

3.3 **Smooth, no breakdowns.**
- Titles and caption chunks cut in and out by design; sheen and word alpha ramps follow moments.md 1.5. Nothing else moves.
- A title never crosses a footage cut and never overlaps another title. Never start a title within 3 f after a cut while another is still running.
- No empty or black areas are introduced. Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, slides, letter-by-letter typing, rotation, zoom, blur, glitch, flashes, boxes behind text, italics, outlined titles, extra colours (title colour, its sheen, white), lowercase titles.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Free lane (head / top / low) | Brightness of lane | Best title mode | Crop anchor |
|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Per scene choose the lane (moments.md 1.3): head lane above a speaker's hair line (face top − 0.02H), top lane for face-free shots, low lane when a face sits in the upper half of a non-speaker shot. Decide the title block budget (0.105H on speaker shots).

**Step 3 — Caption chunks.**
- 2–5 words, 0.7–1.6 s, split at punctuation, never end on an article, preposition or conjunction, chunk changes at cuts, no chunk crossing a cut. Start = first word start; end = min(last word end + 0.1, next start − 0.05), before the next cut.
- Pick title phrases: 1–3 words per title, meaning-carrying nouns or verbs, 1.1–1.8 s apart (T3 rhythm), max 1 title per shot unless the shot is longer than 3 s.
- Output a caption table `# | Start–End | Shot | Text` and a title table `# | Start–End | Lines | Lane`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 or T2 + C1 |
| Theme or topic word | The noun the whole video is about | T1 |
| Contrast or turn | "but", "isn't", "instead", "the truth" | T3 swap |
| Person → B-roll cut | Scene table | X1, T1 in the top lane |
| B-roll → person cut | Scene table | X1, T2 in the head lane |
| Any later cut | Scene table | X1 |
| List or steps | "first", "second", 3+ parallel phrases | T3 per item |
| Numbers, amounts, time phrases | Digits, "one year" | K1 or T1 |
| Face in the top half of a non-speaker shot | Scene table | T4 |
| Long static shot (> 2.5 s) | Scene table | T3 swap mid-shot |
| Payoff or call to action | Last line | T1 or K1, then E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1 or T2** (opening title), **C1** (the caption system on every spoken line), **T3 rhythm** (at least two title swaps in a video longer than 5 s), **X1** (a beat on every cut). Unless physically impossible: for a video shorter than 3 s, one title only, never drop the caption.
- A visible change every ~1.5–3 s (new chunk, title, cut). Never two titles at once. K1 at most once in 6 s.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and ≥ 0.04W from the edges, titles not over the face, title letters still readable around the caption.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render each title mask once (render at 2× in the Didone font, squeeze width × 0.60, shared cap height per block) and each caption word once. Per frame only the sheen colour field and alpha change.
- Exact numbers from moments.md. Draw text at 2× and downscale. Download fonts from the Google Fonts GitHub repo if missing, else use the fallbacks. Variable fonts: set the weight axis (Bodoni Moda axes are Weight then Optical size). Measure text before drawing; lay out each chunk completely before its first word appears so no word moves.
- Keep the render script in a scratch folder.
- Style-specific notes: title colour is a parameter (default #CF3D3F; ask nothing, use the user's brand colour if given); the demo used cobalt. Clamp every crop box (`box offset can't be negative`).
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every title. Look at them.
- Checklist: captions correct, in order and readable; titles uppercase, tall, centred, 0.70W wide, accent colour with sheen; caption sits just under the title block, never overlapping it; no word moves after it appears; faces safe; no effects on cuts; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_tall_serif_stack.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use T1 or T2 settled above the subject plus one C1 chunk fully visible, in the head or top lane.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (tall narrow serif capitals in one bold colour stacked above the person, a faint shimmer across them, tiny bold white serif captions building word by word on their lower edge, plain cuts).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; transitions, glitches, blurs, flashes, bouncing or spinning text, lowercase titles, boxes behind text, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a typography-only piece rendered in code on a plain dark or light plate (user's palette if given): T1/T3 titles and C1 captions, plain cuts. No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects on cuts or any effect not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
