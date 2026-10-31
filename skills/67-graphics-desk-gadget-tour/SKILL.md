---
name: 67-graphics-desk-gadget-tour
description: Makes the "Desk Gadget Tour" animated graphic (a title typed on a handheld gadget on a grid desk, a full camera whirl, then a two-line headline typed on the paper) from the user's own text and colours, as a finished 9:16 video. Use when the user wants a gadget screen title reveal, desk flat-lay intro, typed headline over graph paper, or a vertical app or product teaser opener.
---

# 67 · Desk Gadget Tour

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Screen text (≤ 14 chars) | yes | none |
| P2 | Headline line 1 (≤ 22 chars) | yes | none |
| P3 | Headline line 2 (≤ 20 chars) | yes | none |
| P4 | Footer text | no | none |
| P5 | Edge label | no | none |
| P6 | Gadget colour | no | #1E1E1E |
| P7 | Paper colour | no | #E4E4E4 |
| P8 | Text colour | no | #0A0A0A |
| P9 | Edge label colour | no | #C9A45C |
| P10 | Grid | no | on |
| P11 | Desk props | no | on |

### 2.2 Read everything the user gave
Read the message, attached images and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Screen text (max 14 characters)", "Headline line 1 (max 22 characters) and line 2 (max 20), line 2 finishes the thought"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; text and gadget screen must contrast with the paper.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Text auto-fits and never overflows the screen or the frame.
- Output: 1080×1920, 30 fps, 6.53 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: draw props, gadget and text sprites; fit text.
- Step 3: Build every frame from description.md at 1080×1920 (analytic grid, warped sprites, sub-frame motion blur) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at every beat's end. Look at them. Checklist: every value on screen and spelled exactly; text typed in the right order; nothing clipped; headline clear of props; whirl without banding; motion matches description.md. Fix and re-render.
- Step 5: Deliver `desk-gadget-tour.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final settled frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, typing times, text, colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
