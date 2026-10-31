---
name: 85-graphics-twin-swoosh-callouts
description: Makes the "Twin Swoosh Callouts" animated graphic (a glowing portrait image card on a dark stage that a camera pushes in on, then two glowing brush swooshes sweep out to the right and each ends in a short glowing label) from the user's own image, two labels and colours, as a finished 16:9 video. Use when the user wants a two-callout image card, glowing swoosh labels, neon brush-stroke annotations, or a portrait photo with two glowing tags.
---

# 85 · Twin Swoosh Callouts

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Card image (portrait) | yes | none |
| P2 | Label 1 (lower, ≤ 18 chars) | yes | none |
| P3 | Label 2 (upper, ≤ 18 chars) | yes | none |
| P4 | Swoosh tail colour | no | #E97C11 |
| P5 | Swoosh head colour | no | #FFFF59 |
| P6 | Label colour | no | #FDDF00 |
| P7 | Glow colour | no | #FFC800 |
| P8 | Card border colour | no | #EED89B |
| P9 | Stage colour | no | #121114 |
| P10 | Focal point | no | auto |

### 2.2 Read everything the user gave
Read the message, attached images, videos and documents. Map each piece to parameters using description.md section 2.1. A still from a video may fill the card. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits ("Card image (a portrait photo or illustration; I'll crop it, the subject stays whole)", "Label 1 (max 18 characters)", "Label 2 (max 18 characters)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Label length (auto-fit to 70%, else ask to shorten). Image short side at least 540 px (else warn and upscale with Lanczos). Colours as hex; glow and label colours must stand out from the stage.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Image: cover-fit crop only, never stretched. Keep the focal point (auto-detect a face or subject, else centre; honour hints).
- Labels auto-fit and never leave the frame or touch a swoosh.
- Output: 1920×1080, 30 fps, 6.0 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load the image, detect its focal point, crop to the card, build the card and letter sprites at 2.4 px per unit.
- Step 3: Build every frame from description.md at 1920×1080 with sub-frame motion blur and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`. Frames after 4.7 s are identical; render once.
- Step 4: Check: a contact sheet (4 fps) plus the frames at 1.9 s, 2.7 s and 5 s. Look at them. Checklist: both labels spelled exactly; nothing clipped or overlapping; subject inside the card; swooshes end beside their labels; motion matches description.md. Fix and re-render.
- Step 5: Deliver `twin-swoosh-callouts.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, swoosh draw-on times, label type-on times, colours and the image crop.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never stretch the image. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
