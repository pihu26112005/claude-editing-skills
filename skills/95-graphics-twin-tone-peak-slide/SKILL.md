---
name: 95-graphics-twin-tone-peak-slide
description: Makes the "Twin-Tone Peak Slide" animated graphic (a glass orb on a dome, a glowing area chart that climbs to a peak, a marker line, then a second-colour fall with a two-word label) from the user's own text and colours, as a finished 9:16 video. Use when the user wants a rise-and-fall chart, peak and decline graphic, glowing area chart reveal, trend turning-point animation or vertical data teaser on black.
---

# 95 · Twin-Tone Peak Slide

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Label (1 or 2 words, ≤ 16 chars) | yes | none |
| P2 | Rise colour | no | #12D63A |
| P3 | Fall colour | no | #FF0A14 |
| P4 | Icon colour | no | #8173EF |
| P5 | Marker colour | no | #FFFFFF |
| P6 | Background colour | no | #000000 |
| P7 | Label colour | no | same as P3 |

### 2.2 Read everything the user gave
Read the message and any brand assets. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If the label is missing, ask for it in one message ("Label for the peak, 1 or 2 words, max 16 characters"). Mention the optional colours in one line with their defaults. Stop and wait.
### 2.4 Validate
Label length (auto-fit to 70%, else ask to shorten). Colours as hex; P2 and P3 in different hue families; strong contrast with the background.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's label on screen. No faces, no people, no numbers.
- Text auto-fits and never overlaps the orb.
- Output: 1080×1920, 30 fps, 4.0 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fit the label, build the chart strip and icon sprite at 2×.
- Step 3: Build every frame from description.md (720×1280 canvas, Lanczos to 1080×1920, sub-frame motion blur on fast moves) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at 1.2 s, 1.6 s and 3.5 s. Look at them. Checklist: label spelled exactly; chart peak lands on the marker; fall area is right of the marker; orb and chart never collide with the label; slide is smooth. Fix and re-render.
- Step 5: Deliver `twin-tone-peak-slide.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers (icon, rise area, marker, fall area, label), the slide keyframes from description.md section 4, wipe times, text and colours.

## 7. NEVER DO
Never invent content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
