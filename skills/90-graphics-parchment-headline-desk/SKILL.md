---
name: 90-graphics-parchment-headline-desk
description: Makes the "Parchment Headline Desk" animated graphic (a dated tag, a two-line headline and a detail paragraph typing onto grid parchment, a cut-out portrait rising from the corner, a rule with a masthead line, then marker highlights sweeping over the text) from the user's own text and portrait, as a finished 16:9 video. Use when the user wants a news-style headline card, vintage story intro, parchment explainer, highlighted headline reveal or character intro on old graph paper.
---

# 90 · Parchment Headline Desk

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Date tag text (≤ 14 chars) | yes | none |
| P2 | Headline (≤ 70 chars, 2 lines) | yes | none |
| P3 | Detail text (≤ 170 chars, 2 lines) | yes | none |
| P4 | Masthead line (≤ 22 chars) | yes | none |
| P5 | Portrait image (cut-out) | yes | none |
| P6 | Detail highlight phrase | no | auto (middle of line 1) |
| P7 | Tag colour | no | #D01010 |
| P8 | Highlight colour | no | #F6C500 |
| P9 | Text colour | no | #141210 |
| P10 | Paper colour | no | #C2A878 |
| P11 | Grid | no | on |

### 2.2 Read everything the user gave
Read the message, attached images and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Headline (max 70 characters)", "Portrait (a cut-out of one person or subject on a transparent background works best; any photo is accepted)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Portrait at least 700 px tall (else warn, upscale with Lanczos). The highlight phrase must sit inside one line of the detail text. Colours as hex with strong contrast to the paper.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's words on screen. The masthead is the user's own text, never a real publication unless the user supplies it.
- Portrait: scaled to the box height, never stretched, bottom-right anchored. Black and white treatment unless the user asks for colour.
- Text auto-fits and never collides with the portrait, the rule or the tag.
- Output: 1920×1080, 30 fps, 13 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: load the portrait (RGBA), convert to B&W, measure and fit text, build per-word and per-letter sprites at 2x.
- Step 3: Build every frame from description.md at 1920×1080 and pipe to `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus the frames at 2.8 s, 5.0 s and 9.0 s. Look at them. Checklist: every value on screen and spelled exactly; text inside its boxes; portrait not covering text; highlight sits behind the right words; rule and masthead aligned. Fix and re-render.
- Step 5: Deliver `parchment-headline-desk.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, per-beat keyframes from description.md section 5, text, colours and portrait placement.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never stretch the portrait. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
