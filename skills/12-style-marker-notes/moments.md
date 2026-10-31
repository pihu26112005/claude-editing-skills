# moments.md — Marker Notes: Style Bible + Moment Library

This file is the single source of truth for the "Marker Notes" style. Part 1 is the style bible (palette, shapes, type, motion, footage rules, safe zones). Part 2 is the moment library: 12 reusable moves, each with an exact spec, measured on a 540x960, 30 fps reference reel (303 frames, no audio) or written as an extension in the same grammar. Part 3 gives starting combinations. The reference's own words, topic and B-roll are not part of the style and appear nowhere in this file as defaults.

**The look in one line:** a creator-app look on the user's untouched footage: a yellow felt-tip marker band over a keyword, word-by-word captions with a yellow pill that jumps from word to word, a white to-do card that ticks off steps, and a cream "camera roll" page that rises to hold the footage in rounded cards.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, content, anchor, side…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its {{…}} placeholders.

Units: W, H, f (frames at 30 fps; keep seconds at other rates: s = f / 30). Reference values in brackets are for 1080x1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Marker yellow | #FEE059 | keyword band, active-word pill, tick fill, card dot (at 60 % alpha), whole-chunk pill |
| Ink | #1E1D1D | band keyword, pill text, card title, card items, checkbox stroke (active) |
| Caption white | #FFFFFF | inactive caption words on footage |
| Card white | #FFFFFF | to-do card, step chip |
| Card label grey | #929292 | small tracked label on the card |
| Card line grey | #E6E6E6 | card divider, placeholder row lines |
| Checkbox grey | #A9A9A9 | inactive checkbox stroke |
| Done grey | #555555 | struck-through item text and strike line |
| Page cream | #F6F5EF | camera-roll page |
| Page ink | #141414 | page label, captions on the page, pill text on the page |
| Marker streak | #B9A04A | two faint streak lines inside the band (50 % alpha) |

Brand-swap rule: marker yellow is the identity of the style. Replace it only with a colour the user supplied, and keep ink-on-yellow contrast at 4.5:1 or better. Never ask the user about colour. No other accent colours exist.

### 1.2 Containers and shapes

| Element | Geometry (fractions of W/H) [1080x1920] | Notes |
|---|---|---|
| Marker band (T1) | x 0.093W–0.904W [100–976], y 0.129H–0.221H [248–424], centre y 0.175H [336] | ragged ends, layered strokes, no outline |
| Marker tag (T2) | height 0.052H [100], width = text + 0.12W, ✎ anchor | same stroke grammar, smaller |
| Caption pill (C1) | height 0.050H [96], radius 0.015W [16], text-to-edge padding 0.017W [18] | sits on the active word only |
| To-do card (L1) | x 0.087W–0.911W [94–984], y 0.075H–0.402H [144–772], radius 0.033W [36] | white, soft shadow (below) |
| Compact card (L3) | width 0.74W [799], height 0.200H [384], radius 0.033W [36] | ✎ x side, ✎ y band |
| Step chip (L4) | width 0.62W [670], height 0.062H [119], radius 0.031H of full pill | white, one row |
| Page sheet (P1) | full frame, top corners radius 0.05W [54] while rising | colour #F6F5EF, no texture |
| Camera-roll main card | x 0.037W–0.648W [40–700], y 0.109H–0.724H [210–1390] (0.611W x 0.615H, 9:16) | radius 0.041W [44], no border, no shadow |
| Camera-roll thumb 1 | x 0.667W–0.963W [720–1040], y 0.109H–0.411H [210–790] | radius 0.041W [44] |
| Camera-roll thumb 2 | x 0.667W–0.963W [720–1040], y 0.422H–0.724H [810–1390] | gap to thumb 1: 0.010H [20] |
| Page label | x 0.057W [62], vertical centre 0.066H [126] | ✎ user word or omitted |

Shadows: card and chip get one soft shadow, rgba(0,0,0,0.18), blur 0.03W [32], offset y 0.006H [12] (design decision, consistent with the flat look measured). Pill, band, camera-roll cards and page have none. Caption white text on footage gets rgba(0,0,0,0.35), blur 0.008W [9], offset y 0.002H [4]; raise alpha to 0.55 when the footage behind the caption zone has mean luminance above 0.62.

Cover-fit: every footage card is a cover-fit crop of the source at the card's aspect, with crop anchor ✎ (default: face centre, else subject centre, else frame centre). Crop boxes use sub-pixel floats. Never letterbox inside a card.

### 1.3 Layouts

| Layout | Contents | Regions |
|---|---|---|
| FULL | untouched footage full frame, overlays on top | face zone free; band zone top; caption zone 0.675H–0.724H |
| CARD-OVER | FULL + to-do card or chip | card sits in a face-free band (see L1, L3) |
| ROLL | cream page + label + main card + two thumbs + caption zone on the page | geometry in 1.2; caption centre y 0.800H [1536] |

Non-9:16 canvases: build the 9:16 layout at full canvas height, centred, and fill the side areas with page cream (ROLL) or with the untouched footage (FULL, overlays inside the central 9:16 area).

### 1.4 Typography

Set every size by **cap height or ascender height**, not by nominal font size, so any fallback font matches. Measure the text with the real font, then scale.

| Use | Look | Preferred free font | Fallbacks | Target height | Size guide |
|---|---|---|---|---|---|
| Band keyword | heavy, tight, near-black, soft shadow, as written (no case change) | Inter ExtraBold 800 | Poppins Bold, Montserrat ExtraBold, Liberation Sans Bold | ascender height 0.059H [114] | 0.140W [151] |
| Caption | medium, no tracking, centred, white or ink | Inter Medium 500 | DM Sans Medium, Poppins Medium, Liberation Sans | cap height 0.028H [54] | 0.072W [78] |
| Card label | tiny, ALL CAPS, tracking 0.14 em, #929292 | Inter Medium 500 | Poppins Medium | cap height 0.010H [19] | 0.026W [28] |
| Card title | heavy, #1E1D1D | Inter ExtraBold 800 | Poppins Bold, Liberation Sans Bold | cap height 0.032H [62] | 0.080W [86] |
| Card item | medium, #1E1D1D | Inter Medium 500 | Poppins Medium, Liberation Sans | ascender height 0.025H [48] | 0.060W [65] |
| Page label | semibold, page ink | Inter SemiBold 600 | Poppins SemiBold, Liberation Sans Bold | ascender height 0.023H [44] | 0.050W [54] |
| Tag text | heavy, ink | Inter ExtraBold 800 | Poppins Bold | ascender height 0.032H [61] | 0.072W [78] |
| Chip text | medium, ink | Inter Medium 500 | Poppins Medium | ascender height 0.022H [42] | 0.052W [56] |

Download Inter from the Google Fonts GitHub repo (`ofl/inter`) when missing. If there is no network, use the fallbacks and scale by height. Every glyph on screen comes from the user's own words. Label text on the card and page is a user word or is omitted (see T1, L1, P1).

### 1.5 Motion language

| Family | Easing | Typical duration |
|---|---|---|
| Wipes and rises (band, tag, sheet) | easeOutCubic (band), easeOutQuad (sheet), starts fast, lands soft | band 9 f (0.30 s), sheet 10 f (0.33 s) |
| Appearances (card, chip, thumbs, label) | linear alpha + easeOutCubic 8–9 px settle upward | 4–7 f (0.13–0.23 s) |
| Word pop (captions) | linear alpha | 2 f (0.07 s) |
| Tick | linear alpha fill | 6 f (0.20 s) |
| Exits | linear fade, or sheet lowers with easeInQuad | 4 f (0.13 s), sheet 8 f |

Never: bounce, overshoot, spring, tilt, rotation of footage, blur, glow, particles, shake, zoom punch-ins on footage, hard flashes. All curves are continuous. Hold times (measured): band 3.9 s, card 3.2 s, closing page 2.9 s. A visible change lands every 1.5–3 s; captions supply the constant motion.

### 1.6 What may happen to the user's footage

| Allowed | Limits |
|---|---|
| Untouched full frame under overlays | always the default |
| Cover-fit crop and scale into rounded cards (ROLL main card, thumbs) | the primary window is always the live current shot, in sync with the audio |
| Cover with overlays: band, tag, card, chip, sheet | the face is never covered, cut or blurred (1.7) |
| Cream sheet fully covers the frame while rising or lowering | total full-frame cover 0.35 s or less per rise, only while live footage returns in the main card |
| Thumbs show the user's other footage | a still frame, a silent loop of 1.5 s or less (B-roll only, never a speaking face), or another crop of the same shot |

Forbidden: filters or grading, blur, speed changes, freeze of the primary window, trimming, reordering, replacing people or backgrounds, generated footage of any kind, mirroring.

### 1.7 Safe zones

| Zone | Rule |
|---|---|
| Face box | detected per scene; add 0.02 margin each side; no band, tag, card, chip, sheet edge or caption may touch it while speaking |
| Caption zone | centre y 0.700H [1344] on footage, 0.800H [1536] on the page; width up to 0.62W; if the face box bottom is below 0.66H, move the footage caption centre to 0.84H |
| Free band for cards | the largest horizontal band of the frame that holds no face and no caption zone, with 0.01H gap to both |
| Footage text (signs, UI, packaging) | do not cover legible footage text longer than 0.5 s when a free area exists |
| Frame edge | all graphics stay at least 0.03W from the left/right edge, except the band and the sheet |

Priority on collision: face > caption > card/chip > band/tag.

---

## PART 2 — MOMENT LIBRARY

Families: **C** captions · **T** marker title and tags · **L** to-do card and list · **P** page and camera roll.
Energy: E1 calm · E2 medium · E3 strong. **Signature** moments appear in every output (SKILL.md 4, step 5).

### C1 · WORD-PILL CAPTIONS — C · E1 (signature, always on)
**What it is:** each caption chunk builds word by word. A word appears at the moment it is spoken, with a yellow pill under it. When the next word arrives, the pill leaves and the word stays, white. The chunk fades out after its last word.
**Use when:** always, for every spoken or written line. **Avoid when:** never skip it. If the video has no speech, spread the user's text across the video and break at cuts.
**Text (✎):** the user's exact words, chunks of 2–4 words, 24 characters or fewer, split at punctuation, never ending on an article or preposition, at most 1 emphasis word per chunk (the active pill is the emphasis; no extra bold or colour).
**Geometry / Graphics:** chunk layout is computed once for the full chunk and centred at x 0.5W; words keep their final positions while they appear. Pill, type and zone per 1.2, 1.4, 1.7. Footage state: white words + shadow, pill text #1E1D1D. Page state (ROLL): words #141414, no shadow, same pill.
**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| word start | word + pill | alpha | 0 → 1 over 2 f (measured: 62 % at f+0, full at f+1) | linear |
| word end | pill | alpha | 1 → 0 over 1–2 f (measured) | linear |
| last word end + 1 f | whole chunk | alpha | 1 → 0 over 3 f | linear |
| next chunk | first word | start | at least 3 f after the previous chunk's end (measured gap 4–6 f) | n/a |

Word timing follows speech: word start = the spoken start, pill held for the word's spoken length (measured 3–12 f).
**Footage / plate behaviour:** none; footage untouched.
**Captions during it:** this is the caption system. Zone 0.675H–0.724H on footage, 0.800H centre on the page. Never over a face.
**Exit:** chunk fade as above.
**Build notes:** pre-render each chunk's layout at 2x (words, pill rectangles with radius 0.015W) and composite per frame with alpha; pill rectangles are word bbox plus 0.017W per side, 0.050H tall, centred on the cap-height line; measure widths with the real font.
**Flow prompt text:** "The spoken line appears as short word-by-word captions in the lower middle of the frame. Each word fades in the instant it is spoken, sitting on a small rounded yellow label with dark letters; when the next word arrives the label leaves and the earlier word stays in plain white letters with a soft shadow. After the last word the whole line fades away. Allowed words only: {{CAPTION_LINES_WITH_TIMES}}."
**Still-image state:** one chunk fully built, last word on a pill, below the subject.

### C2 · WHOLE-CHUNK PILL — C · E2 (extension in the same grammar)
**What it is:** the payoff or call-to-action chunk sits on one yellow pill as a single block instead of word by word.
**Use when:** the last line of the video, a slogan, a number or time phrase that deserves weight. **Avoid when:** more than once per video, chunks longer than 4 words.
**Text (✎):** the final chunk, 4 words or fewer, 24 characters or fewer.
**Geometry / Graphics:** one pill the full chunk width plus 0.017W per side, 0.050H tall, same radius; ink text #1E1D1D (footage) or #141414 (page).
**Motion:**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–3 | pill + text | alpha | 0 → 1 | linear |
| 0–6 | pill + text | y offset | +0.008H → 0 | easeOutCubic |
| speech end + 12 | pill + text | alpha | 1 → 0 over 4 f | linear |

**Footage / plate behaviour:** untouched.
**Captions during it:** this is the caption.
**Exit:** fade 4 f.
**Build notes:** reuse C1 pill drawing with one rectangle.
**Flow prompt text:** "For the last line, all words appear together at the same moment on one rounded yellow label with dark letters, rising slightly into place, and fade out shortly after the person finishes speaking. Allowed words only: {{FINAL_LINE}}."
**Still-image state:** single pill under the subject carrying the user's text.

### T1 · MARKER KEYWORD BAND — T · E3 (signature opener)
**What it is:** a thick yellow felt-tip stroke wipes left to right above the subject and carries the video's keyword in heavy near-black type.
**Use when:** opening line, theme word, first 0.5 s. **Avoid when:** the area above the head is not free (see anchor rule) or the video is shorter than 2.5 s.
**Text (✎):** one keyword from the user's text, 10 characters or fewer, as the user wrote it (no case change). Choose the theme noun or verb of the opening line; if none fits, the first content word.
**Geometry / Graphics:** band x 0.093W–0.904W [100–976], height 0.092H [176], centre y 0.175H [336] (✎ anchor). Build from 4 stacked strokes of #FEE059: base stroke alpha 1; three strokes at alpha 0.9 with top and bottom edges offset by ±0.004H and right ends offset by −0.006W, +0.003W and −0.002W; left end stepped in 3 notches of 0.004W; two streak lines (#B9A04A, alpha 0.5, 0.002H thick, from x 0.093W to 0.30W at y 0.175H ±0.003H). Fixed random seed. Keyword centred at x 0.5W, size per 1.4, colour #1E1D1D, soft shadow rgba(0,0,0,0.25), blur 0.012W, offset y 0.004H. Band width rule: 0.81W; if the keyword is wider than 0.55W, band width = keyword + 0.20W (max 0.94W).
Anchor rule: the whole band sits at least 0.01H above the hair line of the head; if the head top is above 0.20H, use the lower anchor: centre y 0.58H with the caption zone moved to 0.84H, or use T2 instead.
**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–9 | band | right edge | 0.093W → 0.904W (left edge fixed) | easeOutCubic (measured: 30 %, 53 %, 70 %, 83 %, 92 %, 97 %, 99 % at f1–f7) |
| 1–5 | band | height | 0.081H → 0.092H, centre fixed | easeOutCubic |
| 3–9 | keyword | alpha | 0 → 1 | linear |
| 9 → hold | all | hold | still; hold 2.5–4.2 s (measured 3.9 s) | n/a |

**Footage / plate behaviour:** footage untouched and live.
**Captions during it:** C1 starts on the first spoken word (measured f3); caption zone is clear of the band.
**Exit:** alpha 1 → 0 over 4 f, linear, overlapping the next moment's entrance (measured: band and card cross-fade over f121–f125). Alone: same 4 f fade.
**Build notes:** draw strokes at 2x with a fixed seed, downscale; wipe by clipping the stroke group to x ≤ current right edge; keep ragged right end during the wipe.
**Flow prompt text:** "In the first third of a second, a thick yellow felt-tip marker stroke sweeps from left to right across the upper part of the frame, above the person's head, with slightly rough uneven edges and a few faint streaks. As it settles, the word '{{KEYWORD}}' fades onto the stroke in heavy, rounded, near-black letters with a soft shadow. The stroke stays still until {{END_TIME}} and then fades out. The person and background are not touched."
**Still-image state:** the band settled at the top third, keyword on it.

### T2 · MARKER TAG — T · E2 (extension in the same grammar)
**What it is:** a small marker stroke with 1–3 words, used as a beat on a cut or a mid-video keyword.
**Use when:** person → B-roll cut, B-roll → B-roll cut, a keyword or contrast word ("but", "isn't", "instead"), a number or time phrase. **Avoid when:** within 0.5 s of another big move; more than 2 tags in a row.
**Text (✎):** 1–3 user words, 18 characters or fewer.
**Geometry / Graphics:** height 0.052H [100]; width = text + 0.06W each side; same 4-stroke build as T1 at tag scale (streak lines omitted); text size per 1.4 (tag); default anchor top-left at x 0.06W, y 0.10H; alternate anchors: top-right, or centred above the caption zone at y 0.60H. Never over a face.
**Motion:**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut + 3 → +9 | tag | right edge | left edge → full width | easeOutCubic |
| +3 → +9 | text | alpha | 0 → 1 | linear |
| hold | tag | hold | 0.8–1.6 s | n/a |
| end → +4 | tag | alpha | 1 → 0 | linear |

**Footage / plate behaviour:** untouched.
**Captions during it:** C1 as normal; gap of 0.01H to the caption zone.
**Exit:** fade 4 f.
**Build notes:** reuse T1 stroke code with a scale factor 0.55.
**Flow prompt text:** "A small yellow felt-tip marker stroke wipes in from the left near the {{POSITION}} of the frame, 3 frames after the cut, carrying the words '{{WORDS}}' in heavy near-black letters; it holds for about a second and fades out. Nothing else on the picture changes."
**Still-image state:** the tag settled in its anchor.

### L1 · TO-DO CARD — L · E2 (signature middle)
**What it is:** a white rounded card lands with a small label, a one-word title and a to-do row. The row gets ticked in yellow and struck through when the matching words have been spoken. Empty placeholder rows hint at more to come.
**Use when:** list or steps, an action phrase ("do this", "pay", "start"), a rule or habit, any line that can be a task. **Avoid when:** the free band is shorter than 0.30H (use L3), within 1 s of another big move.
**Text (✎):** title = one user word, 10 characters or fewer, the key verb or noun of the line. Row 1 = 1–3 consecutive user words that complete a step. Label (small caps) = a user word, or omitted. Never print words the user did not write.
**Geometry / Graphics:** card box per 1.2 at the reference anchor. Offsets from the card's top-left (x0 = 0.087W, y0 = 0.075H):

| Element | Offset | Spec |
|---|---|---|
| Label | x +0.052W, baseline +0.035H [68] | 0.026W caps, tracking 0.14 em, #929292 |
| Dot | centre x card right −0.061W, y +0.030H | diameter 0.020W [22], #FEE059 at 60 % |
| Title | x +0.052W, baseline +0.091H [174] | 0.080W heavy, #1E1D1D |
| Divider | y +0.115H [220] | 0.002H [4], #E6E6E6, x +0.052W to right −0.052W |
| Row 1 | centre +0.146H [280] | checkbox 0.050W [54] at x +0.052W, radius 0.013W [14], stroke 0.005W [5] |
| Row 2 | centre +0.193H [370] | grey checkbox + placeholder line #E6E6E6 from x +0.122W |
| Row 3 | centre +0.239H [458] | same as row 2 |
| Item text | x +0.122W [132] (after the checkbox, 0.020W gap) | 0.060W medium, #1E1D1D |

Card bottom keeps 0.065H of empty white under row 3 (measured). Free-band anchor (✎): default top (y0 0.075H) only if the face box top is below 0.42H; otherwise slide the card down into the lower free band, or use L3. The card never overlaps the face box or the caption zone: if the lower band is used, shift the footage caption zone to the nearest free side of the card with 0.01H gap.
**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–4 | card | alpha | 0 → 1 (measured 4 f ramp) | linear |
| 0–7 | card | y offset | +0.009H → 0 (measured 8–9 px at 960) | easeOutCubic |
| tick −0 | row 1 | checkbox fill | 0 → 1 over 6 f (measured f148–f154) | linear |
| tick +0 → +6 | row 1 text | colour | #1E1D1D → #555555 | linear |
| tick +0 → +6 | row 1 strike | length | 0 → full text width, 0.004H thick | linear |
| hold | card | hold | 2.4–4.0 s total (measured 3.2 s), tick lands 0.8–1.0 s after entrance | n/a |

Tick time (✎): at the end of the spoken words of row 1, plus 0.1 s. Tick mark: #1E1D1D, 0.006W stroke, inside the yellow-filled box.
**Footage / plate behaviour:** footage untouched and live.
**Captions during it:** C1 stays in its zone; the card never overlaps it.
**Exit:** if followed by a page (P1), the page rises over it. Otherwise alpha 1 → 0 over 4 f, y offset 0 → −0.006H, linear/easeInCubic.
**Build notes:** draw card, rows and checkboxes at 2x; build the title/label/row text with measured widths; the strike line grows from the left edge of the text.
**Flow prompt text:** "A clean white rounded notes card fades in near the {{POSITION}} of the frame and settles upward by a tiny amount. It has a tiny grey capital label, a bold one-word title '{{TITLE}}', a thin divider, and a first row reading '{{ITEM}}' with an empty checkbox, plus two empty rows with faint lines. When the person finishes saying those words, the checkbox fills yellow with a dark tick and the row text turns grey with a line through it. The card never covers the person's face."
**Still-image state:** card settled with row 1 ticked, in the free band.

### L2 · CARD ROW ADD — L · E1 (extension in the same grammar)
**What it is:** while L1 is up, rows 2 and 3 fill with the next steps and get ticked in turn.
**Use when:** a list of 2–3 actions, a sequence ("first… then… finally"). **Avoid when:** the list has more than 3 items (roll the card: row 1 exits, rows move up one position, a new row enters).
**Text (✎):** 1–3 user words per row, in speaking order.
**Geometry / Graphics:** rows per L1 table. Text starts at x +0.122W.
**Motion:**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| row start | row text | alpha, y | 0 → 1 over 5 f, +0.006H → 0 | linear, easeOutCubic |
| row start | checkbox | stroke | #A9A9A9 → #1E1D1D over 3 f | linear |
| row end + 3 | checkbox | fill + strike | as L1 tick | linear |
| row start | placeholder line | alpha | 1 → 0 over 3 f | linear |

**Footage / plate behaviour:** untouched.
**Captions during it:** C1 as normal.
**Exit:** with the card (L1).
**Build notes:** state machine per row (empty, active, done); hold row text during fades.
**Flow prompt text:** "As the person says each next step, its row on the notes card fills with those words, the empty box turns dark-outlined, and when they finish that step the box fills yellow with a tick and the words turn grey with a line through them. Steps: {{STEP_LIST_WITH_TIMES}}."
**Still-image state:** card with all rows ticked.

### L3 · COMPACT CARD — L · E2 (extension in the same grammar)
**What it is:** a smaller card with a title and one row, for frames where the face sits high or the free band is short.
**Use when:** face box top above 0.42H, short free band (0.18H–0.30H), B-roll with a clear lower area. **Avoid when:** no free band of 0.20H exists (then use L4).
**Text (✎):** same as L1, no placeholder rows, label omitted.
**Geometry / Graphics:** width 0.74W [799], height 0.200H [384]; contents use the L1 type sizes with these offsets from the card's top-left: title baseline +0.062H, divider +0.086H, row 1 centre +0.124H. ✎ x anchor: centred, left (x 0.04W) or right (right edge 0.96W). ✎ y anchor: top of the free band plus 0.01H.
**Motion:** same table as L1 (4 f alpha, 7 f settle, 6 f tick).
**Footage / plate behaviour:** untouched.
**Captions during it:** C1 zone must not overlap; move to 0.84H when the card is in the lower band.
**Exit:** 4 f fade.
**Build notes:** reuse L1 drawing with a compact flag.
**Flow prompt text:** "A smaller white rounded notes card fades in {{POSITION}}, below the person's face, with a bold one-word title '{{TITLE}}' and one row '{{ITEM}}'; when the words are spoken the box fills yellow with a tick and the row turns grey with a line through it."
**Still-image state:** compact card ticked, in the free band.

### L4 · STEP CHIP — L · E2 (extension in the same grammar)
**What it is:** a one-row white chip with a checkbox and 1–3 words that ticks, over B-roll or any short shot.
**Use when:** a step or action word on a short shot, a list item inside a B-roll cut, numbers or amounts ("3 steps"). **Avoid when:** the shot already carries a tag or card.
**Text (✎):** 1–3 user words, 22 characters or fewer; digits only if the user wrote them.
**Geometry / Graphics:** width 0.62W [670] (or text + 0.16W), height 0.062H [119], fully rounded ends; checkbox 0.040W at x +0.045W; text 0.052W medium. ✎ anchor: centred, top band y 0.12H (default) or lower band y 0.60H; never over a face or the caption zone.
**Motion:**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| cut + 3 → +7 | chip | alpha | 0 → 1 | linear |
| cut + 3 → +10 | chip | y offset | +0.009H → 0 | easeOutCubic |
| +0.4 s → +6 f | checkbox | fill + strike | as L1 tick | linear |
| hold | chip | hold | up to 1.5 s | n/a |
| end → +4 | chip | alpha | 1 → 0 | linear |

**Footage / plate behaviour:** untouched.
**Captions during it:** C1 as normal.
**Exit:** fade 4 f.
**Build notes:** same drawing helpers as L1.
**Flow prompt text:** "A small white pill-shaped chip fades in near the {{POSITION}} of the frame, with a checkbox and the words '{{WORDS}}'; after a moment the checkbox fills yellow with a dark tick and the words turn grey with a line through them; the chip fades out after about a second and a half."
**Still-image state:** chip settled, ticked.

### P1 · CAMERA-ROLL PAGE — P · E3 (signature closer)
**What it is:** a cream sheet with rounded top corners rises from the bottom edge and covers the frame; the live footage reappears inside a rounded main card with two smaller rounded thumbs beside it, a small label on top, and the captions below on the cream.
**Use when:** the last 25–35 % of the video, the payoff or call-to-action line, the final cut. **Avoid when:** the page would start within 3 f of a cut or inside a caption chunk (start on a chunk boundary), or fewer than 1.8 s remain.
**Text (✎):** page label = one user word (the topic word), or omitted; captions per C1/C2 in page state.
**Geometry / Graphics:** ROLL per 1.2. Main card = live current shot, cover-fit, crop anchor ✎ (the face box must sit inside the crop with 0.04 margin). Thumbs ✎ = the user's other footage (see 1.6): thumb 1 = the nearest B-roll or a still of the previous shot, thumb 2 = the next nearest; never a speaking face in motion. Sheet colour #F6F5EF.
**Motion:**

| t (f @30) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–10 | sheet | top y | 1.00H → 0 (measured: 80 %, 61 %, 45 % at f1–f3) | easeOutQuad |
| 0–10 | sheet | side inset | 0.045W → 0 (rounded corners 0.05W) | linear |
| 4–10 | label | alpha | 0 → 1 | linear |
| 4–10 | main card | alpha | 0 → 1 (measured 6 f ramp) | linear |
| 4–10 | main card | y offset | +0.003H → 0 | easeOutCubic |
| 6–13 | thumb 1 | alpha | 0 → 1, 7 f | linear |
| 6–13 | thumb 1 | y offset | +0.008H → 0 | easeOutCubic |
| 8–15 | thumb 2 | alpha | 0 → 1, 7 f; stagger 2 f | linear |
| 8–15 | thumb 2 | y offset | +0.008H → 0 | easeOutCubic |
| 15 → end | all | hold | 1.8 s or more (measured 2.9 s) | n/a |

t0 (✎) = a chunk boundary or a footage cut + 3 f minimum.
**Footage / plate behaviour:** the primary window is the live current shot, always in sync; cuts on the page switch the main card hard (P4). The sheet covers the full frame for about 0.3 s only.
**Captions during it:** the chunk that starts after the sheet passes 0.72H renders in page state at centre y 0.800H. A chunk already showing when the sheet reaches the caption zone finishes first: start P1 at a chunk boundary.
**Exit:** none (closer, holds to the end). If the story must return to full frame, use P3.
**Build notes:** draw the sheet as a rounded rectangle with supersampling; composite footage cards with sub-pixel cover-fit crops; label and captions on top.
**Flow prompt text:** "Starting {{START_TIME}}, a smooth off-white sheet with rounded top corners rises from the bottom of the frame in about a third of a second and covers it. The same live video then appears inside a tall rounded card on the left, with two smaller rounded cards stacked on its right showing {{OTHER_FOOTAGE_DESCRIPTION}}, appearing one after another a moment apart. A small bold label '{{LABEL}}' sits above the top left; the spoken words appear in dark letters below the cards, word by word, with the current word on a small yellow rounded label. The video and audio keep playing without any change."
**Still-image state:** page settled with main card, two thumbs, label and one caption chunk.

### P2 · ROLL FROM STILLS — P · E2 (extension in the same grammar)
**What it is:** the ROLL layout when the user has a single shot: the thumbs are other crops or stills of the same footage.
**Use when:** single talking head, one continuous shot, no B-roll. **Avoid when:** B-roll exists (use P1).
**Text (✎):** as P1.
**Geometry / Graphics:** as P1. Thumb 1 = still of the current shot taken at least 1.5 s earlier (or a different moment); thumb 2 = a detail crop (hands, object, background) of the current shot at the thumb's aspect. Crop anchors ✎. No thumb may show the speaker's face in motion; stills are allowed.
**Motion:** same as P1.
**Footage / plate behaviour:** the main card is live; thumbs are still frames only.
**Captions during it:** as P1.
**Exit:** none.
**Build notes:** extract thumbs with a single-frame seek; pre-render once.
**Flow prompt text:** "As in the page closer, but the two smaller rounded cards show still frames and a close-up crop taken from the same video, not new footage."
**Still-image state:** as P1 with two crops of the photo.

### P3 · PAGE LOWER — P · E2 (extension in the same grammar)
**What it is:** the reverse of P1: the page contents fade, the sheet drops, and full-frame live footage is back.
**Use when:** the page is used mid-video and the story returns to a full frame (talking head after a list). **Avoid when:** the video ends on the page.
**Text (✎):** none.
**Geometry / Graphics:** as P1, reversed.
**Motion:**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–4 | label, thumbs | alpha | 1 → 0 | linear |
| 0–4 | main card | alpha | 1 → 0 | linear |
| 2–10 | sheet | top y | 0 → 1.00H | easeInQuad |

**Footage / plate behaviour:** the live shot under the sheet is the same shot as the main card; it plays continuously.
**Captions during it:** switch to footage state at the chunk boundary after the sheet passes 0.72H.
**Exit:** none.
**Build notes:** render sheet over live full-frame footage.
**Flow prompt text:** "The off-white page lowers out of the frame in a quarter of a second while its cards fade, and the full-frame live video is back, unchanged."
**Still-image state:** not used.

### P4 · ROLL SWAP — P · E2 (extension in the same grammar)
**What it is:** the camera-roll thumbs refresh on a footage cut or on a long static hold, so the page keeps moving.
**Use when:** a footage cut while the page is up, or a page held longer than 2.8 s. **Avoid when:** within 0.5 s of another big move.
**Text (✎):** none.
**Geometry / Graphics:** ROLL geometry. On a cut the main card switches hard with the footage; the shot that just ended becomes thumb 1 (still), thumb 1 moves to thumb 2, the old thumb 2 leaves.
**Motion:**

| t (f) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0–6 | thumb 1 | content | cross-fade old → new | linear |
| 2–8 | thumb 2 | content | cross-fade old → new, stagger 2 f | linear |

**Footage / plate behaviour:** the main card is live; hard switch only on the footage cut.
**Captions during it:** unchanged.
**Exit:** none.
**Build notes:** pre-extract thumb stills; cross-fade in alpha.
**Flow prompt text:** "On the cut, the two small cards beside the main video quietly change to other stills from the same material, one after the other, while the main card keeps playing."
**Still-image state:** not used.

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | T1 at 0 s | T2 on the person → B-roll cut; L1 or L2 at the list or action line; L4 on a B-roll step | P1 at the last chunk boundary, C2 on the payoff |
| Single talking head | T1 | L1 (L3 if the face is high); T2 on a contrast word | P2 with C2 |
| B-roll only | T1 on shot 1 | T2 on cuts; L4 on steps | P1, P4 on cuts |
| Long video (over 25 s) | T1 | alternate L1/L2 and T2 every 6–8 s; P1 + P3 once mid-video, P1 at the end | P1 |
| Very short (under 5 s) | T1 (hold 1.5 s) | L4 | P1 or P2 |
| Still image + text | T1 over the image | none | settled P1 layout (main card = the image, two crops) or full-bleed image + C2 |

Each video gets its own selection based on its own hook points. Never paste a row blindly.
