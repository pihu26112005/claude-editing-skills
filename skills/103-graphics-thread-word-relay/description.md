# description.md: Thread Word Relay

A square, generic social-thread card. A sentence is spoken one word at a time. For each word the card flickers rapidly through several different invented posters who all wrote that same word, so the word stays locked in place while avatar, handle, age and likes change around it. Faded posts above and below drift with the flicker. After the last word the card holds.
**The graphic in one line:** a fixed post slot cycles through many different users' posts of the same word, crossfading, one word after another.
**Format:** 1:1 · 1080×1080 · 30 fps · 4.8 s (reference 250×250, 30 fps, 4.8 s; all fractions below are of W and H, multiply by 1080)

## 1. Canvas
- Flat near-white background #FAFAFA (measured about 250,250,250). No grid, no vignette, no grain.
- No platform logos, names or UI chrome anywhere. The post UI is generic.
- Content is left-weighted and clips at the right edge (long age or handle text may run past the edge, as measured).

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Words | yes | none, must ask | list of exactly 6 words (a sentence split in order), each ≤ 10 chars | E4, B1–B6 |
| P2 | Handles | no | 15 neutral generated handles (@user_01 …) | list of ≥ 8 invented handles, ≤ 14 chars each | E3 |
| P3 | Avatars | no | procedural generated avatars | any number of square images, circle-cropped, or auto | E2 |
| P4 | Neighbour lines | no | grey skeleton bars | ≥ 6 short sentences, ≤ 60 chars | E7 |
| P5 | Accent colour | no | #2F7BE0 (measured blue of the reply link) | hex | E6 reply link |
| P6 | Background colour | no | #FAFAFA (measured) | hex, light | canvas |
| P7 | Text colour | no | #0F0F0F (measured) | hex, dark | E3, E4 |
| P8 | Ages and like counts | no | generated mix (minutes to months, 12 to 12K) | lists | E3, E5 |

### 2.1 How to infer parameters from user material
- Words: split the user's sentence or slogan into 6 words, in order. If it has fewer or more, ask for a 6-word line.
- Handles and neighbour lines: take from a user list of names or sample comments; else defaults.
- Avatars: user photos or logos, circle-cropped around the focal point; else procedural.
- Accent colour: a brand colour with good contrast on the background.

## 3. Elements
Focal slot centre line y = 0.43 (avatar centre). All x are from the left edge.
### E1 · Slot
Fixed. Never moves while words change (the match cut). Everything below sits inside it.
### E2 · Avatar
Circle, diameter 0.176 (190 px), centre (0.20, 0.43). Changes with every flicker slot. Procedural default: gradient disc with a simple face, cat, robot or ghost figure. User images cover-fit.
### E3 · Handle and age
Handle at x 0.36, y 0.376 (centre 406 px), Inter SemiBold 54 px, colour P7. Age follows 22 px right, Inter 44 px, grey #828282.
### E4 · Word
x 0.36, y 0.50 (centre 540 px), Inter Bold 84 px, colour P7. Always the current word of P1; in non-final flicker slots the casing varies (as typed, lower, capitalised), in the last slot of each word it is exactly as the user typed it.
### E5 · Action row
y 0.64 (centre 691 px). Thumb-up outline icon at x 0.36 (52 px), like count at x 0.40, thumb-down icon at x 0.56, "Reply" at x 0.64. Inter Medium 44 px, grey #606060.
### E6 · Reply link
Present in about 55 percent of slots, y 0.705, a chevron and "N replies" at 44 px in the accent P5.
### E7 · Neighbour posts
Same layout, one above (centre y 467-520) and one below (467+520), blurred (gaussian 2.2 px), faded to 42 percent. Body lines at 50 px in place of the word. They change with the flicker slot like the focal post.

## 4. Camera
None. Static.

## 5. Timeline (beats)
Flicker slot length 0.15 s (4.5 frames). Each word owns 5 slots (0.75 s). 6 words × 0.75 s = 4.5 s, then 0.3 s hold on the last slot.
### B1–B6 · Word 1 to word 6 — 0.75 s each, starts at 0, 0.75, 1.5, 2.25, 3.0, 3.75 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| slot start + 0.00 to 0.55 × 0.15 | whole card | hold slot k | static | none (measured) |
| slot start + 0.55 × 0.15 to 0.15 | whole card | crossfade slot k to k+1 (all elements incl. avatar, neighbours) | 0 → 1 | smoothstep (design) |
| last slot of word | E4 | casing | exact user casing | none |
| across a word boundary | E4 | word | word n → word n+1 | same crossfade |
### B7 · Hold — 4.5–4.8 s
Last slot stays, no fade.

## 6. Build notes
- Draw each slot as a full 1080×1080 frame at 2× supersample (Pillow), downscale with Lanczos, keep 30 frames of crossfade by blending two pre-rendered slot frames (30 slot frames in RAM, about 100 MB).
- Neighbours: draw on their own layer, gaussian blur, mix 42 percent with the background, then draw the focal post sharp on top.
- Per slot use a seed so avatar, handle, age, like count and reply link differ; never repeat the same handle in adjacent slots.
- Font: Inter variable (opsz 14–32, wght 400–700). Icons are drawn as plain polylines.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The last slot: final word in place, crisp, handle and avatar of the last poster, faded neighbours above and below.

## 8. Never
- Never move the slot; only its content changes.
- Never show a real platform name, logo or colour scheme, or real people's names.
- Never use other words than P1 in the focal slot.
- Never use a different number of words.
