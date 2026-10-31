# moments.md — Y2K Chrome: Style Bible + Moment Library

This file is the single source of truth for the Y2K Chrome style. Part 1 is the style bible (palette, geometry, type, motion, footage rules, safe zones). Part 2 is the moment library. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments. Palette and lettering come from one reference still (an icy-blue Y2K poster with liquid-chrome lettering); every motion, timing and window value is a design decision, proven on a 720x1280, 24 fps, 10 s render and labelled "(design, not measured)".

**The look in one line:** an icy-blue early-2000s web world: liquid-chrome bubble lettering, four-point sparkles, holographic pill captions, and B-roll shown inside glossy retro OS pop-up windows, while speaker shots stay full-frame inside a paper-white poster border.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (24 fps in the demo; keep seconds at other rates). Pixel values are for 720×1280; scale by W/720 for other sizes.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Ice sky | #7491BF → #93B5E6 → #80B5DD → #B9CCD8 (top to bottom) | Page behind window shots (measured from the reference background) |
| Paper white | #EBE1DF | Poster border around speaker shots, inset photo (measured from the reference margin) |
| Chrome ramp | #FFFFFF, #BAD2F6, #5676C4 (horizon), #E2EEFF, #B0B8F4, #DECEFC | Fill of chrome lettering, top to bottom |
| Chrome edge | #3E4CA0 | Dark outline of chrome lettering |
| Tie violet | #6B5AA7 (measured on the reference tie) | Window outlines, keyword colour base |
| Keyword violet | #5B3FC8 | Emphasis word inside a pill |
| Ink navy | #1E2A55 | Caption text, window labels |
| Holo pill | #FFC3EC, #C4B5FF, #A5EBFF, #C9FFE6 | Scrolling pill gradient (pink, lilac, cyan, mint) |
| Window body | #F4F7FF → #B0BCEE | Window frame; inactive window #F0F1F7 → #C4C8DA |
| Sparkle tints | white, #96E1FF, #C8AAFF, #FFAAE1 | Four-point stars |

Brand-swap rule: a brand colour replaces Keyword violet and the lilac stop of the holo pill; keep the icy page, white and chrome. No warm colours, no black.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Poster frame (speaker shots) | Paper-white border 22 px on every side, inner corner radius 36 px, light paper grain. Footage fills the rest, never scaled. |
| Window card (B-roll shots) | Outer 608×790 px at x centre 0.50W, y centre 0.41H [520]; radius 34; 7 px white edge + 3 px #6B5AA7 line; title bar 50 px (chrome gradient white → #C4D6F8 → #8CA4E4 → #DEE8FF), body border 16 px, 6 px gap below bar. Inner footage 576×718 cover-fit, crop anchor ✎ (0 = top). Soft shadow #242C78 at 42 %, blur 16, offset +12 y. |
| Window buttons | Three glossy discs r 12 at the bar's right: cyan (minimise bar), lilac (square), pink (cross). Glyphs only, no text. |
| Window label | Optional, in the bar after a small lilac star: one of the user's own words from that shot, as written, no trailing punctuation. Poppins SemiBold 22. |
| Back window (cascade) | Same chassis, inactive grey-lilac bar, offset (−44, −48) px behind the main window, shows the still of the previous shot. |
| Holo pill | Height 92, fully rounded, width = text + 76; 3.5 px white outline plus faint inner line; top-half gloss (white 40 %); lilac shadow 35 %. Gradient scrolls right at 150 px/s. |
| Dialog box | 560×176 window chassis (bar 46), body gradient #FAFCFF → #DCE6FC, star glyph left, one phrase centred. No buttons with words. |
| Inset photo | 170×214, white border 8, #6B5AA7 hairline, shadow. |
| Loading bar | x 100–620, h 46 at y 0.76H [972]; white capsule, 14 blocks cycling pink, lilac, cyan, mint, each glossy. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Title lane | 0.05, 0.02, 0.95, 0.12 [centre y 100] | T1 chrome title (above the face box) |
| Window lane | 0.08, 0.10, 0.92, 0.72 | W1, W2 main window |
| Keyword lane | centre y 0.73H [940] (window shots), 0.69H [880] (speaker shots) | K1, E1 |
| Caption lane | centre y 0.85H [1090], height 92 | C1 pill, C2 dialog |
| Inset slot | x 36–206, y 800–1014 | W3 |
| Loader slot | centre y 0.76H [972] | L1 |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Chrome title and keyword | Wide black bubble letters with a liquid wave (±0.045 em), chrome fill, dark blue outline, white glow, mixed case as written | Archivo Black wide (wght 900, wdth 118) | Poppins Black, Outfit Black | Title 104 px (two words, total ≤ 680 px wide); keyword 150 px (≤ 640 px wide) |
| Pill words | Rounded geometric semibold, ink navy | Poppins SemiBold | Outfit SemiBold, Manrope Bold | 42 px; shrink in 2 px steps until the pill ≤ 640 px wide, min 30 |
| Pill keyword | Same size, extra bold, keyword violet | Poppins ExtraBold | Poppins Bold | = pill size |
| Dialog text | Poppins SemiBold, navy, centred | Poppins SemiBold | Outfit SemiBold | 56 px, shrink to fit |
| Window label | Poppins SemiBold, navy | Poppins SemiBold | Outfit | 22 px |

### 1.5 Motion language (design, not measured)

- Everything that appears pops with a slight overshoot (ease-out-back, 1.5–1.9) over 0.25–0.4 s. Pops are small (0.78–0.94 → 1.0), never from zero.
- Chrome lettering gets a diagonal white shine sweep 0.4 s after it lands (0.6–0.7 s long, once).
- Sparkles twinkle: scale = sin(pi·u)^0.75 over 0.55–0.85 s, never rotate, never linger.
- Idle motion is sub-pixel float: windows ±4 px at 2.2 rad/s, pills ±2 px, keywords ±3 px.
- The page drifts: soft diagonal light streaks 14 px/s and slow bubbles.
- Exits are 0.15–0.25 s shrink-and-fade (0.85 scale), except at footage cuts, which switch hard.
- Never: shake, glitch, blur, spin, slides across the frame, typing letter by letter, colour grading.

### 1.6 What may happen to the user's footage

| Allowed | Limit |
|---|---|
| Speaker shot full frame inside the paper poster border | Border covers ≤ 22 px per edge |
| Any shot inside a window card (cover-fit crop, anchor ✎) | Crop must keep the main subject; the primary window plays live, in sync with the audio |
| Still of the previous shot in the back window; still of the speaker in the inset | Stills only, taken from the user's own footage |
| Star Cut flare over a cut | ≤ 0.35 s, white at ≤ 95 % fading to 0; only on cuts between non-speaker shots, or if a face shows, ≤ 0.15 s |
| Sparkles, chrome type, pills, dialogs on top | Outside the face box; never over a speaking mouth |

Forbidden: grading, recolouring, speed changes, trimming, reordering, replacing the footage, blur of any shot, cut-outs.

### 1.7 Safe zones

- Face box (speaking): never covered; keep x 0.30–0.70, y 0.13–0.42 clear of type, pills and sparkles (the renderer rejects stars inside it on speaker shots).
- T1 title bottom edge ≤ 0.145H [185]. On a face higher than 0.15H, shrink the title to 84 px or drop it to E1 only.
- Caption lane y 0.81–0.89H. If a face sits there, move the lane to y 0.07H and keep T1 off.
- Window shots: anchor the crop on the face or subject; a non-speaking face may sit in a window but stays whole.

---

## PART 2 — MOMENT LIBRARY

Families: T title · K keyword · C caption · W window · L loader · X transition · S sparkle · B backdrop · E end. Energy: low · mid · high.

### T1 · CHROME TITLE — T high (signature, design not measured)
**What it is:** the opening phrase as two liquid-chrome bubble words that drop in one after the other at the top of a poster-framed speaker shot.
**Use when:** the video starts on a speaker or any shot with free space above the subject. **Avoid when:** the top 15 % holds a face or key text.
**Text (✎):** the first 1–3 words of the user's text (the topic words), as written, moved out of the captions.
**Geometry / Graphics:** chrome lettering 104 px, gap 26 px, centred x 0.50W, y centre 100 [0.078H]; scale down to fit 680 px.
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start (first word) | word 1 | y offset, alpha | −60 px → 0, 0 → 1 over 0.4 s | back 1.6 |
| +0.22 s | word 2 | same | same | back 1.6 |
| +0.45 s | each word | shine sweep | left → right over 0.6 s | linear |
| end − 0.0 s | both | y, alpha | 0 → −30 px, 1 → 0 over 0.25 s | out |
**Footage:** full frame inside B1.
**Captions during it:** C1 pills from the next word on.
**Exit:** rise and fade 0.25 s, ending before the first cut.
**Build notes:** render each word once (chrome_text), cache, paste with alpha; S1 burst at +0.2 s around the title.
**Flow prompt text:** "At the top of the frame the words {{TITLE}} appear in shiny icy-blue chrome bubble letters with a wavy liquid shape and a dark blue edge, dropping in one word at a time, with a light shine sweeping across."
**Still-image state:** both words settled, shine off.

### K1 · CHROME KEYWORD — K high (signature, design not measured)
**What it is:** one key word in giant chrome lettering that pops over the lower part of a window or speaker shot.
**Use when:** a theme word, a list step, a number or the payoff word. **Avoid when:** it would sit on a face or the same word is already a title.
**Text (✎):** one user word (with its punctuation if the user wrote it), moved out of the caption.
**Geometry / Graphics:** chrome 150 px, width ≤ 640, centre x 0.50W, y centre 940 over a window (overlapping its bottom edge) or 880 over a speaker shot.
**Motion:** pop 0.55 → 1.0 (back 1.8, 0.4 s) with alpha in 0.1 s; shine sweep at +0.4 s (0.7 s); float ±3 px; exit 0.25 s fade with scale 1.06.
**Footage:** unchanged. **Captions during it:** C1 pill below at the caption lane.
**Exit:** fade 0.25 s, or hold to the end of the video (E1).
**Build notes:** start 0.04 s after a cut when the word falls on a cut; pair with S1.
**Flow prompt text:** "The word {{KEYWORD}} pops in large over the lower part of the picture in shiny chrome bubble letters, with a quick shine sweep and small sparkles."
**Still-image state:** word settled.

### C1 · HOLO PILL CAPTION — C mid (signature, design not measured)
**What it is:** a glossy holographic pill (pink, lilac, cyan, mint) whose gradient scrolls slowly; words fill it one by one and one word is violet and extra bold.
**Use when:** every spoken line that is not a K1 or C2 phrase. **Avoid when:** a face sits in the caption lane (shift the lane).
**Text (✎):** 2–5 words, ≤ 26 characters, one line, as written; keyword ≤ 1 per pill, ≤ 4 per video.
**Geometry:** pill height 92, centre x 0.50W, y 1090; width = text + 76 (max 640 + 76 clamp via font shrink).
**Motion:** pill pops 0.78 → 1.0 (back 1.9, 0.25 s) with alpha 0.08 s at the first word's start; each word fades in over 0.12 s at its own start time; gradient scrolls 150 px/s; exit 0.15 s shrink to 0.85 and fade.
**Chunk rules:** start = first word start; end = min(last word start + 0.55, next start − 0.05); min 0.7 s; split at punctuation; never end on an article, preposition or "and".
**Footage:** unchanged. **Exit:** hard replace by the next pill is allowed on a cut.
**Build notes:** compose pill at 2x then downscale; cache nothing per frame except fonts.
**Flow prompt text:** "A glossy rounded pill with a soft pink, lilac, cyan and mint shine slowly shifting sits in the lower part of the frame and shows the words {{CAPTION}} appearing one by one in dark navy rounded letters, with {{KEYWORD}} in bold violet."
**Still-image state:** all words visible.

### C2 · DIALOG CAPTION — C mid (design, not measured)
**What it is:** a small retro pop-up dialog with a chrome title bar that carries one short phrase instead of a pill.
**Use when:** a turn, a list item or a short punchy phrase (2–3 words). **Avoid when:** twice in a row.
**Text (✎):** 2–3 user words, ≤ 18 characters, as written.
**Geometry:** 560×176 chassis, centre x 0.50W, y centre 1085; star glyph at left; text navy 56 px centred in the remaining width.
**Motion:** pop 0.8 → 1.0 (back 1.9, 0.28 s); exit 0.15 s shrink and fade.
**Footage:** unchanged. **Build notes:** reuse the window chassis with bar 46, border 14.
**Flow prompt text:** "A small old-computer pop-up box with a shiny blue-lilac title bar and three round buttons appears in the lower part of the frame with the words {{PHRASE}} inside it."
**Still-image state:** box settled.

### W1 · POP-UP WINDOW CARD — W high (signature, design not measured)
**What it is:** a B-roll shot shown inside a glossy retro OS window floating on the icy page, with a soft shadow and a slow float.
**Use when:** any non-speaker shot, or a speaker shot that needs a change of scene. **Avoid when:** the shot is already a tight face close-up that cannot spare its crop.
**Text (✎):** optional window label (one user word from that shot).
**Geometry:** see 1.2 Window card; crop anchor ✎ (0 = top).
**Motion:**
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut | window | scale | 0.94 (hard switch with the cut) | none |
| cut + 3 f | window | scale | 0.94 → 1.0 over 10 f | back 1.5 |
| always | window | y | ±4 px at 2.2 rad/s | sine |
**Footage:** live, in sync. **Captions during it:** C1/C2 at the caption lane.
**Exit:** hard cut with the footage cut.
**Build notes:** chassis built once at 2x with a transparent hole; paste footage under it; shadow layer behind; scale the whole window image per frame.
**Flow prompt text:** "The shot plays inside a shiny pale-blue and lilac old-computer window with a glossy title bar and three round buttons, floating on a soft icy-blue sky background with a gentle shadow."
**Still-image state:** window at scale 1.

### W2 · CASCADE WINDOWS — W high (design, not measured)
**What it is:** W1 with a greyed second window behind it holding a still of the previous shot, so steps stack like open programs.
**Use when:** a list or process where each shot follows the last (step 2 after step 1). **Avoid when:** the previous shot was the speaker (use W3 instead).
**Geometry:** back window offset (−44, −48), inactive bar, previous shot's last frame cropped at anchor 0.5; main window shifted +4 x, +8 y.
**Motion:** as W1; back window floats ±3 px.
**Footage:** previous-shot still only. **Exit:** hard cut.
**Flow prompt text:** "Behind the playing window sits a second, greyed-out window frozen on the previous shot, slightly up and to the left, like stacked computer windows."
**Still-image state:** both windows visible.

### W3 · INSET PHOTO — W mid (extension from the reference's corner inset, design not measured)
**What it is:** a small white-bordered still photo of the speaker pinned over the window's lower-left corner, as in the reference poster.
**Use when:** the first window shot after a speaker shot, to keep the speaker present. **Avoid when:** it would hide the window's subject.
**Geometry:** 170×214 incl. border at x 36–206, y 800–1014 final position.
**Motion:** rises from +260 px below, 0.4 s ease-out, starting 0.25 s after the cut; alpha in 0.1 s.
**Footage:** still of the last speaker frame (crop anchor 0.22). **Exit:** hard cut.
**Flow prompt text:** "A small white-bordered snapshot of the speaker slides up and rests over the lower-left corner of the window."
**Still-image state:** snapshot in place.

### L1 · LOADING BAR — L mid (design, not measured)
**What it is:** a chrome-and-pastel segmented loading bar under the window that fills with the shot, no words.
**Use when:** a time span ("one year", "in 30 days"), progress, a wait or a build-up. **Avoid when:** nothing in the story is about time or progress.
**Geometry:** see 1.2 Loading bar.
**Motion:** fade in 0.15 s; blocks fill in steps linearly from the shot's start + 0.12 s to its end − 0.07 s.
**Footage:** unchanged. **Exit:** hard cut.
**Flow prompt text:** "Under the window a shiny segmented loading bar fills block by block in pink, lilac, cyan and mint."
**Still-image state:** bar half full.

### X1 · STAR CUT — X high (signature, design not measured)
**What it is:** a white four-point star flares open from the centre of the window as the shot changes.
**Use when:** a cut between two non-speaker shots. **Avoid when:** a speaking face is under the star (then ≤ 0.15 s or skip).
**Geometry:** star size 460 → 1160 px, centred on the window centre (x 0.50W, y 0.41H [520]).
**Motion:** over 8 f from the cut: size grows with ease-out, alpha 0.95 → 0 (power 1.2).
**Footage:** the new shot is already playing beneath. **Build notes:** star sprite = astroid polygon with glow, built once at 256 px.
**Flow prompt text:** "As the shot changes, a big soft white four-point star flares open in the middle of the window and fades away."
**Still-image state:** none.

### S1 · SPARKLE BURST — S mid (signature, design not measured)
**What it is:** 5–9 four-point stars fly out of a point and twinkle for about 0.7 s.
**Use when:** a title or keyword lands, a window pops in, a cut, the payoff. **Avoid when:** they would cross a speaking face (reject any star inside the face box).
**Geometry:** star size 40–60 px, spread 70–330 px, tints white, cyan, lilac.
**Motion:** each star waits 0–0.18 s, lives 0.56–0.84 s, scale sin(pi·u)^0.75, drifts out with ease-out.
**Build notes:** seeded random per burst; reuse sprite.
**Flow prompt text:** "A handful of small shiny four-point sparkles pop out around {{WHERE}} and twinkle for a moment."
**Still-image state:** a few stars frozen near the lettering.

### B1 · POSTER FRAME — B mid (design from the reference margin)
**What it is:** the speaker shot full frame inside a paper-white poster border with rounded inner corners, and four tiny twinkles on the corners.
**Use when:** speaker shots and any shot that stays full frame. **Avoid when:** the footage has important content at its edges.
**Geometry:** see 1.2 Poster frame. **Motion:** present from frame 0; corner twinkles size 40, period 1.9 s.
**Flow prompt text:** "The picture sits inside a thin off-white paper border with softly rounded inner corners, like a printed poster."
**Still-image state:** border plus footage.

### B2 · ICY PAGE — B low (design, palette measured)
**What it is:** the sky-blue page behind windows: vertical gradient, drifting pale light streaks, soft bubbles and a little grain, with 6–7 ambient twinkle stars.
**Use when:** any window shot. **Motion:** streaks 14 px/s diagonal; ambient stars size 52, period 1.7 s, phases staggered.
**Flow prompt text:** "Behind the window is a soft icy-blue sky with slow pale streaks of light, floating bubbles and tiny twinkling stars."
**Still-image state:** page only.

### E1 · CHROME CLOSER — E high (signature, design not measured)
**What it is:** K1 on the last word(s) held to the end with a larger S1 burst, over a speaker shot in B1.
**Use when:** the last line or a CTA. **Avoid when:** the video ends on B-roll with no space (use K1 and C1).
**Text (✎):** the last 1–2 user words. **Geometry:** K1 at y 880; burst 9 stars, spread 330, size 60, life 0.8 s at the word's start + 0.03 s.
**Motion:** as K1, no exit. **Flow prompt text:** "On the last line the closing words {{WORDS}} pop up in big shiny chrome letters with a burst of sparkles and stay until the end."
**Still-image state:** word settled with stars.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | B1 + T1 + S1, C1 | W1 + W3 on the first B-roll, then W2 / L1 / X1 / C2 on later shots | B1 + C1 + E1 |
| Single talking head | B1 + T1 | K1 on 2–3 hook words, C1, S1 bursts, one C2 | E1 |
| B-roll only | W1 + K1 on the topic word | W2 chain with X1 on every cut, L1 on a time phrase, C2 | W1 + K1 held to the end |
| Still image | B1 + T1 | K1 | E1 |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
