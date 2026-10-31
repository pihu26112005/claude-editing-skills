---
name: 33-style-bauhaus-pop
description: Applies the "Bauhaus Pop" motion-graphics style (flat orange, cobalt, mustard and cream poster colours; a condensed cream banner stamp; cream label-bar captions with the newest word in orange; black-edged footage cards with a retracting extruded shadow; a falling curtain of circles and bars to a blue shape wall) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a bold poster, geometric, Bauhaus, colour-block or label-caption look.
---

# 33-style-bauhaus-pop — Bauhaus Pop

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
- Allowed transforms (moments.md 1.6): full-frame display; cover-fit crops into cards; a still of the speaker in a secondary card (≤ 1.5 s); curtain and wall covering a non-speaking shot (wall hold ≤ 1.0 s, total cover ≤ 1.7 s, once per 8 s); overlays.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word; case as written except banner and tag, which are uppercase. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining the banner words, all caption chunks, wall words and tag words, in order, reproduces the user's text word for word. Run it before building (`assert`).

3.3 **Smooth, no breakdowns.**
- Continuous curves from moments.md; hard switches only on footage cuts and caption chunks.
- Never start a banner entrance within 0.4 s after a cut; banner exit ends on or before the first cut; never start a curtain pass within 0.25 s after a cut.
- The face box (speaking) stays visible from frame 0: banner height shrinks to clear it, no curtain or wall over a speaking face, flashes none.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: bounce, spring, tilt, outlines, gradients, glow, shake, zoom punches, extra colours, text in other fonts, lowercase banner.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.** `ffprobe`; scene cuts with `select='gt(scene,0.3)'` (retry 0.12–0.2); look at 2–4 frames per scene. Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Chin y | Best card layout | Crop anchor |
|---|---|---|---|---|---|---|---|

Speech timing: speech-to-text word timestamps only to time the user's words; else `silencedetect=n=-30dB:d=0.12` plus syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops; no speech → spread across the video, breaking at cuts.

**Step 2 — Safe zones and framing plan.** Per scene: face box, banner height (≤ face top − 0.01H), bar lane (moments.md 1.7), card crop anchors.

**Step 3 — Caption chunks.** 2–5 words, ≤ 2 lines, split at punctuation, never end on an article or preposition, chunk changes on cuts; banner words removed from the first chunk; start = first word, end = min(next start − 0.05, cut). Caption table `# | Start–End | Mode | Text` and the audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence | T1, C1 |
| Theme or topic word | The noun the video is about | T1 text |
| Contrast or turn | "but", "isn't", "instead" | C1 |
| Person → B-roll cut | Scene table | L1 (speaker still on top) |
| B-roll → B-roll cut | Scene table | L2 + X1 |
| B-roll → person cut | Scene table | E1 |
| List or steps | 3+ parallel phrases | C2, C3, X2 + W1 |
| Numbers, time phrases | Digits, "one year" | C3 or W1 |
| Long static shot (> 1.5 s) | Scene table | C1 chunk change |
| Payoff or call to action | Last line | E1 |

**Step 5 — Choose moments.** Signature moments are mandatory: **T1**, **C1**, **L1**, **X1**, **X2** (+ **W1** with it). For a video under 4 s: shorten T1's hold, one card moment, one curtain pass; never drop T1 and C1. A visible change every ~1.5–3 s; never two big moves < 0.6 s apart; L1/L2 ≤ 2× each, W1 once. Plan table `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason`.

**Step 6 — Adapt.** Copy specs, change only ✎ fields. Check every frame: face safe, captions inside frame, nothing collides.

**Step 7 — Build.** Python + ffmpeg: decode raw frames, composite per frame with Pillow, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`. Pre-render banner letters, collage and wall once; draw polygons and ellipses at 2× and downscale; sub-pixel crops via `Image.resize(box=floats)` with clamped boxes; fonts from the Google Fonts GitHub repo if missing (DM Sans, Anton). Keep the render script outside the skill folder. No code execution → editor build sheet (layers, keyframes, SRT).

**Step 8 — Check.** Contact sheet (fps 1.2) plus frames around every cut, the curtain and the card peel; look at them. Checklist: captions correct and readable; faces safe; no unintended jumps; primary in sync; duration/fps/resolution/audio match; signature moments present. Fix and re-render.

**Step 9 — Deliver.** `<original name>_bauhaus_pop.mp4`; brief reply with the plan table, assumptions and what the user may want changed.

## 5. STILL MODE (C4)
Banner with the user's headline word, a poster card with the photo (never altered), bar caption below. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s, split at cuts, CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, face, clothes, movements, background, colours, timing and audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP · 3 STYLE (plain words: flat orange, blue, yellow, cream and black poster colours, cream label strips, framed cards with a long black shadow) · 4 TEXT INVENTORY (every allowed word, "Nothing else is written anywhere.") · 5 TIMELINE (`[start–end s] MOMENT NAME. <Flow prompt text, filled>`) · 6 CAPTIONS (line, time range, newest word orange) · 7 NEGATIVE (changing the person, face, outfit, background, new scenes, reordered shots, changed footage colours or audio, extra or misspelled text, gradients, glow, shake). Plain words only. Deliver in code blocks plus caption table and SRT; advise 2–4 generations and keep the best.

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Master prompt → section 6. Final video → a graphics-and-typography-only piece in code (banner, cards with colour fields, wall, captions; no fake footage). Image → typography poster in code.

## 8. NEVER DO
- Never replace footage, person or image. Never pause, reorder, speed up or trim; never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen or let an AI model draw captions in edit/still mode.
- Never break the "never" list or invent moments.
- Never ask beyond missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
