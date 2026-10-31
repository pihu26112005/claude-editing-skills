---
name: 79-graphics-arrow-label-burst
description: Makes the "Arrow Label Burst" animated graphic (a glowing centre phrase types in on a dark hand-drawn grid, then four crayon arrows fire out one by one and four coloured labels pop at their tips) from the user's own text and colours, as a finished 16:9 video. Use when the user wants a text mind map, four-point text diagram, arrow-and-label explainer, neon marker keyword burst or branching text intro on a dark grid.
---

# 79 · Arrow Label Burst

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Centre text (≤ 16 chars) | yes | none |
| P2 | Label 1 (top-left, ≤ 20 chars) | yes | none |
| P3 | Label 2 (top-right, ≤ 20 chars) | yes | none |
| P4 | Label 3 (bottom-left, ≤ 20 chars) | yes | none |
| P5 | Label 4 (bottom-right, ≤ 20 chars) | yes | none |
| P6 | Centre text colour | no | #F9CB04 |
| P7 | Arrow colour | no | #F9CB04 |
| P8 | Label 1 colour | no | #FCFCFC |
| P9 | Label 2 colour | no | #CE26F1 |
| P10 | Label 3 colour | no | #2DE819 |
| P11 | Label 4 colour | no | #13BEEF |
| P12 | Background colour | no | #1F1F1F |
| P13 | Grid | no | on |
| P14 | Dust specks | no | on |

### 2.2 Read everything the user gave
Read the message, attached files and brand assets. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Centre text (max 16 characters)", "4 labels (max 20 characters each, in order top-left, top-right, bottom-left, bottom-right)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex with strong contrast to the background; if low, say so and suggest the default.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's words on screen.
- Text auto-fits its box and never collides with an arrow.
- Output: 1920×1080, 30 fps, 4.03 s, animation stepped at 15 fps (each frame shown twice).

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Measure and fit text; build the arrow strokes.
- Step 3: Build every frame from description.md at 2x world size, warp to 1920×1080 with the push-in zoom, and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at each label pop and the last frame. Look at them. Checklist: every text spelled exactly; nothing clipped; arrows end near their labels without touching; motion matches description.md. Fix and re-render.
- Step 5: Deliver `arrow-label-burst.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, timings from description.md section 5, stroke paths, text, colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
