# 48 · Podcast Headline

## Results
**Same footage, styled by Claude.** Nothing was replaced, recoloured or retimed: Claude only added one fixed hook headline at the top and clean word-by-word captions low in the frame.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/48-caption-podcast-headline.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

The classic podcast-clip look, as a caption style. One bold two-line headline, the hook of your clip (by default its opening sentence), fades in at the top and stays there. It is made of: the first line in white lettering straight on the footage, the second in black on a crisp white box. The headline words are not repeated; underneath, bold white captions carry the rest of the script word by word low in the frame, switch to black-on-white box captions on busy shots, and flip one key word into its own white box for emphasis. The footage stays full-frame and untouched, with plain hard cuts.

**Give it:**
- a video + its captions → it adds the style to your video without changing the footage;
- an image + text → a poster in this style;
- just a script → it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it, then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: a scene map with timestamps, every headline and caption line with times, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, keep your face clear of the headline, find hook points, and place moments without breaking your video.
- [moments.md](moments.md) holds the style bible (palette, white boxes, type, motion) and 8 moments, from the two-line headline stack to the end hold.

**Try it:**

```
/motion-graphics-skills:48-caption-podcast-headline
Add this caption style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
