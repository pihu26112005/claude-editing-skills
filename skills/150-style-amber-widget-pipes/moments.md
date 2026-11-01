# moments.md — Amber Widget Pipes: Style Bible + Moment Library

This file defines the **Amber Widget Pipes** style completely. SKILL.md decides which moments to use and when; this file defines exactly what each moment looks like and how it moves. The style was measured on a 720x1280, 30 fps reference (11.3 s) and proven on a 720x1280, 24 fps demo; tuned values are synced here.

**The look in one line:** the footage stays live while soft interface pieces float around it: a stack of frosted pills that resolves from pixel blocks behind the speaker's head, plain white widget cards with growing charts and flipping switches, a row of tick tiles, a tinted gradient page that the footage shrinks into as a rounded window, and a glowing tube that forks into two labelled branches. Captions are small sentence-case white lines with one accent word, or label pills on the page.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, anchor, side). Everything else is the style.
4. Final video: build from the spec. Google Flow master prompt: use each moment's **Flow prompt text** (plain words), filling its {{…}} placeholders.

Units: W, H, f (frames at 30 fps in the reference; the demo values are at 24 fps, keep seconds at other rates). Pixel values are for 720x1280; scale by W/720.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette
Measured on the reference: periwinkle accent (about #5B5BF5), page gradient #B1AEFC at the top to #F4F3FA at the bottom, white cards, near-white chips. The accent is a **parameter** (ACCENT); the table lists the measured default and the value used on the public demo.

| Role | Reference default | Demo value | Used for |
|---|---|---|---|
| ACCENT | `#5B5BF5` | amber `#FF9F0A` | top pill fill, caption key word, chart line/area, switch on-state, tick badges, pipe tube, big title word |
| ACCENT-LIGHT | `#B9B8FF` | `#FFCD78` | pipe inner highlight |
| ACCENT-INK | `#3F3FC0` | `#8A4000` | text inside frosted pills and card icons (deep, readable on white) |
| ACCENT-DEEP | `#4A4AD0` | `#D67000` | chart stroke |
| PAGE-TOP / PAGE-BOTTOM | `#B1AEFC` / `#F4F3FA` | `#FFC48A` / `#FFF8EE` | gradient page, vertical, with faint vertical streaks (sine banding, 2.5 % luminance) |
| CARD | `#FFFFFF` | `#FFFFFF` | widget cards, end pills |
| FROST | white 55–62 % over a 14 px blur of the footage | same | pills and tiles over footage |
| SKELETON | `#EBEBF9` | `#ECE2D4` | placeholder bars, chips, switch off-state |
| CAPTION | `#FFFFFF` + soft dark shadow | same | lane captions |
| TITLE-STROKE | n/a | `#381B00` | 5 px outline under the big accent title word |

No other accent colour. Brand variant ✎: ACCENT and its four tints may become one brand hue; everything else stays neutral.

### 1.2 Containers
- **Pill:** fully rounded rectangle, height 0.055–0.08 H [70–80 px at 720]. Top pill is solid ACCENT; the others are FROST. Soft shadow 0 / +6 px, blur 12, 12–20 %.
- **Widget card:** white, radius 28–30 px, shadow +10 px, blur 18, 22–25 %. Width 0.65–0.73 W, height 0.21–0.33 H. UI chrome that would need invented words is drawn as skeleton bars, icons, charts and switches, never as fake text or numbers.
- **Tile:** 96x96 px frosted rounded square, radius 22, five in a row, gap 18.
- **Window (L1):** the footage as a rounded rectangle x 0.05–0.95 W, bottom flush with the frame (y 0.62 H to 1.0 H), radius 30 on the top corners only, soft shadow upward. It always plays the live shot, cropped by cover-fit (4:3 crop, vertical anchor ✎ on the subject).
- **Pipe:** tube 36 px wide (2x supersampled), ACCENT with ACCENT-LIGHT highlight 10 px offset 6 px left, glow blur 14 at 50 %; elbows rounded radius 44.

### 1.3 Layouts (fractions of W, H)
| Name | Geometry |
|---|---|
| Top lane | y 0.035–0.275 H, used by the pill stack and tile row |
| Under-chin title | y 0.44–0.68 H, centred |
| Bottom caption lane | text centre y 0.76 H (B-roll shots) |
| Page, widget zone | y 0.06–0.55 H |
| Page, caption pill | centre y 0.47 H (card page) or 0.09 H (pipe page) |
| Page window | x 0.05–0.95 W, y 0.62–1.0 H |

### 1.4 Typography
| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Pill text | sentence case, semibold, ACCENT-INK | Poppins SemiBold | Inter SemiBold | 34–38 px (0.028 H) |
| Lane caption | sentence case, semibold, white, shadow 75 % | Poppins SemiBold | Inter SemiBold | 52 px (0.041 H) |
| Caption key word | same, ACCENT | same | same | same |
| Title small line | UPPERCASE, tracking 0.07 em, white | Poppins SemiBold | Montserrat SemiBold | 58 px |
| Title big word | UPPERCASE, heavy, ACCENT, glow + dark stroke | Poppins ExtraBold | Montserrat ExtraBold | 112 px, fits 0.86 W per line |

All text sits at least 0.05 W from the side edges. Every word is the user's word.

### 1.5 Motion language
- Arrive: fade plus 8–10 px rise (cards 30 px rise), ease-out-cubic, 5–9 f.
- Pixel resolve (T1): content drawn blocky (16, 11, 8, 5, 3, 2, 1 px blocks) over 8 f while fading in.
- Draw-on: chart lines and pipes grow along their path, ease-in-out, 1.0–1.1 s.
- Page entry and exit: the footage scales into or out of the window over 10 or 9 f, ease-in-out-cubic, while the page fades in over the same time.
- Never: bounce, tilt, spin, shake, flashes, hue-shifted footage.

### 1.6 What may happen to the user's footage
Allowed: full-frame; moved and scaled into the L1 window (a cover-fit crop of the live shot); a frosted blur used only as the backdrop of a pill or card; the speaker placed in front of pills (person mask, T1 only). The primary shot always plays live and in sync. Forbidden: replacing a shot, recolouring, speed changes, hiding the whole shot for more than the 10 f transition, blur on the face.

### 1.7 Safe zones
- Face box never covered while speaking. T1 pills sit behind the head: pill text is placed in the side zones and asserted to be at least 85 % visible against the person mask on every frame after it has appeared.
- Title and cards stay out of the face box; the under-chin title starts below the chin (0.44 H on a speaker with the face at 0.15–0.40 H).
- Bottom lane avoids on-footage text; the footage's own corner watermark is not covered.

---

## PART 2 — MOMENT LIBRARY
Families: T title, C caption, W widget, P pipe, L layout, X transition, M movement. Energy: low / mid / high.

### T1 · PILL STACK RESOLVE — T mid (signature, opener)
**What it is:** three pills stacked behind the speaker's head, carrying the opening phrase. They fade in on the spoken words, resolving from pixel blocks to sharp.
**Use when:** the video opens on a speaker (talking head). **Avoid when:** no person or the head fills the top of the frame (use W1 + C1 instead).
**Text (✎):** the first 3–6 words split in 2–3 pill phrases, 2–3 words each; case as written.
**Geometry:** pill 1 solid ACCENT, centred, y 0.035–0.105 H, width text + 70 px, text ACCENT-INK on accent (dark `#381B00` on amber). Pill 2 FROST, x 0.05–0.95 W, y 0.125–0.19 H, text right-aligned, 34 px from the right inner edge, 34 px font. Pill 3 FROST, y 0.21–0.275 H, text left-aligned at the left inner edge 26 px, 30 px font. Pills 2–3 run behind the head (person mask on top). Text stays in the side zones.
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word time | pill n | alpha, pixel block | 0 → 1, 16 px → 1 px over 8 f | ease-out-cubic (alpha over 6 f) |
**Footage:** full frame, untouched; person mask EMA 0.6/0.4 plus 1.2 px blur. **Captions during it:** none, the pills are the captions. **Exit:** hard cut on the footage cut.
**Build notes:** render each pill as an RGBA tile, block-downsample with BOX then NEAREST, paste with its own alpha, frost the backdrop first, then composite the original frame back through the mask.
**Flow prompt text:** "Behind the speaker, a stack of {{3}} rounded pills appears one by one on the spoken words: a solid {{ACCENT}} pill on top and two frosted white pills behind the head, saying exactly {{PHRASES}}. Each pill sharpens from blocky pixels into crisp text."
**Still-image state:** all pills sharp.

### C1 · LANE CAPTION — C low (signature)
**What it is:** one to three words per line, sentence case, white with a soft shadow, words fading in as spoken, with one ACCENT key word.
**Use when:** any speech on full-frame shots, especially B-roll. **Avoid when:** a page scene is up (use C2).
**Text (✎):** 3–5 words, ≤ 26 characters, one key word (≤ 1 per chunk, ≤ 3 per video).
**Geometry:** centred, text centre y 0.76 H on B-roll; under the chin (y 0.44 H) on speakers; 52 px; max width 0.86 W.
| t | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word time | word | alpha, y | 0 → 1, +10 px → 0 over 5 f | ease-out-cubic |
**Exit:** hard cut at chunk end. **Flow prompt text:** "A short white caption, {{WORDS}}, with the word {{KEY}} in {{ACCENT}}, fades in word by word near the bottom."

### C2 · PILL CAPTION — C low (signature on pages)
**What it is:** the chunk sits in a frosted white pill (height 80, radius full) with ACCENT-INK text 36 px, words fading in as spoken.
**Use when:** L1 pages. **Text (✎):** one chunk, ≤ 28 characters, may wrap to two lines (height 132, radius 40).
**Geometry:** width = text + 76 px, ≤ 0.9 W, centred x; centre y ✎ (0.47 H under a card, 0.09 H over a pipe). Pill fades in over 6 f; words as C1.
**Exit:** hard cut with the footage, or 4 f fade when a page hands over. **Flow prompt text:** "A rounded frosted pill saying {{WORDS}} appears, words one by one."

### W1 · TICK TILES — W mid
**What it is:** five frosted tiles drop in a row with a person icon; ACCENT tick badges pop on one after another.
**Use when:** lists, steps, "people", progress. **Geometry:** row centred, y 0.065 H, tiles 96 px, gap 18. Tiles stagger 2 f from ✎ time, rise 26 px over 7 f; badge r = 15 px at +10 f, +4 f per tile, scale 1 → 1.25 → 1 over 6 f.
**Exit:** hard cut. **Flow prompt text:** "A row of five frosted square tiles with person icons drops in; small {{ACCENT}} tick badges appear on them one at a time."

### W2 · STAT CARD — W mid
**What it is:** a white card (x 0.175–0.825 W, 468x270 px) fades up from frost, with an icon, two skeleton bars, a rising line chart with area fill and a dot, and six chips (the last in ACCENT).
**Geometry:** y 0.047 H (top lane). Card rises 34 px over 9 f; chart draws over 24 f starting at +8 f. **Use when:** growth, results, over-time phrases. **Exit:** hard cut. **Flow prompt text:** "A clean white dashboard card appears at the top with a line chart that draws upward and ends in a dot."

### W3 · TOGGLE CARD — W mid
**What it is:** a white card (x 0.133–0.867 W, y 0.067–0.40 H) with a header and three rows; a switch in each row flips to ACCENT in turn (6 f each, +8 f apart, first at +14 f).
**Use when:** automation, settings, "set it once". **Exit:** 4 f fade at the next cut. **Flow prompt text:** "A white settings card with three rows; the switches turn on one after another in {{ACCENT}}."

### P1 · PIPE FORK — P high (signature)
**What it is:** a pill label with a glowing tube that runs down and forks into two branches ending in two white pills (icon dot plus skeleton bar).
**Geometry:** label pill centre (0.5 W, 0.09 H); stem from y 0.125 H to 0.205 H; branch left to x 0.27 W ending y 0.336 H; branch right to x 0.73 W ending y 0.4375 H; end pills 300x64 px.
**Motion:** tube draws 26 f, ease-in-out, starting 10 f after the label; end pills rise 10 px and fade in during the last 22 % of the draw. **Use when:** a split, a choice, "from one, two". **Exit:** 4 f fade at the cut. **Flow prompt text:** "A glowing {{ACCENT}} tube grows down from a label and splits into two branches that end in white pills."

### L1 · PAGE WINDOW SETTLE — L high (signature layout)
**What it is:** after a cut, the new shot stays full frame for 3 f, then scales over 10 f into the bottom window while a tinted gradient page fades in behind it.
**Use when:** a B-roll shot that carries a UI moment. **Geometry:** see 1.2. Crop anchor (✎): vertical centre of the subject (0.43 H on a phone close-up, 0.27 H on a man at a counter). Page cards enter 11 f after the settle.
**Footage:** live, in sync. **Exit:** X1. **Flow prompt text:** "The shot shrinks smoothly into a rounded window at the bottom while a soft {{PAGE COLOUR}} gradient page fills the rest."

### X1 · WINDOW EXPAND — X mid
**What it is:** on the cut after a page scene the new shot appears in the window, holds 3 f, expands to full frame over 9 f as the page fades out; page widgets fade out over 4 f at the cut.
**Flow prompt text:** "The window grows smoothly back to the full frame as the page fades away."

### T2 · GLOW WORD TITLE — T high (signature, closer)
**What it is:** an under-chin title: a small white uppercase line and one or two giant ACCENT lines with glow and a dark stroke, words popping on their beats.
**Text (✎):** the last 3–4 words; small line = connector words, big lines = payoff word(s).
**Geometry:** small line 58 px at y 0.44 H, big lines 112 px at +78 px and +182 px, centred; ≤ 0.86 W each. Words fade and rise 12 px over 5 f; glow blur 12 at 55 %. **Exit:** none, holds to the end.
**Flow prompt text:** "Under the speaker's chin: {{SMALL WORDS}} in small white capitals, then {{BIG WORDS}} huge in glowing {{ACCENT}} capitals."

### M1 · WINDOW DRIFT — M low (extension in the same grammar, not measured)
**What it is:** in a page scene longer than 2 s, the crop inside the window drifts up to 1.05x over the shot. Reset at every cut.

---

## PART 3 — RECOMMENDED COMBINATIONS
| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 | W1 / W3 / P1 on B-roll, L1 for a UI shot, W2 on a growth line | T2 |
| Single talking head | T1 | C1 under the chin, W2 and W1 on a split top lane | T2 |
| B-roll only | L1 + C2 | W3, P1, W2 | C1 with key word |
| Still image | C1 + W2 on the poster | none | none |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
