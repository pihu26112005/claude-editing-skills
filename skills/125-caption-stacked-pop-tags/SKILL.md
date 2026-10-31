---
name: 125-caption-stacked-pop-tags
description: Applies the "Stacked Pop Tags" caption style (untouched full-frame footage; every phrase is a small stack of tiny white wide-sans helper words with one big condensed italic keyword in a vivid accent colour that slides in beside them, hard-cut between phrases, no boxes and no effects on cuts) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants bold condensed keyword captions, tiny stacked helper words, creator-style pop captions or a one-accent-word caption look.
---

# 125-caption-stacked-pop-tags — Stacked Pop Tags

Style data lives in [moments.md](moments.md). Read it fully before planning.

## 1. YOUR JOB

You are a motion designer who knows one style. Steps: collect inputs (section 2) → analyse the footage scene by scene and line up the captions → find hook points and choose moments → copy each moment's spec verbatim and adapt only the ✎ fields → deliver the final video/image (build and check) or a Flow master prompt.

The value you add is choosing the keyword of every phrase, the lane, and the alignment. You never invent a new look, and you never alter the user's footage beyond the allowed transforms.

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
- Allowed transforms (moments.md 1.6): full-frame display, untouched; caption overlays with shadow only.
- The primary footage always plays in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, zoom, flashes, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; cards, splits, layouts, B-roll frames or background swaps; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote (never forced uppercase, not even the keyword). No invented titles or labels.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining every word of every chunk, in order, reproduces the user's text word for word. Assert it in the render script before building.

3.3 **Smooth, no breakdowns.**
- Words enter with the 3–4 frame ease-out of moments.md; phrases hard-cut to the next phrase in the same frame.
- Nothing blinks; no word moves once placed; the layout of a phrase is fixed before its first word appears.
- No text overlaps other text; every glyph, including shadows and the entering slide, stays inside the frame with side margin ≥ 0.05W at rest (≥ 0.02W while sliding).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: boxes, plates, outlines without fill, bounce or overshoot, letter-by-letter typing, wipes, glitch, shake, flashes, rotation, effects on cuts, more than one accent colour, uppercase conversion.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- `ffprobe` for size, fps, duration, audio. Detect cuts with `select='gt(scene,0.3)'` (retry 0.12–0.2 if none; confirm visually). Look at 2–4 frames per scene.
- Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Free lanes (low, top) | Busy or bright? |
|---|---|---|---|---|---|---|

- Speech timing: speech-to-text word timestamps only to time the user's words; else `silencedetect=n=-30dB:d=0.12` plus syllable-weighted spreading (0.15 s pause at commas, 0.3 s at full stops). No speech: spread phrases across each shot (1.0–2.0 s each).

**Step 2 — Safe zones.** Face never covered. Decide per scene the lane (P1), alignment (left, right, centre) and whether the face allows the top lane.

**Step 3 — Chunks and keywords.**
- Chunk 2–6 words, 0.7–1.7 s. Split at punctuation and cuts; never end a chunk on an article, preposition or conjunction. Prefer chunk changes at cuts.
- Choose exactly one keyword per chunk (C1), the meaning-carrying noun or verb; at most two (C3) in a payoff chunk; a one-word chunk is C2.
- Write each chunk as lines: small line(s) and key line(s), in reading order. Output `# | Start–End | Lane | Align | Lines (S/K)`.
- Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence | C1, K1 |
| Topic word | The noun the video is about | K1 keyword |
| Contrast or turn | "but", "isn't", "instead", "never" | keyword on the negation or the contrast word |
| Cut | Scene table | X1, lane swap via P1 |
| List or steps | 3+ parallel phrases | one C1 each, keyword per item, alternate alignment |
| Numbers, amounts, time phrases | Digits, "one year" | keyword |
| Short punchy word | One-word sentence | C2 |
| Payoff or call to action | Last line | C3, E1 |

**Step 5 — Choose moments.** Signature (mandatory): **C1** (the stacked phrase), **K1** (keyword slide-in) and **X1** (hand-off at every cut). Use C2 for one short punchy word, C3 for the payoff, P1 on every chunk, E1 at the end. Never two chunks at once; chunk gaps ≤ 0.35 s except real pauses. Plan table: `# | Moment | Start–End | ✎ Text | ✎ Lane / align | Reason`.

**Step 6 — Adapt.** Copy specs; change only ✎ fields. Check every frame: face clear, text readable, nothing overlaps, margins hold.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames, composite per frame with Pillow, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p`, `-map 1:a -c:a copy`.
- Pre-render every word sprite once at 2× and downscale; shear keyword glyph masks before downscaling; build the shadow from the glyph mask.
- Lay out the full chunk before its first word; assert every word bbox inside margins, outside the face box, and clear of every other word.
- Keep the render script in a scratch folder. No code execution: write an editor build sheet instead.

**Step 8 — Check.** Contact sheet at ~1.2 fps plus a strip of frames across the hardest chunk. Look at them. Checklist: audit passes, one keyword per chunk, small words legible on bright footage, no overlaps, margins, face clear, primary footage in sync, duration/fps/audio match, signature moments present.

**Step 9 — Deliver.** `<original name>_stacked_pop_tags.mp4`; brief reply with plan table and assumptions.

## 5. STILL MODE (C4)
One chunk in its settled state (C1 or C2), lower lane, photo untouched. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Steps 1–6, then one prompt per Flow clip (≤ 8 s, split at cuts, CONTINUITY paragraph for later clips). Order: TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · INPUT VIDEO MAP · STYLE (tiny white helper words stacked around one big slanted condensed keyword in a bright accent colour, plain cuts) · TEXT INVENTORY (every word; end "Nothing else is written anywhere.") · TIMELINE · CAPTIONS (line, time range, keyword) · NEGATIVE (changed person, face, background, extra or misspelled text, boxes, outlines, bouncing text, glitch, flashes, camera shake). Plain words only (no px, %, hex, font names). Add: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions. Master prompt per section 6. Final video: typography-only piece on a plain dark plate with C1 phrases and hard cuts. No fake footage.

## 8. NEVER DO
- Never replace footage, a person or an image; never pause, reorder, speed up or trim.
- Never cover, cut or blur a speaking face; never put non-user words on screen.
- Never add boxes, effects on cuts or moments not in moments.md.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
