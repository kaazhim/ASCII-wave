<div align="center">

G L Y P H S C A P E

A landscape built from language. A photograph disguised as a terminal.
What if an image didn't need a single conventional pixel to tell its story?

A high-density, full-color ASCII seascape designed to blur the line between visual art and text. From a distance, it reads like a cinematic ocean landscape. Get closer, and the illusion breaks into thousands of individual characters.

340 columns · 58 rows · 19,720 colored glyphs · 0 JavaScript dependencies

<img width="2416" height="678" alt="preview" src="https://github.com/user-attachments/assets/4ed001e6-c458-417c-b398-6f2a79905854" />



THE ILLUSION

At first glance: the ocean. At 200% zoom: the source code of the illusion.
</div>

01 — The Concept
The image is the interface. The characters are the canvas.

GLYPHSCAPE is a static, desktop-first ASCII artwork that reconstructs a sweeping ocean scene using real text characters, rather than placing a normal picture on the page.

The composition is made of tiny monospace glyphs, each carrying its own RGB color. Together, they form the appearance of a continuous image: blue atmosphere, luminous clouds, distant rock formations, and a textured sea.

The point is perspective:
- Step back: a cohesive landscape emerges.
- Move closer: texture becomes typography.
- Zoom in: the visual resolves into the symbols that built it.
It is deliberately both an image and a piece of text art.
02 — Features
Feature	What it means
High-density ASCII composition	A 340 × 58 grid of actual text characters.
Full-color glyph rendering	Each character has an individually assigned RGB color.
Optical image effect	Dense type, tight line height, and color create a photo-like impression at normal viewing distance.
Zoom-to-reveal detail	Browser zoom makes the individual characters easier to distinguish.
Pure HTML + CSS	The artwork is displayed directly in the browser, without client-side JavaScript.
No runtime dependencies	No frameworks, package manager, APIs, fonts, or external libraries are required to display the artwork.
Text-based output	A plain-text version of the character grid is also provided.


[!NOTE]
This release displays pre-generated, static ASCII artwork. It does not convert images in the browser or animate the ocean in real time.

03 — How It Works
The visual uses a deceptively simple idea: make each image sample a colored character.
                   ORIGINAL VISUAL
                          |
                          v
                 IMAGE DOWNSAMPLING
                          |
                          v
              BRIGHTNESS / TONE MAPPING
                          |
                          v
                  ASCII CHARACTER
                          +
                      RGB COLOR
                          |
                          v
                  HTML <span> GRID
                          |
                          v
                 DENSE MONOSPACE CSS
                          |
                          v
                   GLYPHSCAPE

             FAR AWAY: IMAGE-LIKE
             CLOSE UP: ASCII ART
The rendering approach
1. Image sampling — The source scene is sampled onto a smaller grid, producing 340 columns and 58 rows.

2. Luminance mapping — A brightness estimate determines which character represents each sample. Different glyphs produce different perceived densities.

3. Color preservation — Each selected glyph is assigned the RGB color sampled from its corresponding position in the source image.

4. HTML composition — The characters are written into a <pre> element, with individual <span> elements carrying their colors.

5. Typographic compression — A tiny monospace font, close line spacing, and a black background allow the characters to visually blend when viewed at normal scale.

The result is a static visual illusion built from a real, selectable text layer.
04 — Under the Hood
Property	Implementation
Artwork format	Colored text in HTML
ASCII grid	340 × 58
Total cells	19,720
Character selection	Brightness-based glyph mapping during generation
Color	Inline rgb(r,g,b) per character
Layout	<pre> with colored <span> elements
Typography	Consolas / Lucida Console / Courier New fallback
Background	#000000
Display font size	5px in the supplied HTML
Runtime	Any modern browser with HTML/CSS support
JavaScript	None


Why not just use an image? Because the whole experiment is to make the image out of characters. A regular bitmap would preserve the view, but lose the reveal.

Why black? Dark negative space preserves contrast and makes the blue and cream color values more visually striking.

Why tiny text? The optical blending only happens when the glyphs are sufficiently dense. Make them large enough, and the image starts to show its construction.
05 — Run It Locally
No build step. No installation. No terminal ceremony.

Option A: Open the page
1. Download or clone the repository.
2. Open index.html in a desktop browser.
3. View the artwork at a normal distance, then zoom in to inspect the individual glyphs.
Option B: Serve it locally (optional)
python -m http.server 8000
Then visit http://localhost:8000.
If your HTML file is still named ascii_desktop_dense_latest.html, either open that file directly or rename it to index.html before publishing.

06 — Deploy on GitHub Pages
Because the page is static, it can be published without a build pipeline.
1. Put index.html at the root of the repository.
2. Open Settings → Pages in your GitHub repository.
3. Under Build and deployment, choose Deploy from a branch.
4. Select your main branch and /(root), then save.
5. Once GitHub Pages has deployed it, use the URL shown in the Pages settings.
The preview image in this README comes from assets/preview.png. Keep that file in the repository so the image renders on GitHub.
07 — Repository Structure
GLYPHSCAPE/
|
|-- index.html                    # Colored ASCII artwork
|-- README.md                     # Project documentation
|-- ocean_ascii_desktop_dense.txt # Plain-text ASCII grid
|
`-- assets/
    `-- preview.png              # README preview
The plain-text version keeps the symbols but does not preserve their colors. Open the HTML file for the complete effect.
08 — Viewing Experience
Recommended: desktop or laptop browser, a dark environment, and enough screen width to see the composition comfortably.
Viewing mode	What you'll notice
Fit / normal view	Colors and glyph density merge into an image-like scene.
Browser zoom in	Individual characters become more apparent.
Very close inspection	The illusion breaks down into glyph shape, placement, and RGB values.


The artwork is desktop-first. On narrow viewports, horizontal scrolling may be required. Rendering can also vary slightly by browser, font availability, device scale, and zoom level.
09 — Design Philosophy
     +---------------------------------------+
     |             GLYPHSCAPE                |
     |                                       |
     |     19,720 tiny pieces of text.       |
     |     One continuous visual story.      |
     |                                       |
     |        IMAGE  <-->  LANGUAGE          |
     +---------------------------------------+
The project explores three overlapping ideas:
- Perception: how quickly the eye turns repetition into a recognizable scene.
- Constraint: how much visual information can survive when represented as small characters.
- Duality: the same surface can be experienced as art from afar and readable symbols up close.
It isn't a photograph hiding behind ASCII. The ASCII is what you are looking at.
10 — Current Limitations
- The artwork is static, not an interactive converter.
- The HTML has one <span> per character, so the document is comparatively large for a single piece of visual art.
- Mobile and narrow-window layouts may require scrolling.
- The appearance depends on monospace font metrics and the browser's rendering engine.
- Plain-text exports cannot carry the individual RGB colors.
These are intentional trade-offs of prioritizing a readable, color-accurate character layer over the simplicity of a single raster image.
11 — Future Possibilities
The current release is a proof of concept. Possible next experiments include:
- [ ] Upload an image and generate ASCII in-browser.
- [ ] Add a density slider to compare coarse and fine glyph grids.
- [ ] Add color / monochrome / terminal-green viewing modes.
- [ ] Offer export to HTML, TXT, SVG, and PNG.
- [ ] Add a fullscreen, resolution-aware gallery mode.
- [ ] Explore frame-by-frame animated ASCII sequences.
Roadmap items are ideas, not shipped features.
12 — Credits & Usage
Created as a creative-coding experiment in the aesthetics of colored ASCII art, browser typography, and optical perception.

If you fork or remix the concept, make something strange with it. The interesting part begins when the characters stop looking like characters.

License: No license is included in this package. Add a LICENSE file if you want to explicitly grant reuse rights.
<div align="center">

LOOK CLOSER.
The ocean was never made of pixels here. Only the illusion was.

GLYPHSCAPE — an exercise in seeing text differently.
</div>
