---
name: 130-caption-whisper-blob
description: Applies the "Whisper Blob" caption style (untouched full-frame footage; every phrase split into a tiny hand-brushed white whisper line and one fat rounded saturated keyword on a solid dark slab that rises in, bent into an arch or wave, hopping between top and bottom lanes to stay off the face) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants chunky bubble keywords, hand-written small words, creator-style bold captions or colourful pop captions.
---

# 130-caption-whisper-blob — Whisper Blob

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
- Allowed: full-frame display, untouched; text, slab and shadow overlays only.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; cards, splits, B-roll frames, background swaps, blur, zoom, grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, case as written. Numerals only if the user wrote them.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining every chunk's words in spoken order reproduces the user's text word for word. Run it in code (`assert " ".join(words) == TEXT`) before building.

3.3 **Smooth, no breakdowns.**
- Entrances and exits per moments.md 1.5; hard switches only at chunk ends and on footage cuts (lane hop).
- Every glyph, slab and shadow stays ≥ 0.05W from the left and right edges at every frame, including during entrances. Assert the text bounding boxes in the render script.
- Never two chunks on screen at once; the whisper line never touches its keyword; no glyph over the speaking face box.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: horizontal slides, bounce, shake, outline-only or hollow text, letter-by-letter typing, glitch, gradients, extra colours beyond the two accents plus white, forced capitals, effects on cuts.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe moves as smooth and cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.** `ffprobe`; scene cuts with `select='gt(scene,0.3)'` (retry 0.12–0.2, confirm visually); look at 2–4 frames per scene. Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Lane choice (top/bottom) | Brightness |
|---|---|---|---|---|---|---|

Speech timing: speech-to-text word timestamps only to time the user's words, else `silencedetect=n=-30dB:d=0.12` plus syllable-weighted spreading (0.15 s at commas, 0.3 s at full stops). No speech: spread phrases across each shot, 1.0–2.5 s each.

**Step 2 — Safe zones.** Per scene: lane (bottom when the face is above 0.40H; top when no face or the face is low), checked against the face box.

**Step 3 — Caption chunks.** One chunk = 1–4 words of the spoken text: 1 keyword (or a 2-word pair) plus the connective words around it. Chunk 0.5–1.5 s, split at punctuation, never end on an article or preposition unless it is a whisper word. Colour order accent A, white, accent B repeating; payoff in accent B. Output a table `# | Start–End | Whisper words | Keyword | Colour | Warp | Lane`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence | C1 + C2 from the first word, optional T1 |
| Topic word | The noun the video is about | C2 accent A |
| Contrast or turn | "but", "isn't", "instead" | C2 white |
| Person → B-roll or back | Scene table | C5 |
| Any later cut | Scene table | C5 |
| List or steps | 3+ parallel phrases | C2 per item, alternate C3/C4 |
| Numbers, amounts, time phrases | Digits | K2 |
| Long static shot | > 2 s | next chunk starts mid-shot, no new moment |
| Payoff | Last line | K1 + E1 |

**Step 5 — Choose moments.** Mandatory: C1 + C2 on every chunk, C3 and C4 alternating, K1 on the payoff, C5 on every cut. One keyword colour change per chunk; no two chunks overlap. Plan table: `# | Moment | Start–End | ✎ Text | ✎ Lane | Reason`.

**Step 6 — Adapt.** Copy specs, change ✎ fields only; check every frame: faces safe, text inside the frame, readable on that shot's brightness.

**Step 7 — Build.** Python + ffmpeg, decode raw frames, composite per frame with Pillow, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p`, `-map 1:a -c:a copy`. Pre-render each chunk's whisper words and keyword once at 2× (warp by per-column shift, tilt by rotate, slab + blurred shadow baked), downscale, auto-shrink keywords to ≤ 0.88W. Lay out a chunk fully before its first word. Assert every bounding box inside 0.05W–0.95W and clear of the face box per lane. Keep the render script in a scratch folder. Fonts: Paytone One and Caveat Brush (Google Fonts), fallbacks in moments.md. No code execution: write an editor build sheet instead.

**Step 8 — Check before delivering.** Contact sheet at 1–4 fps plus frames around every cut and every chunk start. Look at them. Checklist: captions correct and in order; text inside the frame and off the face; no overlap; whisper readable; colours as planned; duration, fps, resolution and audio match. Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** `<original name>_whisper_blob.mp4`. Reply briefly with the plan table, assumptions and what the user may want changed.

## 5. STILL MODE (C4)
One chunk in its settled state (C1 + C2) in the bottom lane (or top lane if the subject is low). Never alter the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Run steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips): 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · 2 INPUT VIDEO MAP · 3 STYLE (tiny white hand-brushed words above one huge fat rounded colourful word on a dark solid shadow, arched or wavy, rising into place, top or bottom of the frame away from the face) · 4 TEXT INVENTORY (every allowed word; end with "Nothing else is written anywhere.") · 5 TIMELINE · 6 CAPTIONS · 7 NEGATIVE (changing or replacing the person, face, outfit or background; new scenes; reordered shots; changed audio; extra or misspelled text; hollow or outlined letters; sliding text; shake). Plain words only. Deliver prompts in code blocks plus a caption table and an SRT; say "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time the captions, choose moments. Final video: typography-only piece on a plain dark plate, chunks per C1/C2, no fake footage. Image: typography poster in code.

## 8. NEVER DO
- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never use effects or moments not in moments.md; never break the 3.4 never-list.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
