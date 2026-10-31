---
name: 35-caption-lime-glow
description: Applies the "Lime Glow" caption style (full-frame untouched footage, captions that pop in as white semibold plain words over one heavy slanted lime keyword with a green glow on a soft dark floor, plus a giant outlined slanted title with a red and cyan fringe that slides across the top) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants bold neon-lime keyword captions, tech or fitness reel captions, or a glowing outlined headline.
---

# 35-caption-lime-glow — Lime Glow

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
- Allowed transforms (moments.md 1.6): full-frame display, untouched; the bottom floor scrim (max 44 % black, whole video); text, glow and title overlays.
- The footage always plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, B-roll frames, background swaps, graphic transitions; blur, glitch, warp, zoom, flashes, grading; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every caption word is the user's exact word, in the case the user wrote. Titles are the user's own word in UPPERCASE (the only forced case). Never invent a title word.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks reproduces the user's text word for word and in order (words moved into a title still appear in the captions). Run it before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; footage cuts stay plain; captions continue across cuts.
- Every element enters and exits with its moment's motion; nothing blinks; no word moves after it has appeared.
- Never start a title within 3 f after a cut; a title may hold across a cut.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, exact look and motion. Never: layouts or cards, bounce beyond the 0.92 → 1 settle, letter-by-letter typing, wipes, shake, flashes, rotated captions, extra colours, forced uppercase on captions.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h fractions) | Caption-zone luminance (0–1) | Title strip clear? | Crop anchor |
|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise `silencedetect=n=-30dB:d=0.12` + syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones.** Apply moments.md 1.7 per scene: caption baselines, title strip height, footage text.

**Step 3 — Caption chunks.**
- 2–5 words, 0.6–1.5 s, split at punctuation, never end on an article, preposition or conjunction, prefer boundaries on cuts.
- One keyword group per chunk (1 meaning-carrying word, or 2 for K2); at most 1 chunk in 3 without a keyword (C2); plain words after the keyword go to line 2 (K1).
- Output a caption table: `# | Start–End | Moment | Line 1 | Line 2 (lime)`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1, C1 |
| Theme or topic word | The noun the video is about | T1 title word, keyword |
| Contrast or turn | "but", "isn't", "instead", "never" | keyword, C3 |
| Any cut | Scene table | X1 |
| List or steps | Parallel phrases | C1 per item, K2 |
| Numbers, amounts, time phrases | Digits, "one year" | K2 |
| Long static shot (> 2 s) | Scene table | caption variety (C2 → C1) |
| Payoff or call to action | Last line | T2, E1 |

**Step 5 — Choose moments.**
- Signature moments, mandatory: **C1** (the caption system) and **T1** (opener title). Add **T2** for a payoff word when the video is longer than 6 s and a quiet shot with the title strip clear exists. For a video shorter than 3 s, shorten T1's hold, never drop it.
- A visible change every ~1–2.5 s (new chunk). Never two titles at once; T1 and T2 ≥ 3 s apart. C3 ≤ 2×.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position | Reason |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each spec; change only ✎ fields. Check every frame: faces safe, glyphs ≥ 0.04W from edges, white words readable on bright footage.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every word and title once at 2x (glow, shadow, gradient, outline baked in); downscale with LANCZOS when pasting.
- Fonts: Inter (wght 600), Barlow Black Italic, Anton; download from the Google Fonts GitHub repo if missing, else the fallbacks.
- Lay out each chunk completely before its first word appears. The floor scrim is multiplied into the footage once per frame.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Contact sheet at 1–3 fps plus frames around every cut and every title. Look at them.
- Checklist: captions correct, in order and readable; plain words white, keywords lime with glow; no word moves after it appears; faces safe; titles outlined and above the face; margins respected; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_lime_glow.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use settled states: T1 at the top, one C1 chunk at the lower lines, floor scrim on.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** plain words: clean white caption words, one heavy slanted lime green keyword on a lower line with a green glow, a soft dark fade at the bottom, a giant slanted outlined title with a faint red and blue fringe at the top.
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range, plain words and lime keyword.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed audio or music; extra or misspelled text; garbled captions; transition effects, glitches, blurs, flashes, bouncing or spinning text, camera shake.

Plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: typography-only piece rendered in code (plain dark plate in the user's palette if given, T1 title, C1 chunks, hard cuts between plates). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the footage from the audio.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add cards, layouts or effects not in moments.md; never invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
