---
name: 126-caption-arc-crown-caps
description: Applies the "Arc Crown Caps" caption system (untouched full-frame footage; the key word of each phrase as a bold accent-colour arch with a small 3D edge curved above the speaker's head, and the small words stacking as tilted white heavy caps on the chest, with a huge white solo word on punchlines) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants kinetic reels captions, a curved headline word over the head, bold keyword arches, tilted white word stacks.
---

# 126-caption-arc-crown-caps — Arc Crown Caps

Style data lives in [moments.md](moments.md). Read it fully before planning. This is a caption system only: no cards, layouts, transitions or footage effects.

## 1. YOUR JOB

You are a motion designer who knows one style. Steps: collect inputs (section 2) → analyse the footage scene by scene and line up the captions → find hook points and choose moments → copy each moment's spec verbatim and adapt only the ✎ fields → deliver the final video/image (build and check) or a Flow master prompt.

The value you add is choosing the keyword of every phrase and placing the stack so nothing touches a face. You never invent a new look, and you never alter the user's footage.

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
- Allowed transforms (moments.md 1.6): none. Full frame, untouched, live and in sync with the audio. Text, outline and shadow layers only.
- Forbidden: replacing or regenerating any shot, person, face, object or background; zoom, crop, blur, glitch, flashes, grading or filters; cards, splits, masks, cut-outs, B-roll frames, transitions; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. UPPERCASE is a display transform of this style; punctuation stays. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all words from the arch keywords, stack words and solo words in time order reproduces the user's text word for word (assert it in code before building).

3.3 **Smooth, no breakdowns.**
- Continuous curves from moments.md; every element enters and exits with its moment's motion; nothing blinks; one arch at a time.
- All text (including entrance scale and blur halo) inside x 0.05W–0.95W and y 0.02H–0.98H; assert the bounding boxes of every text sprite in the build.
- Captions never overlap each other, and no glyph, extrusion or shadow touches the speaking face box (test by ink mask, not by bbox).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md, exact look and motion. One accent colour per video. Never: boxes or plates behind text, bounce, spring, slides, letter-by-letter typing, shake, flashes, scale pops after the entrance, more than one arch at once, lowercase, extra colours.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

- **Step 1 Ingest & analyse:** ffprobe; scene cuts (threshold 0.3, retry 0.12–0.2 if none; confirm visually); 2–4 frames per scene and **look at them**; scene table `Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Head top y | Arch zone free? | Chest lane free? | Bright (luma > 0.55)?`; speech timing (speech-to-text word timestamps only to time the user's words, else `silencedetect=n=-30dB:d=0.12` + syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops; no speech → spread across the video, breaking at cuts).
- **Step 2 Safe zones:** per shot, the face box and the lanes (1.3). Decide per shot: crown arch (C1) or low arch (K1); chest, lower or side lane for the stack.
- **Step 3 Pick words:** split text into phrases at punctuation (3–6 words). Per phrase choose ONE keyword (topic noun, instruction verb, number, time phrase, payoff word; never an article or preposition). Everything else is stack. Put one solo word (C3) on a punchline if the phrase ends on a strong word. Compute hold per keyword (0.65–1.45 s, longer for slower speech) and end = min(start + hold, next keyword − 0.02 s); a keyword placed in the crown zone must end before a cut to a shot whose face sits in that zone. Group the stack words per phrase (exit 0.5 s after the last word, ≥ 0.15 s before the next group).
- **Step 4 Hook points:** `Hook point | How to spot it | Typical moments` for: opening line (T1), topic word (C1), contrast or turn word (C1), list items (C1 + C2), numbers and time phrases (C1), punchline (C3), each cut (K1/lane switch, no new keyword within 3 frames if avoidable), long static shot (keep C4 rhythm), payoff (C1 or E1).
- **Step 5 Choose moments:** C1, C2, C3 and C4 mandatory; K1/C6 only where a face demands it; a visible change every 0.8–2 s; no two keywords closer than their hold. Output plan table `# | Moment | Start–End | ✎ Text | ✎ Lane/tilt | Reason`.
- **Step 6 Adapt:** copy the spec, change only ✎ fields; choose the accent: reference default amber unless the user gives a brand colour; if the footage is dominated by that hue, pick a contrasting saturated colour (one per video).
- **Step 7 Build:** Python + ffmpeg: decode raw frames, composite per frame with Pillow, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 0:v -map 1:a -c:a copy`. Pre-render each text sprite once at 2x and downscale. Arch letters: place on a circle (radius 0.95W), rotate to the tangent, extrude, shadow. Run the caption audit and bbox/face/overlap asserts every frame. Fonts: Poppins Black / ExtraBold (download from the Google Fonts GitHub repo if missing; fallbacks in 1.4). No code execution → editor build sheet (text-on-path layers, keyframes, SRT).
- **Step 8 Check:** contact sheet (1–3 fps) + frames at every keyword change and cut; **look at them**. Checklist: words correct and in order; arches readable and not cut off; faces clear; white words readable on bright shots; no overlap; margins; duration/fps/resolution/audio match; signature moments present. Fix and re-render; never deliver unchecked.
- **Step 9 Deliver:** `<original name>_arc_crown_caps.mp4` (claude.ai: `/mnt/user-data/outputs/`); brief reply with the plan table, accent used, assumptions.

## 5. STILL MODE (C4)
One arch keyword in the crown zone, a settled white stack in the chest lane; never alter the photo; export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Same steps 1–5, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, face, clothes, movements, background, colours, timing and audio EXACTLY as they are. Only add the captions described below.") · 2 INPUT VIDEO MAP · 3 STYLE (plain words) · 4 TEXT INVENTORY (every allowed word; "Nothing else is written anywhere.") · 5 TIMELINE (`[start–end s] MOMENT NAME. <Flow prompt text, filled>`) · 6 CAPTIONS (each line with time range) · 7 NEGATIVE (no new people, no changed footage, no boxes, no extra text, no flashes).

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Master prompt → section 6 with story scenes. Final video → typography-only piece rendered in code on a flat dark plate (no fake footage).

## 8. NEVER DO
Never replace footage, person or image; never pause, reorder, speed up or trim; never desync; never cover, cut or blur a speaking face; never put non-user words on screen or let an AI model draw captions in edit or still mode; never show two arches at once or let captions overlap; never let text cross the 0.05W side margins; never add boxes, bounce, flashes or extra colours; never ask beyond missing inputs + the one output question; never deliver without looking at rendered frames.
