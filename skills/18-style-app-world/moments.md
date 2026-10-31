# moments.md — App World: Style Bible + Moment Library

This file defines the **App World** style completely. SKILL.md decides *which* moments to use and *when*; this file defines *exactly what each moment looks like and how it moves*.

**The look in one line:** the video turns into a product demo. Clean app interface pieces float over untouched footage: a phone screen slides in beside the speaker, a frosted checklist ticks off steps, a white app dialog drops from the top and fills in, and on the big moment the room fades to a dark app screen while the speaker stays cut out in front of a live progress bar. Captions are bold white two-liners with one soft-pink word.

How to use it:
1. Pick moments by ID (SKILL.md, steps 4–5).
2. **Copy the moment's full spec unchanged** into the edit plan.
3. Change **only** the fields marked ✎ (time, text, which footage goes in a screen, side). Everything else (shapes, sizes, fonts, motion curves, durations, layer order) is the style.
4. For a **final video**, build from the spec. For a **Google Flow master prompt**, use each moment's **Flow prompt text** (plain words: no px, %, hex codes or font names), filling its `{{…}}` placeholders.

Units: `W` = frame width, `H` = frame height, `f` = frames at 30 fps (at other frame rates keep the **seconds**). Reference values in brackets are for 1080×1920.

---

## PART 1 — STYLE BIBLE

### 1.1 Palette

| Role | Hex | Used for |
|---|---|---|
| GLASS | `#2A2624` at 68 % over a blur of the footage (lighter washes out on bright shots) | frosted cards (checklist, phone body tint) |
| PAPER-UI | `#FFFFFF` | app dialogs, input fields |
| UI-INK | `#1C1A19` | text inside white UI |
| UI-MUTED | `#8E8A86` | secondary UI text, empty checkboxes, skeleton lines |
| PINK | `#F4A7B9` | the one accent: checked boxes, buttons, progress fill, the caption key word |
| PINK-DEEP | `#E8708F` | pressed button, progress bar end |
| NIGHT | `#1D1517` | the dark app screen of A4 |
| CAPTION | `#FFFFFF` | captions, with a soft dark shadow |

No other accent colour. Brand variant ✎: PINK may become one brand colour; everything else stays neutral.

### 1.2 Containers
- **Card:** rounded rectangle, radius 0.035 W [38 px], 1 px inner hairline `#FFFFFF` at 14 % on glass / `#E8E6E1` on white, soft shadow 0 / +0.012 H, blur 0.03 W, black 28 %.
- **Frosted glass:** the footage behind the card, Gaussian-blurred (radius 0.025 W) and darkened with GLASS. Never a flat grey.
- **Phone:** rounded rectangle 9:19.5, radius 0.045 W, black bezel 0.008 W, a small notch pill; the screen is a white or NIGHT app page.
- **Skeleton lines:** UI chrome that would need invented words is drawn as rounded grey bars (UI-MUTED at 35 %), never as fake text.

### 1.3 Typography

| Use | Look | Preferred font (free) | Fallbacks | Size |
|---|---|---|---|---|
| Caption | bold geometric sans, sentence case, two lines max | Inter Bold (wght 700) | Plus Jakarta Sans Bold, Arial Bold | 0.042 H [81 px] |
| Caption key word | same, PINK | same | same | same |
| Card title | small caps label, letter-spaced 0.12 em | Inter SemiBold | same | 0.016 H [31 px] |
| Card item / UI text | medium sans | Inter SemiBold (wght 600) | same | 0.022 H [42 px] (smaller reads poorly in shared GIFs and phone feeds) |
| Timer / counters | tabular monospace digits | JetBrains Mono SemiBold | IBM Plex Mono | 0.024 H [46 px] |
| Label caption (A6) | uppercase, letter-spaced 0.08 em, white→PINK gradient | Inter ExtraBold | same | 0.026 H [50 px] |

All words are the user's words. UI chrome without user words uses icons, numbers or skeleton bars.

### 1.4 Motion language
- **Arrive:** slide 0.04 H + fade, ease-out-cubic, 8–10 f; tiny overshoot allowed only on the phone (A1), 3 %.
- **Fill:** checkboxes pop PINK with a 6 f scale 70 → 110 → 100 %; progress bars fill linearly; typed text appears 2 letters per frame.
- **Leave:** fade + 0.02 H drift up, ease-in-quad, 6 f.
- **Dark-screen fade (A4):** background darkens over 10 f; the person stays.
- UI pieces never rotate, never bounce more than 3 %, never cover a face.

### 1.5 What may happen to the user's footage
- Default: footage stays full-frame and untouched; UI floats over it.
- A1 phone and A3 dialog may show **the user's own footage** (a still or a live inset of the current frame) inside their screens.
- A4 replaces the **background behind the person** with NIGHT, only with a clean person matte, max 2.5 s per use and 25 % of the video. Without a clean matte, use A4-CARD: shrink the footage into a rounded card on NIGHT instead.

### 1.6 Safe zones
- Face box: never covered by any card, caption or phone.
- Top zone (0.06–0.30 H): checklist and dialogs. Side zone (outer 0.30 W at chest height): phone. Bottom zone (0.72–0.86 H): captions.
- If the face is in the top zone, cards go in the bottom zone and captions move to 0.62 H.

---

## PART 2 — MOMENT LIBRARY

Family codes: **UI** (interface pieces), **CAP** (captions), **CUT** (scene treatment). Energy: ● low · ●● medium · ●●● high.

### A1 · PHONE MOCK-UP — UI ●●● (signature)
**What it is:** A phone slides in beside the speaker at chest height showing an app page made from the user's own footage.
**Use when:** a person shot where the line names a result, a profile, a product, "all you need is…".
**Text (✎):** title on the screen = 1–3 user words. Other rows = skeleton bars or numerals.
**Geometry:** phone 0.25 W wide, centred x 0.80 W (✎ side away from the face), centre y 0.52 H. Screen: white page; top a round avatar (still of the speaker), the title in UI-INK bold, a PINK pill button (no text, or one user word), a 3×2 grid of thumbnails from the user's other shots.
**Motion:** slide in from +0.08 W with 3 % overshoot, 10 f; gentle float ±0.004 H (sine, 2 s period) while on screen; leave 6 f.
**Flow prompt text:** "A small smartphone slides in beside the person at chest height, showing a clean white app page with a round photo of them, the words \"{{TITLE}}\", a soft pink button and a grid of small thumbnails from the video. It floats gently and never covers the face."

### A2 · GLASS CHECKLIST — UI ●● (signature for lists)
**What it is:** A frosted-glass card at the top with a small letter-spaced title and 2–4 items; each item's circle fills PINK with a check as it is spoken.
**Use when:** the captions list steps, rules or tips.
**Text (✎):** title = 1–3 user words (UPPERCASE); items = each item's user words, ≤ 22 characters; a counter "1 of 3" in numerals.
**Geometry:** card x 0.06–0.94 W, top 0.07 H; row height 0.05 H; checkbox circle 0.026 H; PINK fill + white tick when done; done items stay full white, pending items UI-MUTED.
**Motion:** card arrives 10 f; the counter updates on each tick; card stays across cuts until the list ends, then leaves 6 f.
**Flow prompt text:** "A frosted glass card floats at the top of the frame with a small spaced title \"{{TITLE}}\" and a short checklist: {{ITEMS}}. As each item is said, its circle fills soft pink with a tick."

### A3 · APP DIALOG — UI ●●● (signature middle)
**What it is:** A white app window drops from the top: first an empty drop zone, then a confirmation line with thumbnail clips of the user's footage, then the user's words typing into an input with a PINK send button.
**Use when:** a B-roll shot or a line describing an action ("do it", "add", "send", "start").
**Text (✎):** confirmation = 1–4 user words with a ✓; typed input = the spoken line (≤ 30 characters).
**Geometry:** card x 0.06–0.94 W, top 0.06 H, height 0.21 H; thumbnails 0.13 W wide, 4:3; input bar with PINK round send button at its right.
**Motion:** drop in 10 f; drop zone (dashed outline) 0.4 s → swap to the confirmation row with thumbnails sliding in 3 f apart → typing 2 letters/frame → send button pulses PINK-DEEP on the last word; leave 6 f.
**Flow prompt text:** "A clean white app window drops in at the top. Small thumbnails of the video slide into it, then the words \"{{TYPED}}\" type into a text box and a soft pink send button pulses."

### A4 · DARK APP SCREEN — CUT ●●● (signature closer)
**What it is:** The room fades to a deep plum-black app screen; the speaker stays cut out in front. A glass card at the top shows a running task with a countdown timer and a PINK progress bar.
**Use when:** the payoff / CTA / the line where "the work happens".
**Text (✎):** task title = 2–5 user words; timer = numerals counting down to 00:00.
**Geometry:** NIGHT fills the background with a soft vignette; card x 0.06–0.94 W, top 0.03–0.07 H (as high as needed to clear the head), height 0.105 H; timer right-aligned; progress bar 0.006 H tall at the card bottom.
**Motion:** background fade 10 f; card arrives 8 f later; timer counts down and the bar fills linearly over the card's life; at the end the bar flashes PINK-DEEP once.
**Fallback A4-CARD:** if the matte is poor, the footage shrinks (12 f, ease-in-out) into a rounded card 0.80 W wide centred at 0.58 H on NIGHT, card on top as above.
**Flow prompt text:** "The room behind the person fades to a deep dark plum app screen while they stay in front. At the top a frosted card shows \"{{TASK}}\" with a timer counting down and a soft pink progress bar filling."

### A5 · BOLD CAPTIONS — CAP (always on)
**What it is:** Two-line bold white captions in the lower third; one meaning word per chunk is PINK.
**Text (✎):** user's words verbatim, chunks of 2–6 words split over max 2 lines (≤ 18 characters per line).
**Geometry:** centred x; baseline of line 2 at 0.835 H (✎ 0.62 H if the face is low, or just above a bottom card); shadow 0 / +0.003 H, blur 0.01 W, black 65 % with a 2 px dark stroke so pink stays readable on bright footage.
**Motion:** each chunk fades in over 4 f with a 0.01 H rise; swaps instantly on the next chunk.
**Flow prompt text:** "Bold white captions in two short lines near the bottom, one key word in soft pink. The ONLY caption lines, in order, are: [a-b s] \"{{CHUNK_1}}\", …"

### A6 · LABEL CAPTION — CAP ●● (accent)
**What it is:** A single uppercase letter-spaced line with a white-to-pink gradient, used once for a punchy 2–4-word phrase (e.g. "SPEND → SAVE").
**Text (✎):** 2–4 user words; an arrow "→" allowed between them.
**Geometry / motion:** baseline 0.86 H; letters reveal left to right over 8 f.
**Flow prompt text:** "One short line \"{{LABEL}}\" in spaced-out bold capitals fading from white to soft pink appears near the bottom."

### A7 · SLOW PUSH — CUT ● (extension)
Footage scale 100 → 104 % linear over a shot longer than 1.5 s with no other UI arrival. Never during A4.
**Flow prompt text:** "The shot drifts in very slowly."

---

## PART 3 — RECOMMENDED COMBINATIONS (starting points, not templates)

| Story shape | Opener | Middle | Closer |
|---|---|---|---|
| Talking head → B-roll list → talking head | A1 phone on the first line | A2 checklist ticking through the list across cuts; A3 dialog on an action line over B-roll | A4 dark app screen on the payoff |
| Single talking head | A1 phone | A2 checklist, A6 label | A4 |
| B-roll / product only | A3 dialog | A2 checklist, A7 push | A4-CARD |
| Still image | A1 phone beside the subject + one A5 caption | — | — |
