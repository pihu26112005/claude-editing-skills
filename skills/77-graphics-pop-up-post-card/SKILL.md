---
name: 77-graphics-pop-up-post-card
description: Makes the "Pop-up Post Card" animated graphic (a generic social post card that rises on black, types its text word by word, ticks a like counter with a burst, then drops away) from the user's own name, handle, text, avatar and counts, as a finished 16:9 video. Use when the user wants an animated post mockup, social post card, engagement counter animation, like-burst card or fake-feed post intro.
---

# 77 · Pop-up Post Card

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Display name (≤ 20 chars) | yes | none |
| P2 | Handle (≤ 20 chars) | yes | none |
| P3 | Post text (≤ 60 chars, 4 to 12 words) | yes | none |
| P4 | Avatar image | yes | none |
| P5 | Reply count | yes | none |
| P6 | Share count | yes | none |
| P7 | Like count (10 to 999) | yes | none |
| P8 | Accent colour | no | #ED2162 |
| P9 | Card colour | no | #FFFFFF |
| P10 | Stage colour | no | #000000 |
| P11 | Text colour | no | #0A0A0A |
| P12 | Meta colour | no | #6A7076 |

### 2.2 Read everything the user gave
Read the message, attached images, videos and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Post text (max 60 characters)", "Avatar image (any photo or logo; I'll crop it to a circle)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Avatar size (upscale with Lanczos if small). Colours as hex with strong contrast to the card. Counts are integers.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's words and numbers on screen.
- No real platform logos, names or badges. Use the neutral icons the spec defines.
- Avatar: cover-fit crop to a circle, never stretched.
- Text auto-fits and never overflows the card.
- Output: 1920×1080, 30 fps, 7.27 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: crop the avatar; measure and fit the post text.
- Step 3: Render every frame from description.md (3 px per unit, downscale 2×) streaming into ffmpeg `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (2 fps) plus the settled frame. Look at them. Checklist: every value on screen and spelled exactly; nothing clipped; counts end on the given numbers; the like burst lands on the heart; motion matches description.md. Fix and re-render.
- Step 5: Deliver `pop-up-post-card.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: card layers, keyframes from description.md section 5, text, colours and avatar crop.

## 7. NEVER DO
Never invent content or counts. Never change the design. Never use real platform branding. Never stretch the avatar. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
