---
name: 68-graphics-sliding-card-rail
description: Makes the "Sliding Card Rail" animated graphic (five image cards on a tilted, perspective rail: the camera flies in from far away, then glides card to card along a drawn-on accent line with a white knob and label under each) from the user's own five labels, five images and accent colour, as a finished 9:16 video. Use when the user wants a 5-step timeline, step-by-step process rail, perspective card carousel, roadmap or progress-line explainer.
---

# 68 · Sliding Card Rail

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1–P5 | Labels 1 to 5 (≤ 14 chars each) | yes | none |
| P6–P10 | Images 1 to 5 | yes | none |
| P11 | Accent colour (rail) | no | #FF2300 |
| P12 | Band colour | no | #202020 |
| P13 | Backdrop colour | no | #161616 |
| P14 | Label colour | no | #FFFFFF |
| P15 | Focal points | no | auto |

### 2.2 Read everything the user gave
Read the message, attached images, videos and documents. Map each piece to parameters using description.md section 2.1. Stills from a video may fill the images. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "5 step labels (max 14 characters each)", "5 images (any photos; I'll crop them to 5:3 and keep the subject)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Label length (auto-fit to 70%, else ask to shorten). Image width at least 900 px (warn and upscale with Lanczos if small). Colours as hex; the accent needs strong contrast with the band.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, perspective and camera exactly as description.md.
- Only the user's words on screen. Exactly 5 steps.
- Images: cover-fit crop only, never stretched. Keep the focal point (auto-detect a face or subject, else centre; honour hints).
- Labels auto-fit and never touch the knob or the card.
- Output: 720×1280, 30 fps, 10.1 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load images, crop to 5:3, pre-render the world strip (cards and labels) at 2.5 px per unit and 1.25 px per unit.
- Step 3: Build every frame from description.md: project the strip through the yawed pinhole camera, draw the rail and knobs analytically, add sub-frame motion blur, supersample 2×, and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frame where each card is centred. Look at them. Checklist: every label spelled exactly; nothing clipped; subjects inside the cards; the rail ends where description.md says; the knob is centred under each label; the motion matches. Fix and re-render.
- Step 5: Deliver `sliding-card-rail.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final settled frame (description.md section 7) as a PNG at 720×1280.

## 6. NO CODE EXECUTION
Give an editor build sheet: a 3D-rotated layer of five cards, camera keyframes from description.md section 4, rail wipe times, labels, colours and image crops.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never stretch images. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
