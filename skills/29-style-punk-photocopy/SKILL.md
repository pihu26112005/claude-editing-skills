---
name: 29-style-punk-photocopy
description: Applies the "Punk Photocopy" motion-graphics style (live full-frame footage, acid-yellow brush strokes and torn yellow paper wipes, a black-plate halftone speech-bubble poster, white deckle-edge photo cards, and hard black caption bars with white slab-serif words and one big yellow keyword) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a punk, zine, photocopy, cut-and-paste, black-and-yellow, DIY or gig-poster look.
---

# 29-style-punk-photocopy — Punk Photocopy

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
- Allowed transforms (from moments.md 1.6): full-frame live display; T1 echo stack (≤ 0.8 s, once); windows showing the user's own footage (bubble with live footage, round zoom window, photo cards with a still or ≤ 1.5 s loop of another of the user's shots); yellow strokes, torn wipes, caption bars and labels over the picture; M1 slow push (≤ 1.06 per shot).
- The primary footage always plays live, in real time, in sync with the audio, in full colour.
- Forbidden: replacing or regenerating any shot, person, face, object or background (the reference's black-and-white archive photos and mouth close-up are NOT reproduced; use only the user's own footage); desaturating or recolouring footage; blur, glitch, warp, flashes or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote (no forced uppercase). Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks and poster labels (in order) reproduces the user's text word for word. Run it with an assert before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on footage cuts, caption words and chunks, and the T1 stack jump (the style's own grammar).
- Every wipe, card and poster enters and exits with its moment's motion; nothing blinks; no empty or black areas except the T1 stack margin and the P1 plate.
- Never start a card entrance within 0.12 s after a cut; wipes and posters are built around the cut, not after it.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, spring, letter-by-letter typing, fades on captions, rounded caption bars, shadows on caption text, extra colours beyond black, white and acid yellow, blur, glitch, shake, flashes, colour grading of footage.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts under the wipes.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Speaking face? | Subject centre | Caption lane y | Card side | Poster ok? |
|---|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: caption lane y (below the chin, off footage text), card side (away from the subject), whether a poster fits (no speaking face), wipe type (W1 or W2 by face position), brush bands.

**Step 3 — Caption chunks.**
- 1–3 words, ≤ 20 characters, split at punctuation, never end on an article or preposition, chunk changes at cuts when possible; end = next chunk start (gap > 0.6 s: last word start + 0.6 s).
- Pick one keyword per chunk (skip about 1 chunk in 4): nouns, verbs and the payoff word; ≤ 1 per chunk.
- Output a caption table: `# | Start–End | Mode | Text | Keyword | Lane y`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 |
| Theme or topic word | The noun the whole video is about | keyword in C1 |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | C2, L1 |
| Person → B-roll cut | Scene table | K1 (speaker still on a card), P1 on B-roll |
| B-roll → B-roll cut | Scene table | W1, P1 |
| B-roll → person cut | Scene table | W2 |
| List or steps | "first", "second", 3+ parallel phrases | P1 or K1 per item, keywords |
| Numbers, amounts, names | Digits, proper nouns | C2 or L1 |
| Long static shot (> 1.5 s) | Scene table | D1, M1 |
| Section change without a cut | Pause, new topic word | D1 |
| Payoff or call to action | Last line | C2, W2 into it, E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1** (opener), **C1** (caption system), **P1** (poster, on a B-roll or no-face shot), **K1** (card), **W1** (torn wipe). Unless physically impossible: a video shorter than 5 s may drop P1 or K1 (never both), never drop T1, C1 or W1.
- A visible change every ~1.5–3 s. Never two big moves < 0.6 s apart; never a card or poster during a wipe.
- Variety: each of P1, W1, W2, K1 at most 2× (≥ 3 s apart); different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, bars readable and inside the frame (≥ 0.04W from the edges), cards away from faces and bars.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render static assets (bar states per chunk, labels, cards, brush strokes, plate dust) once; use fixed seeds so cards, strokes and dust never change between renders.
- Use the exact easing curves of the moments. Sub-pixel crops via `Image.resize(..., box=floats)`; clamp boxes (`box offset can't be negative`).
- Draw text and shapes at 2× and downscale for anti-aliasing. Roboto Slab (variable) from the Google Fonts GitHub repo (`ofl/robotoslab`) if missing, else Zilla Slab Bold or Bitter. Use `set_variation_by_axes([weight])`. Measure text before drawing; size every bar for the whole chunk.
- Layer order: footage → T1 stack and strokes → P1 poster → K1 cards → W1/W2 → caption bars (always on top).
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around T1, every wipe, the poster in and out, and every card. Look at them.
- Checklist: captions correct, in order and readable; bars sized to the chunk; words pop on their spoken start; faces safe at every wipe frame; no unintended jumps; primary footage in sync and in colour; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_punk_photocopy.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: T1 strokes at the edges, one C1 chunk (or C2 word) on its bar, optionally one L1 label.
- Default poster layout: photo full frame, strokes on the right and bottom edges, bar at 0.62–0.68H.
- Never alter, recolour or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (photocopy-punk zine: bright yellow brush strokes and torn yellow paper wipes, black speckled poster with a speech-bubble window, white torn photo cards, captions on solid black bars with white words and one large yellow word).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range and its yellow word.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; black-and-white or recoloured footage; changed audio or music; extra or misspelled text; garbled captions; glitches, blurs, flashes, bouncing or spinning text, all-capital text, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (plain black or yellow paper plates, T1 strokes, C1 bars, P1 labels, W1 wipes between plates). No fake footage.
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
