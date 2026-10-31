# 7 · Cutout Board

## Results

**Same footage, styled by Claude.** Every shot plays in real time: nothing was recoloured or retimed, and the people and objects are the original footage. Claude only matted the subject onto a cutting mat for two short beats and added the typography.

![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/7-style-cutout-board.gif)

Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)

## The style

A designer's desk. On the key statement the background snaps away and the speaker becomes a sticker, with a thick, hand-cut yellow outline that wobbles like stop-motion. The sticker sits on a green cutting mat with a grid, crop marks and tiny yellow dots.

Captions mix three voices: small elegant serif words, one hot-pink highlighter tag, and one giant ultra-wide black word on a long white label strip. Each caption group jumps to a new empty spot in the frame. Everything snaps on and off like paper on a board.

**Give it:**
- a video plus its captions, and it adds the style to your video without changing the footage;
- an image plus text, and it makes a poster in this style;
- just a script, and it asks about your story, then writes a Flow master prompt or builds a typography-only video on the cutting mat.

**Choose what you get back.** Once Claude has everything it needs, it asks one question:

| Option | What you get |
|---|---|
| **Final video / image** | Claude edits and renders it (including the sticker cutouts), then checks the frames before handing it over |
| **Master prompt for Google Flow** | One detailed prompt per clip: a scene map with timestamps, exactly when the cutting-mat moments happen, every caption group with its serif, pink and giant words, placement and times, the allowed-words list and things to avoid. Plus an SRT backup |

**What's inside:**
- [SKILL.md](SKILL.md) tells Claude how to read your input, test the cutout matte per shot, choose the pink and giant words, and place moments without breaking your video.
- [moments.md](moments.md) holds the style bible (mat, sticker outline, palette, typography, caption composition, motion) and 8 moments measured from a reference video, from the board pop to the giant label word.

**Needs (for final videos):** Python with Pillow, NumPy and `onnxruntime`, plus the 4.6 MB `u2netp.onnx` matting model (Claude downloads it if missing), and `ffmpeg`.

**Try it:**

```
/motion-graphics-skills:7-style-cutout-board
Add this style to my video. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
[attach video]
```
