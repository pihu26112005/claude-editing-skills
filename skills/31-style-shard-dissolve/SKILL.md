---
name: 31-style-shard-dissolve
description: Applies the "Shard Dissolve" motion-graphics style (hot vermilion-orange slanted slats that slice across the footage, a heavy yellow italic title, an orange-framed inset window with a square B-roll card and a giant outline word, grain dissolves between shots, split-weight white captions of thin words and heavy italic keywords, and a closing wall of giant grey words) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants an orange, bold, sporty, slanted, sliced, motivational or high-energy caption look.
---

# 31-style-shard-dissolve — Shard Dissolve

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
- Allowed transforms (from moments.md 1.6): full-frame display; scale into the inset window (0.875, top-anchored crop) and back (L1, L2); a card showing a still of another of the user's shots; M1 punch-in (≤ 1.12 total); slats and grain specks over the footage (X1, X2, T1); the closing word wall after the last spoken word (E1, ≤ 1.5 s).
- The primary window always plays the current footage in real time, in sync with the audio, and never freezes.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, colour grading or filters; speed changes; freezing the primary footage; trimming, reordering, adding or removing shots; changing resolution, fps or audio. Grain and slat remnants are orange or white specks, never frozen copies of the footage.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Captions keep the case the user wrote. Only the title, the ticker word and the wall word are UPPERCASE, and all three are one topic word taken from the user's own text (or a title the user supplied). Never invent a title. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks (plus any words deliberately moved into the title) reproduces the user's text word for word and in order. Run it before building (`assert`).

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on the footage's own cuts and for caption chunks (hard cuts by design).
- Every element enters and exits with its moment's motion; nothing blinks; no empty or black areas (the inset frame is Vermilion by design).
- Never start a window move (L1, L2) within 3 f after a cut. Never run two big moves (T1 exit, X1, X2, L1, L2, M1, E1) less than 0.5 s apart, except the cut beat itself.
- Slats and grain never hide a speaking face (moments.md 1.6, 1.7).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, spring, rotation of footage, blur, glitch or RGB split, shake, flashes, colour grading, letter-by-letter typing, per-word movement in captions, extra colours, lowercase title, shadows on the card.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as the footage's own cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Face bottom edge | Crop anchor for the inset window (0–0.14H) | Best moment on entry (X1 / X2 / none) |
|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (0.8–1.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: caption lane (baseline 0.715H, or 0.88H if the face bottom is below 0.62H), whether T1's title fits above the head, whether L1 fits (subject inside the window, face bottom ≤ 0.58H), crop anchor, which still goes on the card.

**Step 3 — Caption chunks.**
- 2–4 words per chunk, ≤ 24 characters, 0.5–1.5 s, split at punctuation, never end on an article, preposition or conjunction, chunk changes at cuts when possible.
- Pick keywords: 0–2 heavy words per chunk (meaning-carrying nouns and verbs); at most one chunk in four has none; one C2 heavy solo chunk for a verdict or number.
- Output a caption table: `# | Start–End | Text | Keywords | Mode (C1/C2)`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 |
| Theme or topic word | The noun the whole video is about | T1 title, K1 ticker, E1 wall word |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | keyword, C2 |
| Person → B-roll cut | Scene table | X1 |
| B-roll → person cut | Scene table | X2 |
| Any later cut | Scene table | X1 or X2, card swap inside L1 |
| List or steps | "first", "second", numbered items, 3+ parallel phrases | L1 across the steps (card = previous step) |
| Numbers, amounts, names | Digits, proper nouns | C2 |
| Long static shot (> 2 s) | Scene table | M1 or L1 |
| Section change without a cut | Pause, new topic word | L1 or L2 |
| Payoff or call to action | Last line | M1, then E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1** (opener), **C1** (all captions), **E1** (closer), **X1 or X2** on every cut, and **L1** whenever the video has at least two consecutive shots of 1.2 s or more (use it on the longest run of B-roll or steps). Unless physically impossible: for a video shorter than 3 s, shorten T1's hold and E1, never drop them.
- A visible change every ~1.5–3 s (new chunk, cut beat, layout move). Never two big moves < 0.5 s apart. Never a window move within 3 f after a cut.
- Variety: C2 at most 1 per 3 s; M1 at most 2×; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and inside the frame (≥ 0.04W from the edges), the title not over the head, the card not over a face, the wall only after the last spoken word.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render static assets once: title, ticker strip, word wall, every caption chunk (shadow baked in), card stills. Use fixed seeds for the grain fields.
- Use the exact easing curves of the moments. Sub-pixel crops via `Image.resize(..., box=floats)`; clamp boxes (`box offset can't be negative`).
- Draw text and shapes at 2× and downscale for anti-aliasing. Download Barlow from the Google Fonts GitHub repo (ofl/barlow) if missing, else use the fallbacks. Measure text before drawing.
- Style-specific notes: light and heavy words share one baseline (`anchor="ls"`); draw heavy words char by char for tracking −0.02em; the ticker is an outline made by stroking glyphs and clearing their interiors; slats are polygons drawn at 2× and clipped per band; compose order is footage or inset frame → ticker → card → grain → slats → title → wall → captions.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every moment. Look at them.
- Checklist: captions correct, in order and readable on bright shots too; heavy words slanted and light words thin; no word moves after the chunk appears; title clear of the head; slats never over a speaking face; window subject inside the frame; card not over a face; grain sparse; wall only after the speech; primary footage in sync and live; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_shard_dissolve.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: T1 (title at the top, slats at the edges and the bottom), one C1 chunk in the lane, optionally K1 along the bottom with L1's frame and card using a crop of the same photo.
- Default poster layout: photo full frame, title at the top, slats at the edges, caption at 0.715H.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (bright orange slanted bars slicing across the picture, a heavy slanted yellow title, an orange frame around a shrunken picture with a square card and a giant outlined word along the bottom, drifting grain between shots, captions of thin white words with heavy slanted keywords, a closing page of giant grey words).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range and heavy words.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; blur, glitch, colour split, flashes, bouncing or spinning text, lowercase title, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (flat Vermilion plates, T1 slats and title, C1 and C2 captions, K1 ticker, X1 slat reveals between plates, E1 wall as the closer). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync or freeze the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
