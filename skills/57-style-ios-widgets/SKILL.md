---
name: 57-style-ios-widgets
description: Applies the "iOS Widgets" motion-graphics style (untouched full-frame footage with frosted glass home-screen widgets dropping into the top corners, solid blue check pills ticked by a mouse cursor, a glass capsule closer, a white profile card whose Follow button gets clicked, and bold white captions with one word in a blue pill) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants iOS widgets, frosted glass UI, system blue pills, cursor clicks, a follow card or a phone-interface look.
---

# 57-style-ios-widgets — iOS Widgets

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
- Allowed transforms (moments.md 1.6): full-frame display; glass widgets, pills, capsule, card and cursor drawn over it, each blurring only the footage under its own shape.
- The primary footage always plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; grading or filters on the footage outside a panel; blur or zoom of the footage; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Avatars come from a still crop of the user's own speaker or subject. Never generate a person.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word with the user's case. The only other words are the UI labels "Follow" and "Following" inside F1 (drop F1 if the user objects).
- Widget, pill and capsule text is a complete phrase copied as-is from the user's captions (a whole step or noun phrase), or a counter numeral ("0/3", "3/3" for the steps in the script), or a real number the user wrote. Never assemble labels from scattered words or fragments; if no complete phrase fits, leave the widget text out. No percentage text on progress bars.
- The Follow card shows only the avatar (still crop) and the Follow/Following button. A name or handle appears only if the user gives it.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks (C1 chunks plus the E1 capsule text) reproduces the user's text word for word and in order. Check that every widget and pill text is a verbatim contiguous phrase of the user's text (or a counter). Run both before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on the footage's own cuts and for caption chunks.
- Panels exit before a cut (≥ 0.05 s) and never across it; new panels never start within 0.3 s after a cut.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md, with their exact look and motion. Never: full-frame slides, wipes, flashes, shake, glitch, rotation, footage blur or zoom, extra colours, outline text, more than 3 pills in one shot, two glass widgets over the speaker's face.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Free corners (left/right top) | Lane luminance (0–1) | Pill field free? | Crop anchor |
|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: which top corners are free for widgets, where the pill field goes (move up if the face is low), caption lane (C1 or C2), whether the bottom is free for F1.

**Step 3 — Caption chunks.** Use the C1 rules (3–5 words, split at punctuation, never end on an article, preposition or conjunction, changes at cuts when possible). Mark ≤ 1 keyword per chunk, ≤ 3 per video. The last 2–4 words become E1 text. Output a caption table `# | Start–End | Mode | Text | Keyword`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1 (+W2) |
| Theme or topic phrase | A complete noun phrase the video is about | T1 progress header |
| List or steps | "first", "then", 2–3 parallel phrases | K1 per item |
| Growth, time, effort phrase | "more", "year", "every day" | W2, T2 |
| Contrast or turn | "but", "isn't", "instead" | keyword pill in C1 |
| Person → B-roll cut | Scene table | K1 starts on the B-roll |
| B-roll → person cut | Scene table | E1 or F1 |
| New topic without a cut | Pause, new topic word | T2 |
| Numbers, names | Digits the user wrote | counter widget (T1/T2) |
| Long static shot (> 2 s) | Scene table | M1 floats, K1 |
| Payoff or call to action | Last line | E1 + F1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1** (opener), **K1** (at least one pill when there is any list or claim; else one pill on the key phrase), **C1** (captions), **E1** (last line), **F1** (call to action, last 1.5 s). Unless physically impossible: for a video shorter than 3 s drop F1 first, then K1; never drop C1.
- A visible change every ~1.5–3 s. Never two big moves < 0.5 s apart. T2 only once per video and only on a shot with a free corner.
- Output the plan table: `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason`.

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, text readable and inside the frame (≥ 0.04W from the edges), pills not on a face, E1 above F1.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow, NumPy and OpenCV, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Glass: blur each frame once (Gaussian σ 14), then inside each rounded-rect mask blend: backdrop × (1 − up to 0.20 darkening by brightness) with saturation ×1.4, white 22 % tint, a white 0→11 % top sheen and a 1.6 px white 45 % rim; shadow under it. The card uses white 80 % and no darkening.
- Draw masks, text and icons at 2–3× and downscale. Pre-render widget content, pill sprites (unchecked and checked), caption words (and a plain and a pill version of each keyword), the capsule and the card states (Follow, Following) once.
- Fonts: Inter (variable, weights per moments.md 1.4); fallbacks Manrope, Plus Jakarta Sans. Download from the Google Fonts GitHub repo if missing. Measure text before drawing.
- Cursor: pre-render at 6× (arrow with white outline, soft shadow); tip is the hot spot.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Contact sheet at 1–3 fps plus frames around every click, every cut and the F1 sequence. Look at them.
- Checklist: captions correct, in order and readable; one blue keyword pill at most per chunk; glass readable on bright shots; pills not covering faces; cursor tip on the pill icon at the click; no panel across a cut; E1 and F1 do not collide; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** `<original name>_ios_widgets.mp4` (claude.ai: `/mnt/user-data/outputs/`); brief reply with a compact plan table, assumptions, what the user may want changed.

## 5. STILL MODE (C4)

Moments in their settled state: T1 widgets (bar full), K1 pills ticked with the cursor on the last, F1 card with Following, or E1. Default poster: widgets top, pills in the pill field, text in the capsule. Never alter the photo; export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Same steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP (scene by scene with timestamps) · 3 STYLE (plain-words paragraph: frosted glass widgets, bright blue tick pills, a mouse cursor, a white profile card, bold white captions) · 4 TEXT INVENTORY (every allowed word, tricky words spelled letter by letter, plus "Follow" and "Following") · 5 TIMELINE (each moment with start and end, its Flow prompt text filled in) · 6 CAPTION LINES with times · 7 DO NOT list (no extra words, no logos, no new people, no colour changes, no camera moves) · 8 AUDIO (keep the original). Never write px, %, hex codes, font names or the word "karaoke". Add an SRT backup.

## 7. GENERATE MODE (C1)

Plan scenes from the story, time the captions, choose moments. Master prompt → section 6 with story scenes. Final video → an interface-only piece rendered in code (soft gradient backdrop, widgets, pills, cursor, card), no fake footage. Image → a poster in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image; never pause, reorder, speed up or trim; never desync the footage.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen (except Follow and Following) or let an AI model draw captions in edit or still mode.
- Never break the style's "never" items (3.4) or invent moments.
- Never ask beyond missing inputs plus the one output question.
- Never deliver without looking at the rendered frames.
