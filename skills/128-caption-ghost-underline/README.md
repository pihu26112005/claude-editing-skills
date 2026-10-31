# 128 · Ghost Underline

## Results

**Same footage, styled by Claude.** Nothing was replaced, recoloured or retimed: Claude only added a title and word-by-word captions with underlined italic keywords over the full-frame clip.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/128-caption-ghost-underline.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

A modern caption style with no boxes or effects on the footage. Each phrase sits in the middle of the frame and builds word by word: every word starts as a dim ghost-grey and firms up to heavy white within a fifth of a second. One key word per phrase switches to a slim serif italic in a pale tint and carries a thin gradient underline. Phrases cut away cleanly, a short italic title can open the video, and the last word can land alone, large.

**Give it:**
- a video + its captions → it adds the caption style to your video without changing the footage;
- an image + text → a poster in this style;
- just a script → it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it, then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: scene map with timestamps, exact caption lines with times and keywords, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, keep faces and edges clear, find hook points and place moments without breaking your video.
- [moments.md](moments.md) holds the style bible (palette, type, lane, motion) and 8 moments, from the ghost word build to the end hold.

**Try it:**

```
/motion-graphics-skills:128-caption-ghost-underline
Add this caption style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
