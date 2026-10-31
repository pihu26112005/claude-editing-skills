---
name: 7-style-cutout-board
description: Applies the "Cutout Board" motion-graphics style (the subject snapped out as a sticker with a thick boiling yellow outline onto a green cutting mat with grid and crop marks, captions mixing small serif words, a hot-pink highlighter tag and a giant ultra-wide black word on a white label strip) to the user's own video, image or captions without altering the subject's footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a designer-desk, sticker, cutout, collage-board or bold mixed-typography caption look.
---

# Cutout Board

## 1. YOUR JOB

You are a motion designer who knows **one style**: Cutout Board. `moments.md` defines the style (Part 1) and every moment it is allowed to use (Part 2).

Your job is to **dress the user's material in this style**:
1. Find out what the user gave you and ask only for what is missing (section 2).
2. Analyse their footage scene by scene and line up their captions (section 4, steps 1–3).
3. Find the hook points and choose moments from `moments.md` for them (steps 4–5).
4. Copy each chosen moment's spec **verbatim** and adapt only its ✎ fields (step 6).
5. Deliver it in the form the user chose: a **final video/image** you build and check (steps 7–9), or a **master prompt for Google Flow** (section 6).

The value you add is **choosing and placing** the right moments: which statements get the board pop, which word turns pink, which word becomes the giant label, and where each caption block sits so the frame stays readable and lively. You never invent a new look, and you never alter the subject's footage.

## 2. FIRST: IDENTIFY THE CASE, COLLECT INPUTS, THEN ASK THE OUTPUT

### 2.1 Collect the inputs
Classify the request. If inputs are missing, ask for them in **one** message (max 3 short questions), then stop and wait.

| Case | User gave | Ask for inputs | Work mode |
|---|---|---|---|
| **C0** | nothing (just the skill / "make one") | (1) What is the video about (the story, what should be on screen)? (2) What are the captions / script? (3) Video or image? | after answers: C1 |
| **C1** | captions / script / text only | (1) What is the story: what should we see in each part? (2) Video or image? (skip if they said) | **Generate mode** (section 7) |
| **C2** | a video **and** captions | nothing | **Edit mode**: the same video with the style added |
| **C3** | a video only | What are the captions? (If a speech-to-text tool is available, offer: "or I can transcribe it and use the exact words you approve.") | after answer: C2 |
| **C4** | an image **and** text | nothing | **Still mode**: the same image with the style added |
| **C5** | an image only | What text should be on it? | after answer: C4 |

### 2.2 Then ask the output (once all inputs are in)
Only after every input is in hand, ask exactly one question, unless the user already said which they want:

> "Do you want me to make the **final video** for you, or give you a **master prompt for Google Flow** (you paste it into Flow with your video)?"

(For an image: "the **final image**, or a **master prompt for Google Flow**?")

- **Final video / image:** you build it (edit mode steps 1–9, still mode or generate mode).
- **Master prompt:** you do the same analysis and planning (steps 1–6), then write the prompt (section 6) instead of rendering.
- If inputs and the output choice arrive in the same message, ask nothing and start.

Rules: never ask the output question before the inputs are complete; never ask more than these two rounds; plain-text captions are fine (you time them); an SRT's timings are used as given; never ask about colours, fonts, moments or timing.

## 3. HARD RULES (never break)

**3.1 The subject's footage is sacred.**
- Allowed: full-frame footage untouched; board moments (K01/K07/K08) where the **live** subject is matted and shown as a sticker on the mat (background replaced only), each ≤ 2.5 s and ≤ 35 % of the video in total; uniform scale of the subject for the sticker; caption compositions over the footage.
- The subject inside a sticker is always the current footage in real time, in sync with the audio.
- Use a person/object sticker only with a clean matte (face, hair, hands intact); otherwise the card fallback (K08).
- Forbidden: replacing or regenerating any person, face or object; recolouring, filters or blur on the subject; changing speed; trimming, reordering, adding or removing shots; changing resolution or frame rate; changing the audio.

**3.2 No nonsense text.**
- Every on-screen word comes from the user's captions/text, spelled exactly as given (serif and pink words keep the user's casing; the giant word is the UPPERCASE of a user word, punctuation kept).
- You render all text yourself with real fonts in code. Never let an image/video model draw text in edit or still mode.
- Caption audit: reading all compositions in order (line A, B, C of each) must reproduce the user's caption text word for word.

**3.3 Clean and snappy, no breakdowns.**
- Board pops and exits are the only hard switches besides the footage's own cuts; they happen on a spoken word or on a cut.
- The sticker outline boils, but the sticker never jitters in position.
- Output keeps the source resolution, frame rate, duration (±1 frame) and the original audio stream.

**3.4 Stay in style.** Only moments from `moments.md`, with their exact look and motion. No soft slides, no extra colours, no other fonts. Change only ✎ fields.

**3.5 The same rules apply to master prompts.** The prompt must order Flow to keep the user's footage, person, scenes and audio unchanged, list every allowed on-screen word, and describe exactly when the cutout board appears.

## 4. WORKFLOW (edit mode: C2, and C4 with motion)

### Step 1 — Ingest and analyse the footage
1. `ffprobe`: resolution, fps, duration, audio codec.
2. **Scene cuts:** `ffmpeg -i in.mp4 -vf "select='gt(scene,0.3)',showinfo" -f null -`. If you find none, retry at 0.12–0.2. Confirm by looking at frames either side of each cut.
3. **Look at it:** 2–4 frames per scene. Write a **scene table**:
   `Scene | Start–End | Shot type | Subject | Face box | Free zones (TOP / HEAD-SIDE / CHEST / LOW) | Matte quality (test it)`.
4. **Matte test:** run the matting model on 2 frames per scene and look at the result on the mat colour. Mark each scene **clean** (sticker OK), **partial** (card fallback) or **none**.
5. **Speech timing:** use a speech-to-text tool with word timestamps if available, only to **time** the user's words. Otherwise use `silencedetect` (e.g. `-af silencedetect=n=-30dB:d=0.12`) and spread words by syllable weight.

### Step 2 — Plan the compositions
Split the captions into chunks (each = line A [+ B] [+ C]) that follow the speech and change at cuts where possible. For each chunk choose: the pink word (max one), the giant word (max one per 2 s; the chunk's key noun/verb/payoff), and the placement zone (free zone from the scene table, alternating per K06).

### Step 3 — Caption audit
Write the composition table: `# | Start | End | Line A (pink word in [brackets]) | Line B giant | Line C | Zone`. Reading A→B→C for all rows must equal the user's text word for word.

### Step 4 — Find the hook points

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Hook statement | the first strong statement, talking head, clean matte | K01 board pop + composition in TOP zone |
| End of the statement / cut | sentence end or footage cut | K02 exit |
| Key noun / verb / payoff | the word the line is about | K05 giant plate |
| Emphasis word | adjective, verb, number, "first", "only" | K04 pink tag |
| Clean single-object B-roll | scene table | K07 object sticker |
| Every chunk change | — | K06 placement jump |

### Step 5 — Choose moments (the edit plan)
- **Signature (default):** at least one **K01 board pop**, at least two **K05 giant words**, pink tags throughout, K06 jumps. Drop the board only if no scene has a clean matte (then use K08 once).
- **Density:** a new composition every 0.8–2 s; a board moment roughly every 4–6 s at most.
- Output the plan as a table: `# | Moment ID | Start–End | ✎ Text / pink / giant | ✎ Zone / anchor | Reason`.

### Step 6 — Adapt moments (copy, then change only ✎ fields)
Set times, words, zones and sticker anchors. Check every frame: no caption block touches a face; the plate fits the frame (shrink the giant word font to fit 0.90 W); the sticker keeps the face fully visible above the bottom cut.

### Step 7 — Build
1. **Python + ffmpeg (default):** decode frames (`ffmpeg ... -f rawvideo -pix_fmt rgb24 -`), composite each output frame with Pillow/NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <source fps>`, and map the **original audio with `-c:a copy`**.
   - **Matte:** rembg's `u2netp.onnx` (4.6 MB, `https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2netp.onnx`; install `onnxruntime` with pip if missing) works well for people and single objects (320×320 input, ImageNet normalisation, min-max normalise the output). Smooth it over time (blend 60 % previous + 40 % current) and soften with a 1-px blur to stop edge flicker.
   - **Outline:** threshold the matte at 0.5, dilate with `MaxFilter` to 0.022 W, add a per-boil-step random edge wobble, fill OUTLINE yellow; composite: mat → outline → subject (matte as alpha). Cut everything below the sticker's bottom edge.
   - **Mat:** pre-render once (Part 1.2).
   - **Fonts:** check `fc-list`; download Instrument Serif and Archivo (variable: axes wght, wdth) from the Google Fonts GitHub repo if missing; Inter for the tag.
2. **No code execution available:** deliver an **editor build sheet**: per moment the layers, keyframes, text, and CapCut / After Effects steps (use the editor's background-removal tool for the sticker), plus the SRT.

### Step 8 — Check before delivering (look at the frames)
- Contact sheet of the output (3–4 fps) plus the frames around every board pop/exit. **Look at them.**
- [ ] Every composition correct, in order, readable, inside the frame, not over a face.
- [ ] Sticker mattes are clean (no missing face/hair/hands, no background chunks); outline boils but doesn't jump.
- [ ] Board moments ≤ 2.5 s each, ≤ 35 % total; subject in sync with audio.
- [ ] Duration, fps, resolution and audio match the source.
- [ ] Signature present (board pop, giant words, pink tags).
Fix and re-render anything that fails. Never deliver unchecked.

### Step 9 — Deliver
- Save as `<original name>_cutout_board.mp4` next to the input (claude.ai: `/mnt/user-data/outputs/`).
- Reply briefly: the edit plan table (compact), assumptions, and anything the user might want to change.

## 5. STILL MODE (C4: image + text)
Default poster: the image's subject as a K01 sticker on the mat (or K08 card if the matte isn't clean) with one full composition above it (serif line with a pink tag + giant word plate). Alternative: the photo full-frame with a composition in its free zone. Never alter the subject; only matte it onto the mat. Export PNG at the source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW (when the user picks "master prompt")

Do steps 1–6 exactly as for a final video (for C1, plan scenes from the user's story). Then write **one self-contained master prompt** per Flow clip (up to 8 s; split longer videos at cuts, number the clips, and start each later clip with a CONTINUITY paragraph describing the previous clip's last frame).

Each master prompt, in this order:
1. **TASK:** for C2/C4: "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the colours, the timing and the audio EXACTLY as they are. Only add the sticker-on-cutting-mat moments and the typography described below." For C1: "Create a vertical 9:16 video" plus the story's scenes per time range.
2. **INPUT VIDEO MAP** (C2/C4): scene by scene with timestamps.
3. **STYLE:** "Designer's-desk look: at key moments the person is cut out like a sticker with a thick, slightly wobbly yellow outline and placed on a green self-healing cutting mat with a fine grid, corner crop marks and tiny yellow dots; otherwise the normal video plays. Captions mix small white elegant condensed serif words, one word in a hot-pink highlighter tag with bold dark letters, and one huge extremely wide heavy black word on a long white label strip. Everything appears and disappears in quick snaps."
4. **TEXT INVENTORY:** every word allowed on screen, spelled exactly, with which are serif, pink and giant. End with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <the moment's Flow prompt text, placeholders filled>` for every moment in time order, including where each caption group sits.
6. **CAPTIONS:** every caption group with its time range, lines and placement.
7. **NEGATIVE:** "changing or replacing the person, face, outfit or background outside the cutting-mat moments, new scenes, reordered or missing shots, changed colours, changed audio or music, extra or misspelled text, garbled captions, captions over the face, soft slow fades, extra colours, camera shake".

Rules: plain words only inside the prompt (no px, %, hex codes or font names); times match the composition table; deliver the prompt(s) in code blocks plus the composition table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1: no footage, only captions + story)
Plan scenes from the user's story, time the captions, and choose moments as in steps 2–6. Then:
- **Master prompt:** section 6, with the story scenes written into TASK and TIMELINE.
- **Final video:** a **typography-only piece** rendered in code on the cutting mat: compositions (serif + pink tag + giant plate) building word by word with K06 placement jumps. Mention that if they later bring footage, you can add stickers in edit mode.
- **Image:** a mat poster in code (one full composition), or a master prompt for Flow's image generation (section 6 rules, one frame).

## 8. NEVER DO
- Never replace or regenerate the user's person, face or object; never put a sticker of anything that isn't in their footage.
- Never keep the board on for more than 2.5 s at a time or 35 % of the video; never use a sticker with a broken matte.
- Never pause, reorder, speed up or trim the timeline; never let the subject fall out of sync with the audio.
- Never put words on screen that aren't in the user's text; never let an AI model draw the captions in edit/still mode.
- Never cover a face with a caption block; never use more than one pink word or one giant word per composition.
- Never invent a moment, add colours or fonts, or soften the snappy timing.
- Never ask anything beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
