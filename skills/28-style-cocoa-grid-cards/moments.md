# moments.md — Cocoa Grid Cards: Style Bible + Moment Library

This file is the single source of truth for the Cocoa Grid Cards style. Part 1 is the style bible (palette, page, cards, type, motion, footage rules, safe zones). Part 2 is the moment library: every move the style knows, with specs measured on a 1078x1920, 30 fps, 22.4 s reference reel. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** a warm graph-paper page (cream, then dark cocoa) on which the speaker's footage lives as a rounded card that rises in, swells to full frame, slides aside for a dark text page and settles back into a card, with every phrase typed word by word inside a cocoa label bar.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. The reference ran at 30 fps; the demo build ran at 24 fps, so keep seconds when the fps differs. Reference values in brackets are for 1080×1920 (measured on 1078×1920).

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Cream page | #EDE2DB | Page behind the card at the start |
| Cream grid line | #E0D5CE | Graph-paper lines on the cream page |
| Cocoa page | #4B3B37 | Dark text page, caption bars |
| Cocoa grid line | #5C4C48 | Graph-paper lines on the cocoa page |
| Ink | #4D3D37 | Italic title on the cream page |
| Tick | #6F645D | Thin guide lines above and below the card |
| Cream text | #F2E9E4 | Caption text on bars and on the cocoa page |
| Chip white | #FFFFFF | Topic chip box |
| Chip ink | #221A18 | Chip text and icon |

Brand-swap rule: if the user gives a brand colour, replace Cocoa page (and the bar) with a dark shade of it and Cream page with a pale tint of it. Keep text contrast high. No accent colours exist in this style.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Page | Full frame. Graph-paper grid: line pitch 0.0835W [90], line width 0.003W [3], first vertical line at x ≈ 0, first horizontal line at y = 0.032H [61]. Same grid on both pages. |
| Card (settled) | Live footage in a rounded rectangle. Corner radius 0.045W [48]. No border, no shadow. Card 1 (opener): x 0.167–0.831W, y 0.315–0.829H [180–896, 604–1592]. Card 2 (return): x 0.10–0.90W, y 0.1875–0.81H [108–968, 360–1556]. Both are ≈ 0.72 wide-to-tall. |
| Card crop | Cover-fit: scale = card width / source width (so the source keeps its full width), vertical window anchored on the face (face centre at 0.30 of the card height). Crop anchor ✎. While the card grows or moves, the crop window interpolates continuously. |
| Tick lines | Two 0.002W [3] wide vertical lines at x = 0.50W: top one from y = 0 to 0.104H [200], bottom one from the card's bottom edge to the page bottom. Cream page only. |
| Caption bar | Rectangle, #4B3B37 at 95 %, sharp corners, height 0.0615H [118], centred on x = 0.50W, centre y = 0.70H [1344]. Width = full chunk text width + 2 × 0.028W [30] padding; text left-aligned at the left padding. Fixed on the page: it does not move with the card. |
| Topic chip | White rectangle, sharp corners, height 0.047H [91], centre x = 0.50W, centre y = 0.228H. Contents: small asterisk icon (0.033W) then uppercase text. Width = padding 0.03W + icon + gap + text + padding 0.03W. |
| Inset card | Small rounded card (radius 0.03W) of the user's own footage on the cocoa page, 0.40W × 0.30H, x 0.50–0.90W, y 0.58–0.88H, with an italic label under its bottom-right corner. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 fractions) | Use |
|---|---|---|
| Title line | centre x 0.50W, centre y 0.218H [419] | Italic title word between the top tick and the card |
| Bar lane | x 0.04–0.96W, y 0.669–0.731H | Bar captions (all states: card, full frame) |
| Staircase | first line centre y 0.46H [884]; line pitch 0.93 × font size; first line starts at x = 0.15W; each next line starts at (previous start + 0.5 × previous line width), kept right edge ≤ 0.92W | Bare staircase caption on the cocoa page or over footage |
| Serif line | centre x 0.50W, centre y 0.60H | Serif words on full-frame footage |
| Topic chip | centre y 0.228H | Cocoa page |
| Inset card | x 0.50–0.90W, y 0.58–0.88H | Cocoa page, under the staircase |

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Title | Italic transitional serif, semibold, mixed case as written, cocoa ink | Newsreader Italic (wght 600) | Lora Italic, Playfair Display Italic | 0.088W [95]; 6-letter word ≈ 0.24W wide |
| Bar caption | Humanist grotesque sans, medium, lower-case as written, cream, letter-spacing 0 | Work Sans Medium (wght 500) | Manrope Medium, Inter Medium | 0.085W [91]; shrink to ≥ 0.07W if width + padding > 0.92W |
| Bare staircase | Same sans, cream, soft shadow on footage | Work Sans Medium | Manrope, Inter | 0.085W [91]; line pitch 0.93 em |
| Serif line | Roman serif, medium, white, soft shadow | Newsreader Medium (wght 500) | Lora, Playfair Display | 0.115W |
| Chip text | Uppercase sans, medium, tracked, near-black | Work Sans Medium | Manrope, Inter | 0.053W; letter-spacing 0.06 em |
| Inset label | Small italic serif, cream | Newsreader Italic | Lora Italic | 0.036W |

Font note: Work Sans and Newsreader were identified by letterform and match the reference closely. Download Work Sans from the Google Fonts GitHub repo (ofl/worksans) if missing.

Rules: case exactly as the user wrote it, except the chip, which is uppercase by style. No outline-only text. Nothing is rotated. Text on footage gets a soft shadow (0, +3 px, blur 6 px, #000000 at 42 % at 61 px type); text on a bar or the page has none.

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Card rise | exponential ease-out (1 − 2^(−10u)) from below the page | 0.45 s (opener), most of the move in the first 0.2 s |
| Card expand to full frame | smoother-step in-out (slow start, fast middle) | 0.8 s |
| Card settle (full frame to card) | cubic ease-out | 0.7–1.6 s (reference 1.6 s; the demo used 0.7 s) |
| Slide aside | cubic ease-in, footage moves right off frame | 0.5 s |
| Slide return | exponential ease-out, footage enters from the right | 0.5 s |
| Caption word | ease-out alpha ramp, no movement | 0.08–0.1 s |
| Caption chunk change | hard cut, bar resizes in the same frame | 1 f |
| Title / chip | alpha + 0.012H rise (title); letter-by-letter type-on at 0.065 s per letter (chip) | 0.3 s / 0.5 s |
| Cuts | hard cut inside the card or full frame, no effect | 0 f |

Never: bounce, overshoot, spring, rotation, tilt, glitch, shake, blur, flashes, colour accents, wipes other than the slide, scale pops on captions, effects on cuts.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Cover-fit crop into a rounded card (scale ≥ 0.66, full width kept) | Primary footage plays live in the card, in sync with the audio |
| Growing, shrinking and sliding the footage window | Per the moments; continuous curves only |
| Rising in from the bottom edge at the opener | The speaking face is clear of the page edge by 0.2 s |
| Covering the footage with the cocoa page (D1) | Only on a shot without a speaking face, ≤ 1.2 s per cover, once or twice per video, ≤ 15 % of total duration; the audio keeps playing |
| Inset card of the user's own footage (S1) | A still of the current shot (≤ 1.5 s); never a different person or scene than the user supplied |
| Text, bar, chip, page and tick overlays | Per 1.7 |

Forbidden: replacing, regenerating, reordering, retiming or trimming footage; speed ramps; freezing the primary window; blur, glitch, warp, colour grading or filters of any kind; adding footage the user did not supply.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face (speaking) | Never covered by the bar, staircase, serif line, chip or inset card; never cut by a card edge. If a face sits at y 0.62–0.78H, move the bar lane to y 0.88H (bar centre) for that shot. |
| Card crop | Keep the whole face box inside the card with ≥ 0.03H margin; shift the vertical window, not the scale. |
| Bar lane | y 0.669–0.731H by default. Never over a face. |
| Serif line | y 0.60H; use y 0.82H if a face sits at 0.50–0.70H. |
| Footage text (signs, UI) | If readable footage text sits in the bar or serif lane for more than 1 s, switch the lane (bar to 0.88H, serif to 0.82H). |
| Edges | Every glyph and bar stays ≥ 0.04W from the left and right edges. |

---

## PART 2 — MOMENT LIBRARY

Family codes: **P** page · **C** caption · **K** card move · **D** dark page · **T** tag · **S** secondary · **X** cut · **E** ending.
Energy legend: ● calm · ●● medium · ●●● high.

### P1 · GRID PAGE OPEN — P ●● (signature opener)
**What it is:** the video opens on an empty cream graph-paper page; the caption bar starts typing first, the italic title fades in above, and the footage rises into a rounded card from the bottom edge.
**Use when:** every video, at the start; the first shot has a person or a main subject. **Avoid when:** the first shot is a face that is already speaking and the page would hide it beyond 0.2 s (then start the rise at t = 0 as in the Motion table).
**Text (✎):** title = one word from the user's own words (the topic word), as written, ≤ 12 characters; omit the title if none fits.
**Geometry / Graphics:** cream page + grid (1.2), Card 1, tick lines, title line (1.3), title in Ink.
**Motion (reference at 30 fps; demo values at 24 fps in brackets):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.5–1.0 [0.0–0.45] ✎ | card | y offset | card top 0.67H → 0.315H (card clipped by the page bottom) | exponential ease-out |
| 0.5–1.0 [0.45–0.7] ✎ | tick lines | alpha | 0 → 1 | linear |
| 0.6–0.9 [0.35–0.65] ✎ | title | alpha, y | 0 → 1, +0.012H → 0 | cubic ease-out |
| hold | card, title, ticks | — | final state | — |

**Footage / plate behaviour:** live footage inside the card; first shot visible from the first frame (the demo started the rise at t = 0 so the face is in view by 0.2 s).
**Captions during it:** C1 bars run from the first spoken word; the first bar may appear before the card.
**Exit:** K1 expands the card over the page.
**Build notes:** pre-render both pages once at 2× and downscale; draw ticks on an RGBA overlay; card via `Image.resize(..., box=floats)` with a 3× anti-aliased rounded mask.
**Flow prompt text:** "The video opens on a warm cream graph-paper page. The footage rises from the bottom edge into a rounded card in the middle of the page, while a short italic serif title, {{TITLE}}, fades in above it and two thin vertical guide lines appear above and below the card."
**Still-image state:** card settled, title visible.

### C1 · LABEL BAR CAPTION — C ●● (signature, the caption system)
**What it is:** each phrase sits in a cocoa label bar near the lower third; the bar is sized to the whole phrase at once and the words type in from the left, one by one.
**Use when:** always while the footage is in a card or full frame. **Avoid when:** the cocoa page is showing alone (use C2).
**Text (✎):** the user's exact words, case as written. Chunk rules: 2–3 words, ≤ 20 characters at the base size; split at punctuation; never end a chunk on an article, preposition or conjunction; a chunk lasts 0.6–1.4 s; a single long word may stand alone for up to 1.2 s; prefer chunk changes at cuts.
**Geometry / Graphics:** bar per 1.2, text per 1.4, bar width fixed to the full chunk before the first word appears. If the phrase is too wide, shrink the font down to 0.07W, else split.
**Motion (measured on the reference, 30 fps: words every 0.2–0.4 s, chunks ≈ 1.0 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start ✎ | new word | alpha | 0 → 1 (0.08 s) | ease-out |
| word start ✎ | earlier words | — | unchanged | — |
| chunk end ✎ | bar + words | — | replaced by the next bar in the same frame | hard cut |

Word start = the word's spoken start time. Chunk end = next chunk's first word start, or min(last word end + 0.4 s, next mode change).
**Footage / plate behaviour:** untouched; the bar overlays the card or the full frame, centred on x = 0.50W regardless of the card.
**Captions during it:** this is the caption system.
**Exit:** hard cut.
**Build notes:** one sprite per word (2× then downscale); bar pasted at integer pixel positions; measure with `font.getlength` of the whole chunk first.
**Flow prompt text:** "Near the lower third, each short phrase appears inside a dark brown label bar that already fits the whole phrase, and the words appear one by one from the left in clean cream lettering. When a phrase is complete the next phrase replaces it at once. The only words are {{CAPTION_WORDS}}."
**Still-image state:** one full chunk in the bar.

### K1 · CARD EXPAND — K ●●● (signature)
**What it is:** the rounded card swells to the full frame, its corners squaring off, and the page disappears behind it.
**Use when:** the story moves from the setup to the main body; a sentence boundary or a cut ≥ 0.3 s earlier; footage that benefits from full frame (B-roll, products, a face that must be larger). **Avoid when:** within 0.1–0.25 s after a cut; once only per card state.
**Text (✎):** none.
**Geometry / Graphics:** rect interpolates from Card 1 (or Card 2) to the full frame; radius 0.045W → 0.
**Motion (reference 4.6–5.4 s; demo 2.35–3.15 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.6–5.4 [2.35–3.15] ✎ | card rect | all four edges | card → (0,0,W,H) | smoother-step (measured: top edge 604, 600, 592, 572, 496, 204, 60, 28, 0 px at 0.1 s steps) |
| same | card | radius | 0.045W → 0 | same |

**Footage / plate behaviour:** live; the crop window opens to the whole frame as the rect grows.
**Captions during it:** bars stay in place.
**Exit:** none (ends in full frame).
**Build notes:** compute scale = max(rect w / W, rect h / H); vertical window offset = clamp(anchor − 0.30 × window height).
**Flow prompt text:** "The rounded video card smoothly grows until it fills the whole frame, its corners straightening, and the cream page disappears behind it."
**Still-image state:** none.

### D1 · SLIDE-ASIDE TEXT PAGE — D ●●● (signature)
**What it is:** the full-frame footage slides off to the right and a dark cocoa graph-paper page takes over; a white topic chip types in at the top and the phrase appears as a bare staircase of cream words.
**Use when:** a topic word, number or time phrase deserves a beat; a B-roll or object shot without a speaking face (0.8–1.2 s cover). **Avoid when:** a face is speaking in the shot (do not cover it); never twice within 3 s.
**Text (✎):** chip = 1–2 of the user's words in uppercase (≤ 14 characters); staircase = the user's words of the current phrase (C2).
**Geometry / Graphics:** cocoa page + grid, chip (1.2), staircase (1.3).
**Motion (reference 10.6–11.0 s out; demo 7.05–7.55 s out, hidden 7.55–8.42 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 7.05–7.55 ✎ | footage | x offset | 0 → +W | cubic ease-in |
| 7.58–8.10 ✎ | chip | letters | one by one, 0.065 s per letter | linear |
| word starts ✎ | staircase words | alpha | 0 → 1 (0.1 s) | ease-out |

**Footage / plate behaviour:** footage slides out live; the shot keeps playing under the page (audio continues). Cover ≤ 1.2 s.
**Captions during it:** C2 only; no bar on the bare page.
**Exit:** D2.
**Build notes:** the chip box grows with the typed text but its final width is centred on 0.50W; the staircase words are already on screen over the footage when the slide starts and stay fixed while the footage leaves.
**Flow prompt text:** "The picture slides off to the right and reveals a dark brown graph-paper page. A small white tag typing {{CHIP_TEXT}} in capital letters appears near the top, and the words {{CAPTION_WORDS}} appear in cream lettering as a staircase, each line starting a little further right."
**Still-image state:** dark page, chip and staircase.

### D2 · SLIDE RETURN — D ●●● (pairs with D1)
**What it is:** the footage glides back in from the right edge and fills the frame.
**Use when:** ends a D1 cover; the cut to the next shot may happen under the page. **Avoid when:** without a preceding D1.
**Text (✎):** none.
**Geometry / Graphics:** full-frame footage.
**Motion (reference 14.2–14.7 s; demo 8.42–8.92 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 8.42–8.92 ✎ | footage | x offset | +W → 0 | exponential ease-out (measured left edge 1040, 348, 112, 52, 20, 0 px at 0.1 s steps) |

**Footage / plate behaviour:** live. If a footage cut falls under the page, the new shot slides in; start the slide ≥ 3 f after the cut.
**Captions during it:** C1 may start on the first word after the slide begins.
**Exit:** settles in full frame; K2 may follow.
**Build notes:** same renderer as D1 with the sign reversed.
**Flow prompt text:** "The picture glides back in from the right edge until it fills the frame again."
**Still-image state:** none.

### K2 · CARD SETTLE — K ●● (same move reversed)
**What it is:** the full-frame footage shrinks back into a rounded card on the cocoa page.
**Use when:** after D2 or at the closing line, to finish on the card look. **Avoid when:** a face would be cut by the card crop.
**Text (✎):** none.
**Geometry / Graphics:** full frame → Card 2; radius 0 → 0.045W.
**Motion (reference 14.8–16.4 s, 1.6 s; demo 8.95–9.65 s):**

| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 8.95–9.65 ✎ | rect | all edges | full → Card 2 | cubic ease-out (measured top edge 36, 136, 184, 216, 252, 268, 292, 304, 312, 324, 332 px at 0.1 s steps) |

**Footage / plate behaviour:** live.
**Captions during it:** C1 bar stays fixed on the page.
**Exit:** holds as a card.
**Build notes:** window offset uses the face anchor (0.30 of the card height).
**Flow prompt text:** "The picture shrinks smoothly into a rounded card sitting on a dark brown graph-paper page."
**Still-image state:** Card 2 on the cocoa page.

### T1 · TOPIC CHIP — T ● (part of D1; may stand alone)
**What it is:** a small white tag that types a topic word in capitals, with a tiny asterisk icon.
**Use when:** a topic, step name or number is introduced on the cocoa page. **Avoid when:** more than 14 characters; it never appears over footage.
**Text (✎):** user's word(s), uppercase.
**Geometry / Graphics:** chip per 1.2.
**Motion:** letters appear one by one, 0.065 s per letter; hold until the page ends.
**Footage / plate behaviour:** none (cocoa page only).
**Captions during it:** C2 below.
**Exit:** covered by D2.
**Build notes:** pre-render one sprite per letter count; draw the icon as four crossing lines.
**Flow prompt text:** "A small white rectangular tag near the top types out {{CHIP_TEXT}} in capital letters, with a tiny asterisk before it."
**Still-image state:** the full tag.

### C2 · BARE STAIRCASE — C ●● (caption on the page or over footage)
**What it is:** the phrase appears word by word as cream lettering with no bar, each line starting further right than the one before.
**Use when:** during D1, or over full-frame B-roll for a short phrase. **Avoid when:** on a speaking face shot, or over bright footage (use C1).
**Text (✎):** user's words; 1–2 words per line, ≤ 3 lines.
**Geometry / Graphics:** Staircase (1.3), font per 1.4; shadow on footage.
**Motion:** word alpha 0 → 1 over 0.1 s at each word start; the whole phrase stays until the page ends; no movement.
**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** hard cut with the next phrase or D2.
**Build notes:** lay out all lines before the first word; line k start = start(k−1) + 0.5 × width(k−1), right edge clamped to 0.92W.
**Flow prompt text:** "The words {{CAPTION_WORDS}} appear one by one in cream lettering without any box, stepping down and to the right line by line."
**Still-image state:** whole phrase.

### C3 · SERIF LINE — C ●● (extension in the same grammar)
**What it is:** a short phrase in white roman serif, one word after another, centred below the middle of the frame.
**Use when:** a payoff or contrast phrase of 1–3 words deserves a quieter, editorial beat on full-frame footage; max 2 per video. **Avoid when:** over bright footage or a face at 0.50–0.70H.
**Text (✎):** user's words, ≤ 18 characters.
**Geometry / Graphics:** Serif line (1.3), font per 1.4, soft shadow.
**Motion:** each word alpha 0 → 1 and +0.012H → 0 over 0.2 s (cubic ease-out); phrase holds; hard cut at the end.
**Footage / plate behaviour:** untouched.
**Captions during it:** replaces the bar for its duration.
**Exit:** hard cut.
**Build notes:** same sprite method as C1.
**Flow prompt text:** "Near the middle of the frame, the words {{CAPTION_WORDS}} fade up one by one in a refined white serif, then are replaced by the next caption."
**Still-image state:** the phrase.

### S1 · INSET CARD — S ●● (extension in the same grammar)
**What it is:** a small rounded card of the user's own footage slides up beside the staircase on the cocoa page, with a tiny italic label.
**Use when:** during D1, to show what the line is about. **Avoid when:** the user has no related shot (skip it).
**Text (✎):** label = one of the user's words, as written.
**Geometry / Graphics:** inset card and label (1.2); the card shows a still of the current shot, cover-fit.
**Motion (demo 7.66–8.02 s):** card rises 0.6 × (H − y) → rest position, cubic ease-out, 0.36 s; label alpha with it; covered by D2.
**Footage / plate behaviour:** still of the shot (≤ 1.5 s).
**Captions during it:** C2 above it.
**Exit:** covered by D2.
**Build notes:** grab the still from the frame at the middle of the cover.
**Flow prompt text:** "A small rounded card showing a still from the footage slides up on the right of the dark page, with the word {{LABEL}} written under it in tiny italic letters."
**Still-image state:** the card with its label.

### X1 · CUT IN CARD — X ● (every footage cut)
**What it is:** the footage changes with a plain hard cut while the card, page, title and bar stay exactly where they are.
**Use when:** every cut while the footage is in a card or full frame. **Avoid when:** never add an effect.
**Text (✎):** none.
**Motion:** hard cut; crop anchor ✎ switches to the new shot's subject on the same frame; a chunk change is preferred on the cut frame.
**Footage / plate behaviour:** untouched; no big move starts within 3 f of the cut; a cut under the cocoa page (D1) is hidden by it.
**Captions during it:** per C1.
**Exit:** none.
**Build notes:** anchor table per shot (face y and frac).
**Flow prompt text:** "At each cut the picture inside the card simply changes to the next shot with no effect; the page and the captions stay where they are."
**Still-image state:** none.

### E1 · END HOLD — E ● (extension in the same grammar)
**What it is:** the closing card or full frame holds with the last bar until just before the end.
**Use when:** every video. **Avoid when:** never.
**Text (✎):** last chunk.
**Motion:** the bar holds to min(last word end + 0.4 s, end − 0.08 s); the page and card stay still.
**Footage / plate behaviour:** live to the last frame.
**Captions during it:** per C1.
**Exit:** video ends.
**Build notes:** none.
**Flow prompt text:** "The last caption stays in its bar until the very end while the card holds still on the page."
**Still-image state:** final card.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll (→ talking head) | P1 + C1 | X1 on every cut; K1 at the first sentence boundary; C3 on a payoff; D1 on a B-roll shot with a topic phrase | D2 + K2 + E1 |
| Single talking head, no cuts | P1 + C1 | K1 after the first sentence; D1 only if the shot has no speaking face (skip otherwise); C3 on one phrase | K2 + E1 |
| B-roll only, no speech | P1 (user's title words, if any) + C1 | X1 on every cut; D1 with S1 on one shot; C2 phrases | D2 + E1 |
| Still image + text | P1 settled (card of the image), bar with the text | — | — |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

---

## TUNING NOTES (from the demo2 render, 720x1280, 24 fps)

- Card rise 0.0–0.45 s (exponential ease-out) so the speaker's face is visible by 0.2 s; bar started with the first word at 0.10 s.
- Card 1 hold 0.45–2.35 s; K1 expand 2.35–3.15 s (cut at 1.83 s is 0.5 s earlier; the next cut at 3.25 s lands after the expand).
- Bar font 0.085W (61 px at W 720); "automate your" and "investments," split because the 3-word chunk would exceed 0.92W; "about earning more." (19 characters) fits.
- C3 serif line used on "what's left." (5.70–6.85 s) at y 0.60H, clear of the grocery face (y 0.10–0.37H).
- D1: staircase "Do it / for one / year" at 0.085W starting 6.90 s over the plant shot, slide-out 7.05–7.55 s, chip "ONE YEAR" typed 7.58–8.10 s, inset still of the plant shot with the label "year" 7.66–8.02 s, page hidden the footage for 0.87 s (7.55–8.42 s) and covered the cut at 8.375 s; D2 slide-in 8.42–8.92 s; K2 settle 8.95–9.65 s with Card 2; last bar "happens." held to 9.92 s.
- The title (Saving) is covered by the card during K1; no tick lines or title return after the page changes to cocoa.
- Anchor table used (face y, fraction of card height): S1 0.275/0.30, S2 0.5/0.5, S3 0.5/0.5, S4 0.24/0.25, S5 0.5/0.5, S6 0.275/0.30.
