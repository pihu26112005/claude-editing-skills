# 125 · Stacked Pop Tags

## Results

**Same footage, styled by Claude.** Nothing in the video is replaced, recoloured or retimed: Claude only added a caption system of tiny stacked helper words around one big slanted keyword per phrase.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/125-caption-stacked-pop-tags.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

A caption style for creator-style talking videos. Each phrase builds as a small stack: tiny white wide-sans helper words, some dropped a notch lower, around one huge slanted condensed keyword in a hot accent colour with a hard shadow. The keyword slides in from the side, the stack sits low on the screen (or up top when the shot has no face there), switches sides from phrase to phrase, and hard-cuts to the next one. The footage stays full frame and untouched.

**Give it:**
- a video + its captions → it adds the caption style to your video without changing the footage;
- an image + text → a poster in this style;
- just a script → it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it, then checks the frames before handing it over |
| **Master prompt for Google Flow** | One prompt per clip: scene map with timestamps, every caption line with keyword and lane, allowed-words list and things to avoid, plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) — how Claude reads your input, picks keywords and lanes that keep your face clear, and builds the captions without breaking your video.
- [moments.md](moments.md) — style bible + 7 moments measured from a reference video, from the stacked phrase to the end hold.

**Try it:**

```
/motion-graphics-skills:125-caption-stacked-pop-tags
Add this caption style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
