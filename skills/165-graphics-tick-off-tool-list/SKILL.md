---
name: "165-graphics-tick-off-tool-list"
description: "Makes the \"Tick-Off Tool List\" animated graphic (a light app-style checklist page with a title, five rows of icon tile, bold name and two short description lines, and a checkbox on the right that ticks row by row, with a barely-there camera drift) from the user's own titles, row texts, icons and colours, as a finished 9:16 video. Use when the user wants an install list, setup checklist, tool stack screen, step-by-step status list or animated to-do table."
---

# 165 · Tick-Off Tool List

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Title prefix (grey, ≤ 10 chars) | yes | none |
| P2 | Title (bold, ≤ 24 chars) | yes | none |
| P3 | Five row names (≤ 14 chars each) | yes | none |
| P4 | Five role lines (≤ 28 chars each) | yes | none |
| P5 | Five reason lines (≤ 30 chars each) | yes | none |
| P6 | Five icons (emoji, one letter, or image per row) | no | drawn generic glyph or first letter |
| P7 | Column header labels | no | ITEM / DONE |
| P8 | Tick colour | no | #222222 (measured) |
| P9 | Icon tile colours | no | one soft gradient per row |
| P10 | Page tone | no | #ECEAE3 |
| P11 | Tick times | no | 1.55, 2.47, 3.27, 3.97, 4.77 s |

### 2.2 Read everything the user gave
Map messages, lists, images and brand assets to parameters using description.md 2.1. State the mapping in a short list.
### 2.3 Check completeness
If a required parameter is missing, ask for all missing ones in one numbered message with limits. Mention optional ones in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Image icons: any size, cover-fit into the tile. Colours as hex with strong contrast against the page.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: layout, timing, motion exactly as description.md.
- Only the user's words on screen.
- Always five rows. No brand logos drawn by you: use neutral glyphs, letters, emoji or the user's images.
- Text auto-fits and never collides with the checkbox or the icon.
- Output: 1080×1920, 30 fps, 6.7 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: draw or crop the five icon tiles, fit text.
- Step 3: Build every frame from description.md (static layers at 2x, rows pre-rendered, checkboxes redrawn per frame at 4x) and encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (fps 2) plus the frames at every tick. Look at them. Fix and re-render.
- Step 5: Deliver `tick-off-tool-list.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final table, one line on what can be changed.

## 5. STILL MODE
Render the settled frame (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, stagger and tick keyframes from description.md section 5, text, colours.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
