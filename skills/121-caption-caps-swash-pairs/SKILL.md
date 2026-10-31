---
name: 121-caption-caps-swash-pairs
description: Applies the "Caps Swash Pairs" caption style (untouched full-frame footage, tiny wide-tracked white capital words that appear one by one above and below one giant white italic serif keyword in the lower third, a soft shadow, one optional accent-coloured payoff word, hard-cut chunks) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants editorial, small caps plus big italic serif, minimal poster-like captions.
---

# 121-caption-caps-swash-pairs — Caps Swash Pairs

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
- Allowed transforms (moments.md 1.6): full-frame display, untouched; text overlays with a soft shadow.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; crop, zoom, split, cards, blur, glitch, flashes, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Caps rows are the user's words converted to capitals; keywords keep the user's case. Numerals only if the user wrote them.
- Titles (T1, T2) use only the user's own words (or a title the user supplied); never invent a title.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all chunk words (pre, keyword, post, solo) in order, plus any words deliberately moved into a title, reproduces the user's text word for word. Assert it before building.

3.3 **Smooth, no breakdowns.**
- Continuous ease-out entrances from moments.md; chunks leave with hard cuts by design; nothing blinks, nothing moves after it appears.
- Never place a title in the same time range as a pair block's first 0.3 s; captions and titles never overlap each other.
- Keep text inside 0.07W–0.93W, keep the face box clear (x 0.34–0.66, y 0.15–0.40 of the frame), keep the bottom 0.05H free.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: boxes, plates, outlines, glow, bounce, overshoot, slides, letter-by-letter typing, scale pops, effects on cuts, uppercase keywords, more than one accent colour, a tinted caps row, rotation.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth fades and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Watermark or logo corner? | Lower-third luminance (0–1) |
|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.0 s each).

**Step 2 — Safe zones.** Face box clear; pair block at y ≥ 0.70H; if a subject's face sits in the lower half (low-angle or close-up), raise the whole block by up to 0.12H but keep it below the face. Note any watermark corner.

**Step 3 — Caption chunks.**
- Chunk 3–6 words, 0.9–2.0 s; split at punctuation; never end a chunk on an article, preposition or conjunction when the next word can join it; prefer chunk changes at cuts.
- Per chunk pick ONE keyword (a meaning-carrying noun or verb). Words before it go in the pre row, words after it in the post row (≤ 2). A chunk without a good keyword becomes C2. A video needs at least 3 keyword blocks.
- Start = first word start; end = min(last word end + 0.1, next chunk start − 0.05); minimum 0.8 s.
- Output a caption table: `# | Start–End | Moment | Pre | Keyword | Post | Side`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 (optional), C1 |
| Theme or topic word | The noun the whole video is about | C1 keyword |
| Contrast or turn | "but", "isn't", "instead", "never" | C2 then C1 |
| Person → B-roll or later cut | Scene table | block change on the cut frame |
| List or steps | 3+ parallel phrases | one C1 each, alternate side L and R |
| Numbers, amounts, names, time phrases | Digits, proper nouns | keyword or C3 |
| Long static shot (> 2 s) | Scene table | C1 + C2 alternation |
| Payoff or call to action | Last line | K1 + E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory: **C1** (at least 3 blocks) and **C2** (at least 1 line when the text has a connective phrase). Unless physically impossible: for a video under 3 s use one C1 only.
- A visible change every ~1.5–3 s. C3 at most 2× and ≥ 3 s apart. K1 once. T1/T2 only if the user's text has a real topic phrase.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Side/anchor | Reason |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame: face clear, text inside the frame, no overlap with a title, post caps clear of any watermark corner.

**Step 7 — Build.**
- Python + ffmpeg: decode raw RGB frames, composite per frame with Pillow, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render each word at 2x and downscale to 1x, then add the shadow; place words with sub-pixel-free integer positions computed before the first frame.
- Fonts: Montserrat (variable, wght 600) and Playfair Display Italic (wght 500); download from the Google Fonts GitHub repo if missing, else use the fallbacks.
- Keyword: start at 0.18W; shrink in steps of 0.006W until width ≤ 0.84W.
- Rows are clamped to 0.07W–0.93W; check crops (`box offset can't be negative` → clamp).
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.** Contact sheet (3–4 fps) plus frames around every chunk change; look at them. Checklist: captions correct and in order; caps small, keyword large; no word moves after appearing; face clear; nothing outside the frame; no title/caption overlap; accent used once at most; footage in sync; duration, fps, resolution, audio match. Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_caps_swash_pairs.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

Use T1 (optional) and one settled C1 block on the photo; never alter the photo; export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add small captions …"
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** plain words: small spaced white capital words around one very large white italic serif word in the lower third, soft shadow, plain cuts, no boxes.
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every block with time range, small words, big word, which side the trailing words sit.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed audio; extra or misspelled text; boxes, outlines, glow, bouncing or spinning text; camera shake; transitions.

Use plain words only. Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

Plan scenes from the story, time the captions, choose moments. Master prompt: section 6 with story scenes. Final video: a typography-only piece in code on a plain dark plate (or the user's palette), C1/C2 blocks with hard cuts between. No fake footage.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects not in moments.md, never invent moments, never break the style's "never" items (3.4).
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
