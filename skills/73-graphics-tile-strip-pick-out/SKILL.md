---
name: 73-graphics-tile-strip-pick-out
description: Makes the "Tile Strip Pick-Out" animated graphic (a tilted stream of 15 numbered rounded tiles flattens into a row, a hand cursor glides along it, hovers and clicks one tile, the strip fans away and the chosen tile settles large in the centre) from the user's own label word, chosen number and colours, as a finished 16:9 video. Use when the user wants a pick-one-from-many, choose-a-clip, select-an-item, cursor-click or numbered thumbnail strip animation.
---

# 73 · Tile Strip Pick-Out

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Label word (≤ 10 chars) | yes | none |
| P2 | Chosen number (1 to 15) | yes | none |
| P3 | Emblem (ring / peak / bars) | no | ring |
| P4 | Tile palette (15 hex) | no | measured purple to teal set |
| P5 | Background tone | no | navy #050B11 with blue glow |
| P6 | Label colour | no | #FFFFFF |
| P7 | Cursor | no | on |

### 2.2 Read everything the user gave
Read the message, attached images and brand assets. Map each piece to parameters using description.md section 2.1. A brand colour may seed the palette. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Label word (max 10 characters, e.g. the kind of item being picked)", "Chosen number (1 to 15)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Label length (auto-fit to 70%, else ask to shorten). Number is an integer from 1 to 15. Colours are hex and the label stays readable on every tile.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's label word on screen, plus the "No.<number>" lines the graphic defines.
- Exactly 15 tiles. Tile 1 rightmost and in front at rest.
- Text auto-fits its tile and never overflows.
- Output: 1920×1080, 30 fps, 6.0 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: build the 15 tile sprites (palette, emblem, text fitted), the hand cursor and the background glow.
- Step 3: Build every frame from description.md at 1920×1080 (tile layer at 2×, sub-frame motion blur) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus one strip around the lift and fan-away (3.6 to 5.2 s). Look at them. Checklist: label and numbers spelled exactly; the chosen tile is the requested number; nothing clipped or ghosted; the cursor lands on the chosen tile and is gone after the lift; motion matches description.md. Fix and re-render.
- Step 5: Deliver `tile-strip-pick-out.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: 15 tile layers with the keyframes of description.md section 5, the cursor path, text, colours and emblem.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
