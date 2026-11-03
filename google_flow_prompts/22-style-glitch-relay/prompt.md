# Google Flow prompt · Glitch Relay
**Type:** motion style (a complete look: layouts, graphics, transitions and captions)  ·  **Source:** your uploaded short video  ·  **Output:** the same video, restyled

## 0. HOW TO USE THIS FILE
1. Open Google Flow and upload the source material named under INPUTS (your video, images or clips).
2. Fill in every field of the INPUTS block below (write NONE where a field is optional and you have nothing for it).
3. Paste this whole file into the Flow prompt box and generate.
4. Check the result against the FINAL CHECK at the end; if something is off, regenerate and quote the failed rule.

---

## 1. YOUR TASK
You are a professional short-form video editor. Take the uploaded short video and apply the "Glitch Relay" motion style to it.

The look in one sentence: Live full-frame footage, glowing lavender word-by-word relay captions, a stacked title that snaps up with a white lightning crack, mirror-fold zoom-blur chroma-split glitch on every cut.

Re-edit the uploaded video in this style: it may use the layouts, containers, graphics, transitions and captions of the style bible below, but the footage itself (people, scenes, voices, sound, order and timing of shots) is never replaced, recoloured, retimed or reordered.

## 2. INPUTS (fill in before pasting)
VIDEO: the short video uploaded in Flow. This is the only footage you may use; never generate new footage, people or scenes.
SCRIPT (optional): <paste the exact words you want shown as captions, or write NONE>
EXTRA NOTES (optional): <words to emphasise, parts to skip, an accent colour as a hex value, or NONE>

## 3. HOW TO USE THE INPUTS
3.1 SCRIPT is provided (anything other than NONE)
- Use exactly those words, in exactly that order, as the on-screen words. Do not paraphrase, correct, translate, add or drop words (apart from splitting them into caption chunks as the style bible says).
- Ignore all text that is already in the video as a source of words (old captions, subtitles, titles): the script wins.
- Time the words to the speech you hear in the video: each caption chunk appears when its first word is spoken and leaves when its last word ends. If the script and the speech differ, follow the speech's timing and keep the script's words.

3.2 SCRIPT is NONE
- Listen to the audio of the uploaded video and transcribe the speech word for word (same language, same spelling style, keep the speaker's own words, numbers and names). That transcript is the script.
- If the video already shows captions you may read them only as a spelling aid for names and unusual words; never copy their look or position.
- Mark pauses and sentence ends from the audio; they decide where chunks break.

3.3 Existing captions and text from another style (do this BEFORE adding anything)
- Scan the whole uploaded video for burned-in captions, subtitles, karaoke words, titles, lower thirds, emoji or word stickers, progress bars, watermarks and any other text or graphics that a previous edit added on top of the footage.
- Remove all of them completely in every frame where they appear: reconstruct the footage behind them cleanly (no ghost outlines, no smeared or blurred patches, no colour shifts). Original footage must look as if the old text had never been there.
- Keep text that belongs to the scene itself (street signs, shop names, product labels, phone or laptop screens, book covers, clothing prints), unless it is clearly an old caption.
- The reason: this style brings its own captions and graphics. If the old ones stay, the same words appear twice on screen, one in the old look and one in the new look. That must never happen.
- Only after the video is clean, add this style's text and graphics from the script.

3.4 EXTRA NOTES
- Apply them if given (emphasis words, parts to skip, accent colour as a hex value). They never override the hard rules in section 4. If an accent colour is given, swap this style's accent colour for it everywhere; keep neutral colours as they are.

3.5 Audio
- The soundtrack of the uploaded video stays exactly as it is, in sync. Do not generate or add any voice, music or sound of your own.

3.6 Language
- Captions are written in the language that is spoken (or that the script is written in). Keep punctuation as written in the script; for a transcript, add natural punctuation.

## 4. HARD RULES (never break these)
- Footage fidelity: same people, same scenes, same shot order, same timing, same sound. Output length equals input length (within one frame).
- The speaking face is never covered, blurred or distorted while the person speaks.
- Every word on screen comes from the script (or the transcript). Spell it exactly. No extra words, no filler, no lorem ipsum.
- Captions are in sync with the speech: a chunk starts when its first word is spoken.
- Only one caption system is ever visible: old captions are removed first (3.3), then this style's captions are added.
- Use only the fonts, colours, shapes and motion described in the style bible below. Do not mix in other looks.
- Keep everything inside the frame with the style's safe margins.

## 5. HOW TO BUILD THE EDIT (work in this order, silently)
1. WATCH the whole video: list its shots with start and end times (every cut), note who speaks, where the face is in each shot and where the quiet or busy areas of the frame are.
2. PREPARE THE WORDS (section 3): remove old captions, then get the script (given or transcribed) and split it into caption chunks the way the style bible's caption section says (chunk size, line breaks, emphasis words).
3. TIME THE WORDS to the audio: for every chunk, its start and end second.
4. PLACE THE MOMENTS: choose from the moment library below. Use each signature moment where the video gives it a reason (openers on the first words, cut moments on real shot cuts, closers after the last spoken word); use the recommended combinations as starting points, not as a fixed template. Do not use more variety than a short video can carry.
5. CHECK THE SAFE ZONES (style bible): the speaking face is never covered; text stays inside the safe margins; if footage content (a sign, a screen) sits where the caption lane is, move the lane as the style bible says.
6. RENDER the video: every graphic and word appears and disappears exactly as the moments describe (timing, easing and entrance), cut to cut, and stays in sync with the audio.

## 6. STYLE BIBLE
### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Caption white | #FFFFFF | Words already spoken in the current chunk |
| Caption lavender | #C5B5FD | The newest word in a chunk |
| Caption dim | #7F879B at 0–100 % alpha | The fade-in stage of a new word |
| Title lavender | #E3D1FA | Stacked title fill |
| Glow violet | #B79CFF | Soft outer glow on title and on lavender words |
| Glow white | #FFFFFF | Soft outer glow on white words |
| Caption shadow | #000000 at 50 % | Small drop shadow under all caption words |
| Bolt white | #FFFFFF with #DCCBFF glow | Lightning cracks |
| Fringe red / blue | channel shift only | Chroma split in transitions (no flat colour is drawn) |

Brand-swap rule: if the user gives a brand colour, replace Caption lavender, Title lavender and Glow violet with tints of it (same lightness); keep white and black as is. Never add other colours. The footage's own colours are never touched.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, no cards, no borders, no masks, no rounded corners. |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor = the speaker's face box (or the main subject on B-roll). |
| Overlays | Text and light effects only. No boxes, bars, stickers, gradients or vignettes. |
| Backdrop | None. There is no page colour; the footage is the whole picture. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Caption lane | 0.09, 0.66, 0.91, 0.78 [97,1267,983,1498]; centre line y = 0.72H [1382]; text centred at x = 0.50W | Every caption chunk |
| Title block | 0.17, 0.05, 0.83, 0.17 [187,102,897,320] | Stacked title, final state |
| Title block, small state | 0.335, 0.085, 0.665, 0.14 [362,163,718,269] | Stacked title before it snaps up |
| Alt caption lane (face conflict) | 0.09, 0.82, 0.91, 0.92; centre y = 0.87H | Only if the face box reaches below 0.62H |
| Alt title block (face conflict) | same width, shifted so its bottom edge sits ≥ 0.03H above the face top | Only if the face box top is above 0.20H |
| Alt title block, tuned (720x1280 demo, hair top at 0.145H) | cap height 0.0425H, line pitch 1.13 x cap, top edge 0.028H, bottom edge 0.12H; small state top edge 0.050H, scale 0.50 | Proven on a talking head whose head top sits at 0.145H; the title is then ≈ 0.30W wide |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Caption word | Heavy geometric sans, UPPERCASE, round bowls, tight but not touching, centred | Josefin Sans Bold | Poppins Bold, Outfit ExtraBold, Montserrat ExtraBold | Cap height 0.046H [88]; font size ≈ 0.117W [126]; letter-spacing 0 to −0.01em |
| Caption emphasis word | Same face as caption | same | same | 1.6× the caption size, bottom-aligned to the caption baseline |
| Title | Same face, UPPERCASE, two stacked lines, centred, very tight tracking (−0.02em), tight leading | same | same | Cap height 0.053H [102]; font size ≈ 0.135W [146]; line pitch 0.060H [116]; widest line ≤ 0.66W [710] |
| Counter numeral (T2) | Same face, one numeral | same | same | Cap height 0.053H [102] |

Font note: the exact family of the reference was identified by letterform shape only (splayed M, circular C/O, pointed A, straight-leg R). Check the render against the title crop and fall back in the order above. Download from the Google Fonts GitHub repo if missing.

Rules: all text UPPERCASE. Words exactly as the user wrote them (punctuation kept). No outline-only text. No italics. Text never rotates or tilts.

Caption look (all words): fill colour per 1.1, outer glow 10 px radius at 60 % alpha (tuned: gain 1.44 on a sigma of 0.6 x radius so it reads at 720 W) in the glow colour matching the word, plus a drop shadow (0, +6 px, blur 8 px, black 50 %).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Entrances of text | ease-out (strong, quartic: 1−(1−t)^4) | 3 f for a caption word, 8 f for the title snap |
| Exits of text | hard cut or 2 f linear fade | 1–2 f |
| Warp-in (before a cut) | ease-in (t^2) | 4–8 f |
| Warp-out / landing (after a cut) | ease-out (strong) | 9–11 f |
| Beat punch | instant scale step then ease-out blur decay | 6 f |

Never: bounce, overshoot, spring, rotation of text, wipes, slides, sliding captions, zoom-out reveals, colour changes other than white↔lavender, shake, strobe longer than 11 f.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Scale-in (punch or drift) about the face (or subject) anchor | Total scale ≤ 1.30 over the whole video; face never cropped by the frame edge |
| Zoom blur, mirror fold, chroma split, brightness lift, soft blur | Only inside X1, X2 and M1 windows; footage returns to untouched pixels afterwards; brightness lift ≤ +25 % |
| Overlaying text and bolts | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming, trimming or colour-grading footage outside the windows above; speed ramps; freezing; adding B-roll that the user did not supply. The primary footage plays live, in sync with the audio, at all times (a warp only distorts the pixels of the live frame). A shot is never fully hidden: the mirror fold keeps the real frame visible in both halves.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by text or bolts. Lightning is routed around the face box with ≥ 0.04W clearance. Warps may distort the face only inside the X1/X2/M1 windows (≤ 0.8 s each). |
| Caption lane | Fixed at y = 0.72H unless the face box reaches below 0.62H (then Alt lane). |
| Title block | Top of frame; moves only per 1.3 Alt. |
| Footage text (signs, UI) | If readable footage text sits in the caption lane for more than 1 s, use the Alt caption lane for that chunk. |
| Edges | Every glyph stays ≥ 0.04W from the left and right edges. |

---

## 7. MOMENT LIBRARY
Family codes: **T** title · **L** light effect · **C** caption · **X** transition · **M** footage motion · **E** ending.

### MOMENT T1 · STACK TITLE SNAP
**What it is:** a two-line stacked title appears small near the top, waits briefly, then snaps up to double size with a white lightning crack, glows, holds, and cuts out.
**Use when:** the opening line states the topic; the video starts on a speaker or calm shot; the first sentence has 2–3 topic words. **Avoid when:** the first 0.4 s already contains a hard cut or a face in the title block that cannot be moved (use Alt).
**Text:** 2–3 words from the user's own words (or a title the user supplied), UPPERCASE, split into two lines (1–2 words per line), widest line ≤ 12 characters at final size (shrink the size so the widest line is ≤ 0.66W).
**Geometry / Graphics:** Title lavender fill with Glow violet outer glow (18 px radius, 55 % alpha). Final state in the Title block; small state in the small-state block (scale 0.50 of final, same centre x = 0.50W, top edge 0.085H).
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.33–0.42 [8–10] | title | alpha | 0 → 1 (small state) | linear, 2 f |
| 0.42–0.67 [10–16] | title | scale | 0.50 → 0.52 (slow creep) | linear |
| 0.67–0.96 [16–23] (tuned when the first cut is < 2 s away: 0.45–0.74 [11–18]) | title | scale | 0.52 → 1.00 (width 0.344W → 0.658W); top edge 0.085H → 0.053H | strong ease-out (quartic) |
| 0.67–1.08 [16–26] | title | glow alpha | 55 % → 100 % at 1.0 s → 55 % | triangle |
| 0.96–2.50 [23–60] | title | hold | final state, no motion | — |
| 2.50–2.58 [60–62] | title | alpha | 1 → 0 | linear, 2 f |

Tuned for a first cut at 1.83 s: fade-in 0.30 s, snap 0.45–0.74 s, hold to 1.28 s, fade-out 1.28–1.36 s (X1 window starts 1.67 s); bolts 0.45–0.87 s. The 1.2 s minimum after the snap yields when a cut is closer than 2.6 s.

Start time: 0.33 s after the first word (≈ 0.3–0.5 s into the video). Hold: until 0.3–0.4 s before the first big transition, never longer than 2.6 s total on screen; minimum 1.2 s on screen after the snap.
**Footage / plate behaviour:** footage untouched.
**Captions during it:** captions run normally in the caption lane; the title never shares a region with them.
**Exit:** 2 f linear fade, at least 0.3 s before any X1/X2 window starts.
**Flow prompt text:** "Early in the video, a short two-line title in all capital letters, reading {{TITLE_LINE_1}} over {{TITLE_LINE_2}}, fades in small near the top of the frame in soft lavender with a gentle violet glow. After a moment it smoothly grows to about double size while a white lightning crack flashes across the edges of the picture, then it holds for about a second and a half and disappears. It never covers the speaker's face."
**Still-image state:** final state (size 1.00, glow 55 %).

### MOMENT L1 · LIGHTNING CRACK
**What it is:** two or three jagged white cracks flicker across the picture while the title snaps up.
**Use when:** with T1; optionally once more at a payoff word (max 2 per video). **Avoid when:** the face box fills > 60 % of W and no side margin is free (shorten to the top and bottom edges only).
**Text:** none.
**Geometry / Graphics:** 2–3 polylines, each 8–14 random-walk points, running from one frame edge to another. Width tapers 17 px → 5 px [at 1080 W; tuned up from 10 → 3, which read too thin at 720 W]. White core with a 14 px #DCCBFF glow (blur sigma 0.8 x radius, gain 3.0). Bolts run edge to edge below or beside the face box (e.g. left edge y 0.56H to right edge y 0.47H; left edge y 0.30H to bottom x 0.22W; right edge y 0.12H to bottom x 0.82W). All points stay ≥ 0.04W away from the face box.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.67–0.75 [16–18] | bolts | alpha | thin cracks 40 % → full | step |
| 0.75–1.04 [18–25] | bolts | per-frame | redraw with new jitter (≤ 0.02W) every frame; peak at 0.75 s [18] and 1.0 s [24] | flicker |
| 1.04–1.08 [25–26] | bolts | alpha | 100 % → 0 | 1–2 f |

Total 0.42 s (10–11 f). The bolt seed is fixed per video so a re-render is identical.
**Footage / plate behaviour:** footage untouched under the bolts; add +6 % brightness during the two peaks (optional).
**Captions during it:** unchanged.
**Exit:** hard cut after the last flicker frame.
**Flow prompt text:** "As the title grows, a few thin jagged white lightning cracks flicker quickly across the edges of the picture for under half a second, never crossing the speaker's face, then vanish."
**Still-image state:** none (omit in stills).

### MOMENT C1 · RELAY CAPTION
**What it is:** one line of one or two words at a time. The newest word fades in as a dim ghost and settles into lavender while the word before it turns white. When the chunk ends it disappears in one frame and the next chunk starts a moment later.
**Use when:** always, for every spoken or written line. **Avoid when:** never.
**Text:** the user's exact words, UPPERCASE, punctuation kept. Chunk rules: 1–2 words; ≤ 16 characters per chunk, spaces included (a single longer word stands alone and is scaled to fit 0.82W); split at punctuation; never end a chunk on an article, preposition or conjunction ("a", "the", "of", "and", "to"); prefer chunk changes at footage cuts.
**Geometry / Graphics:** Caption lane, centred on x = 0.50W, one line, cap height 0.046H. The chunk's total width ≤ 0.82W (scale down the whole chunk if wider). Two-word chunks use a word gap of 0.30 em.
**Motion:**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | new word | alpha | 0 → 1 | ease-out, 3 f (0.125 s) |
| word start | new word | colour | Caption dim → Caption lavender | same 3 f |
| word start | previous word | colour | lavender → white | instant (1 f) |
| chunk end | all words | alpha | 1 → 0 | hard cut (1 f) |
| chunk end → next start | gap | empty lane | 2–4 f (0.08–0.17 s) | — |

Position stays fixed during a chunk: the first word is already placed where the full chunk will be centred (no sliding). Chunk length 0.4–1.0 s typical; a chunk start = its first word's start time; chunk end = min(last word end + 0.1 s, next chunk start − 0.08 s); minimum 0.4 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system. During an X1 window the lane is empty from the swap − 0.17 s until the next chunk starts (at or just after the swap).
**Exit:** hard cut per the table.
**Flow prompt text:** "Large all-capital captions in the lower third of the frame show one or two words at a time. Each new word fades in softly in pale lavender with a gentle glow while the previous word turns white. When the line ends the words vanish at once and the next words appear a moment later. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one chunk, last word lavender, the other white.

### MOMENT C2 · GIANT EMPHASIS WORD
**What it is:** a single payoff word as its own chunk at 1.6× size.
**Use when:** a strong adjective, number or turn word ("but", "never", a price) opens a sentence or sits alone. **Avoid when:** the word is longer than 9 characters (it would exceed 0.82W); max 2 per video, ≥ 3 s apart.
**Text:** one user word, UPPERCASE, punctuation kept.
**Geometry / Graphics:** C1 look at 1.6× size, bottom edge on the caption baseline, centred x = 0.50W, lavender once settled.
**Motion:** C1 timings (3 f fade-in from dim to lavender); hold 0.25–0.5 s; hard cut out.
**Footage / plate behaviour:** optionally pair with M1 on the same frame.
**Captions during it:** replaces the normal chunk for its duration.
**Exit:** hard cut, then 2–4 f gap, then the next chunk.
**Build notes:** same renderer as C1; scale the font size, not the bitmap.
**Flow prompt text:** "One powerful word, {{WORD}}, appears alone in the lower third at one and a half times the usual caption size, fading in softly from pale grey to lavender, then disappears at once."
**Still-image state:** the word in lavender.

### MOMENT X1 · MIRROR GLITCH WARP
**What it is:** the cut between two shots (or inside one shot) melts through a mirror-folded, zoom-blurred, chroma-split glitch and lands in a soft-focus pull to sharp.
**Use when:** person → B-roll, B-roll → person, any cut where the picture content changes completely. Self-warp (same shot, swap in place) allowed at a sentence boundary on a long static shot, max 2 per video. **Avoid when:** a cut falls within 0.9 s of the previous X1/X2 (use M1 instead).
**Text:** none.
**Geometry / Graphics:** none drawn; the effect is a transform of the live frame (see build notes). Swap time Ts = the footage's own cut time (the swap frame never moves a cut).
**Motion:**

| t relative to Ts (s) [f] | Property | From → To | Ease |
|---|---|---|---|
| −0.17 → 0 [−4 → 0] (outgoing shot; up to −0.33 s [−8 f] for a longer build) | zoom blur strength | 0 → 1.0 | ease-in (t²) |
| same | scale about frame centre | 1.00 → 1.35 | ease-in |
| same | mirror fold (bottom half replaced by the flipped top half, blended) | 0 → 100 % | ease-in |
| same | chroma split (red +dx, blue −dx), dx | 0 → 0.02W [22 px] | ease-in |
| same | brightness lift | 0 → +25 % | ease-in |
| 0 [swap] | shot | outgoing → incoming (cut on the footage's own cut), incoming starts in the full-warp state | hard switch |
| 0 → +0.375 [0 → +9] (up to +0.46 s for the longer instance) | zoom blur, scale, mirror fold, chroma split, brightness | full → none (scale 1.35 → 1.00) | strong ease-out (quartic) |

Demo assignment (tuned): short X1 at the person → B-roll cut and at B-roll → person at a place change; long X1 (8 f in, 11 f out) on the B-roll → speaker return; X2 on B-roll → B-roll cuts, including man → plant. Hits of M1 on the final shot: 9.15 s and 9.65 s (scale 1.07 each, blur 4 px at 720 W).

Short instance: warp-in 4 f + warp-out 9 f = 13 f (0.54 s) at 24 fps. Long instance: warp-in 8 f + warp-out 11 f = 19 f (0.79 s). Choose short by default and long when the shot change is a big scene jump.
**Footage / plate behaviour:** both shots play live; only the pixels are warped; no frame is held or repeated.
**Captions during it:** per C1: lane empty from Ts − 0.17 s; new chunk's first word starts at Ts + 0.04 s to Ts + 0.08 s.
**Exit:** the effect ends by itself (warp-out reaches 0).
**Build notes:** per frame, in float: (1) zoom blur = mean of 12 copies scaled 1.0 → 1+z about the centre (z = 0.35 × strength); (2) mirror: `out[y] = lerp(frame[y], frame[H-1-y], a)` for the bottom half (fold line at 0.5H), `a` = fold amount; (3) chroma split: roll the R plane by +dx and the B plane by −dx; (4) multiply by 1 + lift. Clamp crop boxes to the frame. Keep the audio stream copied, untouched.
**Flow prompt text:** "At the cut from {{SHOT_A}} to {{SHOT_B}}, the picture quickly zooms in and blurs, folds into a mirrored reflection with a colourful red and blue edge split and a brief brightening, switches to the next shot in that same distorted state, and then smoothly un-warps and sharpens into focus in about a third of a second. Everything shown is the original footage; nothing new is added."
**Still-image state:** none (omit in stills).

### MOMENT X2 · SWIRL BLUR PULL
**What it is:** a slow-building swirling blur between two non-person shots (B-roll → B-roll) that snaps sharp on the new shot.
**Use when:** B-roll → B-roll cuts and any cut between two objects or places. **Avoid when:** the shot before or after is the speaker's face in a close-up (use X1).
**Text:** none.
**Geometry / Graphics:** none drawn.
**Motion:**

| t relative to Ts (s) [f] | Property | From → To | Ease |
|---|---|---|---|
| −0.46 → 0 [−11 → 0] (outgoing shot) | rotational + zoom blur strength | 0 → 1.0 (sharpness falls to ≈ 30 % of normal) | ease-in (t²) |
| same | brightness lift | 0 → +13 % (peak at −0.17 s, then easing down) | ease-in |
| same | chroma split dx | 0 → 0.008W [9 px] | ease-in |
| 0 [swap] | shot | outgoing → incoming (on the footage's own cut) | hard switch, incoming lands at full sharpness within 2 f |
| 0 → +0.08 [0 → +2] | blur | 0.6 → 0 | linear |

**Footage / plate behaviour:** both shots live; only blur, small rotation (≤ 6°) and light chroma split on the outgoing shot.
**Captions during it:** the chunk that straddles the cut stays on screen through the blur (captions are not warped); switch chunks on the next word as usual.
**Exit:** none; ends sharp.
**Build notes:** rotational blur = mean of 10 copies rotated 0 → 6° and scaled 1.0 → 1.15 about the centre.
**Flow prompt text:** "At the cut from {{SHOT_A}} to {{SHOT_B}}, the first shot swirls and blurs more and more, brightening slightly with a faint colour fringe, then the next shot appears sharp at once."
**Still-image state:** none.

### MOMENT M1 · BEAT PUNCH
**What it is:** a quick small zoom-in step with a soft-focus pulse that sharpens, used to keep a long talking shot alive.
**Use when:** a long static shot (> 1.5 s) with no cut; a stressed word; a list item; a sentence start. **Avoid when:** within 0.5 s of an X1/X2 window; more than 4 hits in a row.
**Text:** none.
**Geometry / Graphics:** none drawn.
**Motion:**

| t relative to hit (s) [f] | Property | From → To | Ease |
|---|---|---|---|
| 0 | scale about the face anchor | ×1.00 → ×1.07 (a step, cumulative across hits) | instant |
| 0 → +0.25 [0 → +6] | blur radius | 6 px → 0 | ease-out |
| 0 → +0.13 [0 → +3] | brightness | +6 % → 0 | linear |

Spacing: 0.5 s apart when used as a run; choose hits on stressed words or sentence starts. Cumulative scale cap 1.30 for the whole video; after the cap, hits become blur-only pulses.
**Footage / plate behaviour:** live footage, scaled and softened only.
**Captions during it:** unaffected (captions do not scale).
**Exit:** blur decays by itself; the scale stays until the next scene change, where X1/X2 resets it to 1.00.
**Build notes:** resize with `Image.resize(..., box=floats)` for sub-pixel crops about the face anchor; clamp the crop box inside the frame.
**Flow prompt text:** "On the stressed words the picture gently steps in closer by a few percent with a brief soft focus that sharpens again within a quarter of a second, a few times at half-second spacing. The person and background stay exactly the same."
**Still-image state:** none.

### MOMENT M2 · SLOW DRIFT
**What it is:** a barely visible push-in on a long shot so it never looks frozen.
**Use when:** B-roll or a calm shot longer than 1.5 s with no other motion. **Avoid when:** the shot already has a punch or a warp; the footage itself moves a lot.
**Text:** none.
**Geometry / Graphics:** none.
**Motion:** scale ×1.00 → ×1.05 over the shot (linear), about the subject anchor. No blur.
**Footage / plate behaviour:** live footage, scaled only; counts towards the 1.30 cap, reset at the next X1/X2.
**Captions during it:** unaffected.
**Exit:** reset by the next transition.
**Build notes:** same crop routine as M1.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### MOMENT T2 · COUNTER TITLE
**What it is:** a numeral plus the user's own list word, stacked and snapped up with the T1 motion, to mark each item of a list.
**Use when:** the caption lists steps, tips or items ("first…", "second…", numbered points). **Avoid when:** fewer than 3 items; T1 is still on screen.
**Text:** numeral (1, 2, 3…) on line 1; 1–2 of the user's words for that item on line 2; UPPERCASE.
**Geometry / Graphics:** T1 look; line 1 numeral at 1.4× title size; widest line ≤ 0.50W (smaller than T1); block top edge 0.05H.
**Motion:** T1's snap (small state 0.50 scale, hold 6 f, strong ease-out to 1.00 over 8 f), no lightning, hold 1.0 s, 2 f fade out. Place it at the item's first word.
**Footage / plate behaviour:** untouched.
**Captions during it:** normal.
**Exit:** 2 f fade; ≥ 0.3 s clear of transitions.
**Build notes:** reuse the T1 renderer.
**Flow prompt text:** "As each point of the list starts, a small stacked title with the number {{NUMBER}} above the words {{ITEM_WORDS}} fades in near the top, grows to double size, holds for about a second and disappears."
**Still-image state:** final state.

### MOMENT E1 · END HOLD
**What it is:** the last caption chunk stays, the picture settles clean, and no new graphic appears.
**Use when:** every video ends this way unless the last line is a call to action that needs C2. **Avoid when:** the video ends on a transition.
**Text:** the last chunk's words.
**Geometry / Graphics:** C1 at the caption lane.
**Motion:** last chunk holds to min(last word end + 0.1 s, end − 0.25 s); the final 0.25 s [6 f] has an empty caption lane and untouched footage. Optional M2 drift across the last shot.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1.
**Flow prompt text:** "The last words stay in the lower third until just before the end, then disappear and the picture finishes clean."
**Still-image state:** final chunk.

---

## 8. RECOMMENDED COMBINATIONS (starting points, not templates)
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → B-roll → talking head | T1 + L1 + C1 | X1 at the first B-roll cut, X2 between B-roll shots, X1 on the return to the speaker, M1 run on the final speaker shot, C2 on one payoff word | E1 |
| Single talking head, no cuts | T1 + L1 + C1 | M1 run on stressed words (≥ 1.5 s between hits at first), one self-warp X1 at a sentence boundary, T2 if a list appears | E1 + C2 on the last strong word |
| B-roll only, no speech | T1 + L1 (title from the user's words, if any) + C1 | X2 on every B-roll cut, X1 only at a change of place, M2 on long shots | E1 |
| Still image + text | T1 final state (no motion), C1 chunk in the settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

## 9. OUTPUT
- One video, vertical 9:16, same duration, frame rate and resolution as the upload (at least 720 x 1280), original audio track unchanged.
- No watermark, no end card, no title card that is not part of the style.

## 10. NEGATIVE PROMPT (avoid all of these)
- Do not change, replace, recolour, retime or reorder the uploaded footage; do not alter anyone's face, body, outfit or voice.
- Do not add any word that is not in the script / transcript; no misspellings, no random gibberish text, no watermarks, no logos, no stock overlays.
- Never show the same words twice (one copy in an old style and one in the new style); never leave remnants, ghosts or blur patches of removed captions.
- Do not cover the speaker's face while they are speaking; do not let any text run outside the frame or sit on the very edge.
- No black bars, no letterboxing, no extra intro or outro, no end card, no added music or voice-over, no sound effects the style does not ask for.
- No glitches, flicker or warping outside what the style bible describes; no 3D lens flares, no cartoon filters, no beauty filters.

## 11. FINAL CHECK (verify before you finish)
- [ ] Old captions and old on-screen text are gone; nothing is ever shown twice.
- [ ] Every word matches the script or transcript, spelled correctly, and starts with the speech.
- [ ] The face is clear while speaking; no text is cut off or outside the margins.
- [ ] The look matches the style bible (colours, type, shapes, motion), and each moment appears the way its description says.
- [ ] Footage, order, timing and audio are unchanged; length matches the upload.
