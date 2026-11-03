---
name: 159-photo-painted-portrait
description: Step 1 of the Motion Photos pair. Turns one ordinary photo into the exact prompt (and, when an image tool is available, the image) for a dramatic, textured oil-painting version of it, keeping the same people, faces, pose, clothing and composition. Its output is the input of 160-photo-living-painting. Use when the user wants their photo painted as a moody oil painting or wants to make a motion photo or living painting.
---

# 159 · Painted Portrait (Motion Photos, step 1)

## 1. YOUR JOB
Make the painted still that step 2 (`160-photo-living-painting`) animates. The look is fixed: an expressive, dramatic, thick impasto oil painting with loose brushwork, a refined face, smoky painterly background and moody chiaroscuro colour. Identity, pose and composition never change.

You cannot paint pixels yourself. Do one of these:
- **An image generation or editing tool is available in this session:** send the user's photo with the PAINTING PROMPT below and return the result.
- **No image tool (normal case):** give the user the PAINTING PROMPT, ready to paste with their photo into an image model that edits images (Gemini / Google Flow image, ChatGPT image, Midjourney with image reference, Firefly), and say to bring the painted image back for step 2.

## 2. INPUTS (blocking)
- **P1 Photo** (required): ask until it is attached. One person or a small group; portrait or vertical framing works best.
- Optional: P2 colour mood (default: the moody palette below), P3 aspect ratio (default the photo's, ideally 9:16 vertical), P4 anything to keep sharper (jewellery, a logo on clothing).

## 3. LOOK AT THE PHOTO FIRST
Note in one short list: who is in it (count, pose), faces and their direction, clothing (colours, fabric, any print), hair (length, loose or tied), background (indoor, outdoor, sky, walls, plants), light direction. Fill these into the prompt so the model keeps them.

## 4. PAINTING PROMPT (fill the brackets, keep everything else)
```
Transform the provided image into an expressive, dramatic traditional oil painting. Keep the exact same composition, subjects, pose, faces, identity, clothing design and proportions as the original image ([SUBJECTS AND POSE]). Only change the rendering style into a rich, textured painterly artwork.

PAINT TEXTURE: Thick impasto oil paint applied with a palette knife and loose bristle brushes. Heavy, visible, directional brushstrokes everywhere. Paint is layered, smeared, scraped and dragged, with dabs, streaks and broken strokes, so the whole canvas feels hand-painted and slightly rough and cluttered, like a masterful alla prima painting. Canvas weave and paint ridges are subtly visible in the light.

DISTORTED, LOOSE EDGES: Outlines are soft, broken and unfinished. Clothing, hair and background melt into each other through smudged strokes and lost-and-found edges. Fabric folds are built from bold, chunky, angular strokes rather than smooth gradients. Hair is painted as sweeping, dragged, streaky strokes. Parts of the painting are deliberately abstract and impressionistic, with turbulent, swirling, messy brushwork in the background and lower areas.

FOCAL CONTRAST: The faces and main focal points are the most refined area: smooth, soft blended skin with delicate features, gentle highlights and calm, emotional expressions. Detail and sharpness decrease gradually toward the edges, where the paint becomes looser and more abstract.

COLOR: [COLOUR MOOD, default: Rich, deep, moody palette. Cool blue-violet, indigo and plum tones in the background and shadows, contrasted with warm crimson, burnt orange and rust smears. Warm golden, cream and ivory highlights on the main subject and clothing. Skin shows painterly color shifts, with cool blue-purple in shadows and warm orange-gold in lights. Slightly desaturated, earthy, cinematic color harmony with a few bright accents of gold.] Keep the clothing colours of the photo ([CLOTHING]).

LIGHTING: Dramatic chiaroscuro. A soft directional light falls on the faces and the front of the figures ([LIGHT DIRECTION]), with deep, dark, velvety shadows behind. A subtle glow on gold ornaments and jewelry. Atmospheric, moody and emotional, like a classical Romantic or Baroque painting mixed with modern digital painterly art.

BACKGROUND: A stormy, cloudy, smoky backdrop made entirely of overlapping brush swirls and palette knife smears in violet, blue and dark red, with no realistic detail ([BACKGROUND] may stay recognisable as shapes, painted loosely). It blends softly into the subjects with no hard separation.

FINISH: Museum-quality fine art oil painting, highly detailed, masterful artist hand, cinematic, [ASPECT, default vertical portrait] composition.

Do NOT: photorealism, smooth digital gradients, plastic or airbrushed skin, sharp vector outlines, cartoon or anime style, 3D render, flat colors, text, watermark, changing faces, adding or removing people or objects.
```

## 5. CHECK THE PAINTED IMAGE (when the user brings it back, or from your tool)
- Same people, faces recognisable, same pose and clothing; nothing added or removed.
- Loose painterly hair, fabric and background with visible strokes (step 2 animates exactly these areas; smooth photographic areas animate badly).
- No text or watermark. If one of these fails, regenerate with the failed rule repeated at the top of the prompt.

## 6. DELIVER
The painting prompt (filled) or the painted image, plus one line: "Next: give this painting to /160-photo-living-painting to bring it to life."
