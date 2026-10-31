---
name: 80-graphics-flare-sweep-title
description: Makes the "Flare Sweep Title" animated graphic (one bold glowing headline typed on letter by letter over a dark stage, smeared and lit by a sunburst flare at its leading edge, held, then flared again and faded out) from the user's own text and colours, as a finished 16:9 video. Use when the user wants a glowing title, neon headline reveal, light-streak text intro, flare title card or blurred shining text opener.
---

# 80 · Flare Sweep Title

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Headline text (≤ 12 chars, 1 line) | yes | none |
| P2 | Text colour | no | #FCFD00 |
| P3 | Hot tint (new letters, flare core) | no | #FF9A00 |
| P4 | Stage tone (centre / edge) | no | #232120 / #121113 |
| P5 | Sunburst rays | no | on |
| P6 | Exit flare and fade | no | on |
| P7 | Stage rings | no | on |

### 2.2 Read everything the user gave
Read the message, attached images and documents. Map each piece to parameters using description.md section 2.1. State the mapping in a short list.
### 2.3 Check completeness
If the headline is missing, ask for it in one message with its limit ("Headline text, max 12 characters, one line"). Mention the optional ones in one line with defaults ("yellow text on a dark stage, with the exit flare, unless you want different"). Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; the text colour must be bright against the stage (else say so and suggest the default).
### 2.5 Complete input
If everything came in the first message, ask nothing and start.
Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: beats, timing, layout and motion exactly as description.md.
- Only the user's words on screen. Text is set in capitals.
- Text is drawn by code with the specified font, centred, auto-fitted, never clipped.
- Output: 1920×1080, 30 fps, 4.33 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fit the font size, pre-render one mask per letter, build the stage.
- Step 3: Build every frame from description.md at 1920×1080 (flare layers at half resolution), stream into `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet (fps 3) plus the frames at 0.85 s, 2.0 s and 3.3 s. Look at them. Checklist: text spelled exactly; centred; no clipping; the flare smear has no stepped ghost copies; the text is fully crisp during the hold; the stage ends empty.
- Step 5: Deliver `flare-sweep-title.mp4` (claude.ai: `/mnt/user-data/outputs/`), the final parameter table, and one line on what can be changed.

## 5. STILL MODE
If the user wants an image, render the settled frame (description.md section 7) as a PNG at 1920×1080.

## 6. NO CODE EXECUTION
Give an editor build sheet: type-on times, blur and glow keyframes from description.md section 5, colours, font.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
