---
name: 64-graphics-tabletop-card-fan
description: Makes the "Tabletop Card Fan" animated graphic (one card slides onto a table and fans into five, then a tilting camera tours them while three captions type onto the table) from the user's own captions and colours, as a finished 16:9 video. Use when the user wants a card spread, tarot-style reveal, three-step explainer on playing cards, or a tabletop camera tour with captions.
---

# 64 · Tabletop Card Fan

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Caption 1 (≤ 16 chars) | yes | none |
| P2 | Caption 2 (≤ 16 chars) | yes | none |
| P3 | Caption 3 (≤ 16 chars) | yes | none |
| P4 | Card-back artwork | no | generated ornament |
| P5 | Card ink colour | no | #3C280F |
| P6 | Card edge colour | no | #EDD2B2 |
| P7 | Caption colour | no | #5C4225 |
| P8 | Table colour | no | #AA9F8B |

### 2.2 Read everything the user gave
Read the message, attached images and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a caption is missing, ask for all missing ones in one numbered message with limits (for example "3 captions, max 16 characters each, in reading order"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Artwork size (warn and upscale with Lanczos). Colours as hex; captions need strong contrast against the table.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Artwork: cover-fit crop only, never stretched, same on all five cards.
- Captions auto-fit and never overlap.
- Output: 1920×1080, 30 fps, 10.1 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: card texture (700×1000 px), caption masks.
- Step 3: Build every frame from description.md at 1920×1080 with the pinhole camera and sub-frame motion blur; encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus the frames at the end of every beat. Look at them. Checklist: captions spelled exactly; nothing clipped or overlapping; card art intact with no transparent gaps; camera motion matches description.md. Fix and re-render.
- Step 5: Deliver `tabletop-card-fan.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the final wide view (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: card layers on a 3D plane, camera keyframes from description.md section 4, caption type-on times, colours.

## 7. NEVER DO
Never invent content. Never change the design. Never stretch artwork. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
