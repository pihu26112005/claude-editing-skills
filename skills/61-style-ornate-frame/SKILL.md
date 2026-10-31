---
name: 61-style-ornate-frame
description: Applies the "Ornate Frame" motion-graphics style (the footage shrinks into a pointed-arch window on ivory paper inside an engraved gold frame with a beaded line, vine corners and oxblood rosettes; black-lacquer plates carry gold small-caps titles, ivory serif captions, Roman-numeral medallions and a scroll ribbon; gold glints sweep over the frame on cuts) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a Victorian, gothic, engraved, gold-leaf, ornamental-border, storybook or antique-poster look.
---

# 61-style-ornate-frame — Ornate Frame

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

Ask missing inputs in one message (max 3 short questions), stop and wait. Keep asking until every required input is in hand (if an answer is still incomplete, ask only for what is still missing).

### 2.2 The one output question

Only after all inputs are in, ask exactly one question unless already answered: **"Do you want me to make the final video for you, or give you a master prompt for Google Flow (you paste it into Flow with your video)?"** For an image: "final image or Flow master prompt". If inputs and the output choice come in one message, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

3.1 **Footage is sacred.**
- Allowed transforms (moments.md 1.6): scale to 0.775 and clip to the arch window (F1), slow push-in up to 1.035 per shot and 1.06 on the last shot (B1, E1), frame, plates and the ribbon drawn around or over it.
- The primary window always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; grading, glow, blur or glint on the footage; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word, with the case the user wrote (title and ribbon use the font's small caps, which is not a change of words). Numerals only as Roman list counters (M1).
- Title and ribbon words come from the user's own text; never invent a title.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining the title words, all caption chunks and the ribbon words in time order reproduces the user's text word for word. Run `assert` before building.

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md; hard switches only on the footage's own cuts and on caption chunks.
- Every element enters and exits with its moment's motion; nothing blinks; no black or empty areas (the ivory page is the design).
- The face box (x 0.34–0.66, y 0.15–0.40 of the frame for a speaker) is visible from frame 0 and never covered, cut or blurred.
- Start no big move within 3 frames after a cut; the title never fades across a cut; a glint or bloom may start on the cut itself.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md, with their exact look and motion. Never: bounce, shake, glitch, flash, wipe over footage, filters, tilt, extra colours, emoji, sans-serif type, uppercase conversion of captions, ornaments that cover the face, more than 4 glints or 3 blooms or 3 gold emphasis words per video.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth and all cuts as plain cuts.

## 4. WORKFLOW (edit mode)

**Step 1 Ingest and analyse.** `ffprobe`; scene cuts (threshold 0.3, retry 0.12–0.2 if none; confirm visually); look at 2–4 frames per scene. Scene table: `Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Crop anchor | Low-area free for the ribbon?`. Speech timing: use speech-to-text word timestamps only to time the user's words; else `silencedetect=n=-30dB:d=0.12` plus syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops; no speech: spread across the video, breaking at cuts.

**Step 2 Safe zones.** Window clips the top corners (arch): check text or faces near them. Caption plate and header never overlap the window. Ribbon only where the lower window holds no face or key object.

**Step 3 Caption chunks.** 1–4 words, one line, ≤ 540 px at the auto-fit size; split at punctuation; never end on an article or preposition; prefer changes at cuts; start = first word, end = min(last word end + 0.1, next start − 0.05), min 0.4 s. Move the title words and ribbon words out of the caption stream. Gold emphasis ≤ 1 per chunk, ≤ 3 per video. Print the caption table and run the audit.

**Step 4 Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | first words | F1, T1 |
| Theme or topic word | repeated noun | T1, C2 |
| Contrast or turn ("but", "isn't", "instead") | the pivot word | C2 |
| Person → B-roll cut | footage cut | X1 |
| Later cuts | footage cuts | X2 or X1 (alternate) |
| List or steps | "first", "then", three actions | M1 per item |
| Number, amount, time phrase | digits, "a year", "10 minutes" | K1 |
| Long static shot (> 1.5 s) | no cut | B1 |
| Section change without a cut | topic shift | X2 |
| Payoff or CTA | last line | E1, C2 |

**Step 5 Choose moments.** Mandatory: F1, T1, C1, X1, B1 on every shot (state which). Every important cut gets X1 or X2. A visible change every ~1.5–3 s, never two big moves within 0.5 s. Same moment type at most 2x except C1, B1, M1. Output plan table: `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason`.

**Step 6 Adapt.** Copy the spec, change only ✎ fields. Check every frame: face safe, text inside the plate, nothing collides.

**Step 7 Build.** Python + ffmpeg: decode raw frames, composite per frame with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`. Pre-render every ornament once with fixed seeds, at 3x, from clean vector curves (tapered bezier strokes, spiral scrolls, leaf polygons with veins, scalloped rings, beaded rules), shade with the gold ramp and hatch engraving, downscale with BOX. Fonts: Cormorant Garamond and Cormorant SC from the Google Fonts GitHub repo (fallbacks EB Garamond, Playfair Display). Measure text before drawing; auto-fit captions. No code execution: write an editor build sheet (layers, keyframes, SRT).

**Step 8 Check.** Contact sheet (1.2 fps, 6x2) plus a strip around the opening and the trickiest cut; look at them. Checklist: captions correct, in order, inside the plate; face visible from frame 0; no jumps; footage in sync; duration, fps, resolution, audio match; F1, T1, C1, X1 present; ornaments crisp (no jagged edges, no clipped pieces). Fix and re-render; never deliver unchecked.

**Step 9 Deliver.** `<original name>_ornate_frame.mp4`; reply with the compact plan table, assumptions and what the user may want changed.

## 5. STILL MODE (C4)
Use P1: photo cover-fit in the window (anchor ✎), headline in the title plate, subline in the caption plate, ornaments settled, no glint. Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Same steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph for later clips). Order: 1 TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio exactly as they are. Only add …") · 2 INPUT VIDEO MAP (scene by scene with timestamps) · 3 STYLE (plain words: tall pointed-arch window on warm ivory paper, fine engraved gold frame with a dotted line, vine corners with deep red roses, dark lacquered plates with gold and ivory serif lettering) · 4 TEXT INVENTORY (every allowed word, tricky words spelled letter by letter, end "Nothing else is written anywhere.") · 5 TIMELINE (`[start–end s] MOMENT NAME. <Flow prompt text, filled>`) · 6 CAPTIONS (each line with time range and gold word) · 7 NEGATIVE (changing or replacing the person, face, outfit, background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; sans-serif type; flashes; shake; crude, cartoon or clip-art ornaments). Plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT; say "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Master prompt → section 6 with story scenes. Final video → a typography-and-ornament piece rendered in code (the frame with an empty ivory window, plates, captions), no fake footage. Image → poster in code or a Flow image prompt.

## 8. NEVER DO
- Never replace footage, a person or an image; never pause, reorder, speed up or trim; never desync the primary window.
- Never cover, cut or blur a speaking face; never light, grade or filter the footage.
- Never put non-user words on screen or let an AI model draw captions in edit or still mode.
- Never break the style's never-list or invent moments.
- Never ask beyond missing inputs plus the one output question.
- Never deliver without looking at the rendered frames.
