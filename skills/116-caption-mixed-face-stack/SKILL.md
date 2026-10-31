---
name: 116-caption-mixed-face-stack
description: Applies the "Mixed Face Stack" caption style (untouched full-frame footage with a tight stack of two to four lines that mixes heavy white capitals, bright accent capitals, a big italic serif and tiny connector words, each word popping in on its spoken beat, the stack hard-cutting away at chunk end) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants mixed-font, stacked, kinetic, multi-typeface, serif-and-sans or accent-word captions.
---

# 116-caption-mixed-face-stack — Mixed Face Stack

Style data lives in [moments.md](moments.md). Read it fully before planning. This is a caption system only: the footage stays full frame and untouched.

## 1. YOUR JOB

You are a motion designer who knows one style. Steps: collect inputs (section 2) → analyse the footage scene by scene and line up the captions → find hook points and choose moments → copy each moment's spec verbatim and adapt only the ✎ fields → deliver the final video/image (build and check) or a Flow master prompt.

The value you add is choosing the words, the role (typeface) of each word, and the placement of each stack. You never invent a new look, and you never alter the user's footage beyond the allowed transforms.

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

Only after all inputs are in, ask exactly one question unless already answered: **"Do you want me to make the final video for you, or give you a master prompt for Google Flow (you paste it into Flow with your video)?"** For an image: "final image or Flow master prompt". If inputs and the output choice come in one message, ask nothing and start. Never ask about colours, fonts, moments or timing. The accent colour is a parameter: use the default from moments.md 1.1 unless the user names one.

## 3. HARD RULES (never break)

3.1 **Footage is sacred.**
- Allowed transforms (moments.md 1.6): none on the footage itself; only text overlays with shadow.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, layouts, B-roll frames, background swaps, graphic transitions; blur, glitch, warp, zoom, flashes, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Case changes are allowed only where the style dictates: BIG and ACC words are uppercased; SERIF and SM keep the user's case. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all chunk words in order reproduces the user's text word for word. Assert it in code before building, and assert that each word's start time lies inside its chunk.

3.3 **Smooth, no breakdowns.**
- Each word enters with the 0.25 s ease-out rise from moments.md; stacks end with a hard cut; no word moves after landing; nothing blinks.
- Chunk changes may land on a footage cut. Never leave a stack on screen across a long silence (> 1.0 s): end it at last word end + 0.1 s.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: overshoot, bounce, spin, tilt, letter-by-letter typing, karaoke recolouring, glow, outline-only text, boxes, wipes, effects on cuts, more than four lines, more than one accent word per chunk, a second accent colour, uppercase on serif or small words.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Face bottom edge | Stack position (default / shifted / flip) | Busy or bright lane? |
|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread phrases across each shot (0.8–1.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: default block, lane shift or flip (moments.md 1.3), and whether burnt-in text collides.

**Step 3 — Caption chunks.**
- Chunks of 2–6 words (3–4 typical), 14–30 characters, 0.4–1.6 s, split at punctuation, never ending on an article, preposition or conjunction; change chunks at footage cuts when possible.
- Chunk start = first word start; end = min(last word end + 0.1, next chunk start − 0.05), minimum 0.4 s.
- Assign a role to every word (moments.md 1.4): connectors SM, main words BIG, ≤ 1 ACC per chunk, serif for turns and soft words; use ≥ 3 roles in 3+ word stacks, and avoid the same line layout twice in a row.
- Output a caption table: `# | Start–End | Lines (word:role) | Moment`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 |
| Theme or topic word | The noun the whole video is about | K1 |
| Contrast or turn | "but", "isn't", "instead", "the truth" | K2 |
| Person → B-roll cut | Scene table | new chunk on the cut, lane shift or C4 |
| B-roll → person cut | Scene table | new chunk on the cut, default block |
| Any later cut | Scene table | chunk change on the cut |
| List or steps | 3+ parallel phrases | C1/C2 per item, T2 |
| Numbers, amounts, time phrases | Digits, "one year" | K4 or K1 |
| Emphasis word on a face | Stressed word | C3 (≤ 2×) |
| Long silent shot (> 1.5 s) | Scene table | no stack; leave it clean |
| Payoff or call to action | Last line | E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1**, **C1**, **K1**, **K2**, **K3**, **E1**. Unless physically impossible (a video shorter than 3 s: shorten holds, never drop T1 or E1).
- A new stack every ~0.8–1.8 s while speech runs; never two stacks at once; C3 at most 2× and ≥ 3 s apart; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/roles | ✎ Position/anchor | Reason |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame: faces clear, stack inside the margins, readable on that shot.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every word as a 2x sprite (text, shadow, edge), downscale with LANCZOS, keep its baseline offset; lay out each chunk completely before its first word appears; shrink a line by 5 % steps until it fits.
- Entrance by resizing the sprite (0.92 → 1.0) and offsetting 18 px; clamp paste boxes inside the frame. Variable fonts: set the weight with `set_variation_by_name`.
- Download missing fonts from the Google Fonts GitHub repo, else use the fallbacks.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Contact sheet at 3–4 fps plus frames around every chunk change and cut. Look at them.
- Checklist: captions correct and in order; roles legible (four faces visible in the stacks); accent colour readable on every shot; faces clear; no word moves after landing; footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_mixed_face_stack.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use a settled stack (C1 or C2) at the default block; the photo stays full frame and untouched.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** plain-words paragraph: short stacks of two to four lines in the lower middle, mixing heavy white capitals, one bright accent-colour capital word, a big elegant italic serif word and tiny plain white words; words pop in one by one and the stack vanishes at once.
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with time range and the role of each word.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; boxes, glows, bouncing or spinning text, typing effects, transitions, camera shake.

Plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code (plain dark plate, stacks only). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add boxes, layouts, effects on cuts or any other effect not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
