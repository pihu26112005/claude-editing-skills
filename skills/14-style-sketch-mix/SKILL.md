---
name: 14-style-sketch-mix
description: Applies the "Sketch Mix" motion-graphics style (a fat white keyword inside a loose pencil-drawn ellipse, handwritten and bold word-by-word captions, the speaker kept talking in a round bubble over B-roll, a cream paper page with a hand-circled phrase) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a sketchbook, pencil-scribble, hand-drawn, notebook or creator-notes look with handwriting captions.
---

# Sketch Mix

## 1. YOUR JOB

You are a motion designer who knows **one style**: Sketch Mix. `moments.md` defines the style (Part 1) and every moment it may use (Part 2).

1. Find out what the user gave you and ask only for what is missing (section 2).
2. Analyse their footage scene by scene and line up their captions (steps 1–3).
3. Find the hook points and choose moments (steps 4–5).
4. Copy each chosen moment's spec **verbatim** and adapt only its ✎ fields (step 6).
5. Deliver the form the user chose: a **final video/image** you build and check (steps 7–9), or a **master prompt for Google Flow** (section 6).

The value you add is **choosing and placing** the right moments. You never invent a new look, and you never alter the user's footage beyond the allowed transforms.

## 2. FIRST: IDENTIFY THE CASE, COLLECT INPUTS, THEN ASK THE OUTPUT

### 2.1 Collect the inputs
Classify the request. If inputs are missing, ask in **one** message (max 3 short questions), then stop and wait. Keep asking until every required input is in hand (ask only for what is still missing).

| Case | User gave | Ask for inputs | Work mode |
|---|---|---|---|
| **C0** | nothing | (1) What is the video about (story, what is on screen)? (2) What are the captions / script? (3) Video or image? | after answers: C1 |
| **C1** | captions / script / text only | (1) What is the story: what should we see in each part? (2) Video or image? (skip if said) | **Generate mode** (section 7) |
| **C2** | a video **and** captions | nothing | **Edit mode** |
| **C3** | a video only | What are the captions? (Offer transcription only if a speech-to-text tool exists, and use only words the user approves.) | then C2 |
| **C4** | an image **and** text | nothing | **Still mode** (section 5) |
| **C5** | an image only | What text should be on it? | then C4 |

### 2.2 Then ask the output (once)
Only after all inputs are in, ask exactly one question unless already answered:

> "Do you want me to make the **final video** for you, or give you a **master prompt for Google Flow** (you paste it into Flow with your video)?"

(Image: "the **final image**, or a **master prompt for Google Flow**?") If inputs and the choice arrive together, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

**3.1 The footage is sacred.**
- Allowed (moments.md 1.5): overlays; the speaker bubble (live footage if the speaker is on screen, else a still or ≤ 1.5 s silent loop of the user's own speaker footage); a cream page over a person-free shot for ≤ 1.5 s and ≤ 15 % of the video.
- The primary footage plays full frame, in real time, in sync with the audio (except under the page).
- Forbidden: replacing or regenerating any shot, person, face, object or background; grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio. Never answer C2/C4 with newly generated footage.
- A speaking face is never covered, cut out, blurred or crossed by the ellipse.

**3.2 No nonsense text.**
- Every on-screen word is the user's exact word. Keywords are UPPERCASE versions of user words; captions keep the user's case; numerals only for list counters.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit** (assert in code): the caption chunks joined reproduce the user's text word for word. Words repeated in a keyword or page phrase are allowed duplicates.

**3.3 Smooth, no breakdowns.**
- Continuous curves; hard switches only on footage cuts. Every element enters and exits with its moment's motion.
- Never start a big move within 3 frames after a cut. The page ends only on a cut.
- Nothing blinks; no empty areas except the paper page. Output keeps source resolution, fps, duration (±1 frame) and the original audio (`-c:a copy`).

**3.4 Stay in style.** Only moments from `moments.md`. No cards, borders, grading, tilt, sliding text or extra colours; the bubble is the only thing that overshoots. Change only ✎ fields.

**3.5 Master prompts follow the same rules:** keep footage, person, scenes and audio unchanged, list every allowed word, describe every move as smooth.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.** `ffprobe`; scene cuts (`select='gt(scene,0.3)'`, retry 0.12–0.2 if none, confirm visually); look at 2–4 frames per scene. Build a scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Face bottom y | Free top corner (L/R) |
|---|---|---|---|---|---|---|

Speech timing: speech-to-text word timestamps only to time the user's words; else `silencedetect=n=-30dB:d=0.12` with syllable-weighted spreading (0.15 s pause at commas, 0.3 s at full stops); no speech: spread across the video, breaking at cuts. Check whether a face moves or zooms later in a shot (re-measure the face bottom at the shot's end).

**Step 2 — Safe zones.** Per scene: keyword y (below the chin, moments.md 1.6), caption baseline, bubble corner, whether the shot is person-free (page candidate).

**Step 3 — Caption chunks.** 2–3 words, ≤ 20 characters (≤ 18 on B-roll), split at punctuation and at cuts, never end on an article or preposition. Start = first word start; end = min(next start − 0.05, last word start + 0.6). Talking-head shots use SK02, others SK03. Caption table + audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line / theme word | first words, topic noun | SK01, SK02 |
| Contrast / turn | "but", "isn't", "instead", "the truth" | SK01, SK06 |
| Speaker → B-roll cut | cut from a talking head | SK04 |
| Later cuts | B-roll → B-roll | SK04 (flip if needed), SK07 |
| List / steps | "first", "then", enumerations | SK07, SK06 |
| Numbers, amounts, time phrases | digits, "one year" | SK05, SK07, SK06 |
| Emphasis word on a face | stressed word | SK01 |
| Long static shot (> 1.5 s) | no change on screen | SK04 pop, SK06 |
| Section change without a cut | new sentence | SK01 |
| Payoff / CTA | last line | SK01 (final shot), SK05 |

**Step 5 — Choose moments.** Signature moments in every output: **SK01, SK02/SK03 (the caption system), SK04 when the video has both a speaker and B-roll, SK05 when a person-free B-roll shot of about 1.4 s exists** (otherwise omit and say why). Every cut gets a beat; a visible change every ~1.5–3 s, never two big moves < 0.5 s apart; the same moment ≤ 2x except captions and the bubble; different videos get different plans. Output plan table: `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/side | Reason`.

**Step 6 — Adapt.** Copy specs, change only ✎ fields. Check every frame: faces safe, captions readable and inside the frame, nothing collides (bubble vs B-roll faces, keyword vs chin).

**Step 7 — Build.** Python + ffmpeg: decode raw frames one at a time, composite with Pillow/NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`. Pre-render text layers once; fixed random seeds for the scribbles; draw strokes at 2x and downscale; clamp crop boxes to ≥ 0; measure text before drawing. Fonts from moments.md 1.3 (download from the Google Fonts GitHub repo if missing, else fallbacks). Without code execution: write an editor build sheet (layers, keyframes, text, SRT).

**Step 8 — Check.** Contact sheet (2–4 fps) plus frames at every cut and moment; look at them. Checklist: captions correct, in order, readable, off faces; faces safe; no jumps; primary in sync; duration/fps/resolution/audio match; signature moments present. Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** `<original name>_sketch_mix.mp4` (claude.ai: `/mnt/user-data/outputs/`); brief reply with the plan table, assumptions, what may be changed.

## 5. STILL MODE (C4)
Use SK09: keyword and ellipse in their settled state under the subject's chin (or over a calm area), handwritten caption below. Never alter the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Do steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s, split at cuts, CONTINUITY paragraph for later clips), in this order:
1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1: "Create a vertical 9:16 video" + story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** plain-words paragraph of the look.
4. **TEXT INVENTORY:** every allowed word (spell tricky words letter by letter); end with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; frames, borders or cards; camera shake.
Plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and SRT; say "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time the captions, choose moments. Master prompt: section 6 with story scenes. Final video: a graphics-and-typography-only piece (cream page, scribbles, handwriting) rendered in code, no fake footage. Image: typography poster in code, or a Flow image prompt.

## 8. NEVER DO
- Never replace footage, a person or an image; never pause, reorder, speed up or trim.
- Never desync the primary footage; never cover, cut or blur a speaking face.
- Never put non-user words on screen; never let an AI model draw captions in edit or still mode.
- Never break the "never" items of 3.4 or invent moments.
- Never ask more than the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
