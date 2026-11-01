# moments.md — Ring Chip Script: Style Bible + Moment Library

This file is the single source of truth for the Ring Chip Script caption style. Part 1 is the style bible (palette, lanes, type, motion, footage rules, safe zones). Part 2 is the moment library. Values marked "measured" come from a 360x640, 32 fps, 7.25 s reference reel of one talking head with no cuts; everything marked "(design, not measured)" is tuned on a 720x1280, 24 fps demo clip. Part 3 gives starting combinations. SKILL.md tells Claude how to pick and place moments.

**The look in one line:** the footage stays untouched while each phrase becomes one low line of small hand-lettered white words with a soft dark shadow; the key word of the line sits on a rounded solid chip in bold marker lettering, and one other word gets a loose hand-drawn ring.

How to use it:
1. Pick moments by ID (SKILL.md steps 4–5).
2. Copy the moment's full spec unchanged into the edit plan.
3. Change only the fields marked ✎ (time, text, lane, accent colours…). Everything else is the style.
4. Final video → build from the spec. Google Flow master prompt → use each moment's **Flow prompt text**, filling its {{…}} placeholders.

Units: W, H, seconds (s), f = frames at the source fps. Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| Chip fill | #F3D946 (measured, warm yellow) | Rounded chip behind the key word |
| Chip text | #111111 (measured, near black) | Key word on the chip |
| Ring stroke | #DF5C74 (measured, coral pink) | Hand-drawn ring around the echo word |
| Small words | #FFFFFF | All other words |
| Shadow | #000000 at 95 % blur 4 px, offset 3 px down, plus 3 px dark stroke | Keeps white words readable on bright footage (design, not measured) |

Brand-swap rule: chip fill and ring stroke are parameters ✎ (two different hues; chip text stays dark and the ring must read on both light and dark footage). White words and shadow never change. The demo uses a sky-cyan chip (#4CD3F2, text #082236) and a violet ring (#A06BFF).

### 1.2 Containers / shapes

- Footage: always full frame, 100 % of W and H, untouched. No cards, bars, borders, blur plates or colour overlays.
- Chip: rounded rectangle, corner radius 0.36 × chip height, solid fill, no border, no shadow. Chip height 0.039H measured [75 px]; demo 112 px at 720 wide (0.0875H) because the demo words are larger. Horizontal padding 22 px each side.
- Ring: open hand-drawn ellipse, 1.1 turns, a little wobbly, stroke 8 px (demo) [measured ≈ 2.5 px at 360 wide], extra soft dark shadow under the stroke. Encloses one word with ≈ 22 px horizontal and 10 px vertical air; sits slightly low so its tail loops under the word. The ring never touches the chip.

### 1.3 Layouts / lanes

One line per chunk, centred on x = 0.50W. Baseline y of the line:

| Lane | Baseline y | Use |
|---|---|---|
| Chest | 0.60H (reference 0.855H on a speaker framed to the waist; demo raised to clear the hands and phone) | Speaker shots: line stays below the face box (y > 0.40H) |
| Low | 0.80–0.90H (design) | B-roll with a clear lower area; pick the cleanest strip |
| Top | 0.14H (design) | B-roll with calm top area (wall, sky) |

Side margin ≥ 0.05W on every box including the ring. The whole line is shrunk uniformly if wider than 0.82W (demo: scale 0.64–1.0).

### 1.4 Typography

| Use | Look | Preferred free font | Fallbacks | Size |
|---|---|---|---|---|
| Small words | Slanted brush handwriting, mixed case as written, white | Gaegu Bold | Caveat, Gochi Hand | 70 px at 720 wide (≈ 0.097W); reference small caps height ≈ 0.025H |
| Key word | Bold marker handwriting, dark on the chip | Caveat Brush | Gochi Hand, Kalam Bold | 100 px at 720 wide (≈ 1.4 × small) |

Word gap 26 px. Line = small words and the chip word in reading order.

### 1.5 Motion language

| Element | Motion |
|---|---|
| Small word | fade 0 → 100 % over 0.12 s, ease-out cubic, rise 0.008H, at its spoken time; the whole line is laid out first so no word moves |
| Chip + key word | chip fades in and scales 0.85 → 1.0 over 0.18 s, ease-out cubic (no overshoot), at the key word's spoken time; word fades over 0.2 s |
| Ring | starts 0.18 s after the echo word appears; the stroke draws along its path over 0.32 s, ease-out cubic |
| Exit | whole chunk (chip, words, ring) fades out over 0.12 s |
| Never | bounce, overshoot, letter-by-letter typing, slides, wipes, glitch, shake, flashes, effects on cuts, rings around two words at once |

### 1.6 What may happen to the user's footage

Allowed: text, chip and ring overlays with their soft shadows. Nothing else: no mask, no cut-out, no zoom, crop change, blur, colour change, background swap or retime. The footage plays live and in sync.

### 1.7 Safe zones

- Face box (about x 0.34–0.66, y 0.15–0.40 on a front talking head) never receives visible text, chip or ring.
- All boxes (words, chip, ring) inside 0.05W side margins and 0.02H top.
- Two chunks are never visible on the same frame (windows disjoint including fade-out, assert in the build).
- Ring and chip are never on the same word and the ring never overlaps the chip.

---

## PART 2 — MOMENT LIBRARY

Family codes: C caption, K keyword, R ring, E end. Energy: low / medium / high.

### C1 · CHEST LINE — C low (measured)
**What it is:** the base line: 2–6 small hand-lettered white words building word by word in one centred line below the speaker's face.
**Use when:** speaker shot, phrase with no strong word. **Avoid when:** hands or a phone sit exactly on the lane and a cleaner strip exists (use C2).
**Text (✎):** 2–6 words, as written. **Geometry:** lane Chest (1.3), small words (1.4). **Motion:** 1.5 small word. **Exit:** fade 0.12 s.
**Footage behaviour:** untouched. **Captions during it:** this is the caption.
**Build notes:** pre-render each word as a sprite with shadow; lay the whole line out first.
**Flow prompt text:** "A small white handwritten line '{{LINE}}' fades in word by word below the speaker's face, with a soft dark shadow."
**Still-image state:** all words in.

### C2 · LOW LINE — C low (design, not measured)
**What it is:** C1 on B-roll, in the lower lane.
**Use when:** any B-roll shot. **Geometry:** lane Low, y 0.80–0.90H chosen from the shot's cleanest strip. **Motion/Exit:** as C1.
**Flow prompt text:** "Near the bottom of the frame, a small white handwritten line '{{LINE}}' fades in word by word."

### C3 · TOP LINE — C low (design, not measured)
**What it is:** C1 near the top on calm backgrounds. **Use when:** subject fills the lower half. **Geometry:** lane Top (0.14H). **Motion/Exit:** as C1.
**Flow prompt text:** "Near the top of the frame, a small white handwritten line '{{LINE}}' fades in word by word."

### K1 · CHIP KEYWORD — K medium (signature, measured)
**What it is:** one word of the line sits on a solid rounded chip in bold dark marker lettering while the rest stays small white handwriting.
**Use when:** the phrase has one strong word (noun, verb, number). **Avoid when:** two strong words compete (chip one, ring the other, see K2).
**Text (✎):** 1 key word, ≤ 12 characters ideal, as written; 1–5 small words before and after it.
**Geometry:** chip fill ✎ accent (1.1), height and padding 1.2; word 1.4.
**Motion:** chip 1.5 at the key word's spoken time; small words per 1.5. Chunk visible 0.65–1.7 s.
**Footage behaviour:** untouched. **Exit:** fade.
**Build notes:** draw the chip at 3× and downscale; chip text sits on the same baseline as the small words, the chip is centred on the key word's x-height.
**Flow prompt text:** "In the same line, the word '{{KEYWORD}}' appears on a solid {{ACCENT}} rounded label in bold dark handwriting, while '{{OTHER WORDS}}' stay small and white."

### R1 · RING ECHO — R medium (signature, measured)
**What it is:** a loose hand-drawn ring is drawn around one small word of the line.
**Use when:** a contrast, number, or the word that qualifies the chip word. **Avoid when:** the line is already crowded (more than 6 words) or the word is next to the line end with no margin.
**Text (✎):** the ringed word is one of the line's small words, never the chip word. ≤ 1 ring per chunk.
**Geometry:** ring 1.2, colour ✎ ring accent. **Motion:** ring 1.5; if the word's window leaves less than 0.5 s after the ring starts, pick an earlier word.
**Exit:** fades with the chunk.
**Flow prompt text:** "A loose hand-drawn {{RING COLOUR}} ring draws itself around the word '{{WORD}}'."

### K2 · CHIP AND RING — K high (measured: reference shows both in one line)
**What it is:** K1 plus R1 in the same chunk: one chip word and one ringed word, usually the chip after the ring or two words apart.
**Use when:** the phrase has a pair (action and object, first and last). **Limit:** ≤ 3 per 10 s.
**Flow prompt text:** "The word '{{KEYWORD}}' sits on a solid {{ACCENT}} label while a hand-drawn ring draws around '{{WORD}}' in the same line."

### K3 · SOLO CHIP — K high (design, not measured)
**What it is:** a one-word or two-word chunk where the chip word is the whole punchline. **Use when:** payoff, number, name. **Limit:** ≤ 1 per 6 s.
**Geometry:** lane any; chip as 1.2 at scale 1.0. **Motion/Exit:** as K1.
**Flow prompt text:** "One word '{{KEYWORD}}' pops onto a solid {{ACCENT}} label in bold handwriting and fades out."

### E1 · CLOSING CHIP — E medium (extension in the same grammar)
**What it is:** the last chunk as K1 (or K2), held to 0.1 s before the speech ends and never past the end of the shot or a head leaning into the lane.
**Flow prompt text:** "For the last line, the word '{{KEYWORD}}' sits on a solid {{ACCENT}} label and stays until the speech ends."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll → talking head | C1 + K1 | K2 on lists, C2 / K1 on B-roll, C3 on busy lower areas | E1 |
| Single talking head | K1 | K2, C1, K1 | E1 |
| B-roll only | C2 + K1 | C3, K3 | E1 |
| Still image | K1 settled | | |

Each video gets its own selection based on its own hook points. Never paste a row blindly.

### Tuned on the 10 s demo (720x1280, 24 fps)
Chip #4CD3F2 (text #082236), ring #A06BFF stroke 8 px, small words Gaegu Bold 70 px, key word Caveat Brush 100 px, chip height 112 px at scale 1, word gap 26 px, line cap 0.82W, shadows as 1.1, fade-in 0.12 s, chip 0.18 s, ring starts +0.18 s and draws 0.32 s, fade-out 0.12 s. Chunks (start–end, lane, chip word, ring word): 0.10–0.76 C1/K2 Chest (money, Saving); 1.10–1.80 K1 Chest (more.); 2.10–3.20 K2 Low 0.80H (yourself, first,); 3.25–4.85 K2 Low 0.84H (automate, investments,; scale 0.64); 4.95–6.55 K2 Low 0.90H (left., spend); 6.90–8.30 K2 Top 0.14H (year, one); 8.45–9.55 E1/K2 Chest (happens., watch; ended early because the speaker leans toward the camera at 9.6 s).
