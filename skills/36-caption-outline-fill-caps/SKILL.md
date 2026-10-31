---
name: 36-caption-outline-fill-caps
description: Applies the "Outline Fill Caps" caption style (untouched full-frame footage; tall condensed all-caps white captions that appear as hollow outlines and fill solid white word by word as each word is spoken, in one to three centred lines that sit under the chin on speakers and mid-frame on B-roll, plain hard cuts) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants outline text, fill-as-you-speak, condensed uppercase or karaoke-free read-ahead captions.
---

# 36-caption-outline-fill-caps — Outline Fill Caps

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
- Allowed transforms (from moments.md 1.6): full-frame display, untouched; text and soft shadow overlays only. Nothing else.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; zoom, push-in, cards, split screens, slide or whip transitions, blur, glitch, flashes, colour grading or filters of any kind (even if the reference video had cards or push transitions); speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, converted to UPPERCASE (the style's rule). Numerals only if the user wrote them.
- Title words (T1, T2) come from the user's own text (or a title the user supplied); never invent a title.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks (plus any words deliberately moved into a title or a solo keyword or title) reproduces the user's text word for word and in order. Run it before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on the footage's own cuts and for caption chunks (hard cuts by design); word fills are a 2 f snap.
- Every element enters and exits with its moment's motion; nothing blinks; no empty or black areas.
- Never start a title within 0.3 s after a cut, and never let a title run across a cut.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, slides, scale pops, typewriter letter-by-letter, glow, colour change or any accent colour, lowercase, italics, rotation, boxes or plates behind text, effects on cuts, cards or layouts.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Face bottom edge | Key subject band (hands, product, UI) | Best lane (centre y) |
|---|---|---|---|---|---|---|---|

- Find the lane per shot (moments.md 1.3 and 1.7): speaker lane 0.695H under the chin; faceless B-roll lane 0.50H or the emptiest band.
- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene the lane centre y and the number of lines that fit (moments.md 1.7).

**Step 3 — Caption chunks.**
- Chunk rules: 3–6 words per chunk, 1–3 lines, each line ≤ 0.84W wide, split at punctuation, never end on an article, preposition or conjunction, 1.0–1.8 s per chunk, chunk changes on cuts when possible. Choose C1 (two lines), C2 (one line, 2–3 words) or C3 (three lines) by what fits.
- Optional K1 solo word: ≤ 2 per video, ≥ 3 s apart.
- Output a caption table: `# | Start–End | Moment | Text | Lane y | Lines`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1, C1 |
| Theme or topic word | The noun the whole video is about | T1 title words, K1 |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | K1 |
| Person → B-roll cut | Scene table | X1 + L1 (lane to 0.50H or empty band) |
| B-roll → person cut | Scene table | X1 + L1 (lane to 0.695H) |
| Any later cut | Scene table | X1 |
| List or steps | "first", "second", numbered items, 3+ parallel phrases | T2 per item, C1 per item |
| Numbers, amounts, names | Digits, proper nouns | K1 |
| Long static shot (> 2 s) | Scene table | lane shift, new chunk |
| Section change without a cut | Pause, new topic word | T2 |
| Payoff or call to action | Last line | K1, E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **C1** (the outline-fill caption system; C2 and C3 as shape variants), **L1** (lane choice per shot) and **X1** (every cut, with the chunk and lane switched on the cut frame). T1 is optional and used only when the opening line names a topic. Unless physically impossible: for a video shorter than 3 s, use one chunk.
- A visible change every ~1.5–3 s (new chunk, new phrase, title, cut). Never two titles at once. Never a title entrance within 0.3 s after a cut.
- Variety: K1 at most 2× and ≥ 3 s apart; T2 only for a real new topic; vary C1, C2 and C3 by phrase length; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and inside the frame (≥ 0.04W from the edges), titles not over the face, the block not over the key subject.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render static assets (every word's outline and fill mask, every chunk layout) once.
- Use the exact timings of the moments. Lay out each chunk completely before it appears so no word moves.
- Draw text at 2× and downscale. Download fonts (Bebas Neue) from the Google Fonts GitHub repo if missing, else use Anton or Barlow Condensed Bold. Measure text before drawing.
- Keep the render script in a scratch folder.
- Style-specific notes: font size 0.127W, line pitch 0.90 em, word gap 0.25 em; outline = dilate minus erode of the glyph mask; fill snaps over 2 f at the word's spoken start; soft shadow behind every word (needed on bright footage); lines centred on x = 0.50W.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every moment. Look at them.
- Checklist: captions correct, in order and readable; outline words readable on this footage; each word fills at its spoken start; no word moves; lines inside 0.84W; faces safe; no effects on cuts; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_outline_fill_caps.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: one caption chunk (C1) with the first word solid and the rest outlined, plus optionally T1 filled at the top.
- Default poster layout: photo full frame, caption block centred at 0.695H (or 0.50H if a face is low).
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (tall narrow white capitals that appear as thin outlines and fill solid as each word is spoken, centred in one to three lines under the chin or in the empty middle, plain cuts).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range and fill order.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; transition effects, glitches, blurs, flashes, bouncing or spinning text, lowercase text, colours other than white, boxes behind text, cards, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (plain light or dark plate in the user's palette if given, optional T1, C1 chunks, X1 hard cuts between plates). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects on cuts or any other effect not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
