# 115 · Orchid Halo

## Results
**Same footage, styled by Claude.** Nothing was replaced, recoloured or retimed: Claude only added low captions where one word per phrase lands as a large glowing italic.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/115-caption-orchid-halo.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

A caption style for untouched full-frame video. Short phrases appear low on the screen in heavy white sans, one word at a time, exactly when you say them. In every phrase one key word lands as a big italic serif in a soft glowing gradient, tucked right against the small white words, and the whole phrase fades away before the next one begins. It reads like a clean, premium talk-show caption with one bright pop per line.

**Give it:**
- a video + its captions → it adds the caption style to your video without changing the footage;
- an image + text → a poster in this style;
- just a script → it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it, then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: a scene map with timestamps, every caption chunk with its glowing word, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, keep faces clear, choose one accent word per phrase and place captions without changing your video.
- [moments.md](moments.md) holds the style bible (palette, type, layout, motion) and 7 caption moments, from the halo stack to the end hold.

**Try it:**

```
/motion-graphics-skills:115-caption-orchid-halo
Add this caption style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
