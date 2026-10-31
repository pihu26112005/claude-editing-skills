---
name: 108-graphics-highlight-snippet-flicker
description: Makes the "Highlight Snippet Flicker" animated graphic (one marker-highlighted keyword that stays fixed while nine article snippets flip past at about ten cuts a second on crumpled paper, with streaked edges and blurred body text) from the user's own keyword and sentences, as a finished 9:16 video. Use when the user wants a keyword flip-through, highlighted term montage, headline snippet flicker or "everyone is talking about X" effect.
---

# 108 · Highlight Snippet Flicker

## 1. YOUR JOB
You make one animated graphic. Its design is fixed in description.md. Collect the parameter values, check them, render the graphic exactly as specified, check the frames, and deliver. Never change the beats, layout, timing or motion. Never add elements.

## 2. COLLECT THE PARAMETERS
### 2.1 Parameters
| ID | Parameter | Required | Default |
|---|---|---|---|
| P1 | Keyword (≤ 14 chars) | yes | none |
| P2-P10 | Snippets 1 to 9 (lead, tail, aside each) | yes | none |
| P11 | Page title | no | the keyword |
| P12 | Byline name | no | Staff writer |
| P13 | Sub-line | no | none |
| P14 | Tags | no | News, Features, Nature |
| P15 | Highlight colour | no | #D9E23C |
| P16 | Paper colour | no | #ECECE8 |
| P17 | Ink colour | no | #18181A |

### 2.2 Read everything the user gave
Read message, documents and brand assets. Map pieces to parameters using description.md section 2.1 (sentences containing the keyword become snippets). State the mapping in a short list.
### 2.3 Check completeness
If anything required is missing, ask for all of it in one numbered message with limits ("Keyword (max 14 characters)", "9 sentences containing it, or just the words before and after it"). Mention optional items in one line with defaults. Stop and wait.
### 2.4 Validate
Text length (auto-fit to 70%, else ask to shorten). Colours as hex; ink must contrast with the highlight.
### 2.5 Complete input
If everything came in the first message, ask nothing and start. Never ask about anything that is not a parameter.

## 3. HARD RULES
- Same graphic for every user: layouts, hold lengths, cuts and blur exactly as description.md.
- Only the user's words on screen, plus the fixed labels the spec lists.
- Hard cuts between snippets; nothing moves inside a hold.
- Text auto-fits; the keyword never clips.
- Output: 1080×1920, 30 fps, 2.3 s.

## 4. WORKFLOW
- Step 1: Collect and validate. Write a table with final values.
- Step 2: Prepare assets: fonts, paper texture, snippet text, keyword fit.
- Step 3: Build the nine snippets once, then write frames by the hold table, supersampling text where possible. Encode `libx264 -crf 16 -preset slow -pix_fmt yuv420p -r 30`.
- Step 4: Check: a contact sheet of one frame per snippet plus one full-size frame. Look at them. Checklist: keyword spelled right and highlighted in every snippet; box position matches the table; edges smeared, centre sharp; nothing overlaps; hold lengths right. Fix and re-render.
- Step 5: Deliver `snippet-flicker.mp4`, the final parameter table, and one line on what can be changed.

## 5. STILL MODE
Render snippet S1 (description.md section 7) as a PNG at 1080×1920.

## 6. NO CODE EXECUTION
Give an editor build sheet: paper layer, nine snippet comps with cut times from the hold table, highlight boxes, edge blur settings.

## 7. NEVER DO
Never invent content or use any reference content. Never change the design. Never add fades. Never deliver without looking at the frames. Never ask about anything beyond missing or invalid parameters.
