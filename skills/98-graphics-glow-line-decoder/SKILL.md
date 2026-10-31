---
name: 98-graphics-glow-line-decoder
description: Makes the "Glow Line Decoder" animated graphic (a glowing two-line headline over six list lines that go from blur to pixel mosaic to sharp text while the camera zooms in and scrolls down) from the user's own text and colours, as a finished 16:9 video. Use when the user wants a glowing text list reveal, six key points decoding on black, a pixelated-to-sharp text hook or a scrolling checklist intro.
---

# 98 · Glow Line Decoder

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Headline line 1 (≤ 24 chars) | yes | none |
| P2 | Headline line 2 (≤ 24 chars) | yes | none |
| P3–P8 | List lines 1 to 6 (≤ 14 chars each) | yes | none |
| P9 | Headline colour | no | #FDFE00 |
| P10 | List colour | no | #FFFFFF |
| P11 | Background | no | #000000 |

### 2.2 Read everything the user gave
Read the message, attached files and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Headline, 2 lines (max 24 characters each)", "6 list lines (max 14 characters each)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex with strong contrast to the background.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Text auto-fits and never leaves the frame.
- Output: 1920×1080, 30 fps, 6.03 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fit fonts, pre-render the placeholder, mosaic and sharp looks of each line with glow.
- Step 3: Build every frame from description.md at 1920×1080 (world at 3.2 px per unit, sub-frame motion blur), streaming into `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at every beat's end. Look at them. Checklist: every value on screen and spelled exactly; nothing clipped; the mosaic stage is visible; lines sharpen in order; motion matches description.md. Fix and re-render.
- Step 5: Deliver `glow-line-decoder.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: text layers with glow, pixelate effect keyframes, camera keyframes from description.md section 4, text and colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
