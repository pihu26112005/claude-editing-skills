---
name: 115-caption-orchid-halo
description: Applies the "Orchid Halo" motion-graphics caption style (untouched full-frame footage, short low captions in heavy white sans that fade in word by word, with one large glowing italic serif accent word per chunk that settles in as it is spoken) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants glowing accent word, serif italic highlight, neon-glow or sans plus serif caption looks.
---

# 115-caption-orchid-halo — Orchid Halo

Style data lives in [moments.md](moments.md). Read it fully before planning.

## 1. YOUR JOB

You are a motion designer who knows one style. Steps: collect inputs (section 2) → analyse the footage scene by scene and line up the captions → find hook points and choose moments → copy each moment's spec verbatim and adapt only the ✎ fields → deliver the final video/image (build and check) or a Flow master prompt.

The value you add is choosing the accent word of each chunk and placing the block where no face is. You never invent a new look, and you never alter the user's footage.

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
- Allowed: full-frame display, untouched; text, halo and shadow overlays only (moments.md 1.6).
- The footage always plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, zoom, flashes, dimming, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case and punctuation the user wrote. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all chunk words in order reproduces the user's text word for word. Run it before building (assert in code).

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only for chunk changes (which fade 0.12 s).
- Nothing blinks or moves after landing; no empty black areas; no effects on cuts.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Exactly one accent per chunk (the glowing italic serif word), everything else heavy white sans. Never: bounce, overshoot, letter typing, slides, shake, flashes, rotation, uppercase conversion, extra colours, boxes or bars behind text, a second accent.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- `ffprobe` for size, fps, duration, audio. Scene cuts with `select='gt(scene,0.3)'` (retry 0.12–0.2 if none); confirm visually.
- Look at 2–4 frames per scene (view them). Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h fractions) | Face bottom edge | Lane luminance (0–1) | Lane line (0.70–0.80H) |
|---|---|---|---|---|---|---|---|

- Speech timing: speech-to-text word timestamps only to time the user's words; else `silencedetect=n=-30dB:d=0.12` and spread by syllable weight, 0.15 s pause at commas, 0.3 s at full stops. No speech: spread phrases across each shot.

**Step 2 — Safe zones.** Face never covered while speaking. Decide the lane line per scene (moments.md 1.3, 1.7).

**Step 3 — Chunks.**
- 2–5 words, ≤ 30 characters, 0.7–1.6 s; split at punctuation; never end on an article, preposition or conjunction; change at cuts when possible.
- Choose one accent per chunk: the most meaningful noun or verb; at most one chunk in a row without an accent (C2).
- Each word's start = its spoken start; chunk end = min(last word end + 0.15, next start − 0.05), min 0.5 s.
- Output a caption table `# | Start–End | Layout (A/B/C/S) | Words | Accent`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First 0.5 s | T1 or C1 |
| Topic word | The noun the video is about | accent in T1 |
| Contrast or turn | "but", "isn't", "instead", "never" | accent on the turn word |
| Person → B-roll cut | Scene table | new chunk on the cut |
| List or steps | "first", 3+ parallel phrases | K2 per item |
| Numbers, names | Digits, proper nouns | K1 |
| Filler line | Connecting words | C2 |
| Payoff or call to action | Last line | K1, E1 |

**Step 5 — Choose moments.**
- Mandatory: **C1** on chunks (the caption system) and at least one of **K1 / K2** in the video. For a video shorter than 3 s keep one chunk.
- A visible change every ~1–2 s. K1 at most 2× and ≥ 3 s apart. Plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Accent / lane | Reason |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each spec and change only ✎ fields. Check every frame: faces safe, text readable and inside the frame, nothing collides.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every word once at 2× and downscale. Variable fonts: set axes in order [wght, opsz] for Newsreader Italic (check `get_variation_axes()`). Accent halo = two gaussian blurs of the glyph mask coloured in the accent hue, composited under the gradient fill; keep colour channels in 0–255 and alpha separate.
- Lay out each chunk completely before its first word appears. Download fonts from the Google Fonts GitHub repo if missing, else use fallbacks. Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Contact sheet at ~1.2–4 fps plus frames around every chunk change and cut. Look at them.
- Checklist: words correct and in order; one glowing accent per chunk; no word moves after landing; text readable on bright footage; faces safe; no effects on cuts; duration, fps, resolution and audio match.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_orchid_halo.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)
- One settled chunk (C1 or K1) at the lane line (0.765H). Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order:
1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …"
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** plain-words paragraph: heavy white sans caption words fading in one by one, one large glowing italic serif accent word per chunk, low in the frame.
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every chunk with its time range, layout and accent word.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed audio; extra or misspelled text; garbled captions; boxes, bars, transitions, glitches, bouncing or spinning text, all-capital text, camera shake.

Plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
- Plan scenes, time captions, choose moments. Master prompt: section 6. Final video: a typography-only piece on a plain dark plate (no shadows), C1 chunks and K1 payoff. Image: a typography poster in code.

## 8. NEVER DO
- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the footage.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects, boxes or moments that are not in moments.md.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
