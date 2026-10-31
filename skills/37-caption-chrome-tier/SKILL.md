---
name: 37-caption-chrome-tier
description: Applies the "Chrome Tier" motion-graphics style (untouched full-frame footage with two-tier captions: small light white sans words and large heavy italic keywords filled with a glossy teal-silver chrome gradient, stepping down the lower frame in a staggered left/right stack, with a one-line headline at the top on opening) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants metallic, chrome, glossy, big-italic-keyword, modern sans caption looks.
---

# 37-caption-chrome-tier — Chrome Tier

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
- Allowed transforms (from moments.md 1.6): full-frame display, untouched; text and shadow overlays only.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, split screens, background swaps, blur, dimming, glitch, warp, zoom, flashes, colour grading or filters of any kind; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote (this style does not force uppercase). Numerals only if the user wrote them.
- Headline words come from the user's own text; never invent a title.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks (including headline chunks) reproduces the user's text word for word and in order. Run it before building (`assert " ".join(words) == TEXT`).

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; words never move after they appear; chunk switches are hard cuts or 3 f fades by design.
- Nothing blinks; no empty or black areas.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, slides, letter-by-letter typing, rotation, blur on text, flashes, effects on cuts, uppercase conversion, plain flat-colour keywords, extra colours, boxes or plates behind text, more than one keyword per chunk (except K3).

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Face bottom edge | Lower-lane luminance (0–1) | Footage text in lane? | Best side (L/R) |
|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: lane (lower by default, top for one-line chunks), side, whether T1 fits.

**Step 3 — Caption chunks.**
- 2–5 words per chunk, 0.6–1.7 s, split at punctuation, avoid ending on an article, preposition or conjunction, chunk changes near cuts when possible (X1).
- Pick exactly one keyword per chunk (a noun, verb or number that carries the meaning); K3 pairs at most twice.
- Output a caption table: `# | Start–End | Side | Lane | Text | Keyword`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First words, first 0.5 s | T1 |
| Theme or topic word | The noun the video is about | keyword in C1 |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | K3, K2 |
| Person → B-roll cut | Scene table | X1, C3 if the lane is blocked |
| B-roll → person cut | Scene table | X1, C3 |
| Any later cut | Scene table | X1 |
| List or steps | "first", numbered items, 3+ parallel phrases | C2 side flips, one keyword per item |
| Numbers, amounts, names | Digits, proper nouns | K1 keyword or K2 |
| Long static shot (> 2 s) | Scene table | C1 chunk change |
| Section change without a cut | Pause, new topic word | T2 |
| Payoff or call to action | Last line | K2, E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **C1 with K1** (every chunk), **T1** (opener, if the face box top allows; else a lower-lane C1), **C2** (side flips whenever two or more chunks are in a row), **X1** (caption carries across cuts). For a video shorter than 3 s, keep one chunk and T1 only.
- A visible change every ~1.5–3 s. K2 at most 2×, ≥ 3 s apart; T2 only for a real new topic; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and inside the frame (≥ 0.07W from the edges), small words not over footage text.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render every word sprite once at 2× and downscale; lay out each chunk completely before its first word appears so no word moves.
- Use Inter (variable weight 380) for small words and Inter Tight Black Italic for keywords; download fonts from the Google Fonts GitHub repo if missing, else use the fallbacks. Track letters per character; place baselines with `getbbox("H")`.
- Keyword gradient: build with NumPy from the moments.md stops, mask with the text, add the dark edge and shadow.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut and every chunk change. Look at them.
- Checklist: captions correct, in order and readable; small words white and light, keywords chrome; no word moves after it appears; lines do not overlap; faces safe; no effects on cuts; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_chrome_tier.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: one C1 chunk in the lower lane (or T1 at the top if the face allows).
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (small thin white words, big heavy slanted keywords with a glossy blue-silver metal shine, a staggered stack in the lower frame, plain cuts).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range, side and keyword.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; boxes behind text, flat-colour keywords, transition effects, glitches, blurs, flashes, bouncing or spinning text, all-capital text, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a typography-only piece rendered in code (plain dark or light plate in the user's palette if given, C1 chunks, hard cuts between plates). No fake footage.
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
