---
name: 86-graphics-macro-screen-query-pan
description: Makes the "Macro Screen Query Pan" animated graphic (a generic search page seen up close on a pixel-grid monitor: the camera zooms into a rounded search bar, a query types in, then the camera pans along the bar to its magnifier icon and a cursor clicks toward it) from the user's own query text, title word and colours, as a finished 16:9 video. Use when the user wants a search-bar typing animation, query reveal, keyword hook, topic reveal on a screen, or a close-up monitor search intro.
---

# 86 · Macro Screen Query Pan

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements. Never add a real search engine's name, logo or colours.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Query text (≤ 32 chars, 1 line) | yes | none |
| P2 | Title word above the bar (≤ 8 chars) | no | Search |
| P3 | Title colour | no | #34495E |
| P4 | Ink colour (bar outline, text, icon, cursor outline) | no | #151515 |
| P5 | Screen tone | no | #B2B1B3 |
| P6 | Pixel-grid strength | no | 100% |
| P7 | Cursor | no | on |

### 2.2 Read everything the user gave
Read the message, attached files and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If P1 is missing, ask for it in one message with its limit ("Query text, max 32 characters, one line"). Mention the optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; ink must contrast strongly with the screen tone. Refuse a title that is a real search engine's name: pick a neutral word and say so.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout, motion and camera exactly as description.md.
- Only the user's words on screen.
- Generic page only: no real search engine logo, name, wordmark colours or branded layout. The title is a single flat colour.
- Text auto-fits and never collides with the bar edge or icon.
- The pixel grid and colour fringe sit in screen space and never move with the camera.
- Output: 1920×1080, 29.97 fps, 7.0 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fit the query and title text; draw the static page (title, bar, icon) at 4.2 px per unit with a mip pyramid.
- Step 3: Build every frame from description.md at 1920×1080, with sub-frame motion blur on moves, then the screen overlay. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30000/1001`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at 2.0 s, 5.3 s and 6.5 s. Look at them. Checklist: query spelled exactly; typing finishes by 1.9 s; text inside the bar; icon and cursor land together; pixel grid visible and fixed; motion matches description.md. Fix and re-render.
- Step 5: Deliver `macro-screen-query-pan.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled hold frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, camera keyframes from description.md section 4, typing times, text, colours and the pixel-grid overlay settings.

## 7. NEVER DO
Never invent content. Never change the design. Never use a real search engine's branding. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
