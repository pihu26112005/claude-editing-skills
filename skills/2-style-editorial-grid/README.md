# 2 · Editorial Grid

## Results

**Same footage, styled by Claude.** Every shot plays in real time inside the cards: nothing was replaced, recoloured or retimed. Claude only placed the footage in cards on a white page, moved the cards, and added the typography.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/2-style-editorial-grid.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

A quiet, gallery-white page where your footage lives inside sharp-cornered cards. The video opens full-frame and settles into a centred card while a tiny, widely spaced keyword types on above it. Monospaced uppercase captions appear word by word in a white bar.

On every cut the cards rearrange. One card swells, then splits into an asymmetric grid: a portrait card plus a landscape card bleeding off the edge. Later cuts mirror it or stack it, with small step numbers counting off a list. The ending is one huge, bold black word with a typed tagline under the still-playing footage.

There's no colour except your footage, no bounce and no shadows: precision is the decoration.

**Give it:**
- a video plus its captions, and it adds the style to your video without changing the footage;
- an image plus text, and it makes a poster in this style;
- just a script, and it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it, then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: a scene map with timestamps, every layout change, which footage goes in which card, all typography, exact caption lines with times, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, plan a card for every shot, find hook points, and place moments without breaking your video.
- [moments.md](moments.md) holds the style bible (palette, grid layouts, cards, typography, motion) and 15 moments measured from a reference video, from the opening card settle to the title page.

**Try it:**

```
/motion-graphics-skills:2-style-editorial-grid
Add this style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
