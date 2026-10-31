# 5 · Depth Headline

## Results

**Same footage, styled by Claude.** The video itself is untouched: no crop, zoom or retime. Claude only added the headline words (cut out around the person so they sit behind him) and the captions.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/5-caption-depth-headline.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

One giant, ultra-condensed white word stands **behind the speaker**, like it's painted on the wall, with their head overlapping the letters. The instant that word is spoken it snaps to bright yellow with a soft see-through yellow box. Below, small bold captions light up word by word in yellow and leave the headline word out, because the giant word says it. Every change is an instant cut, timed to the speech and the footage's cuts.

Read the headlines alone and they tell the story: **MONEY · MORE · FIRST · AUTOMATE · LEFT · YEAR · WATCH · HAPPENS**.

**Give it:**
- a video plus its captions, and it adds the style to your video without changing the footage;
- an image plus text, and it makes a poster in this style;
- just a script, and it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it (with a person cut-out so the words sit behind them), then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: a scene map with timestamps, every headline word with its yellow-hit times, exact caption lines with times, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, group the words, pick the headline word for each beat, place it behind the person so it stays readable, and build it without touching your footage.
- [moments.md](moments.md) holds the style bible (palette, depth cut-out, typography, placement rungs, timing) and 6 moments measured from a reference video.

**Needs (for the final video):** Python with Pillow and NumPy, `ffmpeg`, and a person-segmentation model (MediaPipe selfie segmenter or rembg).

**Try it:**

```
/motion-graphics-skills:5-caption-depth-headline
Add this style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
