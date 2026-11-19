---
name: "166-graphics-focus-pill-folder-tree"
description: "Makes the \"Focus Pill Folder Tree\" animated graphic (a light page with a root folder card and an indented folder tree where the other folders dim, an outlined pill hops from a focus folder to a newly typed sub-folder, a thumbnail file and a second sub-folder while the camera follows) from the user's own folder names, file name and thumbnail, as a finished 9:16 video. Use when the user wants a folder tree, file structure explainer, project hierarchy or directory walkthrough animation."
---

# 166 · Focus Pill Folder Tree

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Root name (≤ 16 chars) | yes | none |
| P2 | Root sub-label (≤ 24) | yes | none |
| P3 | Folder names 1 to 4 (≤ 14 each) | yes | none |
| P4 | Focus folder name (≤ 14) | yes | none |
| P5 | Focus folder sub-label (≤ 24) | yes | none |
| P6 | Last folder name (≤ 14) | yes | none |
| P7 | New sub-folder name (≤ 20) | yes | none |
| P8 | File name (≤ 32) | yes | none |
| P9 | File thumbnail image | yes | none |
| P10 | Second sub-folder name (≤ 14) | yes | none |
| P11 | Second sub-folder sub-label (≤ 26) | yes | none |
| P12 | Placeholder name | no | untitled folder |
| P13 | Folder colour | no | #6BB0EF / #529BE7 |
| P14 | Text colour | no | #131313 |
| P15 | Page tone | no | #EFEEE7 / #E6E2DA |
| P16 | Pill colour | no | #333333 |

### 2.2 Read everything the user gave
Read the message, attached images and documents. Map each piece to parameters using description.md section 2.1 (a real folder layout, a brand colour, a file preview). State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Root name (max 16 characters)", "A thumbnail image for the file (any aspect, I'll crop it)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Thumbnail width (warn and upscale with Lanczos if small). Colours as hex with strong contrast to the page.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- The thumbnail is cover-fit cropped, never stretched.
- Text auto-fits and never leaves its card or pill; the root card widens to its text.
- Output: 1080×1920, 30 fps, 8.8 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: crop the thumbnail, measure and fit text, wrap the file name.
- Step 3: Build every frame from description.md at 2160×3840, downscale to 1080×1920, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus the frames at each beat's end. Look at them. Checklist: every value on screen and spelled exactly; only one pill at a time; the typed name completes; nothing clipped at any camera position; the final frame shows the whole tree. Fix and re-render.
- Step 5: Deliver `focus-pill-folder-tree.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, pill and dim timings, text, colours and the thumbnail crop.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never stretch the image. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
