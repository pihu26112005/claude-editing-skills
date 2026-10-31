---
name: 103-graphics-thread-word-relay
description: Makes the "Thread Word Relay" animated graphic (a square, generic social-thread card that flickers through many different invented posters all writing the same word, one word at a time, to spell out a sentence) from the user's own words, handles and colours, as a finished 1:1 video. Use when the user wants a word-by-word comment flicker, thread match cut, crowd-says-it sentence reveal or fast avatar-swap text gag.
---

# 103 · Thread Word Relay

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Words (exactly 6, in order, ≤ 10 chars each) | yes | none |
| P2 | Handles (≥ 8 invented) | no | generated @user_NN |
| P3 | Avatars | no | procedural |
| P4 | Neighbour lines | no | skeleton bars |
| P5 | Accent colour | no | #2F7BE0 |
| P6 | Background colour | no | #FAFAFA |
| P7 | Text colour | no | #0F0F0F |
| P8 | Ages and like counts | no | generated |

### 2.2 Read everything the user gave
Read the message and attachments. Map each piece to parameters using description.md 2.1. State the mapping in a short list.
### 2.3 Check completeness
If P1 is missing or not 6 words, ask for it in one message ("A sentence of exactly 6 words, each up to 10 characters"). Mention the optional items in one line with defaults. Stop and wait.
### 2.4 Validate
Word length (auto-fit to 70%, else ask to shorten). Handles must be invented, never real people. Colours as hex with strong contrast to the background. Avatars: cover-fit circle crops.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's words in the focal slot. No real platform names, logos or people.
- Images: cover-fit circle crop, never stretched.
- Text auto-fits its box.
- Output: 1080×1080, 30 fps, 4.8 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: avatars, handle pool, neighbour lines.
- Step 3: Build 30 slot frames at 2× supersample, crossfade them per description.md section 5, encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (fps 4) plus a strip around one word change. Look at them. Checklist: each word spelled exactly and in the same position; nothing clipped except the allowed right-edge run-off; avatars round and whole; crossfades smooth. Fix and re-render.
- Step 5: Deliver `thread-word-relay.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
Render the last slot (description.md section 7) as a PNG at 1080×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: one fixed post template, 30 swaps of avatar, handle and word at 0.15 s, 0.08 s crossfades, blurred faded neighbours.

## 7. NEVER DO
Never invent content beyond handles and filler, never change the design, never use real platform branding, never deliver without looking at the frames, never ask about anything beyond missing or invalid parameters.
