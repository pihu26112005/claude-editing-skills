---
name: 109-graphics-shattered-front-page-pullback
description: Makes the "Shattered Front Page Pullback" animated graphic (a newspaper front page cut into nine ragged pieces that drift apart and snap back together while the camera pulls out from a giant headline close-up to the whole page) from the user's own masthead, headline, subhead and photo, as a finished 1:1 video. Use when the user wants a newspaper headline reveal, front-page intro, breaking-news card, cracked-paper headline or pieces-coming-together title.
---

# 109 · Shattered Front Page Pullback

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Masthead (≤ 22 chars) | yes | none |
| P2 | Headline line 1 (≤ 12 chars) | yes | none |
| P3 | Headline line 2 (≤ 12 chars) | yes | none |
| P4 | Subhead (≤ 90 chars) | yes | none |
| P5 | Photo | yes | none |
| P6 | Edition tag (≤ 14 chars) | no | EXTRA |
| P7 | Dateline (≤ 28 chars) | no | blank |
| P8 | Photo caption (≤ 48 chars) | no | blank |
| P9 | Body text | no | grey placeholder lines |
| P10 | Tag colour | no | #D8452E |
| P11 | Paper colour | no | #D3C2A7 |
| P12 | Ink colour | no | #28221D |
| P13 | Underlay grey | no | #B8B8BB |

### 2.2 Read everything the user gave
Read the message, attached images and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits (for example "Masthead (max 22 characters)", "Headline in 2 lines (max 12 characters each)", "Subhead (max 90 characters)", "1 photo (any aspect; I'll crop it and turn it sepia)"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Photo short side at least 500 px (warn and upscale with Lanczos if small). Colours as hex with strong contrast between ink and paper.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen. Empty optional text stays empty; body text without P9 is grey placeholder lines, never invented words.
- Photo: cover-fit crop only, never stretched, centred or on the user's focal hint. Sepia treatment as specified.
- Text auto-fits its box and never overflows.
- Output: 1080×1080, 30 fps, 7.0 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fit text, crop and treat the photo, draw the full page at 4× (3420×2548).
- Step 3: Split the page into nine pieces, build each piece's edge, shadow and mip levels, then render every frame from description.md at 1080×1080 (3 sub-frames per frame for motion blur) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30` with a silent AAC track.
- Step 4: Check: a contact sheet (2 fps) plus frames at 0, 2.6, 3.4 and 5.5 s. Look at them. Checklist: every value on screen and spelled exactly; headline readable at the end; no text clipped by the page edge; pieces re-form the page; cracks thin at the end; motion matches description.md. Fix and re-render.
- Step 5: Deliver `shattered-front-page-pullback.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled page (description.md section 7) as a PNG at 1080×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: the page as one layered artwork cut into nine shards, camera keyframes from description.md section 4, shard keyframes from section 5, text, colours and photo crop.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never stretch the photo. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
