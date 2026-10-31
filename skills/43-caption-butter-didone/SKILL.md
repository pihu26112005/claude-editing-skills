---
name: 43-caption-butter-didone
description: Applies the "Butter Didone" caption style (untouched full-frame footage; pale butter-yellow high-contrast Didone type; a small lowercase caption block that pops in word by word near the bottom with one CAPITAL keyword per phrase; and a giant edge-to-edge capital version of the key spoken word slamming in across the top, with hard pops and hard cuts only) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a fashion-magazine, Didone, serif, pale yellow, giant keyword or word-by-word caption look.
---

# 43-caption-butter-didone — Butter Didone

Style data lives in [moments.md](moments.md). Read it fully before planning. This is a caption system only: the footage stays full frame and untouched.

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
- Allowed transforms (from moments.md 1.6): full-frame display, untouched; text and shadow overlays only.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, zooms, B-roll frames, background swaps, graphic transitions; blur, tint, darkening, colour grading or filters of any kind; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. The only change allowed is uppercase: giant words are always uppercase (trailing punctuation dropped) and each caps keyword is uppercased. Numerals only if the user wrote them.
- Giant words come from the user's own text; never invent a title.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** the caption words of every chunk plus the giant words, in spoken order, reproduce the user's text word for word. Run it before building.

3.3 **Smooth, no breakdowns.**
- This style is hard pops and hard cuts by design; do not add fades or slides. Words never move after they appear (lay out each chunk completely first).
- Giant words and chunks never straddle a footage cut: end them on the cut frame.
- Never leave a speaking face covered; pick the giant band from the face box (moments.md 1.3, 1.7).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: fades, slides, bounce, scale pops, letter-by-letter typing, rotation, wipes, glitch, shake, flashes, label boxes, outlines, a second text colour, lowercase giants, or effects on cuts.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all pops as instant and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Face top / bottom | Giant band (free, face-safe, low-face, none) | Lane clear? | Crop anchor |
|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones.** Face never covered while speaking. Decide per scene: giant band from the face top (moments.md 1.3), caption lane shift (C3), whether footage text clashes.

**Step 3 — Caption chunks and keywords.**
- 2–5 words per chunk, split at punctuation, never end on an article, preposition or conjunction, end at a footage cut when possible. Chunk start = first word's spoken start; chunk end per moments.md C1.
- Pick giant words: one meaning-carrying noun or verb per phrase, at most one per chunk, ≥ 1.5 s apart, 4–5 per 10 s at most. Remove each giant from its caption line.
- Pick one caps keyword (K1) per chunk where useful, never the giant word.
- Output a caption table: `# | Start–End | Text | Giant word | Caps keyword | Lines`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | C1, T1 on the topic word |
| Theme or topic word | The noun the whole video is about | T1 |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | K1 or T1 |
| Person → B-roll cut | Scene table | end/start chunks on the cut; T3 if the shot has no face |
| B-roll → person cut | Scene table | new chunk, T1 face-safe |
| List or steps | "first", "second", 3+ parallel phrases | T1 or K1 per item |
| Numbers, amounts, time phrases | Digits, "one year", "every day" | T1/T3 on the number or unit word |
| Long pause | Silence > 0.5 s | clean gap, no caption |
| Single punchy word | One-word beat | C2 |
| Payoff or call to action | Last line | T1 on the last key word, E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **C1** (caption block), **K1** (caps keyword in most chunks) and **T1** (giant keyword, T3 on face-free shots). For a video shorter than 3 s, use one chunk and one giant; never drop them. If no shot has a legal giant band, say so and keep C1 + K1 only.
- Density: a text change at least every ~1.5–2.5 s while speech runs; a giant every 2–3 s; never two giants within 1.5 s.
- Variety: T2 only for a real two-word idea on a face-free shot; C2 at most 2×; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions inside the frame (≥ 0.07W from the edges), giants ≥ 0.03W from the edges, nothing across a cut.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every word and every giant once at 2× and downscale with LANCZOS; shadows baked in. Variable font: set the weight and optical-size axes (Bodoni Moda axes are [weight, optical size]).
- Use letter-by-letter drawing with tracking (giant −0.035em, caption −0.01em). Fit each giant to 0.93W, then limit by the band's cap height. Shrink a chunk's font when a single word is wider than 0.86W.
- Download fonts from the Google Fonts GitHub repo if missing, else use the fallbacks. Measure text before drawing; lay out each chunk completely before its first word appears.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every giant. Look at them.
- Checklist: captions correct, in order and readable on every shot; giants uppercase, fit the width, clear of faces; one colour only; words never move; chunks cleared on cuts; no effects on cuts; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_butter_didone.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: one giant word in the band, one C1 chunk in the lane (K1 inside).
- Default poster layout: photo full frame, giant word at the top, caption block at the bottom lane.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (pale butter-yellow elegant high-contrast serif lettering; small lowercase captions popping in word by word near the bottom with one capital word per phrase; one huge capital word across the top at key moments; everything pops in and out instantly).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range, capital word and giant word.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; fades, slides, bouncing, typing letter by letter, boxes, outlines, a second text colour, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a typography-only piece rendered in code in this style (plain dark plate in the user's palette if given, giant words and C1 chunks popping on the beat). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
