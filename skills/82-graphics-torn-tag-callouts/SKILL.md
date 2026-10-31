---
name: 82-graphics-torn-tag-callouts
description: Makes the "Torn Tag Callouts" animated graphic (a glowing striped two-word label rises on a dark violet glow, tears in two along a zigzag crack, the halves tilt apart and change colour, and each half gets a dashed looping leader line with a bold italic callout) from the user's own words and colours, as a finished 16:9 video. Use when the user wants a split label, torn banner, two-word breakup title, glowing striped tag, or callout leader-line intro.
---

# 82 · Torn Tag Callouts

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Left word (≤ 12 chars) | yes | none |
| P2 | Right word (≤ 12 chars) | yes | none |
| P3 | Callout 1, over the left half (≤ 14 chars) | yes | none |
| P4 | Callout 2, over the right half (≤ 14 chars) | yes | none |
| P5 | Start colour (whole label before the tear) | no | #FF9419 |
| P6 | Left half colour | no | #FF0A14 |
| P7 | Right half colour | no | #09FB02 |
| P8 | Background glow colour | no | #4A08C0 |
| P9 | Leader line colour | no | #FFFFFF |

### 2.2 Read everything the user gave
Read the message, attached files and brand assets. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Left word (max 12 characters)", "Callout 1 (max 14 characters)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; the two half colours must differ clearly from each other and from the start colour. Dark label text must stay readable on every colour.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Text auto-fits and never leaves the label or collides with leader lines.
- Output: 1920×1080, 30 fps, 11.5 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: build the label sprite (rounded rect, diagonal stripes, text, crack mask), the two leader paths and the background at 2x.
- Step 3: Build every frame from description.md at 1920×1080 with sub-frame motion blur on the fast moves, streaming frames into `ffmpeg -c:v libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`. Use one worker and never hold all frames in memory.
- Step 4: Check: a contact sheet (2 fps) plus the frames at the end of every beat. Look at them. Checklist: both words and both callouts spelled exactly; the crack falls in the gap between the words; nothing clipped; leaders end on their half; colours match the parameters; motion matches description.md. Fix and re-render.
- Step 5: Deliver `torn-tag-callouts.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, crack and tilt keyframes, colour flashes, leader draw-on times, text and colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
