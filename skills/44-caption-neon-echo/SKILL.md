---
name: 44-caption-neon-echo
description: Applies the "Neon Echo" caption style (untouched full-frame footage, small bold white word-by-word captions, lime italic glowing keywords, a giant scan-lined neon slab for one payoff word, an outline title that slides across the top and a stack of outline echoes behind the speaker) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants neon, lime, glow, bold pop captions or outline text.
---

# 44-caption-neon-echo — Neon Echo

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
- Allowed transforms (moments.md 1.6): full-frame display, untouched; text overlays with shadow; for T2 only, the outline stack drawn behind a person cut-out of the live footage.
- The primary footage always plays in real time in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, B-roll frames, background swaps, graphic transitions; blur, glitch, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. Captions keep the user's case and punctuation; slab, title and stack words are uppercase copies of one user word each. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks reproduces the user's text word for word and in order (slab, title and stack words are extra copies of words already in the chunks). Run it before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on the footage's own cuts and for chunk swaps (hard cuts by design).
- No chunk straddles a cut. Never start T1 within 0.3 s after a cut; T1 ends ≥ 0.2 s before the next cut.
- Faces are never covered. Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: letter-by-letter typing, bounce, slides on captions, boxes behind text, shake, flashes, caption rotation, extra colours.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.** `ffprobe`; scene cuts with `select='gt(scene,0.3)'` (retry 0.12–0.2 if none; confirm visually); look at 2–4 frames per scene. Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Lane luminance | One clear person? | Best lane |
|---|---|---|---|---|---|---|---|

Speech timing: speech-to-text timestamps only to time the user's words; else `silencedetect=n=-30dB:d=0.12` and syllable-weighted spreading (0.15 s pause at commas, 0.3 s at full stops). No speech: spread phrases across each shot.

**Step 2 — Safe zones and framing.** Per scene: lanes clear of the face, title lane free (face top ≥ 0.12H), whether T2 can run (one clear person).

**Step 3 — Caption chunks.** 2–5 words, 0.7–1.6 s, split at punctuation, never end on an article, preposition or conjunction, never straddle a cut. One keyword per chunk at most, ≤ 4 per 5 s. Table: `# | Start–End | Lane | Text | Keyword | Slab`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence | T1, C1 |
| Topic word | The noun the video is about | T1, K1 |
| Contrast or turn | "but", "isn't", "instead" | K1 |
| Any cut | Scene table | X1, C2 |
| List or steps | 3+ parallel phrases | K1 per item, K2 on one |
| Numbers, amounts, time | Digits, "one year" | K2 |
| Payoff or last line | Last sentence | T2, K1, E1 |

**Step 5 — Choose moments.** Mandatory: C1, K1, X1, K2 (once, twice if the video is longer than 8 s), T1 (when the face allows it), T2 (when a person shot exists in the second half). Never two big moves (K2, T1, T2 start) within 0.6 s. Output plan table `# | Moment ID | Start–End | ✎ Text | ✎ Lane | Reason`.

**Step 6 — Adapt.** Copy specs, change only ✎ fields. Check every frame: faces safe, captions inside the frame, readable.

**Step 7 — Build.** Python + ffmpeg: decode raw frames, composite per frame with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`. Pre-render words, slab, title and stack row at 2×. Segmentation for T2: mediapipe ImageSegmenter, VIDEO mode, EMA mask. Measure text before layout; lay out each chunk completely before its first word. Keep the render script in a scratch folder. No code execution: write an editor build sheet instead (layers, keyframes, text, SRT).

**Step 8 — Check.** Contact sheet (3–4 fps) plus frames around each cut, K2, T1 and T2. Look at them. Checklist: captions correct and in order; keywords lime; slab readable; title clear of the face; stack behind the person; no chunk across a cut; duration, fps, resolution, audio match. Fix and re-render.

**Step 9 — Deliver.** `<original name>_neon_echo.mp4`. Brief reply with the plan table, assumptions and what the user may change.

## 5. STILL MODE (C4)
Settled states: T1 at the top or T2 behind a person, one C1 chunk with a lime keyword, optional K2. Never alter the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Run steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP · 3 STYLE (small bold white captions, lime slanted glowing keywords, giant glowing lime slab word, outlined title sliding across the top, outlined word echoed behind the speaker) · 4 TEXT INVENTORY (every allowed word, "Nothing else is written anywhere.") · 5 TIMELINE · 6 CAPTIONS with time ranges and keywords · 7 NEGATIVE (changing the person, face, outfit, background; new scenes; reordered shots; changed colours or audio; extra or misspelled text; boxes behind captions; transitions, flashes, shake). Plain words only. Deliver in code blocks plus a caption table and SRT; say "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Master prompt → section 6. Final video → typography-only piece in code on a plain dark plate (C1, K1, K2, T1; no T2, no fake footage). Image → typography poster.

## 8. NEVER DO
- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the footage.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add cards, splits, background swaps or effects not in moments.md.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
