---
name: 107-graphics-tilted-page-ink-chain
description: Makes the "Tilted Page Ink Chain" animated graphic (three paragraphs on a tilted paper page, three key words circled in hand-drawn ink and linked by curved arrows while the camera glides word to word) from the user's own text, as a finished 9:16 video. Use when the user wants a circled-keyword explainer, highlight-the-key-words text reel, ink annotation chain or marked-up page animation.
---

# 107 · Tilted Page Ink Chain

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Paragraph 1 (220–320 chars) | yes | none |
| P2 | Key word 1 (in paragraph 1) | yes | none |
| P3 | Paragraph 2 | yes | none |
| P4 | Key word 2 | yes | none |
| P5 | Paragraph 3 | yes | none |
| P6 | Key word 3 | yes | none |
| P7 | Ink colour | no | #1F1F1F |
| P8 | Paper tone | no | #F4F4F4 |
| P9 | Text greys | no | #3A3A3A / #747474 / #B4B4B4 |
| P10 | Tilt | no | 10 degrees |

### 2.2 Read everything the user gave
Read the message, documents and brand assets. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Paragraph 1 (220–320 characters)", "Key word 1 (one word that appears in paragraph 1)"). Mention optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Each key word occurs in its paragraph; paragraph lengths fit (else ask to shorten); colours are hex with strong contrast to the paper.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Text never overlaps another block; circles stay on their words.
- Output: 1080×1920, 30 fps, 7.2 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: lay out the paragraphs, find each key word box.
- Step 3: Build every frame from description.md at 1080×1920 (2x supersampled strokes, 7-sample motion blur) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus frames at every beat's end. Look at them. Checklist: every value on screen and spelled exactly; circles around the right words; arrows land on circles; nothing clipped badly; motion matches description.md. Fix and re-render.
- Step 5: Deliver `tilted-page-ink-chain.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
Render the final settled frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, stroke draw-on times, text, colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
