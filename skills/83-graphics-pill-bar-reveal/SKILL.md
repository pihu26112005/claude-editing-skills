---
name: 83-graphics-pill-bar-reveal
description: Makes the "Pill Bar Reveal" animated graphic (a round search-icon bubble rises on a soft radial-gradient background, stretches into a pill-shaped search bar, the user's text fades in word by word, then the bar swells and shrinks away) from the user's own text and colours, as a finished 16:9 video. Use when the user wants an expanding search bar, search-box intro, icon-to-bar reveal or query-typing title on a pastel gradient.
---

# 83 · Pill Bar Reveal

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements. Never add a real search-engine or brand logo, name or colours.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Main text (≤ 24 chars) | yes | none |
| P2 | Icon colour | no | #CDA8EA |
| P3 | Pill colour | no | #F4EBF9 |
| P4 | Text colour | no | #322C35 |
| P5 | Gradient inner colour | no | #D6B0ED |
| P6 | Gradient outer colour | no | #F1E5FA |

### 2.2 Read everything the user gave
Map message, images and brand assets to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If P1 is missing, ask for it in one message ("Main text, max 24 characters, ideally 2 to 4 words"). Mention the colour options in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; text and icon need strong contrast with the pill.
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's words on screen. The icon is a plain generic magnifier, never a real brand mark.
- Text auto-fits and is clipped by the pill; it never leaves the bar.
- Output: 1920×1080, 30 fps, 7.77 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare: measure the text at Inter Medium (opsz 14) 64 px, fit it, compute the final pill width.
- Step 3: Build every frame from description.md at 1920×1080 (pill group drawn at 2× then downscaled), stream to `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (4 fps) plus the frames at 1.2 s, 2.4 s, 3.5 s and 4.9 s. Look at them. Checklist: text spelled exactly; handle swings from down-left to down-right; nothing clipped; clean fade-out.
- Step 5: Deliver `pill-bar-reveal.mp4`, the final parameter table, and one line on what can be changed.

## 5. STILL MODE
Render the settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: layers, keyframes from description.md section 5, colours and text.

## 7. NEVER DO
Never invent content. Never change the design. Never use a real search brand's logo, name or colours. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
