# description.md: Flare Sweep Title

A single bold headline on a dark stage. The letters type on one by one, centred as they grow. A smear and a glow follow the newest letter, and a sunburst flare with dark spokes flashes at the leading edge. The smear relaxes, the crisp headline holds, then the smear and flare return at the middle of the text and the headline fades away.
**The graphic in one line:** a heavy headline types on with a glowing smear and sunburst flare, holds crisp, flares again and fades out.
**Format:** 16:9 · 1920×1080 · 30 fps · 4.33 s (reference 1280×720; world values in 1280 px units, multiply by 1.5 for output)

## 1. Canvas
- Dark stage. Radial tone lookup from the centre, in 1280 px units: r 0 to 60 = 35, r 140 = 33, r 220 = 31, r 300 = 28, r 440 = 24, r 520 = 23, r 540 and beyond = 20 (grey levels, slightly warm: R 0.95, G 0.91, B 0.90 of the grey). The lookup is blurred with sigma 6 px. This gives two faint concentric discs (edges at about r 290 and r 530) and a darker rim.
- No grid, no grain. Nothing else on the canvas.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Headline text | yes | none, must ask | text, ≤ 12 chars, 1 line, set in capitals (auto-fit down to 70%) | E1, B1–B6 |
| P2 | Text colour | no | #FCFD00 (measured) | hex, bright | E1 |
| P3 | Hot tint | no | #FF9A00 (measured by eye) | hex | new letters, flare core |
| P4 | Stage tone | no | #232120 centre, #121113 edge (measured) | 2 hex, dark | canvas |
| P5 | Sunburst rays | no | on | on / off | E3 |
| P6 | Exit flare and fade | no | on | on / off | B5, B6 |
| P7 | Stage rings | no | on | on / off | canvas |

### 2.1 How to infer parameters from user material
- Headline: the shortest strong phrase of the user's topic (a title, a product name, a hook).
- Text colour: a brand colour; keep it bright on the dark stage. Hot tint: a hue about 40 to 60 degrees away from it.

## 3. Elements
### E1 · Headline
Rubik (variable), weight 900, capitals. Size: cap height 147 px at 1920 (font size 210, cap 98 at 1280), tracking -0.02 em, word space 1.5 × the font's space. Centred at x 960, cap-centre y 537 (358 at 1280). Measured full width of a 9-char text about 1200 px (800 at 1280). Auto-fit: width ≤ 1440 px; shrink to 70% (font size 147) at most.
Each letter is a mask; letters have colour P2, blended to P3 while new (see B1).
### E2 · Smear and glow
Built from the visible headline: a leftward one-sided horizontal smear (exponential tail), a gaussian glow, and a radial streak blur around the pivot. All scale with the intensity curve I(t) in section 5.
### E3 · Sunburst
Dark wedges cut through the lit text around the pivot: 12 spokes at angles (deg) -100, -84, -66, -38, -8, 14, 62, 82, 98, 118, 150, -150, half-widths 1.2 to 2.6 deg, strength 0.9 × I, falling off with exp(-r/220 px). Off when P5 is off.
### E3b · Flare core
Additive, at the pivot, strength min(1, 1.2 × I): white core exp(-(r/34 px)^2); halo exp(-r/120 px) × 0.55 in P3; 12 bright rays (same angles as E3, half-widths 1.1 to 2.0 deg) of length about 220 px (1.5 × cap height), colour 0.6 × P3 + 0.4 white, amplitude 0.9. Letters near the pivot are tinted toward P3 with weight min(1, 1.3 × I) × exp(-|x - pivot x|/130 px). Dark wedges (E3) strength is 0.5 × I.
### E4 · Pivot
The flare point. During the type-on it is the right edge of the newest letter. From 0.7 to 1.3 s it glides (smoothstep) to 51% of the text width from its left edge, and stays there.

## 4. Camera
None. Static frame.

## 5. Timeline (beats)
Intensity I(t) (measured peak, design curve): intro I = smoothstep(0.10, 0.90, t) × (1 - smoothstep(0.90, 1.85, t)); exit I = 0.85 × smoothstep(2.6, 3.3, t); I = max of the two.
### B1 · Type-on — 0.10–0.66 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.10 + k × 0.56/(n-1) | E1 letter k (non-space) | alpha 0 → 1 over 0.05 s | | linear (design) |
| same | E1 letter k | colour P3 → P2 | decay exp(-t/0.13) | |
| 0.13 on | E1 | visible letters centred at x = 960 - 277 × exp(-(t-0.13)/0.19) px (measured 455 → 640 at 1280) | | |
### B2 · Flare peak — 0.66–0.9 s
Pivot at the right end, I rises to 1. Smear tail length (half-res px) 30 + 110 × I, glow sigma 5 + 5 × I (half-res), mix 0.45 × I of smeared into crisp text.
### B3 · Relax — 0.9–1.85 s
I falls to 0. The pivot glides to mid text. Letters become crisp.
### B4 · Hold — 1.85–2.6 s
Crisp text, no effects.
### B5 · Exit flare — 2.6–3.35 s
I rises to 0.85, pivot at mid text. Same effect recipe as B2.
### B6 · Fade out — 3.35–4.33 s
| 3.35–3.55 | E1 | alpha 1 → 0.25 (dim ghost) | smoothstep | |
| 3.55–3.85 | E1 | alpha 0.25 → 0 | smoothstep | |
| 3.35–3.70 | E1 | x squeeze to 88% about the pivot | smoothstep | |
| 3.85–4.33 | | empty stage | | |

## 6. Build notes
- Python, NumPy, OpenCV, Pillow, ffmpeg. Render at 1920×1080 float32; the smear, glow and streak layers are computed at 960×540 and upsampled.
- Smear: sum of copies shifted right to left at step 2 px (half-res) with weights exp(-j/(L/3)), then gaussian 2.5 px. Streaks: average of 32 copies scaled about the pivot from 1 - 0.4a to 1 + a to a = 0.14 × I (fewer copies show stepped ghosts). Composite: crisp × (1 - 0.45 I) + smear × 0.45 I, plus glow × 0.55 I, streaks × 0.65 I and smear × 0.12 I, then the wedge factor, then fade, then add to the stage and clip.
- Tint for new letters is per-letter, so it needs the letter masks to be separate.
- Stream raw frames into ffmpeg; never keep all frames. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.

## 7. Still frame
The settled frame at 2.0 s: the crisp headline centred on the dark stage with the faint discs, no flare.

## 8. Never
- Text clipped, off-centre or in lower case.
- Stepped ghost copies in the smear.
- Effects on during the hold.
- More than one line of text.
- Reference content (its words) as a default.
