---
name: 99-graphics-slip-surface-cuts
description: Makes the "Slip Surface Cuts" animated graphic (a typed paper label held centre-frame while the desk surface under it hard-cuts between wood, graph paper and cutting mats every 0.2 s) from the user's own text, optional props and colours, as a finished 9:16 video. Use when the user wants a typed paper-label intro, rapid background-swap title, label-on-desk text reveal or paper slip title card.
---

# 99 · Slip Surface Cuts

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Slip text (≤ 18 chars) | yes | none |
| P2 | Prop image 1 (scene 1 top-right) | no | none |
| P3 | Prop image 2 (scene 1 bottom-left) | no | none |
| P4 | Prop image 3 (scenes 3 and 9) | no | none |
| P5 | Slip colour A | no | #C83A38 |
| P6 | Slip colour B | no | #DDD0BE |
| P7 | Slip colour C | no | #AE835A |
| P8 | Text colour | no | auto |

### 2.2 Read everything the user gave
Read the message and attachments. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If P1 is missing, ask for it in one message ("Slip text, max 18 characters"). Mention the optional ones in one line: props (default none), slip colours (red, pale, kraft). Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Props: cut out opaque photos or use a rounded print; upscale small ones with Lanczos. Colours as hex; keep the text readable on each slip.
### 2.5 Complete input
If P1 came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: 14 scenes, hard cuts every 0.2 s, typing timing and layout exactly as description.md.
- Only the user's words on screen.
- Props are never stretched.
- Text auto-fits its slip and never leaves it.
- Output: 1080×1920, 30 fps, 2.8 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load props, fit the text, pick text colours.
- Step 3: Build every frame from description.md at 1080×1920 (slips at 2x, one worker, streamed into ffmpeg) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (5 fps) plus the frames at every cut. Look at them. Checklist: text spelled exactly; typing keeps its place across cuts; slip inside the frame; props visible and uncropped where specified; no blend between scenes. Fix and re-render.
- Step 5: Deliver `slip-surface-cuts.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
Render the last frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: 14 clips of 6 frames each, slip layer settings from description.md section 3, typing keyframes, colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never blend between scenes. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
