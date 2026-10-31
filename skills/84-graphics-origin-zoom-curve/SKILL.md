---
name: 84-graphics-origin-zoom-curve
description: Makes the "Origin Zoom Curve" animated graphic (dashed axes seen close up, a jagged glowing growth line drawn from the origin while the camera pulls back to reveal a grid, a title and two axis labels) from the user's own text and colour, as a finished 9:16 video. Use when the user wants a growth chart, exponential line graph, hockey-stick curve, dark-mode trend chart or explosive-growth explainer.
---

# 84 · Origin Zoom Curve

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Title (≤ 24 chars) | yes | none |
| P2 | Y-axis label (≤ 16 chars) | yes | none |
| P3 | X-axis label (≤ 16 chars) | yes | none |
| P4 | Accent colour (line, title) | no | #BA00D2 |
| P5 | Label and axis colour | no | #FFFFFF |
| P6 | Background centre / corner | no | #272526 / #121114 |
| P7 | Grid | no | on |
| P8 | Curve seed (jitter) | no | 7 |

### 2.2 Read everything the user gave
Read the message and attachments. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits. Mention optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; the accent must contrast with the dark background, else suggest the default.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Text auto-fits and never collides with the chart.
- Output: 1080×1920, 30 fps, 7.5 s, silent.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fit the three texts, build the curve from the seed.
- Step 3: Build every frame from description.md at 1080×1920 (drawn at 2x, downscaled) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus a full-size frame at 7 s. Look at them. Checklist: texts spelled exactly; nothing clipped; line ends on the top-right grid corner; zoom settles at 4.6 s. Fix and re-render.
- Step 5: Deliver `origin-zoom-curve.mp4`, the final parameter table, and one line on what can be changed.

## 5. STILL MODE
Render the final frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, line draw-on keyframes, text, colours.

## 7. NEVER DO
Never invent content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
