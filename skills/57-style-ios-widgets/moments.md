# moments.md — iOS Widgets: Style Bible + Moment Library

This file is the single source of truth for the iOS Widgets style. Part 1 is the style bible, Part 2 the moment library, Part 3 starting combinations. The look and sizes were measured on three 720x1280 phone-screen crops of one reel (frosted widgets, blue check pills with a cursor, a profile follow card); the motion, timing and the remaining moments are design decisions in the same grammar, marked "(design, not measured)". Every value was tuned on a 720x1280, 24 fps, 10 s render. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays full-frame and untouched while home-screen glass widgets (a counter tile, a progress tile) drop in at the top corners, solid system-blue check pills get ticked off by a mouse cursor as each step is spoken, a frosted capsule carries the last line and a white profile card gets its Follow button clicked, with bold white captions that turn one word into a blue pill.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps (24 fps in the tuned render; at another fps keep the seconds). Pixel values are for 720×1280; scale by W/720.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Value | Used for |
|---|---|---|
| System blue | #256BFD (measured 37,107,253) | Check pills, caption keyword pill |
| Glass | white 22 % tint over the blurred footage, backdrop darkened up to 20 % on bright footage, saturation ×1.4 | Widgets, closer capsule |
| Glass rim | white 45 %, 1.6 px | Edge of every glass panel |
| Glass sheen | white, 0 → 11 % over the top 55 % of the panel | Top highlight |
| Card white | white 80 % over the blurred footage | Follow card |
| Ink | #17171F | Dark text on white pills and the card |
| Follow button | #4F46E5 solid, white text (state "Follow") → #E4E4FF with #584EEE text (state "Following") | F1 |
| Closer tint | #FFD6B0 → #F0C0D0 left to right | Last word of the capsule (peach, measured from the reference's tinted word) |
| Cursor | near-black #0E0E12 arrow with a white 2 px outline | K1, F1 |
| Text white | #FFFFFF | Widget text, captions |

Brand-swap rule: replace System blue and Follow button with the user's brand colour (keep it saturated and dark enough for white text). Glass, white and ink never change.

### 1.2 Containers / shapes

| Item | Spec |
|---|---|
| Footage | Always full frame, 100 % of W and H, live and untouched. No cards around it, masks or colour overlays. Glass panels blur only the footage under themselves. |
| Counter widget | 208 × 236 [measured on the reference: 242 × 300 of 720×1280], corner radius 40, glass |
| Progress widget | 208 × 112–124, radius 34, glass |
| Follow card | 380 × 112 (600 with a user handle) [reference 624 × 116 with name], radius 40, white glass, centred on x = 0.50W |
| Closer capsule | text width + 76 × 88, fully round, glass |
| Check pill | height 62 [measured 58], fully round, width = text + 82 |
| Panel shadow | black 20 %, blur 11 px, offset 8 px down |
| Pill shadow | black 28 %, blur 7 px, offset 4 px down |
| Crop | Cover-fit only when the source is not 9:16. Anchor ✎ = the speaker's face box. |

### 1.3 Layouts / grid

| Layout | Region (x0,y0,x1,y1 as fractions) | Use |
|---|---|---|
| Widget left | 0.033, 0.084, 0.322, 0.268 [24,108,232,344] | Counter widget (default) |
| Widget right | 0.678, 0.084, 0.967, 0.172 (progress) or 0.268 (counter) | Progress widget (default), or counter widget on swap |
| Pill field | y 0.60–0.74, x 0.12–0.88 | Check pills, scattered: centres at (0.30, 0.615), (0.62, 0.668), (0.36, 0.722) |
| Caption lane | centre y = 0.83H [1062], max width 0.84W | C1 captions |
| Closer capsule | centre y = 0.745H | E1 |
| Follow card | centre y = 0.885H [1133] | F1 |

Face rule: widgets keep x ≤ 0.322W on the left and ≥ 0.678W on the right so they never reach a face box of x 0.34–0.66.

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Progress header | semibold, white 94 %, auto-fit to width 146 | Inter 680 | Manrope, DM Sans | 21 down to 14 |
| Counter | bold, white, centred in the widget | Inter 760 | Manrope ExtraBold | 92 down to 40 |
| Check pill text | bold | Inter 700 | Manrope | 27 |
| Caption | bold, white, sentence case as written, soft shadow, centred | Inter 740 | Plus Jakarta Sans, Manrope | 54, line pitch 70, word gap 0.27em |
| Caption keyword | same, inside a blue pill, pill pad 15 left/right | Inter 740 | same | 54 |
| Capsule text | bold | Inter 740 | same | 44 |
| Card button | 720 | Inter | Manrope | 24 |

Rules: text case exactly as the user wrote it. Widget, pill and capsule text is a complete phrase copied as-is from the user's captions, or a counter numeral. UI labels "Follow" and "Following" are the only other words, and only inside F1. Never assemble a label from scattered words.

### 1.5 Motion language

- Entrances: overshoot ease (back, overshoot 1.2–1.8) with a scale from 0.55–0.90 to 1. Exits: ease-out cubic, scale 0.92–0.94 and a short upward drift.
- Idle: every glass panel and pill floats ±2.5–3 px on a sine of 2.4–2.6 s, each with its own phase (M1).
- Cursor: smooth ease-in-out path with a slight arc, click dip 0.86 scale for 0.16 s.
- Click: press dip 5 %, state change in ≤ 0.05 s, pop to 1.10 and back over 0.5 s, white ripple ring growing 8 → 38 px over 0.45 s.
- Never: slides across the whole frame, wipes, flashes, shake, glitch, rotation, extra colours, blur or zoom of the footage.

### 1.6 What may happen to the user's footage

Allowed: full-frame display; glass panels, pills, capsule, card and cursor drawn over it; the panels blur and tint the footage only inside their own shape. Forbidden: replacing or regenerating anything, grading, speed change, trimming, reordering, blur or zoom of the footage outside a panel. Avatar thumbnails inside widgets or the card are a still crop of the user's own speaker (never another person).

### 1.7 Safe zones

- Face box never covered while speaking. Corner widgets stay outside x 0.34–0.66.
- Pill field and captions sit in the lower half; on shots where the face is low (face bottom > 0.55H) move the pill field up to y 0.45–0.58 and keep the caption lane below the face.
- Footage text (a phone screen, a sign) may be covered by a pill for the length of one pill only.

---

## PART 2 — MOMENT LIBRARY

Families: T title/tile, W widget, K check, F follow, E end, C caption, M motion. Energy: low / mid / high.

### T1 · WIDGET STACK DROP — T high (signature opener)
**What it is:** a step-counter glass widget on the left and a progress widget on the right drop in at the top corners and float.
**Use when:** the opening line, from 0.3 s. **Avoid when:** the face box reaches the top corners.
**Text (✎):** big widget = a step counter "0/N" (N = number of list steps in the script; numerals allowed for counters), or a real number the user wrote, otherwise drop the big widget. No header, no sub. Progress widget header = one complete phrase copied as-is from the captions (e.g. a full noun phrase or step), never assembled from scattered words.
**Geometry / Graphics:** counter widget at Widget left (208×236, radius 40); progress widget at Widget right (208×112, radius 34); glass per 1.1; a small white dot icon (r 7) before each header.
**Motion (design, not measured):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.30 s (big), 0.40 s (progress) | panel | y offset, scale, alpha | −56 px, 0.88, 0 → 0, 1.0, 1 over 0.6 s (alpha over 0.2 s) | back 1.3 |
| after landing | panel | idle float | ±3 px, 2.4 s sine | M1 |
| 1.58–1.82 s (or before the next cut) | panel | exit | scale 0.94, −18 px, alpha 1 → 0 over 0.24 s | ease-out cubic |

**Footage:** untouched. **Captions during it:** C1 in the lane. **Exit:** before the next cut (never across a cut).
**Build notes:** blur the whole frame once per frame (Gaussian σ 14) and composite it inside each panel mask; draw masks at 3× and downscale.
**Flow prompt text:** "Two frosted glass home-screen widgets drop softly into the top corners of the frame, one with the step count {{COUNT}} in large bold white letters, one with the words {{PHRASE}} above a thin progress bar that fills while the speaker says them. They float gently and fade out before the next shot. The person is not covered."
**Still-image state:** both widgets settled, bar full.

### T2 · WIDGET SWAP — T mid (extension in the same grammar)
**What it is:** the counter widget returns later with a new word, on the side that is empty in the current shot.
**Use when:** a new topic or a B-roll shot with free corner space. **Avoid when:** within 0.3 s after a cut.
**Text (✎):** counter as in T1, normally "N/N" (all steps done) or the next count; no header or sub.
**Geometry:** counter widget at Widget right (x 488, y 108). **Motion:** as T1 big widget, enter 0.32 s after the shot starts, exit 0.24 s before the next cut. **Footage:** untouched.
**Flow prompt text:** "A single frosted glass widget drops into the top {{SIDE}} corner showing the step count {{COUNT}} in large bold white letters, floats, then leaves before the next shot."

### W2 · PROGRESS FILL — W mid (signature detail of T1)
**What it is:** the progress widget's white bar fills while the user says its phrase.
**Motion (design, not measured):** bar 0 → 100 % over 0.9 s starting 0.25 s before the phrase, ease in-out; track white 31 %, fill white, height 14, round ends, 20 px side padding. No percentage text.
**Use when:** a phrase about growth, effort, time or "more". **Flow prompt text:** "A thin white progress bar inside a glass widget fills smoothly from empty to full."

### K1 · CHECK PILLS — K high (signature)
**What it is:** one blue pill per spoken step. It lands unchecked (white, empty ring), a mouse cursor glides in and clicks it, it turns blue with a tick and stays until the next cut.
**Use when:** lists, steps, 2–3 parallel phrases, "first / then / finally". Also single claims worth a tick. **Avoid when:** more than 3 pills in one shot.
**Text (✎):** 2–4 user words per pill, taken in order.
**Geometry:** pill height 62 [measured 58], fully round; text Inter 700 27, left pad 26, gap 12, icon 22 (empty ring 20 px, 2.6 px grey; tick white 3.6 px stroke), right pad 22; unchecked fill white 92 %, ink text; checked fill System blue, white text. Positions: the pill field in 1.3. Cursor arrow 34×48 sprite, tip on the icon.
**Motion (design, not measured):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | pill | scale, alpha | 0.55, 0 → 1, 1 over 0.42 s | back 1.6 |
| −0.65 s before click | cursor | position | previous pill (first pill: just off the right edge at 0.52H) → this pill's icon over 0.65–0.75 s | in-out + 6 % arc |
| click | pill | scale | 0.95 for 0.08 s, then to 1.10 and back to 1.0 over 0.5 s | sine |
| click | pill | state | unchecked → checked, cross-fade 0.05 s | linear |
| click | ripple | radius, alpha | 8 → 38 px, 0.75 → 0 over 0.45 s | ease-out |
| shot end − 0.22 s | pills, cursor | exit | scale 0.92, alpha → 0 over 0.22 s | ease-out |

Click time = pill start + 0.7–1.1 s (tuned: 0.85, 1.10, 0.70). The cursor stays on the last pill until the exit.
**Footage:** untouched. **Captions during it:** C1 below the pill field.
**Flow prompt text:** "A small bright blue rounded pill with a white tick appears for each point the speaker makes, reading {{POINT_1}}, {{POINT_2}}, {{POINT_3}}. A mouse cursor glides to each one and clicks it, a soft ring spreads, and the pill turns from white to blue."
**Still-image state:** all pills blue and ticked, cursor on the last one.

### F1 · FOLLOW CARD — F high (signature CTA; measured on the reference, motion designed)
**What it is:** a white profile card rises near the bottom with a round avatar, a name, a small line and a solid Follow button; the cursor clicks it and it becomes a pale Following button.
**Use when:** the payoff, call to action, a creator or product name, the last 1.5 s. **Avoid when:** the bottom is busy with footage text.
**Text (✎):** none except the button labels "Follow" then "Following" (closed vocabulary). Only if the user gives their own handle or name, it may appear as a name line (complete, as given). Avatar = a still crop of the speaker (or the main subject) from the user's footage.
**Geometry:** 380×112 (600×112 when a user handle is shown), radius 40, white glass 80 %; avatar r 38 with a blue-to-violet ring (3 px) and a white 2 px gap at the left; button 150×56 round, right pad 22. Handle line (optional): Inter 760 31 ink.
**Motion (design, not measured):**

| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| T0 | card | y offset, scale, alpha | +34 px, 0.90, 0 → 0, 1, 1 over 0.5 s | back 1.25 |
| T0 + 0.35 s | cursor | position | off the bottom-right corner → button over 0.55 s | in-out |
| T0 + 0.9 s | button | state | Follow → Following; card pops 1.025 over 0.35 s | sine |

**Footage:** untouched; keep the face clear (card is in the bottom 14 %). **Captions during it:** only E1 above the card.
**Flow prompt text:** "A white rounded profile card rises near the bottom with a round photo of the speaker and a blue Follow button. A mouse cursor clicks the blue Follow button and it changes to a pale Following button."
**Still-image state:** card visible with Following.

### E1 · GLASS CAPSULE CLOSER — E mid (signature)
**What it is:** the final line sits in a frosted capsule instead of plain captions, last word tinted peach.
**Use when:** the last sentence or call to action. **Avoid when:** shorter than 0.8 s.
**Text (✎):** the last 2–4 user words. **Geometry:** capsule text width + 76 × 88, fully round, centre y 0.745H (above F1), glass tint 14 %; text Inter 740 44 white; last word gradient peach → pink.
**Motion (design, not measured):** from the first word: scale 0.90 → 1, alpha 0 → 1 over 0.35 s, back 1.2; float M1; stays to the end.
**Flow prompt text:** "The final words appear in a soft frosted glass capsule, white letters with the last word in a warm peach tint."

### C1 · CAPTION KEYWORD PILL — C mid (signature captions)
**What it is:** 3–5 word chunks of bold white sentence-case text, centred in the lower lane, one word turns into a blue pill when spoken.
**Rules:** chunk 3–5 words, split at punctuation, never end on an article, preposition or conjunction; max width 0.84W, ≤ 2 lines; ≤ 1 keyword per chunk, ≤ 3 per video; keywords are meaning words, never the last word of a list pill already shown. Chunk start = first word; end = min(next chunk start − 0.04 s, last word start + 1.0 s); min 0.4 s.
**Motion (design, not measured):** words fade in and rise 12 px over 0.16 s, staggered 0.035 s; the full chunk layout is fixed (nothing moves). The keyword shows as white text first; at its spoken time the blue pill pops in (scale 0.70 → 1, back 1.8, over 0.22 s). Chunk fades out over 0.08 s.
**Geometry:** lane in 1.3, text shadow black 38 %, blur 6, 3 px down. **Flow prompt text:** "Bold white captions in the lower part of the frame, two lines at most, one important word sitting in a bright blue rounded pill."

### C2 · CAPTION ON GLASS — C low (extension in the same grammar)
**What it is:** the same chunk inside a frosted capsule (E1 geometry, no tint on the last word) for bright or busy lanes. **Use when:** lane luminance > 0.7 or detail high. **Flow prompt text:** "The words sit inside a soft frosted glass capsule near the bottom."

### M1 · FLOAT — M low (idle motion, applies to every panel)
Sine drift ±2.5–3 px, period 2.4–2.6 s, phase offset per element, starts when the entrance finishes. Never on the captions or the cursor.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 (+W2) | K1 per list step on the B-roll, T2 on a new topic | E1 + F1 |
| Single talking head | T1 | K1 for 2–3 claims, T2 once | E1 + F1 |
| B-roll only | T1 in the emptiest corner | K1 per step, C2 if bright | E1 |
| Still image | T1 widgets only | K1 pills as a static tick list | F1 settled |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
