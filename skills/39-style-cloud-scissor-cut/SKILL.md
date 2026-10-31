---
name: 39-style-cloud-scissor-cut
description: Applies the "Cloud Scissor Cut" motion-graphics style (a powder-blue torn-paper cloud with pencil doodles dropping from the top with a heavy black title, tiny slanted hand-lettered white captions, then a rising frosted paper band with a scissors-in-hand snip that turns captions into bold white block type) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a paper-craft, DIY, doodle, scissors, zine or frosted-paper look.
---

# 39-style-cloud-scissor-cut — Cloud Scissor Cut

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
- Allowed transforms (from moments.md 1.6): full-frame display; the frosted paper band (lower 40 % of the frame at most, footage ghosting through it, the rest clear); the cloud top overlay; caption, doodle, hand and scissors overlays.
- The primary footage always plays in real time, in sync with the audio, under every overlay.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, zoom, colour grading or filters; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- Paper band on screen ≤ 45 % of the video; one hold ≤ 3.5 s. Hand and scissors only for the 0.6–0.85 s snip beat, ≤ 0.35H tall. No doodles outside the band.
- Never answer C2 or C4 with newly generated footage of a different person or scene.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word. This style sets all captions and titles in UPPERCASE; that is the only case change. Numerals only if the user wrote them. No labels, tags or doodle lettering of your own.
- Title words come from the user's own text (or a title the user supplied) and are removed from the caption chunks; never invent a title.
- All text is rendered by code with real fonts; never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks plus the words moved into titles (T1, E1, C3) reproduces the user's text word for word and in order. Run it before building (assert in code, case-insensitive).

3.3 **Smooth, no breakdowns.**
- Continuous motion curves from moments.md. Hard switches only on footage cuts and for caption chunks (hard cuts by design).
- Every element enters and exits with its moment's motion; nothing blinks; no empty frames.
- Never start a cloud drop or paper rise within 0.1 s after a footage cut (a paper rise may end on or just after a cut to hide it). A cloud lift must finish ≥ 3 frames before the next cut.
- Output keeps source resolution, fps and duration (±1 frame) and the original audio stream (`-c:a copy`).

3.4 **Stay in style.** Use only moments from moments.md, with their exact look and motion. Never: bounce, overshoot, spring, rotation, shake, flashes, colour grading, letter-by-letter typing, other wipes, glitch, scale pops on captions, extra colours, lowercase captions, the cloud or paper over a speaking face, full-frame paper, a held hand.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.**
- Run `ffprobe` for size, fps, duration, audio.
- Detect scene cuts with `select='gt(scene,0.3)'`; if none, retry 0.12–0.2; confirm each cut visually.
- Look at 2–4 frames per scene (view them).
- Build the scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h as fractions) | Speaking face? | Bright or busy in lane (0–1) | Band fits under face? | Crop anchor |
|---|---|---|---|---|---|---|---|---|

- Speech timing: use speech-to-text word timestamps only to time the user's own words. Otherwise run `silencedetect=n=-30dB:d=0.12` and spread the words by syllable weight, with a 0.15 s pause at commas and 0.3 s at full stops. No speech: spread phrases across each shot (1.0–2.5 s each).

**Step 2 — Safe zones and framing plan per scene.** Face never covered while speaking. Decide per scene: cloud top (fits above the face?), script lane position, whether the band fits under the face, bold lane.

**Step 3 — Caption chunks.**
- Script chunks (C1): 3–5 words, split at punctuation, never end on an article, preposition or conjunction, 0.8–2 s. Bold chunks (C2): 2–6 words, same rules. Chunk changes at cuts when possible.
- Choose the title words for T1 and E1 (topic words near the start; a time phrase, amount or payoff near the end); remove them from the chunk list. Choose 0–2 C3 solo words.
- Output a caption table: `# | Start–End | Moment | Text | Lines`. Run the caption audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First sentence, first 0.5 s | T1, C1 |
| Theme or topic word | The noun the whole video is about | T1 title words |
| Contrast or turn | "but", "isn't", "instead", "never", "the truth" | C1 chunk break, X1 |
| Person → B-roll cut | Scene table | X1 → X2 (paper top lands on the cut) |
| B-roll → B-roll cut | Scene table | C2 chunk change, or X3 → X1 → X2 |
| B-roll → person cut | Scene table | X3 ending on the cut |
| Any later cut | Scene table | caption chunk change |
| List or steps | "first", "second", 3+ parallel phrases | X2 + C2 per item |
| Numbers, amounts, time phrases | Digits, "one year", "every day" | C3 or E1 |
| Long static shot (> 2 s) | Scene table | scissor snap, caption change |
| Section change without a cut | Pause, new topic word | X1 → X2 band |
| Payoff or call to action | Last line | E1 |

**Step 5 — Choose moments.**
- Signature moments are mandatory in every output: **T1** (opener), **C1** (script captions on face or calm shots), **X2 + C2** (paper band with bold captions, placed under the chin on a talking head), **X3** (exit, if X2 is not holding to the end). Add X1 before every X2 that has ≥ 0.6 s of lead-in. Unless physically impossible: for a video shorter than 4 s, shorten T1's hold and X2's hold, never drop them. If no shot allows an X2 band, state it and use T1, C1, E1 only.
- A visible change every ~1.5–3 s (chunk, title, paper). Never two big moves (cloud, paper) within 0.6 s of each other. Never title and paper-cover covering the same 0.5 s.
- Variety: C3 at most 2×; E1 only once; different videos get different plans.
- Output the plan table:

| # | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason (because the caption says… / because the shot shows…) |
|---|---|---|---|---|---|

**Step 6 — Adapt.** Copy each moment's spec; change only the ✎ fields. Check every frame of the plan: faces safe, captions readable and inside the frame (≥ 0.04W from the edges), the cloud not over the face, the paper band within the lower 40 % and clear of any face.

**Step 7 — Build.**
- Python + ffmpeg: decode raw frames one at a time, composite per frame with Pillow and NumPy, encode with `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`.
- Pre-render once: cloud, cloud shadow, paper layer (with doodles), five scissor states, every caption word, titles. Seeded grain (fixed seeds) so nothing flickers.
- Use the exact easing curves of the moments. Clamp every paste to the frame (paste with cropping, never negative offsets).
- Draw shapes and text at 2× and downscale for anti-aliasing. Download fonts from the Google Fonts GitHub repo if missing, else use the fallbacks. Measure text before drawing; lay out each chunk completely before its first word appears so no word moves.
- Style-specific notes: variable fonts need `set_variation_by_axes([weight, width])` in the file's axis order (Archivo: weight first, then width); script captions get a synthetic shear of 0.18; punch the scissor ring holes through the alpha channel; the paper band layer is 0.38H + 150 px tall with the scallops in its top 150 px; the hand exists only for the snip beat; drawn text sits over the hand but under the cloud.
- Keep the render script in a scratch folder.
- No code execution: write an editor build sheet instead (layers, keyframes, text, CapCut or After Effects steps, SRT).

**Step 8 — Check before delivering.**
- Make a contact sheet at 3–4 fps plus frames around every cut, the paper rise and the paper exit. Look at them.
- Checklist: captions correct, in order and readable on both light and ghosted footage; titles not over a face; no word moves after it appears; paper band only in the lower 40 %, no doodles over footage; scissors snip; paper gone before the next speaker shot; no unintended jumps; primary footage in sync; duration, fps, resolution and audio match; signature moments present.
- Fix and re-render. Never deliver unchecked.

**Step 9 — Deliver.** Save as `<original name>_cloud_scissor_cut.mp4` (claude.ai: `/mnt/user-data/outputs/`). Reply briefly with a compact plan table, assumptions, and what the user may want changed.

## 5. STILL MODE (C4)

- Use the moments in their settled state: T1 cloud and title at the top, the photo full frame below, one C1 chunk in the script lane (or the paper state: paper band in the lower 40 %, doodles, one C2 chunk).
- Never alter or regenerate the photo. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW

Run steps 1–6, then write one self-contained prompt per Flow clip (≤ 8 s; split at cuts; add a CONTINUITY paragraph to later clips). Order inside each prompt:

1. **TASK:** "Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …" (C1 generate mode: "Create a vertical 9:16 video" plus the story scenes).
2. **INPUT VIDEO MAP:** scene by scene with timestamps.
3. **STYLE:** a plain-words paragraph of the look (powder-blue torn-paper cloud with pencil doodles at the top, heavy black title, thin slanted white hand-lettered captions, a frosted paper band rising over the lower part with a quick hand-and-scissors snip, bold white block captions).
4. **TEXT INVENTORY:** every allowed word, tricky words spelled letter by letter, ending with "Nothing else is written anywhere."
5. **TIMELINE:** `[start–end s] MOMENT NAME. <Flow prompt text, filled>`.
6. **CAPTIONS:** every line with its time range and mode.
7. **NEGATIVE:** changing or replacing the person, face, outfit or background; new scenes; reordered or missing shots; changed colours, audio or music; extra or misspelled text; garbled captions; paper covering a speaking face or more than the lower 40 %; bouncing or spinning text, glitches, flashes, camera shake.

Use plain words only (no px, %, hex, font names). Deliver prompts in code blocks plus a caption table and an SRT. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)

- Plan scenes from the story, time the captions, choose moments.
- Master prompt: section 6 with story scenes.
- Final video: a graphics and typography-only piece rendered in code in this style (plain light plate, T1 cloud and title, C1 chunks, X2 band with C2 on it, X3 exit). No fake footage.
- Image: a typography poster rendered in code, or a Flow image prompt.

## 8. NEVER DO

- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim.
- Never desync the primary footage.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen, or let an AI model draw captions in edit or still mode.
- Never add effects or moments not in moments.md; never break the style's "never" items (3.4).
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
