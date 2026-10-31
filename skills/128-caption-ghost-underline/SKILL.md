---
name: 128-caption-ghost-underline
description: Applies the "Ghost Underline" caption style (untouched full-frame footage, mid-frame captions that build word by word as ghost-grey words firming up to white heavy bold sans, one slim serif italic keyword per phrase with a thin two-colour gradient underline, hard-cut chunks, optional italic title) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants bold word-by-word captions, serif italic keywords, underlined highlights or a clean modern caption look.
---

# 128-caption-ghost-underline — Ghost Underline

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
- Allowed (moments.md 1.6): full-frame display untouched; text, shadow and underline overlays.
- The primary footage always plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, boxes, B-roll frames, background swaps, graphic transitions; blur, grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word with the case they wrote. Numerals only if the user wrote them.
- Titles use the user's own words.
- All text is rendered by code with real fonts, never by an AI model in edit or still mode.
- **Caption audit:** joining the title words and all caption chunks reproduces the user's text word for word and in order. Run it before building (assert in code).

3.3 **Smooth, no breakdowns.**
- Words enter with the C1 colour ramp; chunks leave on a hard cut; hard switches only on chunk boundaries and footage cuts.
- Never lay out a chunk so that a word moves after it appears.
- Never start a title within 0.3 s after a cut; a title fade must finish ≥ 0.3 s before a cut.
- Every glyph stays ≥ 0.05W from the side edges; assert every text box in code. Captions and titles never overlap each other and never cover the face box.
- Output keeps source resolution, fps, duration (±1 frame) and the original audio (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: bounce, overshoot, slides, letter-by-letter typing, scale pops, rotation, wipes, glitch, shake, flashes, effects on cuts, uppercase conversion, outline-only text, boxes or plates behind text, a second accent colour beyond the gradient.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm visually.
- View 2–4 frames per scene. Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Face bottom edge | Lane busy/bright (0–1) | Lane shift | Footage text in lane |
|---|---|---|---|---|---|---|---|---|

- Speech timing: speech-to-text word timestamps only to time the user's own words; else `silencedetect=n=-30dB:d=0.12` and syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.0 s each).

**Step 2 — Safe zones.** Face never covered while speaking. Per scene decide lane centre (moments.md 1.7), whether a title fits, and whether text on the footage needs a lane shift.

**Step 3 — Caption chunks.** C1 rules: 2–6 words, ≤ 28 characters per line, split at punctuation, never end on an article, preposition or conjunction, prefer changes near cuts. One K1 keyword per chunk (a second only in chunks of ≥ 5 words); never an article. Output the caption table `# | Start–End | Text | Keyword | Lines`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 |
| Theme or topic word | The noun the video is about | T1 title, K1 |
| Contrast or turn | "but", "isn't", "instead", "never" | K1 |
| Person → B-roll cut | Scene table | X1 |
| B-roll → person cut | Scene table | X1 |
| Any later cut | Scene table | X1 |
| List or steps | "first", numbered or 3+ parallel phrases | one chunk per item with K1 |
| Numbers, amounts, names | Digits, proper nouns | K1 or C3 |
| Long static shot (> 2 s) | Scene table | chunk rhythm only |
| Section change without a cut | Pause, new topic word | T2 |
| Payoff or call to action | Last line | C3, E1 |

**Step 5 — Choose moments.** Signature moments mandatory in every output: **C1** (all captions), **K1** (underlined italic keyword in every chunk that has one). T1 and C3 are strongly recommended; E1 always. A visible change every ~1.5–3 s; C3 at most 2×; T2 only for a real new topic. Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each spec; change only ✎ fields. Check every frame: faces safe, text inside the frame, nothing colliding.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p`, `-map 1:a -c:a copy`.
- Pre-render each word's glyph mask and shadow mask once at 2× then downscale; tint per frame. Download fonts from the Google Fonts GitHub repo if missing, else use fallbacks.
- Measure words with `font.getlength`; lay out each chunk completely before its first word appears. Align sans and serif baselines using font ascents.
- Variable fonts: set axes explicitly (check the axis order with `get_variation_axes`).
- Style notes: keyword weight ≥ 500; underline = 3 px gradient under the glyph advance; shadow 90 % black blurred 6 px.
- Keep the render script in a scratch folder. No code execution: write an editor build sheet (layers, keyframes, text, SRT).

**Step 8 — Check before delivering.** Contact sheet at 3–4 fps plus frames at every cut and moment. Look at them. Checklist: captions correct and in order; ghost-to-white fade visible; keywords italic with underline; no word moves; text inside margins; face clear; title and captions never overlap; no effects on cuts; audio, fps, resolution, duration match. Fix and re-render.

**Step 9 — Deliver.** Save as `<original name>_ghost_underline.mp4`. Reply with a compact plan table, assumptions and what the user may want changed.

## 5. STILL MODE (C4)

Settled state of C1 with K1 (one chunk in the lane) plus optional T1; photo untouched; export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP · 3 STYLE (heavy white sans captions building word by word from grey, one slim slanted pale keyword per phrase with a thin colour-fading underline, plain cuts) · 4 TEXT INVENTORY (every allowed word; end "Nothing else is written anywhere.") · 5 TIMELINE (`[start–end s] MOMENT NAME. <Flow prompt text>`) · 6 CAPTIONS (line, time range, keyword) · 7 NEGATIVE (changing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; boxes, bars, transitions, glitches, blurs, flashes, bouncing text, all-capital text, camera shake). Plain words only. Deliver in code blocks plus a caption table and SRT; say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

Plan scenes from the story, time captions, choose moments. Master prompt: section 6. Final video: a typography-only piece on a plain dark plate with C1, K1, C3 (no fake footage). Image: a typography poster in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary footage.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add cards, boxes or effects, or break the style's "never" items (3.4).
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
