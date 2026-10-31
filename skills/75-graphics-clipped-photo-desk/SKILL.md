---
name: 75-graphics-clipped-photo-desk
description: Makes the "Clipped Photo Desk" animated graphic (a dotted-paper desk seen from above; the camera eases in as pens, paper cards, a paper-clipped tape label, a colour strip and a tilted photo slide onto it, then two text lines type on) from the user's own text, photo and colours, as a finished 9:16 video. Use when the user wants a desk-top title card, clipped photo with a caption strip, sticky-note headline, polaroid-on-desk reel intro or stationery scrapbook title.
---

# 75 · Clipped Photo Desk

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Strip text (≤ 18 chars) | yes | none |
| P2 | Label text (≤ 14 chars) | yes | none |
| P3 | Photo | yes | none |
| P4 | Strip colour | no | #E8F000 |
| P5 | Card colour | no | #8E959E |
| P6 | Pen colour | no | #C8102E |
| P7 | Text colour | no | #17161A |
| P8 | Dot grid | no | on |
| P9 | Focal point | no | auto |

### 2.2 Read everything the user gave
Read the message, attached images, videos and documents. Map each piece to parameters using description.md section 2.1. A still from a video may fill the photo. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Strip text (max 18 characters)", "Label text (max 14 characters)", "1 photo (any photo; I'll crop it to a wide frame and keep the subject whole)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Photo width (warn and upscale with Lanczos if under 1200 px). Colours as hex; strip colour needs strong contrast with the text colour.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Photo: cover-fit crop only, never stretched. Keep the focal point (auto-detect a face or subject, else centre; honour hints).
- Text auto-fits and never leaves its strip or label.
- Output: 1080×1920, 30 fps, 6.0 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load the photo, detect the focal point, crop to 800×470 units; draw every prop as a sprite at 1.5 px per unit with baked shadow; measure and fit both texts.
- Step 3: Build every frame from description.md at 1080×1920 (desk and dots per pixel, sprites by affine warp, sub-frame motion blur) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (fps 2) plus one strip around the photo slide-in and the final frame. Look at them. Checklist: both texts on screen and spelled exactly; nothing clipped; subject visible above the strip; props off-screen at their start; no ghosting banding. Fix and re-render.
- Step 5: Deliver `clipped-photo-desk.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final settled frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers in the order of description.md section 3, the zoom keyframes of section 4, slide-in times of section 5, text and colours, photo crop.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never stretch the photo. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
