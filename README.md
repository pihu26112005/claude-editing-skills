# Motion Graphics Skills

**Teach your Claude one motion-graphics style at a time.** Each skill in this library makes Claude an expert in a single visual style: what it looks like, which moments make it engaging, and how to apply them. Then you give Claude your own material and it dresses it in that style.

- 🎬 **Your video + captions** → the same video, untouched, with the style's captions, paper graphics, pushes and zooms added on top.
- 🖼️ **Your image + text** → a poster in that style.
- ✍️ **Just a script** → Claude asks about your story, then writes clean-footage prompts for your video model, or builds a graphics-only video.

Install it once as a plugin and every style in the library is available to Claude.

> **Status:** early. 76 skills are live (25 motion styles, 25 dynamic captions, 26 motion graphics) and the goal is around 200. Each skill lives in a numbered folder with its own demo.

---

## Contents

- [Why this exists](#why-this-exists)
- [Skill catalog](#skill-catalog)
- [Install](#install)
- [Use a style](#use-a-style)
- [How a style skill works](#how-a-style-skill-works)
- [Repository structure](#repository-structure)
- [Add a new style](#add-a-new-style)
- [FAQ](#faq)
- [License](#license)

---

## Why this exists

If you ask an AI to "make my video look like this style", it usually **replaces your video**: a new presenter, new scenes, and garbled captions. These skills do the opposite:

1. **Your footage stays yours.** Claude may only push, slide or zoom your video and lay style graphics over or under it. It never regenerates, recolours, trims or re-orders it, and the audio is kept as is.
2. **Exact captions.** All text is rendered with real fonts from your words, never drawn by an image or video model, so you get no nonsense words.
3. **No breakdowns.** Every move is eased and continuous, and moments respect the cuts already in your footage, so there are no jumps, black bars or flicker.
4. **A real style, not a guess.** Each skill defines its style precisely in a moment library: every engaging moment with its graphics, typography, motion keyframes, zoom and caption behaviour. Claude chooses moments that fit your story and adapts only their timing, words and position.

---

## Skill catalog

Every skill belongs to one category. The number is only its place in the library; the category is part of its folder name (`<number>-<category>-<name>`).

| Category | What the skill does |
|---|---|
| **Motion Style** (`style`) | A complete motion-graphics look: layouts, cards, transitions, graphics and captions around your footage. |
| **Dynamic Caption** (`caption`) | A caption system only: typography, timing, emphasis and caption motion over your untouched footage. |
| **Motion Graphic** (`graphics`) | A ready-made animated graphic (a diagram, chart or explainer) that Claude renders from your own text, images and colours, in its own 16:9 or 9:16 format. Claude first asks for every value it needs. |

### Motion Styles (25)

| # | Style | Preview | Signature moments | Works with |
|---|---|---|---|---|
| 2 | [**Editorial Grid**](skills/2-style-editorial-grid/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/2-style-editorial-grid.gif" width="240" alt="Original vs after Claude">](skills/2-style-editorial-grid/#results) | Footage in sharp cards on a white page that settle, swell and split into an asymmetric grid on every cut, monospaced captions typed word by word, letter-spaced keywords, step counters, a bold black title word | video + captions · image + text · script |
| 6 | [**Chalk Talk**](skills/6-style-chalk-talk/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/6-style-chalk-talk.gif" width="240" alt="Original vs after Claude">](skills/6-style-chalk-talk/#results) | White chalk circles drawn around the speaker, yellow sketchy titles written then filled, handwritten captions with a dark tag on the spoken word, charcoal brush-stroke wipes over the cuts, footage in a yellow chalk-bordered card, a cream paper quote card to close | video + captions · image + text · script |
| 7 | [**Cutout Board**](skills/7-style-cutout-board/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/7-style-cutout-board.gif" width="240" alt="Original vs after Claude">](skills/7-style-cutout-board/#results) | Subject snapped out as a sticker with a boiling yellow outline onto a green cutting mat with grid and crop marks, captions mixing small serif words, a hot-pink highlighter tag and a giant ultra-wide black word on a white label strip | video + captions · image + text · script |
| 12 | [**Marker Notes**](skills/12-style-marker-notes/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/12-style-marker-notes.gif" width="240" alt="Original vs after Claude">](skills/12-style-marker-notes/#results) | A yellow felt-tip marker band over a keyword, word-by-word captions with a yellow active-word pill, a white to-do card that ticks off steps, and a cream camera-roll page holding the live footage in rounded cards | video + captions · image + text · script |
| 14 | [**Sketch Mix**](skills/14-style-sketch-mix/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/14-style-sketch-mix.gif" width="240" alt="Original vs after Claude">](skills/14-style-sketch-mix/#results) | A fat white keyword in a pencil-scribbled ellipse, word-by-word handwritten captions, a round speaker bubble over B-roll and a cream sketch page with a hand-circled phrase | video + captions · image + text · script |
| 16 | [**Vermilion Cards**](skills/16-style-vermilion-cards/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/16-style-vermilion-cards.gif" width="240" alt="Original vs after Claude">](skills/16-style-vermilion-cards/#results) | Hot orange-red and saffron pages with hard-shadow footage cards, giant condensed title bands, cream label captions with an orange newest word and a black wedge wipe | video + captions · image + text · script |
| 17 | [**Zine Mix**](skills/17-style-zine-mix/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/17-style-zine-mix.gif" width="240" alt="Original vs after Claude">](skills/17-style-zine-mix/#results) | Powder-blue zine paper with a cloud-scalloped header and giant black word, tilted photo cards, doodles, slanted handwritten captions, and a cloud-window closer with a fat white word | video + captions · image + text · script |
| 18 | [**App World**](skills/18-style-app-world/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/18-style-app-world.gif" width="240" alt="Original vs after Claude">](skills/18-style-app-world/#results) | A phone mock-up beside the speaker, a frosted checklist that ticks off steps, a white app dialog that types your line, and a dark app screen with a live progress timer behind the cut-out speaker; bold white captions with one pink word | video + captions · image + text · script |
| 21 | [**Doodle Board**](skills/21-style-doodle-board/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/21-style-doodle-board.gif" width="240" alt="Original vs after Claude">](skills/21-style-doodle-board/#results) | Boiling white pen outline with doodles around the speaker, tilted paper word tags, a pink chart growing behind you, handwritten captions with a pink marker key word | video + captions · image + text · script |
| 22 | [**Glitch Relay**](skills/22-style-glitch-relay/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/22-style-glitch-relay.gif" width="240" alt="Original vs after Claude">](skills/22-style-glitch-relay/#results) | Live full-frame footage, glowing lavender word-by-word relay captions, a stacked title that snaps up with a white lightning crack, mirror-fold zoom-blur chroma-split glitch on every cut | video + captions · image + text · script |
| 24 | [**Mist Rise**](skills/24-style-mist-rise/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/24-style-mist-rise.gif" width="240" alt="Original vs after Claude">](skills/24-style-mist-rise/#results) | White serif captions fading in word by word with italic emphasis, long soft dissolves between shots, a feathered band of B-roll rising like mist while the speaker lifts upward | video + captions · image + text · script |
| 28 | [**Cocoa Grid Cards**](skills/28-style-cocoa-grid-cards/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/28-style-cocoa-grid-cards.gif" width="240" alt="Original vs after Claude">](skills/28-style-cocoa-grid-cards/#results) | Footage as a rounded card on a cream-then-cocoa graph-paper page that rises, swells to full frame and slides aside for a dark text page with a typed white chip, phrases typed into brown label bars | video + captions · image + text · script |
| 29 | [**Punk Photocopy**](skills/29-style-punk-photocopy/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/29-style-punk-photocopy.gif" width="240" alt="Original vs after Claude">](skills/29-style-punk-photocopy/#results) | Black-and-acid-yellow cut-and-paste zine: yellow brush strokes and torn-paper wipes, a speech-bubble poster, deckle-edge photo cards, black caption bars with white slab-serif words and one big yellow word | video + captions · image + text · script |
| 30 | [**Scribble Slate**](skills/30-style-scribble-slate/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/30-style-scribble-slate.gif" width="240" alt="Original vs after Claude">](skills/30-style-scribble-slate/#results) | Chalky stacked title behind the speaker, wobbly yellow marker outline, small handwritten captions with yellow keywords, glitch-wipes onto a charcoal slate or cream paper board with yellow-framed footage cards and doodles | video + captions · image + text · script |
| 31 | [**Shard Dissolve**](skills/31-style-shard-dissolve/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/31-style-shard-dissolve.gif" width="240" alt="Original vs after Claude">](skills/31-style-shard-dissolve/#results) | Slanted vermilion slats slice the footage, the picture shrinks into an orange inset with a B-roll card and giant outline word, shots dissolve through grain, thin white captions with heavy italic keywords | video + captions · image + text · script |
| 33 | [**Bauhaus Pop**](skills/33-style-bauhaus-pop/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/33-style-bauhaus-pop.gif" width="240" alt="Original vs after Claude">](skills/33-style-bauhaus-pop/#results) | Flat orange, cobalt, mustard and cream poster blocks with a stamped condensed banner, cream label-bar captions with the newest word orange, black-edged cards with a retracting extruded shadow, a falling shape curtain to a blue wall | video + captions · image + text · script |
| 38 | [**Aqua Glass Stage**](skills/38-style-aqua-glass-stage/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/38-style-aqua-glass-stage.gif" width="240" alt="Original vs after Claude">](skills/38-style-aqua-glass-stage/#results) | Footage in frosted-glass cards gliding between a sky-blue gradient and a white stage with pink and blue slabs, frosted caption chips with one bold italic keyword, a gradient outline around the speaker at the end | video + captions · image + text · script |
| 39 | [**Cloud Scissor Cut**](skills/39-style-cloud-scissor-cut/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/39-style-cloud-scissor-cut.gif" width="240" alt="Original vs after Claude">](skills/39-style-cloud-scissor-cut/#results) | A powder-blue doodled paper cloud with a heavy black title, hand-lettered captions, then a frosted paper band with a scissors-in-hand snip and bold white captions | video + captions · image + text · script |
| 57 | [**iOS Widgets**](skills/57-style-ios-widgets/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/57-style-ios-widgets.gif" width="240" alt="Original vs after Claude">](skills/57-style-ios-widgets/#results) | Frosted home-screen widgets drop into the corners with a step counter, a cursor clicks blue check pills for each step, and a Follow card and glass capsule close the clip | video + captions · image + text · script |
| 58 | [**Y2K Chrome**](skills/58-style-y2k-chrome/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/58-style-y2k-chrome.gif" width="240" alt="Original vs after Claude">](skills/58-style-y2k-chrome/#results) | An icy-blue Y2K web world: liquid-chrome bubble titles, four-point sparkles, holographic pill captions and B-roll in glossy retro pop-up windows | video + captions · image + text · script |
| 60 | [**Swiss Poster**](skills/60-style-swiss-poster/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/60-style-swiss-poster.gif" width="240" alt="Original vs after Claude">](skills/60-style-swiss-poster/#results) | A six-column hairline grid locks your footage into red or paper modules, with giant flush-left bold captions, step numerals, one red circle and a column-sweep swap on every cut | video + captions · image + text · script |
| 61 | [**Ornate Frame**](skills/61-style-ornate-frame/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/61-style-ornate-frame.gif" width="240" alt="Original vs after Claude">](skills/61-style-ornate-frame/#results) | Footage in a pointed-arch window on ivory paper inside an engraved gold frame with beaded lines, vine corners and oxblood rosettes, lacquer caption plates in ivory serif, gold glints on cuts | video + captions · image + text · script |
| 148 | [**Cream Ink Pages**](skills/148-style-cream-ink-pages/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/148-style-cream-ink-pages.gif" width="240" alt="Original vs after Claude">](skills/148-style-cream-ink-pages/#results) | Bold white word-by-word captions with an amber label keyword cutting to cream paper pages that hold the live footage in a rounded card beside plum ink captions and a rolling step counter, with a scalloped badge and drawn stickers | video + captions · image + text · script |
| 150 | [**Amber Widget Pipes**](skills/150-style-amber-widget-pipes/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/150-style-amber-widget-pipes.gif" width="240" alt="Original vs after Claude">](skills/150-style-amber-widget-pipes/#results) | Frosted pills resolving from pixel blocks behind the speaker, white widget cards with growing charts and flipping switches, a gradient page the footage shrinks into as a rounded window, a glowing tube that forks in two and a glowing giant-word title | video + captions · image + text · script |
| 152 | [**Mosaic Gloss**](skills/152-style-mosaic-gloss/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/152-style-mosaic-gloss.gif" width="240" alt="Original vs after Claude">](skills/152-style-mosaic-gloss/#results) | A rounded footage card on a pastel gradient page, pixel-mosaic wipes on every cut, glowing typed keywords over whisper words, a glossy pill slot with a ball knob and a speech-bubble caption | video + captions · image + text · script |

### Dynamic Captions (25)

| # | Caption | Preview | Signature moments | Works with |
|---|---|---|---|---|
| 5 | [**Depth Headline**](skills/5-caption-depth-headline/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/5-caption-depth-headline.gif" width="240" alt="Original vs after Claude">](skills/5-caption-depth-headline/#results) | One giant ultra-condensed word standing behind the speaker that snaps yellow in a see-through box the instant it's spoken, small bold karaoke captions that leave that word out, hard punchy cuts | video + captions · image + text · script |
| 23 | [**Serif Staircase**](skills/23-caption-serif-staircase/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/23-caption-serif-staircase.gif" width="240" alt="Original vs after Claude">](skills/23-caption-serif-staircase/#results) | Untouched full-frame footage, a tilted white italic serif title rising in, captions building in a staircase of white serif words and yellow italic keywords, black-on-white label boxes on bright shots | video + captions · image + text · script |
| 35 | [**Lime Glow**](skills/35-caption-lime-glow/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/35-caption-lime-glow.gif" width="240" alt="Original vs after Claude">](skills/35-caption-lime-glow/#results) | White semibold words over one heavy slanted lime keyword with a green glow, and a giant outlined slanted title with a red and cyan fringe sliding across the top | video + captions · image + text · script |
| 36 | [**Outline Fill Caps**](skills/36-caption-outline-fill-caps/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/36-caption-outline-fill-caps.gif" width="240" alt="Original vs after Claude">](skills/36-caption-outline-fill-caps/#results) | Tall condensed all-caps captions that appear as hollow outlines and snap solid white word by word as each word is spoken | video + captions · image + text · script |
| 37 | [**Chrome Tier**](skills/37-caption-chrome-tier/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/37-caption-chrome-tier.gif" width="240" alt="Original vs after Claude">](skills/37-caption-chrome-tier/#results) | Small thin white words plus huge heavy italic keywords with a glossy teal-silver chrome fill, stacking in a zigzag down the lower frame | video + captions · image + text · script |
| 41 | [**Water Fill Caps**](skills/41-caption-water-fill-caps/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/41-caption-water-fill-caps.gif" width="240" alt="Original vs after Claude">](skills/41-caption-water-fill-caps/#results) | Small ultra-bold white lead-in words under the face that land on one giant keyword filled with a blue water texture | video + captions · image + text · script |
| 42 | [**Gradient Stack**](skills/42-caption-gradient-stack/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/42-caption-gradient-stack.gif" width="240" alt="Original vs after Claude">](skills/42-caption-gradient-stack/#results) | Small white bold words build a line, then one giant extra-bold gradient keyword blurs in under it in a new deep colour each phrase, zigzagging between the top and middle | video + captions · image + text · script |
| 43 | [**Butter Didone**](skills/43-caption-butter-didone/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/43-caption-butter-didone.gif" width="240" alt="Original vs after Claude">](skills/43-caption-butter-didone/#results) | Pale butter-yellow Didone captions pop in word by word with one capital keyword, while a giant edge-to-edge capital of the key word slams in across the top | video + captions · image + text · script |
| 44 | [**Neon Echo**](skills/44-caption-neon-echo/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/44-caption-neon-echo.gif" width="240" alt="Original vs after Claude">](skills/44-caption-neon-echo/#results) | Small bold white captions with glowing lime italic keywords, a giant scan-lined neon slab for the payoff word, and outline echo rows behind the speaker | video + captions · image + text · script |
| 48 | [**Podcast Headline**](skills/48-caption-podcast-headline/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/48-caption-podcast-headline.gif" width="240" alt="Original vs after Claude">](skills/48-caption-podcast-headline/#results) | A fixed bold hook headline at the top (white line over a black-on-white box line) and clean word-by-word bold captions low in the frame, the classic podcast-clip look | video + captions · image + text · script |
| 115 | [**Orchid Halo**](skills/115-caption-orchid-halo/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/115-caption-orchid-halo.gif" width="240" alt="Original vs after Claude">](skills/115-caption-orchid-halo/#results) | Heavy white sans words fade in low as spoken and one large glowing orchid-pink italic serif accent word per phrase settles in, tucked against the sans line | video + captions · image + text · script |
| 116 | [**Mixed Face Stack**](skills/116-caption-mixed-face-stack/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/116-caption-mixed-face-stack.gif" width="240" alt="Original vs after Claude">](skills/116-caption-mixed-face-stack/#results) | Two to four line word-by-word stacks mixing heavy white caps, one bright accent caps word, a big italic serif and tiny connector words, hard-cut away at each phrase end | video + captions · image + text · script |
| 117 | [**Tall Serif Stack**](skills/117-caption-tall-serif-stack/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/117-caption-tall-serif-stack.gif" width="240" alt="Original vs after Claude">](skills/117-caption-tall-serif-stack/#results) | Tall narrow high-contrast serif capitals in one bold colour cut in above the subject with a drifting sheen, tiny white serif captions building word by word along their lower edge | video + captions · image + text · script |
| 119 | [**Crown Word Script**](skills/119-caption-crown-word-script/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/119-caption-crown-word-script.gif" width="240" alt="Original vs after Claude">](skills/119-caption-crown-word-script/#results) | One heavy condensed uppercase keyword with a thick black outline pops in above the head while flowing white script captions with a thin outline build word by word at the lower left | video + captions · image + text · script |
| 121 | [**Caps Swash Pairs**](skills/121-caption-caps-swash-pairs/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/121-caption-caps-swash-pairs.gif" width="240" alt="Original vs after Claude">](skills/121-caption-caps-swash-pairs/#results) | Tiny wide-tracked white caps words orbiting one giant white italic serif keyword in the lower third, with an optional single accent-tinted payoff word | video + captions · image + text · script |
| 125 | [**Stacked Pop Tags**](skills/125-caption-stacked-pop-tags/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/125-caption-stacked-pop-tags.gif" width="240" alt="Original vs after Claude">](skills/125-caption-stacked-pop-tags/#results) | Tiny white helper words stacked around one huge slanted condensed keyword in a hot accent colour that slides in and hard-cuts to the next phrase | video + captions · image + text · script |
| 126 | [**Arc Crown Caps**](skills/126-caption-arc-crown-caps/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/126-caption-arc-crown-caps.gif" width="240" alt="Original vs after Claude">](skills/126-caption-arc-crown-caps/#results) | The key word of each phrase curves over the head as a chunky accent arch with a small 3D edge while the small words pile up as tilted white caps on the chest | video + captions · image + text · script |
| 128 | [**Ghost Underline**](skills/128-caption-ghost-underline/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/128-caption-ghost-underline.gif" width="240" alt="Original vs after Claude">](skills/128-caption-ghost-underline/#results) | Mid-frame captions building word by word from ghost-grey to heavy white sans, each phrase with one slim serif-italic keyword carrying a gradient underline | video + captions · image + text · script |
| 130 | [**Whisper Blob**](skills/130-caption-whisper-blob/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/130-caption-whisper-blob.gif" width="240" alt="Original vs after Claude">](skills/130-caption-whisper-blob/#results) | Tiny hand-brushed white whisper words over one fat rounded keyword on a solid dark slab, bent into an arch or wave, hopping between top and bottom lane to stay off the face | video + captions · image + text · script |
| 135 | [**Gilt Crest Serif**](skills/135-caption-gilt-crest-serif/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/135-caption-gilt-crest-serif.gif" width="240" alt="Original vs after Claude">](skills/135-caption-gilt-crest-serif/#results) | Tiny white serif helper lines fading in word by word beside one giant heavy gradient-serif keyword per phrase, tucked behind the top of the speaker's head or placed in a lower lane | video + captions · image + text · script |
| 136 | [**Pixel Resolve Serif**](skills/136-caption-pixel-resolve-serif/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/136-caption-pixel-resolve-serif.gif" width="240" alt="Original vs after Claude">](skills/136-caption-pixel-resolve-serif/#results) | Tiny white serif whispers beside tall stretched Didone capitals that resolve from a pixel mosaic, bend into arches and waves, slip behind the head and end on one giant mixed-case word | video + captions · image + text · script |
| 139 | [**Full Bleed Caps**](skills/139-caption-full-bleed-caps/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/139-caption-full-bleed-caps.gif" width="240" alt="Original vs after Claude">](skills/139-caption-full-bleed-caps/#results) | One giant ultra-heavy condensed capital keyword per phrase in a flat accent colour stretched edge to edge at the top and tucked behind the hair, plus a tiny word-by-word line with the keyword in bold | video + captions · image + text · script |
| 140 | [**Sky Fill Sans**](skills/140-caption-sky-fill-sans/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/140-caption-sky-fill-sans.gif" width="240" alt="Original vs after Claude">](skills/140-caption-sky-fill-sans/#results) | Small bold white sans words fading in around one giant extra-heavy keyword filled with a drifting cloud-and-sky texture, across the chest or in a top or low lane, clear of the face | video + captions · image + text · script |
| 143 | [**Sash Orbit Plate**](skills/143-caption-sash-orbit-plate/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/143-caption-sash-orbit-plate.gif" width="240" alt="Original vs after Claude">](skills/143-caption-sash-orbit-plate/#results) | A glossy teal sash orbiting the speaker, back half behind the head and front half over the chest, carrying a tracked uppercase title, with every other line on a small dark rounded plate with an accent border | video + captions · image + text · script |
| 144 | [**Ring Chip Script**](skills/144-caption-ring-chip-script/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/144-caption-ring-chip-script.gif" width="240" alt="Original vs after Claude">](skills/144-caption-ring-chip-script/#results) | One low line of small hand-lettered white words per phrase, the key word on a solid rounded cyan chip in marker lettering and one other word circled by a loose violet hand-drawn ring | video + captions · image + text · script |

### Motion Graphics (26)

| # | Graphic | Preview | What it shows | You provide |
|---|---|---|---|---|
| 64 | [**Tabletop Card Fan**](skills/64-graphics-tabletop-card-fan/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/64-graphics-tabletop-card-fan.gif" width="240" alt="Tabletop Card Fan demo">](skills/64-graphics-tabletop-card-fan/#results) | One card slides onto a table and fans into five while a tilting camera tours them and three captions type onto the table (16:9) | 3 captions |
| 65 | [**Prompt Pill Reveal**](skills/65-graphics-prompt-pill-reveal/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/65-graphics-prompt-pill-reveal.gif" width="240" alt="Prompt Pill Reveal demo">](skills/65-graphics-prompt-pill-reveal/#results) | A brand pill grows into a prompt box that types your request and sends it, shrinks into a working pill with a spinning star, then bursts open into your result image (16:9) | brand + prompt + result image + caption |
| 67 | [**Desk Gadget Tour**](skills/67-graphics-desk-gadget-tour/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/67-graphics-desk-gadget-tour.gif" width="240" alt="Desk Gadget Tour demo">](skills/67-graphics-desk-gadget-tour/#results) | A title types onto a handheld gadget on a grid desk, the camera zooms in and spins a full turn, then a two-line headline types out beside it (9:16) | screen text + 2 headline lines |
| 68 | [**Sliding Card Rail**](skills/68-graphics-sliding-card-rail/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/68-graphics-sliding-card-rail.gif" width="240" alt="Sliding Card Rail demo">](skills/68-graphics-sliding-card-rail/#results) | Five perspective image cards on an accent rail with a knob and label under each, the camera flying in and gliding card by card (9:16) | 5 labels + 5 images |
| 72 | [**Step Ink Scroll**](skills/72-graphics-step-ink-scroll/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/72-graphics-step-ink-scroll.gif" width="240" alt="Step Ink Scroll demo">](skills/72-graphics-step-ink-scroll/#results) | Three oversized ink-worn capital headlines on crumpled paper snap sideways in five hard steps to reveal their endings (16:9) | 3 headlines |
| 73 | [**Tile Strip Pick-Out**](skills/73-graphics-tile-strip-pick-out/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/73-graphics-tile-strip-pick-out.gif" width="240" alt="Tile Strip Pick-Out demo">](skills/73-graphics-tile-strip-pick-out/#results) | A tilted stream of fifteen numbered tiles flattens into a row, a hand cursor clicks one, the strip fans away and the chosen tile settles large in the centre (16:9) | label word + chosen number |
| 75 | [**Clipped Photo Desk**](skills/75-graphics-clipped-photo-desk/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/75-graphics-clipped-photo-desk.gif" width="240" alt="Clipped Photo Desk demo">](skills/75-graphics-clipped-photo-desk/#results) | A dotted-paper desk seen from above: pens, cards, a paper-clipped tape label, a colour caption strip and a tilted photo slide on as the camera eases in, then two text lines type on (9:16) | strip text + label text + 1 photo |
| 77 | [**Pop-up Post Card**](skills/77-graphics-pop-up-post-card/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/77-graphics-pop-up-post-card.gif" width="240" alt="Pop-up Post Card demo">](skills/77-graphics-pop-up-post-card/#results) | A clean white social post card rises on black, the name and handle wipe in, the post lands word by word and a like counter ticks and bursts before the card exits (16:9) | name + handle + post text + avatar + counts |
| 79 | [**Arrow Label Burst**](skills/79-graphics-arrow-label-burst/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/79-graphics-arrow-label-burst.gif" width="240" alt="Arrow Label Burst demo">](skills/79-graphics-arrow-label-burst/#results) | A glowing centre phrase types in on a dark hand-drawn grid, then four crayon arrows grow out one by one with a coloured label popping in at each tip (16:9) | centre text + 4 labels |
| 80 | [**Flare Sweep Title**](skills/80-graphics-flare-sweep-title/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/80-graphics-flare-sweep-title.gif" width="240" alt="Flare Sweep Title demo">](skills/80-graphics-flare-sweep-title/#results) | A heavy headline types on letter by letter with a glowing smear and sunburst flare at its leading edge, holds crisp, then flares again and fades out on a dark stage (16:9) | 1 headline |
| 82 | [**Torn Tag Callouts**](skills/82-graphics-torn-tag-callouts/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/82-graphics-torn-tag-callouts.gif" width="240" alt="Torn Tag Callouts demo">](skills/82-graphics-torn-tag-callouts/#results) | A glowing striped two-word label rises, tears along a zigzag crack, and its halves tilt apart and recolour, each gaining a dashed looping leader and a typed callout (16:9) | 2 label words + 2 callouts |
| 83 | [**Pill Bar Reveal**](skills/83-graphics-pill-bar-reveal/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/83-graphics-pill-bar-reveal.gif" width="240" alt="Pill Bar Reveal demo">](skills/83-graphics-pill-bar-reveal/#results) | A round search-icon bubble rises, stretches into a pill search bar as the magnifier tilts, your text fades in word by word, then the bar swells and shrinks away on a soft gradient (16:9) | 1 search text |
| 84 | [**Origin Zoom Curve**](skills/84-graphics-origin-zoom-curve/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/84-graphics-origin-zoom-curve.gif" width="240" alt="Origin Zoom Curve demo">](skills/84-graphics-origin-zoom-curve/#results) | A glowing jagged growth line draws from the origin of dashed axes while the camera pulls back, then a grid fades in and a title and two axis labels blur into focus (9:16) | title + 2 axis labels |
| 85 | [**Twin Swoosh Callouts**](skills/85-graphics-twin-swoosh-callouts/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/85-graphics-twin-swoosh-callouts.gif" width="240" alt="Twin Swoosh Callouts demo">](skills/85-graphics-twin-swoosh-callouts/#results) | A glowing portrait image card on a dark stage, the camera pushes in and two gradient brush swooshes sweep out, each ending in a glowing label that types in (16:9) | 1 portrait image + 2 labels |
| 86 | [**Macro Screen Query Pan**](skills/86-graphics-macro-screen-query-pan/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/86-graphics-macro-screen-query-pan.gif" width="240" alt="Macro Screen Query Pan demo">](skills/86-graphics-macro-screen-query-pan/#results) | A close-up pixel-grid monitor shows a search bar; the camera zooms in as your query types, then pans with motion blur to the magnifier as a cursor glides in (16:9) | 1 query + title word |
| 90 | [**Parchment Headline Desk**](skills/90-graphics-parchment-headline-desk/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/90-graphics-parchment-headline-desk.gif" width="240" alt="Parchment Headline Desk demo">](skills/90-graphics-parchment-headline-desk/#results) | A date tag, headline and detail text type onto grid parchment while a cut-out image rises from the corner, a rule and masthead line draw in, then marker highlights sweep the words (16:9) | date + headline + detail + masthead + 1 cut-out image |
| 93 | [**Grit Reel Brush Bar**](skills/93-graphics-grit-reel-brush-bar/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/93-graphics-grit-reel-brush-bar.gif" width="240" alt="Grit Reel Brush Bar demo">](skills/93-graphics-grit-reel-brush-bar/#results) | A one-line title types letter by letter on a sweeping dry-brush colour bar over dark scratched film, with a draw-on line tag and camera-gate marks (16:9) | 1 title |
| 95 | [**Twin-Tone Peak Slide**](skills/95-graphics-twin-tone-peak-slide/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/95-graphics-twin-tone-peak-slide.gif" width="240" alt="Twin-Tone Peak Slide demo">](skills/95-graphics-twin-tone-peak-slide/#results) | A glass orb on a dome beside a glowing area chart that climbs to a peak, a marker line drops, a second-colour fall fills in and a two-word label rises (9:16) | 1 label |
| 98 | [**Glow Line Decoder**](skills/98-graphics-glow-line-decoder/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/98-graphics-glow-line-decoder.gif" width="240" alt="Glow Line Decoder demo">](skills/98-graphics-glow-line-decoder/#results) | A glowing two-line headline over six list lines that go from blur to pixel mosaic to sharp text while the camera zooms in and scrolls down the list (16:9) | 2 headline lines + 6 list lines |
| 99 | [**Slip Surface Cuts**](skills/99-graphics-slip-surface-cuts/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/99-graphics-slip-surface-cuts.gif" width="240" alt="Slip Surface Cuts demo">](skills/99-graphics-slip-surface-cuts/#results) | A typed paper label stays centred while the surface under it hard-cuts every beat between wood, graph paper and cutting mats, with props around it (9:16) | 1 text |
| 103 | [**Thread Word Relay**](skills/103-graphics-thread-word-relay/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/103-graphics-thread-word-relay.gif" width="240" alt="Thread Word Relay demo">](skills/103-graphics-thread-word-relay/#results) | A comment slot in a social thread flickers through many invented users who each write one word, spelling out your sentence while avatars, handles and likes keep changing (1:1) | a 6-word sentence |
| 107 | [**Tilted Page Ink Chain**](skills/107-graphics-tilted-page-ink-chain/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/107-graphics-tilted-page-ink-chain.gif" width="240" alt="Tilted Page Ink Chain demo">](skills/107-graphics-tilted-page-ink-chain/#results) | Three paragraphs on a tilted paper page, one key word in each circled in hand-drawn ink and linked by curved arrows as the camera glides word to word (9:16) | 3 paragraphs + 3 key words |
| 108 | [**Highlight Snippet Flicker**](skills/108-graphics-highlight-snippet-flicker/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/108-graphics-highlight-snippet-flicker.gif" width="240" alt="Highlight Snippet Flicker demo">](skills/108-graphics-highlight-snippet-flicker/#results) | One marker-highlighted keyword stays fixed while article snippets cut past at about ten a second on crumpled paper, with streaked edges and blurred body text (9:16) | 1 keyword + 9 snippets |
| 109 | [**Shattered Front Page Pullback**](skills/109-graphics-shattered-front-page-pullback/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/109-graphics-shattered-front-page-pullback.gif" width="240" alt="Shattered Front Page Pullback demo">](skills/109-graphics-shattered-front-page-pullback/#results) | A newspaper front page breaks into ragged shards that drift apart and snap back together while the camera pulls out from a giant headline to the whole page (1:1) | masthead + 2-line headline + subhead + 1 photo |
| 110 | [**Cursor Morph Widget**](skills/110-graphics-cursor-morph-widget/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/110-graphics-cursor-morph-widget.gif" width="240" alt="Cursor Morph Widget demo">](skills/110-graphics-cursor-morph-widget/#results) | One black-and-white UI shape never cuts as a cursor morphs it through button, loader, check, island, player, slider, toggle, tabs, chart, command palette and toast, looping back to the button (1:1) | button label + track + tabs + metric + search + toast texts |
| 146 | [**Pinned Stamp Timeline**](skills/146-graphics-pinned-stamp-timeline/) | [<img src="https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/146-graphics-pinned-stamp-timeline.gif" width="240" alt="Pinned Stamp Timeline demo">](skills/146-graphics-pinned-stamp-timeline/#results) | Three dated picture stamps pinned on a scrolling paper ruler with counted years-later tapes, a pull-back to a gap bracket, a torn note card and a horizontal ruler recap (9:16) | 3 events + 3 pictures + headlines |

Style and caption previews show the original footage next to Claude's result; click one to see the full before/after. Graphic previews show the graphic filled with sample text and images.

---

## Install

### Claude Code

```bash
claude plugin marketplace add pihu26112005/claude-editing-skills
claude plugin install claude-editing-skills@claude-editing-skills
```

Or from inside a session:

```
/plugin marketplace add pihu26112005/claude-editing-skills
/plugin install claude-editing-skills@claude-editing-skills
```

Update later to get new styles:

```bash
claude plugin update claude-editing-skills@claude-editing-skills
```

### claude.ai and Cowork

Once the plugin is listed in Anthropic's directory, open **Customize → Plugins**, search for **Motion Graphics Skills** and add it. Until then, upload a single style as a skill: zip one folder from `skills/` (for example `skills/1-style-torn-paper-scrapbook/`) and add it under **Customize → Skills**. Video editing needs code execution turned on.

### One style without the plugin

```bash
git clone https://github.com/pihu26112005/claude-editing-skills
cp -r claude-editing-skills/skills/1-style-torn-paper-scrapbook ~/.claude/skills/
```

**Requirements for editing videos:** Python 3 with Pillow and NumPy, and `ffmpeg`. Optional: `faster-whisper` for more precise caption timing, and `rembg` or MediaPipe for graphics placed behind a person.

---

## Use a style

**On claude.ai and Cowork:** type `/` in the message box, pick the skill (for example `1-style-torn-paper-scrapbook`), attach your video and paste its captions:

```
/1-style-torn-paper-scrapbook
Add this style to my video. Don't change the footage. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
```

**In Claude Code:** the same, with the plugin name in front:

```
/claude-editing-skills:1-style-torn-paper-scrapbook
Add this style to my video. Don't change the footage. Captions:
"Saving money isn't about earning more. Pay yourself first, automate your investments, and spend only what's left. Do it for one year and watch what happens."
```

You can also just describe it ("add torn paper scrapbook captions to this video") and Claude picks the skill.

What Claude does depends on what you give it:

| You give | Claude asks | You get |
|---|---|---|
| video + captions | nothing | your video with the style added |
| video only | the captions | your video with the style added |
| image + text | nothing | a poster in the style |
| captions / script only | what the story looks like, and video or image | clean-footage prompts (then edits your clips), or a graphics-only video |
| nothing | the story and the captions | as above |

For a video, Claude then:
1. Finds the cuts in your footage, looks at every scene, and marks faces and empty areas.
2. Times your captions to the speech.
3. Finds the hook points: the opening line, contrasts, lists, numbers, emphasis words, scene changes and the payoff.
4. Picks moments from the style's library for those points and adapts their timing, words and placement.
5. Renders, checks the frames itself, and saves `<your video>_torn_paper.mp4` with the original resolution, frame rate, length and audio.

---

## How a style skill works

Every style folder has two working files:

| File | What it holds |
|---|---|
| `SKILL.md` | The workflow: identify the input case, ask only what's missing, analyse scenes, time captions, find hook points, choose and adapt moments, build, check, deliver. Plus the hard rules that protect your footage. |
| `moments.md` | **Part 1, style bible:** palette, paper material, typography, motion language, allowed plate moves, safe zones. **Part 2, moment library:** every engaging moment of the style, each with its purpose, triggers, layer stack, graphics, text rules, keyframe table, plate (zoom/push) behaviour, caption behaviour, exit, build notes, and a text version for video-model prompts. |

Plus `README.md`, which embeds its before/after GIF and the original clip from the companion [motion-graphics-skills-media](https://github.com/pihu26112005/motion-graphics-skills-media) repo, so no video or GIF files live in this repo.

Claude only loads a skill's instructions when your request matches its description. Until then, each style costs only its short description in context.

---

## Repository structure

```
claude-editing-skills/
├── .claude-plugin/
│   ├── marketplace.json        ← makes the repo addable as a marketplace
│   └── plugin.json             ← plugin manifest (name, version, metadata)
├── skills/
│   ├── 1-style-torn-paper-scrapbook/
│   │   ├── SKILL.md
│   │   ├── moments.md
│   │   └── README.md
│   └── <n>-<category>-<name>/
│       └── ...
├── LICENSE
└── README.md
```

Demo videos and GIFs are not stored here. They live in the public [motion-graphics-skills-media](https://github.com/pihu26112005/motion-graphics-skills-media) repo, and each skill's `README.md` embeds them from there with a `raw.githubusercontent.com` link. This keeps the plugin repo small (Anthropic's directory caps a repo's downloadable archive at 50 MiB), no matter how many styles get added.

The repository root is both the marketplace and the plugin: `marketplace.json` lists one plugin whose `source` is `"./"`. Claude Code finds every `skills/<name>/SKILL.md` automatically, so adding a style needs no manifest change.

---

## Add a new style

1. Create `skills/<next-number>-<category>-<name>/`, using lowercase kebab-case. `<category>` is `style`, `caption` or `graphics` (e.g. `35-style-neon-grid` or `36-caption-bold-pop`). Numbers are never reused and run across all categories.
2. Write `moments.md`:
   - **Part 1, style bible:** palette (hex), materials and textures, typography (preferred free fonts and fallbacks), motion language (easing, durations), the allowed plate moves and safe zones.
   - **Part 2, moments:** every engaging moment of the style, each fully specified (purpose, when to use and when to avoid, text rules, layer stack, graphics, keyframe table, plate behaviour, caption behaviour, exit, build notes, generation-mode text). Mark the fields Claude may adapt with ✎.
3. Write `SKILL.md` with frontmatter:
   ```yaml
   ---
   name: <next-number>-<category>-<name>
   description: <The style's signature look in one sentence, then when to use it. 2–3 sentences: every description loads in every session.>
   ---
   ```
   Keep the shared workflow (input cases, hard rules, analysis, hook points, build, checks) and adapt the hook-point table and signature to the new style.
4. Make a demo with the skill on the shared input clip (the original clip lives at `https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4`) and build a side-by-side comparison GIF at 400 px wide, 8 fps and 48 colours (about 2 MB).
5. Push the GIF to the [motion-graphics-skills-media](https://github.com/pihu26112005/motion-graphics-skills-media) repo as `gifs/<n>-<category>-<name>.gif`, then write a short `README.md` for the skill starting with a Results section that embeds it:
   ```markdown
   ![Original vs after Claude: side-by-side comparison](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/gifs/<n>-<category>-<name>.gif)

   Original input clip: [demo2-original.mp4](https://raw.githubusercontent.com/pihu26112005/motion-graphics-skills-media/main/original.mp4)
   ```
   Then describe what the style looks like, what you can give it, and a "Try it" example. Do not commit any video or GIF file into this repo.
6. Add a row to the right table of the [Skill catalog](#skill-catalog), bump `version` in `.claude-plugin/plugin.json`, and run:
   ```bash
   claude plugin validate .
   ```

**Adding a graphic** works the same way, with two differences. The folder is `skills/<n>-graphics-<name>/` and holds `SKILL.md`, `description.md` and `README.md`, with no `moments.md`. `description.md` is the full frame-by-frame specification of the one animation, plus a parameter table (`| P1 | Main text | yes | none, must ask | … |`) that says which values the user must provide and which have defaults. The demo is the graphic rendered with sample content in its own format, saved as `<n>-graphics-<name>/demo.mp4` and `gifs/<n>-graphics-<name>.gif` in the media repo.

Contributions are welcome: one skill per pull request.

---

## FAQ

**Will it change my video?**
No. It only moves or zooms your footage and adds style graphics and captions over or under it. Colours, speed, order, length and audio stay the same.

**Where do the captions come from?**
From your text, word for word. Claude times them to the speech, using speech-to-text timestamps if available and audio pauses otherwise. It never re-words them.

**Do I need a video model?**
Not for editing your own videos or images. A video model only comes in if you start from a script and want new footage. Even then Claude asks for clean footage without text and adds the style afterwards.

**Can I use my brand colours?**
Yes. Mention them and Claude maps them onto the style's colour roles.

---

## License

[MIT](LICENSE). Use, modify and share freely.
