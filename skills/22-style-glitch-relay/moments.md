# moments.md — Glitch Relay: Style Bible + Moment Library

This file is the single source of truth for the Glitch Relay style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, with exact specs measured on a 1080x1920, 24 fps reference reel (9.43 s). Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the speaker's own footage stays clean and live, while a glowing lavender word-by-word caption relay runs along the lower third, a stacked glowing title snaps in with a white lightning crack, and every shot change melts through a mirrored, chroma-split zoom-blur glitch.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 24 fps, so "f" values below are 24 fps frames; at another fps keep the seconds. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Caption white | #FFFFFF | Words already spoken in the current chunk (measured 254,254,254) |
| Caption lavender | #C5B5FD | The newest word in a chunk (measured 197,181,253) |
| Caption dim | #7F879B at 0–100 % alpha | The fade-in stage of a new word (design decision: grey-blue ghost seen on the reference for ~3 f) |
| Title lavender | #E3D1FA | Stacked title fill (measured 227,209,250) |
| Glow violet | #B79CFF | Soft outer glow on title and on lavender words (design decision from reference glow) |
| Glow white | #FFFFFF | Soft outer glow on white words |
| Caption shadow | #000000 at 50 % | Small drop shadow under all caption words |
| Bolt white | #FFFFFF with #DCCBFF glow | Lightning cracks |
| Fringe red / blue | channel shift only | Chroma split in transitions (no flat colour is drawn) |

Brand-swap rule: if the user gives a brand colour, replace Caption lavender, Title lavender and Glow violet with tints of it (same lightness); keep white and black as is. Never add other colours. The footage's own colours are never touched.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, no cards, no borders, no masks, no rounded corners. |
| Crop | Cover-fit only when the source is not 9:16. Crop anchor ✎ = the speaker's face box (or the main subject on B-roll). |
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

## PART 2 — MOMENT LIBRARY

Family codes: **T** title · **L** light effect · **C** caption · **X** transition · **M** footage motion · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### T1 · STACK TITLE SNAP — T ●●● (signature opener)
**What it is:** a two-line stacked title appears small near the top, waits briefly, then snaps up to double size with a white lightning crack, glows, holds, and cuts out.
**Use when:** the opening line states the topic; the video starts on a speaker or calm shot; the first sentence has 2–3 topic words. **Avoid when:** the first 0.4 s already contains a hard cut or a face in the title block that cannot be moved (use Alt).
**Text (✎):** 2–3 words from the user's own words (or a title the user supplied), UPPERCASE, split into two lines (1–2 words per line), widest line ≤ 12 characters at final size (shrink the size so the widest line is ≤ 0.66W).
**Geometry / Graphics:** Title lavender fill with Glow violet outer glow (18 px radius, 55 % alpha). Final state in the Title block; small state in the small-state block (scale 0.50 of final, same centre x = 0.50W, top edge 0.085H).
**Motion (measured on the reference, 24 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.33–0.42 [8–10] ✎ | title | alpha | 0 → 1 (small state) | linear, 2 f |
| 0.42–0.67 [10–16] | title | scale | 0.50 → 0.52 (slow creep) | linear |
| 0.67–0.96 [16–23] (tuned when the first cut is < 2 s away: 0.45–0.74 [11–18]) | title | scale | 0.52 → 1.00 (width 0.344W → 0.658W); top edge 0.085H → 0.053H | strong ease-out (quartic) |
| 0.67–1.08 [16–26] | title | glow alpha | 55 % → 100 % at 1.0 s → 55 % | triangle |
| 0.96–2.50 [23–60] ✎ | title | hold | final state, no motion | — |
| 2.50–2.58 [60–62] ✎ | title | alpha | 1 → 0 | linear, 2 f |

Tuned for a first cut at 1.83 s: fade-in 0.30 s, snap 0.45–0.74 s, hold to 1.28 s, fade-out 1.28–1.36 s (X1 window starts 1.67 s); bolts 0.45–0.87 s. The 1.2 s minimum after the snap yields when a cut is closer than 2.6 s.

Start time ✎: 0.33 s after the first word (≈ 0.3–0.5 s into the video). Hold ✎: until 0.3–0.4 s before the first big transition, never longer than 2.6 s total on screen; minimum 1.2 s on screen after the snap.
**Footage / plate behaviour:** footage untouched.
**Captions during it:** captions run normally in the caption lane; the title never shares a region with them.
**Exit:** 2 f linear fade, at least 0.3 s before any X1/X2 window starts.
**Build notes:** render the title once at final size with Pillow at 2× (supersampled) with glow baked into an RGBA layer; scale that layer per frame with `Image.resize` (LANCZOS) around the top-centre anchor.
**Flow prompt text:** "Early in the video, a short two-line title in all capital letters, reading {{TITLE_LINE_1}} over {{TITLE_LINE_2}}, fades in small near the top of the frame in soft lavender with a gentle violet glow. After a moment it smoothly grows to about double size while a white lightning crack flashes across the edges of the picture, then it holds for about a second and a half and disappears. It never covers the speaker's face."
**Still-image state:** final state (size 1.00, glow 55 %).

### L1 · LIGHTNING CRACK — L ●●● (signature, always with T1)
**What it is:** two or three jagged white cracks flicker across the picture while the title snaps up.
**Use when:** with T1; optionally once more at a payoff word (max 2 per video). **Avoid when:** the face box fills > 60 % of W and no side margin is free (shorten to the top and bottom edges only).
**Text (✎):** none.
**Geometry / Graphics:** 2–3 polylines, each 8–14 random-walk points, running from one frame edge to another. Width tapers 17 px → 5 px [at 1080 W; tuned up from 10 → 3, which read too thin at 720 W]. White core with a 14 px #DCCBFF glow (blur sigma 0.8 x radius, gain 3.0). Bolts run edge to edge below or beside the face box (e.g. left edge y 0.56H to right edge y 0.47H; left edge y 0.30H to bottom x 0.22W; right edge y 0.12H to bottom x 0.82W). All points stay ≥ 0.04W away from the face box.
**Motion (measured on the reference, 24 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.67–0.75 [16–18] ✎ | bolts | alpha | thin cracks 40 % → full | step |
| 0.75–1.04 [18–25] | bolts | per-frame | redraw with new jitter (≤ 0.02W) every frame; peak at 0.75 s [18] and 1.0 s [24] | flicker |
| 1.04–1.08 [25–26] | bolts | alpha | 100 % → 0 | 1–2 f |

Total 0.42 s (10–11 f). The bolt seed is fixed per video so a re-render is identical.
**Footage / plate behaviour:** footage untouched under the bolts; add +6 % brightness during the two peaks (optional).
**Captions during it:** unchanged.
**Exit:** hard cut after the last flicker frame.
**Build notes:** draw at 2× on an RGBA layer, blur a copy for the glow, composite with screen blending; avoid the face box by rejecting points inside it (inflate by 0.04W).
**Flow prompt text:** "As the title grows, a few thin jagged white lightning cracks flicker quickly across the edges of the picture for under half a second, never crossing the speaker's face, then vanish."
**Still-image state:** none (omit in stills).

### C1 · RELAY CAPTION — C ●● (signature, the caption system)
**What it is:** one line of one or two words at a time. The newest word fades in as a dim ghost and settles into lavender while the word before it turns white. When the chunk ends it disappears in one frame and the next chunk starts a moment later.
**Use when:** always, for every spoken or written line. **Avoid when:** never.
**Text (✎):** the user's exact words, UPPERCASE, punctuation kept. Chunk rules: 1–2 words; ≤ 16 characters per chunk, spaces included (a single longer word stands alone and is scaled to fit 0.82W); split at punctuation; never end a chunk on an article, preposition or conjunction ("a", "the", "of", "and", "to"); prefer chunk changes at footage cuts.
**Geometry / Graphics:** Caption lane, centred on x = 0.50W, one line, cap height 0.046H. The chunk's total width ≤ 0.82W (scale down the whole chunk if wider). Two-word chunks use a word gap of 0.30 em.
**Motion (measured on the reference, 24 fps):**

| t (s) [f] | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha | 0 → 1 | ease-out, 3 f (0.125 s) |
| word start ✎ | new word | colour | Caption dim → Caption lavender | same 3 f |
| word start ✎ | previous word | colour | lavender → white | instant (1 f) |
| chunk end ✎ | all words | alpha | 1 → 0 | hard cut (1 f) |
| chunk end → next start | gap | empty lane | 2–4 f (0.08–0.17 s) | — |

Position stays fixed during a chunk: the first word is already placed where the full chunk will be centred (no sliding). Chunk length 0.4–1.0 s typical; a chunk start = its first word's start time; chunk end = min(last word end + 0.1 s, next chunk start − 0.08 s); minimum 0.4 s.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption system. During an X1 window the lane is empty from the swap − 0.17 s until the next chunk starts (at or just after the swap).
**Exit:** hard cut per the table.
**Build notes:** render each word separately at final size so colours can change; compose the chunk with Pillow at 2×, measure width with `font.getlength`, build the glow with a Gaussian blur of the alpha mask; cache every (chunk, state) layer; fade only by multiplying alpha.
**Flow prompt text:** "Large all-capital captions in the lower third of the frame show one or two words at a time. Each new word fades in softly in pale lavender with a gentle glow while the previous word turns white. When the line ends the words vanish at once and the next words appear a moment later. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one chunk, last word lavender, the other white.

### C2 · GIANT EMPHASIS WORD — C ●●● (extension in the same grammar; seen once on the reference)
**What it is:** a single payoff word as its own chunk at 1.6× size.
**Use when:** a strong adjective, number or turn word ("but", "never", a price) opens a sentence or sits alone. **Avoid when:** the word is longer than 9 characters (it would exceed 0.82W); max 2 per video, ≥ 3 s apart.
**Text (✎):** one user word, UPPERCASE, punctuation kept.
**Geometry / Graphics:** C1 look at 1.6× size, bottom edge on the caption baseline, centred x = 0.50W, lavender once settled.
**Motion:** C1 timings (3 f fade-in from dim to lavender); hold 0.25–0.5 s; hard cut out.
**Footage / plate behaviour:** optionally pair with M1 on the same frame.
**Captions during it:** replaces the normal chunk for its duration.
**Exit:** hard cut, then 2–4 f gap, then the next chunk.
**Build notes:** same renderer as C1; scale the font size, not the bitmap.
**Flow prompt text:** "One powerful word, {{WORD}}, appears alone in the lower third at one and a half times the usual caption size, fading in softly from pale grey to lavender, then disappears at once."
**Still-image state:** the word in lavender.

### X1 · MIRROR GLITCH WARP — X ●●● (signature transition)
**What it is:** the cut between two shots (or inside one shot) melts through a mirror-folded, zoom-blurred, chroma-split glitch and lands in a soft-focus pull to sharp.
**Use when:** person → B-roll, B-roll → person, any cut where the picture content changes completely. Self-warp (same shot, swap in place) allowed at a sentence boundary on a long static shot, max 2 per video. **Avoid when:** a cut falls within 0.9 s of the previous X1/X2 (use M1 instead).
**Text (✎):** none.
**Geometry / Graphics:** none drawn; the effect is a transform of the live frame (see build notes). Swap time Ts ✎ = the footage's own cut time (the swap frame never moves a cut).
**Motion (measured on the reference, 24 fps; two instances measured, short and long, see below the table):**

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

Short instance (measured): warp-in 4 f + warp-out 9 f = 13 f (0.54 s) at 24 fps. Long instance (measured): warp-in 8 f + warp-out 11 f = 19 f (0.79 s). Choose short by default and long when the shot change is a big scene jump.
**Footage / plate behaviour:** both shots play live; only the pixels are warped; no frame is held or repeated.
**Captions during it:** per C1: lane empty from Ts − 0.17 s; new chunk's first word starts at Ts + 0.04 s to Ts + 0.08 s.
**Exit:** the effect ends by itself (warp-out reaches 0).
**Build notes:** per frame, in float: (1) zoom blur = mean of 12 copies scaled 1.0 → 1+z about the centre (z = 0.35 × strength); (2) mirror: `out[y] = lerp(frame[y], frame[H-1-y], a)` for the bottom half (fold line at 0.5H), `a` = fold amount; (3) chroma split: roll the R plane by +dx and the B plane by −dx; (4) multiply by 1 + lift. Clamp crop boxes to the frame. Keep the audio stream copied, untouched.
**Flow prompt text:** "At the cut from {{SHOT_A}} to {{SHOT_B}}, the picture quickly zooms in and blurs, folds into a mirrored reflection with a colourful red and blue edge split and a brief brightening, switches to the next shot in that same distorted state, and then smoothly un-warps and sharpens into focus in about a third of a second. Everything shown is the original footage; nothing new is added."
**Still-image state:** none (omit in stills).

### X2 · SWIRL BLUR PULL — X ●●● (extension of the measured grammar; measured once)
**What it is:** a slow-building swirling blur between two non-person shots (B-roll → B-roll) that snaps sharp on the new shot.
**Use when:** B-roll → B-roll cuts and any cut between two objects or places. **Avoid when:** the shot before or after is the speaker's face in a close-up (use X1).
**Text (✎):** none.
**Geometry / Graphics:** none drawn.
**Motion (measured on the reference, 24 fps):**

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

### M1 · BEAT PUNCH — M ●● (measured: four hits at 0.5 s spacing on the reference)
**What it is:** a quick small zoom-in step with a soft-focus pulse that sharpens, used to keep a long talking shot alive.
**Use when:** a long static shot (> 1.5 s) with no cut; a stressed word; a list item; a sentence start. **Avoid when:** within 0.5 s of an X1/X2 window; more than 4 hits in a row.
**Text (✎):** none.
**Geometry / Graphics:** none drawn.
**Motion (measured on the reference, 24 fps; hits at 7.12, 7.62, 8.12 and 8.62 s):**

| t relative to hit (s) [f] | Property | From → To | Ease |
|---|---|---|---|
| 0 | scale about the face anchor ✎ | ×1.00 → ×1.07 (a step, cumulative across hits) | instant |
| 0 → +0.25 [0 → +6] | blur radius | 6 px → 0 | ease-out |
| 0 → +0.13 [0 → +3] | brightness | +6 % → 0 | linear |

Spacing ✎: 0.5 s apart when used as a run; choose hits on stressed words or sentence starts. Cumulative scale cap 1.30 for the whole video; after the cap, hits become blur-only pulses.
**Footage / plate behaviour:** live footage, scaled and softened only.
**Captions during it:** unaffected (captions do not scale).
**Exit:** blur decays by itself; the scale stays until the next scene change, where X1/X2 resets it to 1.00.
**Build notes:** resize with `Image.resize(..., box=floats)` for sub-pixel crops about the face anchor; clamp the crop box inside the frame.
**Flow prompt text:** "On the stressed words the picture gently steps in closer by a few percent with a brief soft focus that sharpens again within a quarter of a second, a few times at half-second spacing. The person and background stay exactly the same."
**Still-image state:** none.

### M2 · SLOW DRIFT — M ● (extension in the same grammar)
**What it is:** a barely visible push-in on a long shot so it never looks frozen.
**Use when:** B-roll or a calm shot longer than 1.5 s with no other motion. **Avoid when:** the shot already has a punch or a warp; the footage itself moves a lot.
**Text (✎):** none.
**Geometry / Graphics:** none.
**Motion:** scale ×1.00 → ×1.05 over the shot (linear), about the subject anchor ✎. No blur.
**Footage / plate behaviour:** live footage, scaled only; counts towards the 1.30 cap, reset at the next X1/X2.
**Captions during it:** unaffected.
**Exit:** reset by the next transition.
**Build notes:** same crop routine as M1.
**Flow prompt text:** "The shot slowly pushes in by a few percent over its length while everything in it moves exactly as before."
**Still-image state:** none.

### T2 · COUNTER TITLE — T ●●● (extension in the same grammar)
**What it is:** a numeral plus the user's own list word, stacked and snapped up with the T1 motion, to mark each item of a list.
**Use when:** the caption lists steps, tips or items ("first…", "second…", numbered points). **Avoid when:** fewer than 3 items; T1 is still on screen.
**Text (✎):** numeral (1, 2, 3…) on line 1; 1–2 of the user's words for that item on line 2; UPPERCASE.
**Geometry / Graphics:** T1 look; line 1 numeral at 1.4× title size; widest line ≤ 0.50W (smaller than T1); block top edge 0.05H.
**Motion:** T1's snap (small state 0.50 scale, hold 6 f, strong ease-out to 1.00 over 8 f), no lightning, hold 1.0 s, 2 f fade out. Place it at the item's first word.
**Footage / plate behaviour:** untouched.
**Captions during it:** normal.
**Exit:** 2 f fade; ≥ 0.3 s clear of transitions.
**Build notes:** reuse the T1 renderer.
**Flow prompt text:** "As each point of the list starts, a small stacked title with the number {{NUMBER}} above the words {{ITEM_WORDS}} fades in near the top, grows to double size, holds for about a second and disappears."
**Still-image state:** final state.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the last caption chunk stays, the picture settles clean, and no new graphic appears.
**Use when:** every video ends this way unless the last line is a call to action that needs C2. **Avoid when:** the video ends on a transition.
**Text (✎):** the last chunk's words.
**Geometry / Graphics:** C1 at the caption lane.
**Motion:** last chunk holds to min(last word end + 0.1 s, end − 0.25 s); the final 0.25 s [6 f] has an empty caption lane and untouched footage. Optional M2 drift across the last shot.
**Footage / plate behaviour:** untouched.
**Captions during it:** per above.
**Exit:** video ends.
**Build notes:** none beyond C1.
**Flow prompt text:** "The last words stay in the lower third until just before the end, then disappear and the picture finishes clean."
**Still-image state:** final chunk.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → B-roll → talking head | T1 + L1 + C1 | X1 at the first B-roll cut, X2 between B-roll shots, X1 on the return to the speaker, M1 run on the final speaker shot, C2 on one payoff word | E1 |
| Single talking head, no cuts | T1 + L1 + C1 | M1 run on stressed words (≥ 1.5 s between hits at first), one self-warp X1 at a sentence boundary, T2 if a list appears | E1 + C2 on the last strong word |
| B-roll only, no speech | T1 + L1 (title from the user's words, if any) + C1 | X2 on every B-roll cut, X1 only at a change of place, M2 on long shots | E1 |
| Still image + text | T1 final state (no motion), C1 chunk in the settled state | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
