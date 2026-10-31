# 130 · Whisper Blob

## Results

**Same footage, styled by Claude.** Nothing was replaced, recoloured or retimed: Claude only added captions, each phrase split into tiny hand-written words and one fat colourful keyword that hops between the top and bottom of the frame.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/130-caption-whisper-blob.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

A caption style for creator videos. Every phrase becomes two layers: a tiny hand-brushed white whisper line for the small connecting words, and one big, fat, rounded keyword in a saturated colour (orange, white or cyan in the demo) sitting on a solid dark shadow. The keyword is bent into an arch or a wave and rises softly into place; the whisper words pop in one by one above it. The footage stays full frame and untouched, and the captions jump between the top and the bottom lane so they never cover the speaker's face.

**Give it:**
- a video + its captions → it adds the style to your video without changing the footage;
- an image + text → a poster in this style;
- just a script → it asks about your story, then writes a Flow master prompt or builds a typography-only video.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it, then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: scene map with timestamps, every caption line with times and colours, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, choose lanes that keep your face clear, chunk the captions and place moments.
- [moments.md](moments.md) holds the style bible (palette, slab, type, motion) and 9 moments, from the whisper line to the end hold.

**Try it:**

```
/motion-graphics-skills:130-caption-whisper-blob
Add this caption style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
