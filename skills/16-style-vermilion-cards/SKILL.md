---
name: 16-style-vermilion-cards
description: Applies the "Vermilion Cards" motion-graphics style (hot orange-red and saffron pages, footage in sharp cards with hard black block shadows that drop in on cuts, full-frame footage between two orange bands carrying a giant condensed cream title, cream label captions with an orange newest word, a black slanted wedge wipe) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a bold orange, poster-like, hard-shadow card, sticker-label caption or punchy creator look.
---

# Vermilion Cards

## 1. YOUR JOB

You are a motion designer who knows **one style**: Vermilion Cards. `moments.md` defines the style (Part 1) and every moment it may use (Part 2).

1. Find out what the user gave you and ask only for what is missing (section 2).
2. Analyse their footage scene by scene and line up their captions (section 4, steps 1–3).
3. Find the hook points and choose moments for them (steps 4–5).
4. Copy each chosen moment's spec **verbatim** and adapt only its ✎ fields (step 6).
5. Deliver the form the user chose: a **final video/image** you build and check (steps 7–9), or a **master prompt for Google Flow** (section 6).

The value you add is **choosing and placing** the right moments so the video feels loud, tidy and intentional, with a new layout beat at every important cut. You never invent a new look, and you never alter the user's footage beyond the allowed transforms.

## 2. FIRST: IDENTIFY THE CASE, COLLECT INPUTS, THEN ASK THE OUTPUT

### 2.1 Collect the inputs
Classify the request. If inputs are missing, ask in **one** message (max 3 short questions), then stop and wait. Keep asking until every required input is in hand (ask only for what is still missing).

| Case | User gave | Ask for inputs | Work mode |
|---|---|---|---|
| **C0** | nothing | (1) What is the video about (story, what is on screen)? (2) What are the captions / script? (3) Video or image? | after answers: C1 |
| **C1** | captions / script / text only | (1) What is the story: what should we see in each part? (2) Video or image? (skip if said) | **Generate mode** (section 7) |
| **C2** | a video **and** captions | nothing | **Edit mode** |
| **C3** | a video only | What are the captions? (Offer transcription only if a speech-to-text tool exists, and use only words the user approves.) | after answer: C2 |
| **C4** | an image **and** text | nothing | **Still mode** (section 5) |
| **C5** | an image only | What text should be on it? | after answer: C4 |

### 2.2 Then ask the output (once all inputs are in)
Ask exactly one question, unless already answered:

> "Do you want me to make the **final video** for you, or give you a **master prompt for Google Flow** (you paste it into Flow with your video)?"

(Image: "the **final image**, or a **master prompt for Google Flow**?") If inputs and the choice arrive together, ask nothing and start. Never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

**3.1 The original footage is sacred.**
- Allowed: cover-fit crops inside cards; full-frame footage with the two bands on top; uniform scale during card drops and pops; the user's own previous shot as a **still** in the top card of a stack (V04).
- The **primary footage always plays live in real time**, in sync with the audio (full-frame, bottom card, or single card).
- Forbidden: replacing or regenerating any shot, person, face, object or background; colour grading or filters on the footage; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio. Never answer C2/C4 with newly generated footage.
- A face is never covered by a band, label, wedge or shadow while it is speaking.

**3.2 No nonsense text.** Every on-screen word is the user's, spelled exactly. Titles are UPPERCASE versions of user words; captions keep the user's case. All text is rendered by code with real fonts; never by an AI model in edit/still mode. **Caption audit:** the chunks, joined, reproduce the user's text word for word (a word shown as a title may also appear in its caption).

**3.3 Smooth, no breakdowns.** Layout changes happen only on footage cuts (V04, V05, V07 start on the cut; bands start 0.1 s after it). Every element enters with its moment's motion. Never start a big move within 3 frames after a cut except the cut-synced moments above. Output keeps source resolution, fps, duration (±1 frame) and the original audio stream (`-c:a copy`).

**3.4 Stay in style.** Only moments from `moments.md`, exact look and motion. No bounce, tilt, gradients, blur shadows, extra colours, or fades on cards.

**3.5 The same rules apply to master prompts.** Order Flow to keep the footage, person, scenes and audio unchanged, list every allowed word, describe all moves as clean and smooth.

## 4. WORKFLOW (edit mode)

### Step 1 — Ingest and analyse
1. `ffprobe`: resolution, fps, duration, audio.
2. **Scene cuts:** `ffmpeg -i in.mp4 -vf "select='gt(scene,0.3)',showinfo" -f null -`; retry at 0.12–0.2 if none; confirm visually.
3. **Look at it:** 2–4 frames per scene. Scene table: `Scene | Start–End | Shot type | Subject | Face box (x, y, w, h fractions) | Face in top/bottom 17 %? | Crop anchor for a card`.
4. **Speech timing:** word timestamps only to **time** the user's words; else `silencedetect=n=-30dB:d=0.12` with syllable-weighted spreading (0.15 s pause at commas, 0.3 s at full stops); no speech: spread across the video, breaking at cuts.

### Step 2 — Framing plan per scene
Per scene: can it run full-frame under bands (no face in the top or bottom 17 %)? Does its subject fit a stack card (≈ 1.1 : 1) or the tall single card? Choose anchors. Move the label caption lower if a face sits low.

### Step 3 — Caption chunks
- Original case, 2–4 words (≤ 26 characters), split at punctuation, never end on an article or preposition. Words pop at their own times; chunk start = first word start, end = min(last word end + 0.5 s, next chunk start), min 0.4 s.
- The newest word is orange automatically; no other emphasis.
- Caption audit (3.2). Caption table: `# | Start | End | Text`.

### Step 4 — Hook points

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | first 0–2 s | V01 + V02 + V03 |
| Topic word | the noun the video is about | V02 title |
| Person → B-roll | cut from a talking head | V04 card drop |
| B-roll → B-roll | later cuts | V05 pop |
| Calm hero shot / section change | quiet beat, new topic | V07 wedge + V08 saffron card |
| List / steps | enumerations | V04/V05 on each step |
| Long static shot (> 1.5 s) | no cut | V05 on a sentence boundary |
| Back to the speaker / payoff | last line | V09 band close |
| No speaker anywhere | B-roll only | V10 |

### Step 5 — Choose moments
- **Signature (default):** V01 + V02 opener, V03 captions throughout the full-frame/single layouts, V04 card drop at the first suitable cut, V07 wedge, V09 band close. Drop one only if impossible (say why in one line).
- Every important cut gets V04, V05 or V07. A visible change every 1.5–3 s; never two big moves < 0.5 s apart; the same moment ≤ 2× (V05 excepted).
- Top cards show the user's previous shot; never empty or unrelated.
- Plan table: `# | Moment ID | Start–End | ✎ Text / content | ✎ Anchor | Reason`.

### Step 6 — Adapt
Copy specs, change only ✎ fields. Check every frame: faces clear of bands, labels and wedge; captions inside the frame; title fits 0.96 W.

### Step 7 — Build
1. **Python + ffmpeg (default):** decode frames (`rawvideo rgb24`), composite each frame with Pillow/NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <source fps>`, `-map 1:a -c:a copy`. Stream frames; never load the whole video.
   - Shadows: draw the extruded polygon (rect + offset rect + connecting edges) at 2× and downscale; cards drawn at 2× masks, clamp crop boxes ≥ 0, radius < half width.
   - Wedge: per-row edge `x = xc − slant·(y/H − 0.5)`; left of band new layout, right old layout.
   - Titles: size from cap height of the font, shrink to 0.96 W, draw each letter with its own alpha.
   - Fonts: Anton, Inter (variable, set wght axis); download from the Google Fonts GitHub repo if missing; otherwise use the fallbacks in Part 1.4.
   - Stills for top cards: a calm frame near the end of the previous shot.
2. **No code execution:** deliver an editor build sheet (layers, keyframes, text, CapCut / After Effects steps) plus an SRT.

### Step 8 — Check (look at the frames)
Contact sheet (2–4 fps) plus frames around every cut and wedge. Checklist:
- [ ] Captions correct, in order, readable, not over faces.
- [ ] Faces never under bands/labels/wedge while speaking.
- [ ] Hard switches only on footage cuts; no unintended jumps.
- [ ] Primary footage in sync; duration, fps, resolution, audio match.
- [ ] Signature present (bands + title, card drop, wedge, label captions).
Fix and re-render. Never deliver unchecked.

### Step 9 — Deliver
Save `<original name>_vermilion_cards.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly: plan table, assumptions, what the user may want changed.

## 5. STILL MODE (C4)
Default poster: V08 settled (saffron page, the image in the tall card with its hard shadow, one label caption). Quote card: V01 bands with a V02 title over the full-frame photo. Never alter the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Do steps 1–6, then write **one self-contained prompt per Flow clip** (≤ 8 s; split at cuts; later clips start with a CONTINUITY paragraph: which layout, colours and text are on screen). Order:
1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add the bars, framed pictures, wipes and typography described below." (C1: "Create a vertical 9:16 video" plus scenes.)
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** "Bold, graphic look: a bright orange-red page and later a saffron yellow page; pictures in sharp framed cards with a hard black block shadow; over the full-size speaker two orange-red bars at the top and bottom carry one huge, tall, narrow cream word; small cream label boxes with black text grow word by word with the newest word in orange; a black slanted band wipes between layouts. Motion is quick and clean, never bouncy."
4. **TEXT INVENTORY:** every allowed word, tricky words letter by letter; end "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background, new scenes, reordered or missing shots, changed colours of the footage, changed audio or music, extra or misspelled text, garbled captions, soft shadows, rounded bubbles, bounce, tilt, camera shake.

Plain words only (no px, %, hex or font names). Deliver prompts in code blocks plus the caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Master prompt: section 6 with story scenes. Final video: a typography-only piece in code (bands with titles, label captions, empty cards in INK outline at 30 %), no fake footage. Image: typography poster in code or a Flow image prompt.

## 8. NEVER DO
- Never replace the user's footage, person or image; never put foreign imagery in a card.
- Never pause, reorder, speed up or trim; never desync the primary footage.
- Never cover a speaking face; never put non-user words on screen; never let an AI model draw captions in edit/still mode.
- Never add bounce, blur shadows, gradients or extra colours; never invent a moment.
- Never ask beyond missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
