---
name: 24-style-mist-rise
description: Applies the "Mist Rise" motion-graphics style (white serif captions that fade in word by word with italic emphasis, long soft dissolves between shots, and a feathered band of B-roll that rises like mist from the bottom while the speaker lifts upward) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants elegant serif captions, soft cross-dissolves, a misty rising B-roll split, or a calm editorial talking-head look.
---

# 24 · Mist Rise

## 1. YOUR JOB

You are a motion designer who knows one style: Mist Rise. Work in this order:

1. Collect the inputs (section 2).
2. Analyse the footage scene by scene and line up the captions with the speech.
3. Find the hook points in the user's story and choose moments from [moments.md](moments.md).
4. Copy each moment's spec verbatim and adapt only the fields marked ✎.
5. Deliver a final video/image (build, then check by looking at frames) or a Google Flow master prompt.

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

Ask missing inputs in **one** message (max 3 short questions), stop and wait. Keep asking until every required input is in hand (if an answer is still incomplete, ask only for what is still missing).

### 2.2 Output question

Only after all inputs are in, ask exactly one question unless it is already answered: **"Do you want me to make the final video for you, or give you a master prompt for Google Flow (you paste it into Flow with your video)?"** (image: final image or Flow master prompt). If inputs and the output choice come in one message, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

**3.1 Footage is sacred.** Allowed transforms in this style (from moments.md 1.6): cross-dissolving between the user's own shots at their existing cuts; lifting the live primary shot straight up by at most 0.2125 H (translation only); showing a frozen still of the user's own footage as a plate or as a ghost (≤ 0.7 s); a slow scale of at most 1.03 on a long shot; captions on top. The primary window always plays the current footage in real time in sync with the audio. Forbidden: replacing or regenerating any shot, person, face, object or background; grading, filters or blur on shown footage; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio; a plate taken from anything except the user's own footage. Never answer C2/C4 with newly generated footage of a different person or scene.

**3.2 No nonsense text.** Every on-screen word is the user's exact word (sentence case as the user wrote it; numerals only for list counters, LST-1). All text is rendered by code with real fonts; never by an AI model in edit/still mode. **Caption audit:** joining all caption chunks reproduces the user's text word for word, in order, with the user's punctuation. Do the audit before building and again on the rendered frames.

**3.3 Smooth, no breakdowns.** Continuous motion curves from moments.md; hard switches only on the footage's own cuts (and the caption chunk exit, which is a one-frame cut by design); every element enters and exits with its moment's motion; nothing blinks; no empty or black areas; never start a big move within 3 frames (0.1–0.25 s) after a cut unless the move is that cut's own transition (DIS-1, DIS-2); never two structural moves closer than 1.0 s. Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

**3.4 Stay in style.** Only moments from moments.md, exact look and motion. The style never has: bounce or overshoot; text that slides, scales, rotates or animates per letter; any colour other than the caption ink; cards, frames, boxes, bars or stickers; tilt, shake, zoom punches or flashes; hard-edged wipes; uppercase captions; outline-only text.

**3.5 Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, and describe all moves as smooth.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- `ffprobe` for resolution, fps, duration, audio.
- Scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm visually. Dissolves and gentle cuts score low.
- Pull 2–4 frames per scene and **look at them**.
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Eye line y | Lift limit U_max | Plate candidate (best still, time) | Bright/dark behind caption zone |
|---|---|---|---|---|---|---|---|---|

  U_max = min(0.2125 H, eye_line_y − 0.08 H). Plate candidate = the sharpest face-free frame of a B-roll shot, or for single-shot videos a sharp frame at least 1.0 s away from the moment of use (SPL-3).
- Speech timing: use speech-to-text word timestamps only to **time** the user's words. Otherwise use `silencedetect=n=-30dB:d=0.12` and spread words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread the captions across the video and break at cuts.

**Step 2 — Safe zones and framing plan per scene.** Face never covered, cut or blurred while speaking. Caption anchor A1 (baseline 0.6875 H) unless a face, mouth, key action or key object sits in the 0.62–0.80 H band; then A2, then A3 (moments.md 1.3). Decide per scene whether SPL moments are allowed (U_max ≥ 0.10 H).

**Step 3 — Caption chunks.** 1–5 words, at most 34 characters, at most 2 lines; split at punctuation; break the line after a comma when there is one, otherwise near 19 characters; never end a chunk on an article or preposition; prefer chunk changes at cuts. Start = first word start; end = min(last word end + 0.1 s, next start − 0.05 s); minimum 0.4 s; leave 2–4 frames of empty screen between chunks. Emphasis = italic (CAP-2): 1–2 words, at most one phrase per chunk, at least one chunk in two, never an article or filler. No colour accents exist in this style. Write the caption table `# | Start–End | Lines | Emphasis | Block centre x`. Alternate the block centre between 0.38 and 0.68 W (change ≥ 0.03 W per chunk, away from the face).

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | first words of the video | CAP-1 on HLD-1 |
| Theme or topic word | the noun the video is about | CAP-2 |
| Contrast or turn | "but", "isn't", "instead", "the truth", "don't" | CAP-2 on the turn word; DIS-1 or DIS-2 if a cut is near |
| Person → B-roll cut | footage cut from face to scene | DIS-1 |
| Any later cut | footage cut between scenes | DIS-1, DIS-2 |
| List or steps | "first", "next", "three ways", numbers | LST-1, SPL-1 / SPL-4 on a new step |
| Numbers, amounts, time phrases | digits, "a year", "every day" | CAP-2 |
| Emphasis word on a face | the speaker leans in or smiles on a word | stay in HLD-1, CAP-2 |
| Long static shot (> 1.5 s) | no cut, no move | DRF-1, or a structural move |
| Section change without a cut | new topic, same shot | SPL-1 / SPL-3 |
| Payoff or call to action | last line | SPL-1 or SPL-3 + CAP-3 |

**Step 5 — Choose moments.**
- Signature, mandatory: CAP-1 and CAP-2 on the whole video; one SPL-1 (or SPL-3 when no B-roll exists); DIS-1 (or DIS-2) on at least one cut when the video has any cut. State which signature moves are used and which could not be (with the reason).
- Every important cut gets a beat (DIS-1 or DIS-2). Use DIS-1 for cuts involving a speaking face; use DIS-2 for B-roll → B-roll.
- Density: captions change every 0.2–0.5 s; a structural move every 2–4 s; never two structural moves closer than 1.0 s.
- Variety: the same moment type at most 2 times (DIS-1 and DIS-2 count as different types); different videos get different plans.
- Secondary content is always meaningful user footage: the plate is a still of a B-roll shot that the story mentions or follows, or (SPL-3) a different moment of the same video.
- Output plan table: `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…)`.

**Step 6 — Adapt.** Copy each spec and change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and inside x 0.12–0.88 W, nothing collides, no structural moves closer than 1.0 s.

**Step 7 — Build (Python + ffmpeg).**
- Decode raw frames from the source with `ffmpeg -f rawvideo -pix_fmt rgb24`, composite per frame with Pillow and NumPy (float32), encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <source fps>`, map `-map 1:a -c:a copy`.
- Pre-render static assets once with fixed seeds: caption chunk layers (per word, with halo and shadow, 4 blur variants), plate stills (cover-fit about 1.2x, anchor ✎), ghost stills (last frame before a cut).
- Exact easing curves from moments.md; sub-pixel moves via `Image.resize(..., box=floats)`; draw text at 2x and downscale.
- Fonts: EB Garamond Regular and Italic from the Google Fonts GitHub repo (`ofl/ebgaramond`); variable files need `font.set_variation_by_name('Regular')` / `'Italic'`. If the download is not possible, use the fallbacks in moments.md 1.4, in order. Measure text with `font.getlength` before drawing.
- Compositing order per frame: primary shot (lifted if SPL) → plate through the feather mask → ghost or dissolve layers → captions on top.
- Style-specific: the plate is a still and never moves while held; the mask feather is vertical only; the caption layout is fixed per chunk and words never reflow; chunk exits are one-frame cuts.
- No code execution available → deliver an editor build sheet instead: layers, keyframes (with the numbers from moments.md), caption text with timings, CapCut / After Effects steps, and an SRT file.

**Step 8 — Check before delivering.** Make a contact sheet at 3–4 fps and extract frames around every cut and moment; **look at them**. Checklist: captions correct, in order and readable, not over faces; caption audit passes on the rendered frames; faces safe (eye line ≥ 0.08 H after any lift); no unintended jumps; the primary shot is in sync; the plate is frozen and has no visible hard edge; ghost lasts ≤ 0.7 s; each word fades in over 4 frames and each chunk leaves in one; duration, fps, resolution and audio match the source; every signature moment is present. Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save `<original name>_mist_rise.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

Show the moments in their settled state: the image at its natural framing, the caption block from CAP-1 (with CAP-2 italics) at anchor A1, soft shadow and halo. Optional: SPL still state (two crops of the same image joined by a soft mist edge, upper crop shifted up by 0.2125 H, caption block on the lower crop). Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6 first, then write one self-contained prompt per Flow clip (≤ 8 s each; split at cuts; add a CONTINUITY paragraph to every clip after the first). Use this order:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph: calm, elegant, white serif lettering that fades in word by word with slanted italic key words, long soft dissolves between shots, and a soft band of the user's own B-roll that rises from the bottom like mist while the speaker glides upward.
4. **TEXT INVENTORY:** every allowed word; tricky words spelled letter by letter; end with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text from moments.md, filled>`.
6. **CAPTIONS:** every phrase with its time range and which words are italic.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled lettering; bounce, shake, zoom punches, flashes, boxes, stickers, coloured text, uppercase lettering, hard-edged wipes.

Plain words only: no px, %, hex codes or font names, and never the words "karaoke" or "highlight". Deliver the prompts in code blocks, plus a caption table and an SRT file, and say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

Plan scenes from the story, time the captions, choose moments. Master prompt → section 6 with the story scenes. Final video → a graphics and typography-only piece rendered in code in this style (the captions, the dissolves and the split mechanics on neutral plates built from the user's description; no fake footage of people). Image → a typography poster in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim; never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, and never let an AI model draw captions in edit or still mode.
- Never break the style's "never" items (3.4) or invent moments.
- Never ask beyond the missing inputs plus the one output question.
- Never deliver without looking at the rendered frames.
