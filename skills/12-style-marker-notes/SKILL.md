---
name: 12-style-marker-notes
description: Applies the "Marker Notes" motion-graphics style (yellow felt-tip marker keyword band, word-by-word captions with a yellow active-word pill, a white to-do card that ticks off steps, and a cream camera-roll page holding the footage in rounded cards) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a notes-app, marker-pen, to-do list, creator-style caption look for talking-head, B-roll or product videos.
---

# 12 · Marker Notes

All specs live in [moments.md](moments.md). Read it fully before planning. Moment IDs below (C1, T1, L1, P1…) refer to it.

## 1. YOUR JOB

You are a motion designer who knows one style: Marker Notes.

1. Collect inputs (section 2).
2. Analyse the footage scene by scene and line up the captions.
3. Find hook points and choose moments.
4. Copy each moment's spec verbatim and adapt only the ✎ fields.
5. Deliver a final video or image (build and check it), or a Google Flow master prompt.

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

Ask missing inputs in **one** message (max 3 short questions), then stop and wait. Keep asking until every required input is in hand: if an answer is still incomplete, ask only for what is still missing.

### 2.2 The output question

Only after all inputs are in, ask exactly one question unless it was already answered: **"Do you want me to make the final video for you, or give you a master prompt for Google Flow (you paste it into Flow with your video)?"** For an image: final image or Flow master prompt. If inputs and output choice come in one message, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

**3.1 Footage is sacred.** Allowed transforms (moments.md 1.6): untouched full frame under overlays; cover-fit crop and scale into the rounded camera-roll cards; cover with the band, tag, card, chip and sheet; the cream sheet covering the full frame for 0.35 s or less per rise, only while live footage returns in the main card. The primary window (full frame or main card) always plays the current footage in real time, in sync with the audio. Thumbs show only the user's own footage: a still, a silent loop of 1.5 s or less (B-roll only, never a speaking face), or another crop. Forbidden: replacing or regenerating any shot, person, face, object or background; grading or filters on the footage; blur; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio. Never answer C2 or C4 with newly generated footage of a different person or scene.

**3.2 No nonsense text.** Every on-screen word is the user's exact word. Case changes: none (the style prints words as written). Numerals appear only if the user wrote them. The small label on the card and the label on the page are user words or are omitted; never print a word the user did not write. All text is rendered by code with real fonts; never by an AI model in edit or still mode. **Caption audit:** join all caption chunks (plus any words deliberately moved into a band, tag, card or chip) and check that they reproduce the user's text word for word, in order.

**3.3 Smooth, no breakdowns.**
- Continuous motion curves (moments.md 1.5).
- Hard switches only on the footage's own cuts.
- Every element enters and exits with its moment's motion; nothing blinks.
- No empty or black areas; the cream page is a design area only inside ROLL.
- Never start a big move within 3 frames (0.1 s) after a cut.
- Never two big moves less than 0.5–0.6 s apart.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

**3.4 Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, tilt or rotation, blur, glow, drop-in stickers, emoji, outline-only text, colours outside the palette, zoom punch-ins on footage, hard flashes, shake.

**3.5 Same rules in master prompts.** Order Flow to keep the footage, person and scenes (and audio) unchanged, list every allowed word, and describe all moves as smooth.

## 4. WORKFLOW (edit mode)

**Step 1. Ingest and analyse.**
- Run `ffprobe` for resolution, fps, duration, audio.
- Scene cuts: threshold 0.3; if none, retry at 0.12–0.2; confirm visually.
- Pull 2–4 frames per scene and **look at them**.
- Build a scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Head top y | Free band (y range without face or caption zone) | Brightness behind caption zone | Best crop anchor for cards |
|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to **time** the user's words. Otherwise use `silencedetect=n=-30dB:d=0.12` and spread syllable-weighted words, with a 0.15 s pause at commas and 0.3 s at full stops. With no speech, spread the text across the video and break at cuts.

**Step 2. Safe zones and framing plan per scene.** Per scene, write the face zone (box plus 0.02), the caption zone (moments.md 1.7), the free band for a card or tag, and the crop anchor for ROLL cards. The face is never covered, cut or blurred.

**Step 3. Caption chunks.**
- C1 chunking: 2–4 words, 24 characters or fewer, split at punctuation, never end on an article or preposition, prefer changes at cuts.
- Start = first word start; end = min(last word end + 0.1 s, next start − 0.05 s); minimum 0.4 s (and at least 3 f gap to the next chunk).
- Emphasis: the active pill only; at most one extra whole-chunk pill (C2) per video, on the last line.
- Write a caption table: `# | Start | End | Words | Zone`.

**Step 4. Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | first 0.5 s | T1, C1 |
| Theme or topic word | repeated noun, title-like phrase in the first sentence | T1 keyword |
| Contrast or turn | "but", "isn't", "instead", "the truth", "not" | T2, L1 |
| Person → B-roll cut | footage cut with the face leaving | T2, L4, P1 (if late) |
| Any later cut | footage cut, B-roll → B-roll | T2, L4, P4 |
| List or steps | "first, then", three things, "tips" | L1, L2, L4 |
| Numbers, amounts, time phrases | digits, "one year", "every day" | T2, L4 |
| Emphasis word on a face | stressed word with the face visible | C1 pill only (no cover) |
| Long static shot (over 1.5 s) | no cut, no moment | L4, T2, P4 |
| Section change without a cut | new topic in the same shot | T2, L1 |
| Payoff or call to action | last line | C2, P1 |

**Step 5. Choose moments.**
- **Signature, mandatory in every output:** C1 for the whole video; T1 within the first 0.5 s; L1 (or L3 when the free band is short, L4 when the video is under 5 s) at a list or action hook between 25 % and 75 % of the video; P1 (or P2 when there is a single shot) as the closer for the last 25–35 % of the video, with at least 1.8 s of hold. State in the plan which are signature.
- Every important cut gets a beat: T2, L4, P4 or a new C1 chunk.
- Density: a visible change every ~1.5–3 s, never two big moves less than 0.5–0.6 s apart.
- Variety: the same moment type at most 2 times; different videos get different plans.
- Secondary windows (thumbs) are filled with meaningful user footage: a previous or next shot, a detail crop, or a still.
- Output plan table: `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…)`.

**Step 6. Adapt.** Copy each spec, change only ✎ fields, and check every frame: faces safe, captions readable and inside the frame, nothing collides, band or card never overlaps the caption zone.

**Step 7. Build.**
- Python plus ffmpeg: decode raw frames, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, then `-map 1:a -c:a copy` for the audio.
- Pre-render static assets once with fixed seeds (the band stroke, chunk layouts, card, sheet).
- Use the exact easing curves of moments.md.
- Sub-pixel crops via `Image.resize(..., box=floats)`; clamp boxes so offsets are never negative.
- Draw all shapes at 2x and downscale for anti-aliasing. Pillow `rounded_rectangle` fails when the radius equals half the width: use half width − 2.
- Download fonts from the Google Fonts GitHub repo if missing (Inter); otherwise use the fallbacks in 1.4 and size by cap height.
- Measure every text with the real font before drawing.
- Style-specific:
  - lay out each caption chunk once for the full chunk and centre it at x 0.5W; words appear in place;
  - the pill is the word box plus 0.017W per side;
  - the band is 4 stacked strokes with a fixed seed;
  - the card and chip share one shadow;
  - the sheet rises over live footage; the main card is a live crop.
- No code execution available: deliver an editor build sheet (layers, keyframes, text, CapCut/After Effects steps) plus an SRT.

**Step 8. Check before delivering.**
- Make a contact sheet at 3–4 fps and extract frames around every cut and every moment. **Look at them.**
- Checklist: captions correct, in order, readable, never over a face; faces safe; no unintended jumps; primary window in sync; duration, fps, resolution and audio match; every signature moment present; no word on screen that the user did not write.
- Fix and re-render. Never deliver unchecked.

**Step 9. Deliver.** Save as `<original name>_marker_notes.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly: compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state.
- Default poster layout: the user's image full-bleed, T1 band above the subject's head (or T2 if the area is not free), and one C2 pill chunk below. When the image is a close crop or has no free top area, use the settled ROLL layout instead: main card = the image, thumbs = two crops of the same image.
- Never alter or regenerate the photo.
- Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (8 s or less; split at cuts; add a CONTINUITY paragraph for later clips). Order of each prompt:

1. **TASK.** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …". For C1: "Create a vertical 9:16 video" plus the story scenes.
2. **INPUT VIDEO MAP.** Scene by scene with timestamps.
3. **STYLE.** A plain-words paragraph of the look (yellow felt-tip stroke, rounded yellow word label, white notes card, off-white page with rounded cards).
4. **TEXT INVENTORY.** Every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE.** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS.** Every line with its time range and which word carries the yellow label.
7. **NEGATIVE.** Changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; blur, tilt, bounce, stickers, emoji, camera shake.

Plain words only: no px, %, hex codes or font names, and never the words that make models print labels. Deliver the prompts in code blocks, plus a caption table and an SRT. Add: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

Plan scenes from the story, time the captions, and choose moments.
- Master prompt → section 6 with the story scenes.
- Final video → a graphics and typography-only piece rendered in code in the style: cream page, marker band with the keyword, word-pill captions, a to-do card, and ROLL cards drawn as empty rounded frames with the user's words. No fake footage.
- Image → a typography poster in code (cream page, band, one C2 pill chunk), or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, and never let an AI model draw captions in edit or still mode.
- Never break the style's never-list (3.4) or invent moments.
- Never ask beyond missing inputs plus the one output question.
- Never deliver without looking at the rendered frames.
