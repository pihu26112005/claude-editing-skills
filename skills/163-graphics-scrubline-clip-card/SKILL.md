---
name: "163-graphics-scrubline-clip-card"
description: "Makes the \"Scrubline Clip Card\" animated graphic (a rounded clip card with a chat panel that becomes a ticking checklist, a timecode and a playhead that sweeps a filmstrip and waveform timeline) from the user's own clip, images and texts, as a finished 9:16 video. Use when the user wants an editor timeline reel, video-editor UI explainer, playhead scrub graphic, workflow or tool-stack breakdown card."
---

# 163 · Scrubline Clip Card

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Clip (image or video) | yes | none |
| P2 | Title lead | yes | none |
| P3 | Title bold | yes | none |
| P4 | Row names (5) | yes | none |
| P5 | Row roles (5) | yes | none |
| P6 | Row reasons (5) | yes | none |
| P7 | Window title | yes | none |
| P8 | Prompt message | yes | none |
| P9 | Result line | yes | none |
| P10 | Pasted message | yes | none |
| P11 | Column headers | no | ITEM / ROLE / REASON |
| P12 | Composer hint | no | Type a message |
| P13 | Footer labels | no | Auto / Model / Std |
| P14 | Playhead colour | no | #E34554 |
| P15 | Waveform colour | no | #3C9C6A |
| P16 | Page colour | no | #E8E4DC |
| P17 | Timeline length (s) | no | 60 |
| P18 | Focal point | no | auto |

### 2.2 Read everything the user gave
Read the message, attached images, videos and documents. Map each piece to parameters using description.md 2.1. A frame or clip from the user's video fills the clip. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits. Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten), image size (upscale small ones with Lanczos), colours as hex with contrast to the page.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion exactly as description.md.
- Only the user's words on screen.
- Images: cover-fit crop only, never stretched, keep the focal point.
- Text auto-fits its box and never overflows.
- Output: 1080×1920, 30 fps, 3.5 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load images, crop, measure and fit text.
- Step 3: Build every frame from description.md at 3x supersampling (downscale to 1080×1920), stream into `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at the paste, the swap and the end. Look at them. Checklist: every value on screen and spelled exactly; nothing clipped; playhead, timecode and revealed timeline agree; ticks land in their boxes.
- Step 5: Deliver `scrubline-clip-card.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final table, and one line on what can be changed.

## 5. STILL MODE
Render the settled frame of description.md section 7 as PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, keyframes per beat, texts, colours, crops.

## 7. NEVER DO
Never invent content; never change the design; never stretch images; never deliver unchecked frames; never ask about anything beyond missing or invalid parameters.
