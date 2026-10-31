---
name: 72-graphics-step-ink-scroll
description: Makes the "Step Ink Scroll" animated graphic (three oversized, ink-worn capital headlines on crumpled paper that snap sideways in five hard steps to reveal their endings) from the user's own three headlines, as a finished 16:9 video. Use when the user wants a stacked headline reveal, ticker-style title pan, distressed typewriter-ink headline sequence, or old-paper title cards.
---

# 72 · Step Ink Scroll

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Headline 1 (top, soft; 16–26 chars) | yes | none |
| P2 | Headline 2 (middle, sharp; 16–26 chars, 2+ words) | yes | none |
| P3 | Headline 3 (bottom, soft; 16–26 chars) | yes | none |
| P4 | Ink colour | no | #000000 |
| P5 | Paper colour | no | #AFAFA1 |
| P6 | Ink wear | no | on |

### 2.2 Read everything the user gave
Read the message and any attachments. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Three headlines, 16–26 characters each; the middle one is the hero"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten; under 16 characters, ask for a longer line, because the lines must run past the frame edge). Colours as hex; ink must be dark and contrast with the paper.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: layout, step timing and offsets exactly as description.md.
- Only the user's words on screen, in capitals.
- Text auto-fits and rows never overlap.
- All steps are hard cuts: no easing, no blur between them.
- Output: 1920×1080, 30 fps, 3.93 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load Cinzel (variable, wght 760), measure and fit each line.
- Step 3: Build the six distinct images from description.md at 1920×1080 (lines at 2× then downscaled), write the 118 frames from the step schedule, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus the final frame at full size. Look at them. Checklist: every headline spelled exactly; lines overflow the right edge at t=0; middle line sharp, others soft; five steps visible; final lines not clipped on the left except by the pan; nothing overlapping. Fix and re-render.
- Step 5: Deliver `step-ink-scroll.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: three text layers, layer positions, the five hard-cut position keyframes from description.md section 4, blur on layers 1 and 3, colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
