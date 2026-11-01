---
name: 148-style-cream-ink-pages
description: Applies the "Cream Ink Pages" motion-graphics style (full-frame footage under bold white word-by-word captions with an amber label-box key word and small drawn stickers, cutting to warm cream paper pages that hold the footage in a rounded card beside plum ink captions, a rolling step number over a gradient progress bar, and a traced scalloped badge) to the user's own video, image or captions without altering the footage, as a finished video/image or a detailed Google Flow master prompt. Use when the user wants a cream paper, step-counter, list-explainer, label-caption or creator-notes look.
---

# 148-style-cream-ink-pages — Cream Ink Pages

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
- Allowed transforms (moments.md 1.6): full-frame display, untouched; live footage scaled into the rounded page card (cover-fit); page, text and sticker overlays.
- The primary window (full frame or card) always plays the current footage in real time, in sync with the audio.
- Forbidden: replacing or regenerating any shot, person, face, object or background; blur, glitch, warp, colour grading or filters on the shown footage; speed changes; trimming, reordering, adding or removing shots; changing resolution, fps or audio.
- A page may cover the footage except the card for at most 3 s at a time.
- Never answer C2 or C4 with newly generated footage.

3.2 **No nonsense text.**
- Every on-screen word is the user's exact word (case as written). Numerals only as step counters.
- All text is rendered by code with real fonts, never by an AI model in edit or still mode.
- **Caption audit:** joining all caption chunks (plus words moved into a badge) reproduces the user's text word for word and in order. Assert it before building.

3.3 **Smooth, no breakdowns.**
- Hard switches only on footage cuts, page cuts (X1) and caption chunks; everything else eases.
- Layout of a chunk is fixed before its first word appears.
- **No overlaps:** assert that no two caption chunks are visible on the same frame, and that captions never overlap stickers, HUD or each other.
- **Inside the frame:** assert every text and graphic bounding box keeps ≥ 0.05W from the left and right edges and sits within 0.03–0.97H.
- **Face safe:** assert no caption, sticker, HUD or badge box intersects the speaking face box while it speaks (captions sit below it).
- Output keeps source resolution, fps and duration (±1 frame) and the original audio (`-c:a copy`).

3.4 **Stay in style.** Only moments from moments.md. Never: footage blur, tilt, glitch, shake, letter-by-letter typing, emoji, extra accent colours, more than 3 label boxes per video.

3.5 **Same rules in master prompts.** Order Flow to keep footage, person, scenes and audio unchanged, list every allowed word, describe all moves as smooth.

## 4. WORKFLOW (edit mode)

**Step 1 — Ingest and analyse.** `ffprobe`; scene cuts with `select='gt(scene,0.3)'` (retry 0.12–0.2); look at 2–4 frames per scene. Scene table:

| Scene | Start–End | Shot type | Subject | Face box (x,y,w,h) | Page-safe (card fits?) | Caption zone free? | Crop anchor |
|---|---|---|---|---|---|---|---|

Speech timing: speech-to-text word timestamps only to time the user's words, else `silencedetect=n=-30dB:d=0.12` with syllable-weighted spreading, 0.15 s pause at commas, 0.3 s at full stops.

**Step 2 — Safe zones.** Face box per scene; caption zone y ≥ 0.54H on a speaker; HUD only left of the face.

**Step 3 — Caption chunks.** 1–3 words per footage chunk (helper above key), 2–3 lines per page chunk, split at punctuation, never end on an article or preposition, chunk changes on cuts when possible. Start = first word's start, end = min(last word start + 0.6, next start − 0.02). One key word per chunk at most; label boxes ≤ 3 per video. Caption table `# | Start–End | Theme (footage/page/badge) | Lines | Flags`. Run the audit.

**Step 4 — Hook points.**

| Hook point | How to spot it | Typical moments |
|---|---|---|
| Opening line | First 0.5 s | C1 (+ U1) |
| Theme word | The topic noun | C1 key word, K1 |
| Contrast or turn | "isn't", "but", "instead" | K1 |
| Person → B-roll cut | Scene table | X1 into P1 |
| B-roll → person cut | Scene table | X1 out, C1 |
| List or steps | 2–4 parallel phrases | P1 + N1 + C2 per step |
| Last list step on footage | Full-frame shot | H1 |
| Numbers, time phrase, slogan | Digits, "one year" | B1 |
| Money, price, result words | Nouns | S1 |
| Payoff / last line | Final chunk | E1 |

**Step 5 — Choose moments.** Signature moments in every output: C1 or K1 (captions), P1 + N1 (at least one page), B1 or E1 (closing beat), X1 on page cuts. A visible change every ~1.5–3 s; page runs 1.2–3.2 s; same moment type ≤ 2× except C1; different videos get different plans. Output plan table `# | Moment ID | Start–End | ✎ Text/content | ✎ Position/anchor | Reason`.

**Step 6 — Adapt.** Copy specs; change only ✎ fields. Check faces, margins, overlaps.

**Step 7 — Build.** Python + ffmpeg: decode frames one at a time, composite with Pillow and NumPy, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r <src fps>`, `-map 1:a -c:a copy`. Pre-render word sprites, stickers, the page, numerals and the card shadow once at 2× and downscale; per-frame only blur, bar and badge trace. Montserrat is a variable font: set the weight axis (700, 800, 900). Use one render worker. Keep the render script in a scratch folder. No code execution: write an editor build sheet instead.

**Step 8 — Check.** Contact sheet (fps 1.2, 6×2) plus frames at every page cut, step roll and the badge; look at them. Checklist: captions correct and in order; no overlap; all text inside margins; faces clear; page flash short; card live and in sync; signatures present; duration, fps, resolution and audio match. Fix and re-render.

**Step 9 — Deliver.** `<original name>_cream_ink_pages.mp4`; reply with a compact plan table, assumptions, what the user may change.

## 5. STILL MODE (C4)
Photo full frame, C1 settled in the caption zone, K1 on the key word; or a page with the photo in the card. Export PNG at source resolution.

## 6. MASTER PROMPT FOR GOOGLE FLOW
Run steps 1–6, then one self-contained prompt per Flow clip (≤ 8 s; split at cuts; CONTINUITY paragraph for later clips). Order: TASK ("Use the attached video as the base. Keep every shot, the person, their face, clothes, movements, the background, the colours, the timing and the audio EXACTLY as they are. Only add …") · INPUT VIDEO MAP · STYLE (plain words: bold white word-by-word captions, golden label box, cream paper pages with a rounded video card and dark plum words, rolling step number over a gradient bar, scalloped badge) · TEXT INVENTORY ("Nothing else is written anywhere.") · TIMELINE · CAPTIONS · NEGATIVE (changing the person, face, outfit or background, new scenes, reordered shots, changed audio, extra or misspelled text, emoji, blur, glitch, shake). Plain words only. Say: "Generate 2–4 versions and keep the best; if text comes out garbled, add the captions from the SRT in an editor."

## 7. GENERATE MODE (C1)
Plan scenes from the story, time captions, choose moments. Final video: pages only (cream page, numerals, bar, badge, captions), no fake footage. Image: typography poster in code.

## 8. NEVER DO
- Never replace footage, a person or an image.
- Never pause, reorder, speed up or trim; never desync the primary window.
- Never cover, cut or blur a speaking face.
- Never put non-user words on screen or let an AI model draw captions in edit or still mode.
- Never add effects or moments outside moments.md.
- Never ask beyond the missing inputs and the one output question.
- Never deliver without looking at the rendered frames.
