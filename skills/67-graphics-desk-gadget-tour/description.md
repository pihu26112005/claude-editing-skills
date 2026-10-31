# description.md: Desk Gadget Tour

A top-down desk scene on grey grid paper. A handheld gadget lies among scattered desk props. Your short title types onto the gadget screen while the camera zooms in and tilts. The camera then whirls one full turn around the desk. A two-line headline types out on the paper beside the gadget and the camera settles into a slow drift.
**The graphic in one line:** a title typed on a gadget screen, a camera whirl over a grid desk, then a two-line headline typed onto the paper.
**Format:** 9:16 · 1080×1920 · 30 fps · 6.53 s (reference 720×1280; world units below are in 720×1280 px at zoom 1, multiply by 1.5 for output)

## 1. Canvas
- Paper #E4E4E4 (measured 228), monochrome desk. Screen-space soft light falloff: centre 100 percent, corners 92 percent (design).
- Grid on paper in WORLD space: pitch 54.8 units (measured), line colour #3A3C3E, width about 2 units (Gaussian sigma 1.0), peak alpha 0.78. Origin offset (20,33) from the gadget centre. The grid moves, rotates and zooms with the camera.
- Fine grain, Gaussian sigma 1.6 levels, new each frame.
- Screen-space overlays (never move): footer text bottom centre, vertical edge label near the left edge.
- Safe margins: headline stays inside the frame at the final frame.

## 2. Parameters
| ID | Parameter | Required | Default | Type / limits | Where it appears |
|---|---|---|---|---|---|
| P1 | Screen text | yes | none, must ask | text, ≤ 14 chars, 1 line (auto-fit to 70%) | E2, B1 |
| P2 | Headline line 1 | yes | none, must ask | text, ≤ 22 chars, 1 line (auto-fit to 70%) | E5, B3 |
| P3 | Headline line 2 | yes | none, must ask | text, ≤ 20 chars, 1 line (auto-fit to 70%) | E5, B3 |
| P4 | Footer text | no | none | text, ≤ 24 chars | E6 |
| P5 | Edge label | no | none | text, ≤ 18 chars, caps recommended | E7 |
| P6 | Gadget colour | no | #1E1E1E (measured) | hex, dark to mid | E1 |
| P7 | Paper colour | no | #E4E4E4 (measured) | hex, light | canvas |
| P8 | Text colour | no | #0A0A0A (measured) | hex, dark | E2, E5, E6 |
| P9 | Edge label colour | no | #C9A45C (measured, gold) | hex | E7 |
| P10 | Grid | no | on | on / off | canvas |
| P11 | Desk props | no | on | on / off | E3 |

### 2.1 How to infer parameters from user material
- Screen text: the product, app or brand name. Headline: the promise, split into a longer line 1 and a shorter line 2 that completes it.
- Footer: the user's site or handle. Edge label: a short tagline or date.
- Colours: P6 from a brand colour (keep the screen readable); P8 dark with strong contrast to the paper.

## 3. Elements
World units, gadget centre = (0,0), y down. Gadget angle +20 degrees (clockwise).
### E1 · Gadget
Handheld console seen from above: body 400×196, corner radius 44, colour P6 with lighter edge line and darker side grips. Screen bezel inset (82,20), screen 218×126 colour #CECECC, slightly lighter top band. Left: round thumbstick (r 22) and three small slots. Right: four round buttons in a diamond (r 9, spacing 17) and one small round button. Tiny shoulder marks on top corners. Soft double drop shadow (offset 12,6 sigma 10 plus contact shadow 3 units).
### E2 · Screen text
Poppins SemiBold, size 25 (cap height about 18), colour P8, tracking -1 percent, centred on the screen when complete, left start fixed (typed left to right). Auto-fit width ≤ 200.
### E3 · Desk props
Monochrome top-down items on the paper with soft shadows and depth blur (sigma 1 to 6 units, stronger far from the gadget): mug, scissors, ruler, potted plant, sticky-note stack, tape roll, pencil, notebook, cord, paperclips, coin. Hand-placed near the gadget (see build notes), randomly scattered further out (seed 67) in a disc of radius 1150 around (100,-50). Clear zones: the gadget and the headline area (x -190..450, y -380..-40).
### E4 · Camera whirl
See section 4.
### E5 · Headline
Line 1: Poppins SemiBold 60, tracking -3 percent, left edge x=-130, baseline y=-224, width ≤ 540. Line 2: Poppins Bold 68, tracking -3 percent, right edge x=410, baseline y=-157, width ≤ 420. Both colour P8, world angle -2 degrees, centre of the pair (130,-215). Each char appears instantly. Lines are never moved by the camera except as part of the world.
### E6 · Footer
Poppins SemiBold 22, colour P8, centred at x=360, baseline y=1215. Screen space.
### E7 · Edge label
Poppins SemiBold 14, tracking 40 percent, colour P9 at 78 percent opacity, rotated 90 degrees, centred at (70,230). Screen space.

## 4. Camera
Camera centre (cx,cy) in world units, zoom z (1 = gadget 400 units wide on a 720 screen), rotation R in degrees (positive turns the world clockwise). Monotone cubic (PCHIP) interpolation through:
| t (s) | cx | cy | z | R |
|---|---|---|---|---|
| 0.00 | 4 | -220 | 1.00 | 0 |
| 1.00 | -10 | 0 | 0.90 | -3 |
| 1.50 | -5 | 5 | 1.05 | -14 |
| 2.00 | 0 | 0 | 1.25 | -32 |
| 2.20 | 10 | 0 | 1.45 | -45 |
| 2.50 | 10 | 0 | 1.45 | -75 |
| 2.75 | 0 | -10 | 1.00 | -165 |
| 3.00 | 0 | 0 | 0.72 | -290 |
| 3.33 | 40 | 40 | 0.85 | -330 |
| 3.75 | 80 | 40 | 0.95 | -352 |
| 4.50 | 100 | 20 | 1.00 | -360 |
| 6.53 | 160 | 120 | 1.00 | -360 |
Positions and rotation were measured from the reference by eye at 4 fps, zoom from gadget width; interpolation is (design). Motion blur: average n sub-frames over a 0.5-frame shutter, n = ceil(degrees per frame × 0.5 / 0.6), max 30.

## 5. Timeline (beats)
### B1 · Type on the gadget — 0.15–2.0 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 0.15–2.00 | E2 | characters shown | 0 → all, even rate | linear (measured) |
| 0–2.0 | camera | zoom, rotation | 1.0 → 1.25, 0 → -32 | smooth (measured) |
### B2 · Whirl — 2.0–3.5 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.0–2.5 | camera | zoom to 1.45, R to -75 | table above | smooth |
| 2.5–3.0 | camera | R -75 → -290, zoom 1.45 → 0.72 | fast spin | smooth (measured) |
| 3.0–3.5 | camera | R → -345, zoom → 0.9 | slows | smooth |
### B3 · Headline types — 2.9–4.5 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 2.90–3.70 | E5 line 1 | characters | 0 → all | linear (measured) |
| 3.90–4.50 | E5 line 2 | characters | 0 → all | linear (measured) |
### B4 · Drift and hold — 4.5–6.53 s
| t (s) | Element | Property | From → To | Ease |
|---|---|---|---|---|
| 4.5–6.53 | camera | centre (100,20) → (160,120) | slow drift | smooth (measured) |

## 6. Build notes
- Canvas 1080×1920. Grid per pixel analytically from world coordinates (distance to nearest line, Gaussian profile), so it is anti-aliased at any zoom.
- Pre-render once: prop canvas (2 px/unit, premultiplied RGBA, items drawn 4× then downscaled, shadow and depth blur per item), gadget sprite (2.4 px/unit with shadow), typed-text sprites (cached per character count). Warp each with an affine matrix (cv2.warpAffine, bilinear) and composite premultiplied.
- Hand-placed props (kind, x, y, rotation): mug (-250,-700), scissors (-330,-390,70), notes (-310,210,-14), tape (-110,350), ruler (160,400,8), plant (-250,-520), pencil (470,-540,84), cord (520,-620), pencil (500,120,92), notebook (640,560,4), coin (330,660), clips (-60,640,30), plant (330,-760), mug (420,820).
- Typing: draw the first k characters at positions from font.getlength of prefixes (keeps kerning). Text auto-fit: shrink size by 3 percent steps to 70 percent.
- Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30` with a silent AAC track.

## 7. Still frame
The settled frame at 6.53 s: gadget left of centre in the upper half, tilted 20 degrees with the screen text; headline lines clearly above it (at least 40 px gap), line 2 right-aligned; props at the edges; footer at the bottom, edge label at left.

## 8. Never
- Never let the headline touch the gadget: the gap between the bottom of any headline line (baseline + 0.28 × font size, plus 2 degrees of tilt) and the gadget's top edge must be at least 27 units (40 px at 1080 wide). Check it at 30 points along each line; if a line is too close (long or short text changes line 2's left edge), move both lines up in 5-unit steps until the check passes. The demo needed a 65-unit lift, already included in the baselines above.
- Never rotate or stretch text on its own; text lives on the desk or the screen.
- Never place props under the headline area.
- Never change the number of text lines or the camera path.
- Never leave the whirl un-blurred (banding of grid lines).
