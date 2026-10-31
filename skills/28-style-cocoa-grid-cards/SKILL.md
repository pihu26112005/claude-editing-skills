---
name: 28-style-cocoa-grid-cards
description: Applies the "Cocoa Grid Cards" motion-graphics style (the footage as a rounded card on a warm graph-paper page that rises in, swells to full frame, slides aside for a dark cocoa text page with a typed white topic chip, and settles back into a card, with every phrase typed word by word inside a brown label bar) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a graph-paper, cocoa, rounded-card, label-bar caption, clean editorial explainer look.
---

# 28-style-cocoa-grid-cards — Cocoa Grid Cards

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
- Allowed transforms (from moments.md 1.6): cover-fit crop into a rounded card (full source width kept, vertical window on the face); growing, shrinking and sliding the footage window (P1, K1, K2, D1, D2); covering the footage with the cocoa page only in D1 (≤ 1.2 s per cover, only on a shot with no speaking face, ≤ 15 % of the duration); an inset still of the user's own footage (S1); text, bar, chip, page and tick overlays.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, colour grading or filters of any kind; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote (the chip is uppercase by style). Numerals only if the user wrote them.
- Title, chip and inset label words come from the user's own text; never invent them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks (plus any words deliberately moved into the title, chip or label) reproduces the user's text word for word and in order. Run it before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on the footage's own cuts and for caption chunks (hard cuts by design).
- Every element enters and exits with its moment's motion; nothing blinks; no empty or black areas (the cream and cocoa pages are the design).
- Never start a card move, slide or expand within 3 frames (0.1–0.25 s) after a footage cut; a cut hidden under the cocoa page is fine.
- The speaking face is in view within 0.2 s of the start.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, spring, rotation or tilt, glitch, shake, blur, flashes, accent colours, wipes other than the slide, scale pops on captions, effects on cuts, borders or shadows on cards.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Speaking face? | Crop anchor (face y, fraction of card height) | Bar lane free? | Can D1 cover it? |
|---|---|---|---|---|---|---|---|---|

- Bar lane free = no face or readable footage text at y 0.64–0.76H. D1 may cover a shot only if no face is speaking in it.
- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: card or full frame, bar lane (default 0.70H or 0.88H), serif lane, anchor, whether D1 fits.

**Step 3 — Caption chunks.**
- C1 chunk rules: 2–3 words, ≤ 20 characters at the base size, 0.6–1.4 s, split at punctuation, never end on an article, preposition or conjunction, chunk changes at cuts when possible; a single long word may stand alone.
- Pick the C3 serif phrases (payoff or contrast, 1–3 words, max 2) and the C2 staircase phrase (inside D1).
- Output a caption table: `# | Start–End | Mode (bar / serif / stair) | Text`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | P1 (title = topic word), C1 |
| Theme or topic word | The noun the whole video is about | P1 title, T1 chip |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | C3 |
| Person → B-roll cut | Scene table | X1, K1 if the full frame helps |
| B-roll → person cut | Scene table | D2 (cut hidden under D1) or X1 |
| Any later cut | Scene table | X1 |
| List or steps | "first", "second", numbered items, 3+ parallel phrases | C1 per item, C3 on the last |
| Numbers, amounts, time phrases | Digits, "one year" | D1 + T1 + S1 |
| Long static shot (> 2 s) | Scene table | K1 or K2 (the card move is the change) |
| Section change without a cut | Pause, new topic word | K1, D1 |
| Payoff or call to action | Last line | D2 + K2 + E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **P1** (opener), **C1** (captions), **K1** (card expands), **D1** with T1 and C2 (a text-page beat, with D2 to return). Unless physically impossible: when no shot lacks a speaking face, shorten D1 to ≤ 0.6 s over a silent beat or replace it by a K2 then K1 pair, never cover a speaking face; for a video shorter than 5 s shorten P1's hold and keep K1.
- A visible change every ~1.5–3 s (new chunk, card move, page change). Never two card moves at once or within 0.6 s. Never a card move within 3 f after a cut.
- Variety: C3 at most 2×; D1 at most 2× and ≥ 3 s apart; K1 once per card state; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and inside the frame (≥ 0.04W from the edges), the bar clear of faces, the card crop holding the whole face.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render static assets (both pages with their grid, every word sprite, chip states, title) once. No random effects.
- Use the exact easing curves of the moments. Footage window: scale = max(rect w / W, rect h / H); crop box via `Image.resize(..., box=floats)`; clamp the window (`box offset can't be negative`); rounded mask at 3× then downscale; Pillow `rounded_rectangle` radius ≤ half width − 2.
- Draw text and shapes at 2× and downscale for anti-aliasing. Download Work Sans (ofl/worksans) and Newsreader from the Google Fonts GitHub repo if missing, else use the fallbacks. Measure the whole chunk before drawing the first word so the bar never resizes mid-phrase.
- Keep the render script in a scratch folder.
- Style-specific notes: the bar is fixed on the page (centre x 0.50W, y 0.70H) and does not follow the card; the bar width = chunk text + 2 × 0.028W; the staircase indent is 0.5 × the previous line width; the chip is uppercase and typed letter by letter; the cream page has tick lines, the cocoa page does not.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every card move. Look at them.
- Checklist: captions correct, in order and readable; bar sized to its chunk; no word moves after it appears; faces clear of the card edge, bar and text; cards rounded with no border; D1 cover ≤ 1.2 s and over a no-face shot; no effects on cuts; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_cocoa_grid_cards.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: P1 final state (cream page, ticks, title word if the user gave one, the photo as Card 1) and one C1 bar with the text.
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (warm cream graph-paper page, rounded video card, dark brown page with a white typed tag, brown label-bar captions with cream words).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range and mode.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; bouncing or spinning cards, borders or shadows on cards, blur, flashes, glitches, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (cream and cocoa pages with grid, P1 title, C2 staircases, T1 chip, bars on empty pages). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face (D1 only over a shot without one).
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects on cuts or any other effect not in moments.md; never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
