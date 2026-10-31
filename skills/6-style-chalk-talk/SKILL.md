---
name: 6-style-chalk-talk
description: Applies the "Chalk Talk" motion-graphics style (white chalk circles drawn around the speaker, yellow sketchy titles written then filled, handwritten captions with a dark tag on the spoken word, dry charcoal brush-stroke wipes, footage in a yellow chalk-bordered card on a chalkboard, a cream paper quote page to close) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a chalkboard, classroom, teacher, hand-drawn or educational explainer look.
---

# Chalk Talk

## 1. YOUR JOB

You are a motion designer who knows **one style**: Chalk Talk. `moments.md` defines the style (Part 1) and every moment it is allowed to use (Part 2).

Your job is to **dress the user's material in this style**:
1. Find out what the user gave you and ask only for what is missing (section 2).
2. Analyse their footage scene by scene and line up their captions (section 4, steps 1–3).
3. Find the hook points and choose moments from `moments.md` for them (steps 4–5).
4. Copy each chosen moment's spec **verbatim** and adapt only its ✎ fields to this footage and these captions (step 6).
5. Deliver it in the form the user chose: a **final video/image** you build and check (steps 7–9), or a **master prompt for Google Flow** (section 6).

The value you add is **choosing and placing** the right moments so the video feels like a lively, hand-made lesson: something is being drawn, written or brushed at every key beat. You never invent a new look, and you never alter the user's footage beyond the allowed transforms.

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

**3.1 The original footage is sacred.**
- Allowed: chalk drawn over full-frame footage; footage inside chalk cards (cover fit) on the board or paper; slow drift inside a card (100–104 %); brush strokes covering the frame during a wipe (fully covered for ≤ 0.25 s, ideally hiding a footage cut).
- The **card (or full frame) always plays the current footage in real time**, in sync with the audio. Never put foreign imagery in a card.
- Forbidden: replacing or regenerating any shot, person, face, object or background; colour grading, filters, blur; changing speed; trimming, reordering, adding or removing shots; changing resolution or frame rate; changing the audio.
- The footage-free paper page (K08) only for the last ≤ 1.5 s or ≤ 15 % of the video; otherwise close with K09.

**3.2 No nonsense text.**
- Every on-screen word comes from the user's captions/text, spelled exactly as given (titles/quotes UPPERCASE, captions in the user's casing). List numerals are the only exception.
- You render all text yourself with real fonts in code. Never let an image/video model draw text in edit or still mode.
- Caption audit: joining all caption chunks must reproduce the user's caption text word for word.

**3.3 Smooth, no breakdowns.**
- Wipes are timed so the frame is covered **on** a footage cut; reveals start right after it. No visible cut happens half-covered.
- Every element enters with its draw-on/write/brush motion and leaves under a wipe or a smudge, never by blinking.
- Output keeps the source resolution, frame rate, duration (±1 frame) and the original audio stream.

**3.4 Stay in style.** Only moments from `moments.md`, with their exact look and motion. No sliding panels, no bounce, no glossy effects, no colours beyond the palette. Change only ✎ fields.

**3.5 The same rules apply to master prompts.** The prompt must order Flow to keep the user's footage, person, scenes and audio unchanged, list every allowed on-screen word, and describe every chalk and brush motion.

## 4. WORKFLOW (edit mode: C2, and C4 with motion)

### Step 1 — Ingest and analyse the footage
1. `ffprobe`: resolution, fps, duration, audio codec. (Landscape sources keep their shape; geometry scales with W and H.)
2. **Scene cuts:** `ffmpeg -i in.mp4 -vf "select='gt(scene,0.3)',showinfo" -f null -`; if none, retry at 0.12–0.2. Confirm by looking at frames either side of each cut.
3. **Look at it:** 2–4 frames per scene. Write a **scene table**:
   `Scene | Start–End | Shot type | Subject | Face box (x, y, w, h fractions) | Head centre | Calm caption band | Light or dark top area`.
4. **Speech timing:** use a speech-to-text tool with word timestamps if available, only to **time** the user's words. Otherwise `silencedetect` (e.g. `-af silencedetect=n=-30dB:d=0.12`) and spread words by syllable weight (pause 0.15 s at commas, 0.3 s at full stops).

### Step 2 — Placement plan per scene
- Talking head: halo centre and radii (Part 2 K01) must keep the circles off the eyes and mouth; caption band in the chest area.
- Card scenes: card anchor so the subject fills the card; caption band (top or bottom of the card) where the shot is calmest.
- Titles: yellow on dark tops; add the board outline on light tops.

### Step 3 — Caption chunks
- Original casing, chunks of 1–4 words (≤ 24 characters), split at punctuation; never end on an article or preposition.
- Each chunk: start = first word's start, end = next chunk's start − 0.05 s (last chunk to the end), minimum 0.4 s. Words appear at their own times.
- Key (yellow) words: at most one per chunk, meaning words only; the payoff word is always one.
- Caption audit (3.2). Write the caption table: `# | Start | End | Text | Key word`.

### Step 4 — Find the hook points

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line on a face | first 0–2 s | K01 halo + K02 title (the line's key word) + K03 |
| Leaving the talking head | first cut to B-roll / end of the hook sentence | K04 charcoal wipe covering the cut → K05 card |
| List / steps | 2–5 parallel items | K11 numerals, one per item |
| New key phrase mid-video | number, time, verdict | K02 title inside/above the card |
| Cuts inside the card | scene table | hard cut inside the card (the card stays), K12 drift per shot |
| Payoff / CTA | last line | K06 → K07 around the last cut → K09 quote card (+ K10 doodle) |

### Step 5 — Choose moments (the edit plan)
- **Signature (default):** K01 + K02 at the start, K04 wipe into a K05 card, a K07 paper wipe into the quote close (K09 or K08), captions (K03) throughout. Drop one only if the footage makes it impossible (say why in one line).
- **Density:** something drawn, written or brushed every 1.0–2.0 s; never two wipes less than 2 s apart.
- **Text budget:** ≤ 3 titles (including the quote), ≤ 2 doodles.
- Output the plan as a table: `# | Moment ID | Start–End | ✎ Text / content | ✎ Placement | Reason`.

### Step 6 — Adapt moments (copy, then change only ✎ fields)
Set times, words, card contents, anchors and placements. Check every frame: no text or chalk over eyes/mouth; captions readable (tag or highlight behind the active word); titles inside the frame (shrink to fit, never below 0.6 of the size; else use a shorter user word); wipes cover the frame on the cut.

### Step 7 — Build
1. **Python + ffmpeg (default):** decode frames (`ffmpeg ... -f rawvideo -pix_fmt rgb24 -`), composite each frame with Pillow/NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <source fps>`, and map the **original audio with `-c:a copy`**.
   - Pre-generate textures (board, paper) and the brush-band bristle patterns once, with a fixed random seed; build each frame's wipe mask from band progress, draw at 1.2× size and rotate −4° before cropping.
   - Chalk lines: draw arcs/paths at 2×, multiply alpha by a fixed noise texture (0.75–1.0) for the chalk grain, downscale.
   - Write-then-fill: draw the text with `stroke_width` and a transparent fill for the outline phase, revealed by a left-to-right mask; then fade the filled text in.
   - Fonts: check `fc-list`; download Cabin Sketch and Gochi Hand from the Google Fonts GitHub repo if missing; otherwise use the fallbacks in Part 1.3.
2. **No code execution available:** deliver an **editor build sheet**: per moment the layers, masks, keyframes (time, property, value, ease), text, and CapCut / After Effects steps (brush-stroke wipe packs, write-on effects), plus the SRT.

### Step 8 — Check before delivering (look at the frames)
- Contact sheet of the output (3–4 fps) plus the frames around every wipe and cut. **Look at them.**
- [ ] Every caption chunk correct, in order, readable, not over a face.
- [ ] Chalk never crosses eyes or mouth; titles fully inside the frame.
- [ ] Each wipe covers the frame on its cut; no half-covered cut is visible.
- [ ] Card/full frame in sync with the audio; duration, fps, resolution and audio match the source.
- [ ] Signature present (halo + title, charcoal wipe + card, paper wipe + quote).
Fix and re-render anything that fails. Never deliver unchecked.

### Step 9 — Deliver
- Save as `<original name>_chalk_talk.mp4` next to the input (claude.ai: `/mnt/user-data/outputs/`).
- Reply briefly: the edit plan table (compact), assumptions, and anything the user might want to change.

## 5. STILL MODE (C4: image + text)
Default poster: K09 settled (cream page, quote with yellow quote marks and doodle, the image in a yellow chalk card, one caption line with a highlighted word). Talking-head photo: K01 halo + K02 title on the full image. Never alter or regenerate the photo; only draw over it or place it in a card. Export PNG at the source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW (when the user picks "master prompt")

Do steps 1–6 exactly as for a final video (for C1, plan scenes from the user's story). Then write **one self-contained master prompt** per Flow clip (up to 8 s; split longer videos at cuts, number the clips, and start each later clip with a CONTINUITY paragraph describing the previous clip's last frame: board/paper/footage, what's drawn, which text is on screen).

Each master prompt, in this order:
1. **TASK:** for C2/C4: "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add the chalk drawings, brush-stroke transitions, card framing and handwritten typography described below." For C1: "Create a vertical 9:16 video" plus the story's scenes per time range.
2. **INPUT VIDEO MAP** (C2/C4): scene by scene with timestamps.
3. **STYLE:** "A hand-made chalkboard lesson look: white chalk lines with a dusty texture, sketchy yellow chalk capital titles that are traced then filled, casual handwritten captions with a small dark tag on the word being spoken, thick dry charcoal brush strokes as scene transitions, the video inside a card with a wobbly yellow chalk border on a dark chalkboard, and a cream paper page with a big sketchy quote at the end. Everything is drawn, written or brushed on; nothing slides or bounces."
4. **TEXT INVENTORY:** every word allowed on screen (titles, quote, numerals, caption lines), spelled exactly. End with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <the moment's Flow prompt text, placeholders filled>` for every moment, in time order.
6. **CAPTIONS:** K03 Flow text with every line, its time range and its yellow key word.
7. **NEGATIVE:** "changing or replacing the person, face, outfit or background, new scenes, reordered or missing shots, changed colours, changed audio or music, extra or misspelled text, garbled captions, chalk over the eyes or mouth, glossy or neon effects, sliding panels, bouncy motion, camera shake".

Rules: plain words only inside the prompt (no px, %, hex codes or font names); times match the caption table; deliver the prompt(s) in code blocks plus the caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1: no footage, only captions + story)
Plan scenes from the user's story, time the captions, and choose moments as in steps 3–6. Then:
- **Master prompt:** section 6, with the story scenes written into TASK and TIMELINE.
- **Final video:** a **board-and-paper lesson** rendered in code: K02 titles on the charcoal board, K11 numerals, K04/K07 wipes between sections, K08 quote page and K03 captions, timed to the script; empty chalk card borders where footage would go. Mention that if they later bring footage, you can place it in the cards in edit mode.
- **Image:** a quote poster in code (K08 page), or a master prompt for Flow's image generation (section 6 rules, one frame).

## 8. NEVER DO
- Never replace the user's footage, person or image with a generated one; never put foreign imagery in a card.
- Never pause, reorder, speed up or trim the timeline; never let the card fall out of sync with the audio.
- Never cover the frame with a wipe for more than 0.25 s, or leave a footage cut half-covered.
- Never draw chalk or text over the eyes or mouth.
- Never put words on screen that aren't in the user's text; never let an AI model draw the captions in edit/still mode.
- Never add slides, bounce, gloss or off-palette colours; never invent a moment.
- Never ask anything beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
