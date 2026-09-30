# Long-WAM · project page

Static project page for **Long-WAM: Scaling the Context of World-Action Models**. It has no build step and no external dependencies, and it works on GitHub Pages as is.

```
index.html               page content
static/css/style.css     styles (dark theme)
static/js/config.js      ← links (arXiv, PDF, code, models), author homepages, arXiv id
static/js/data.js        every number on the page, with its table / figure in the paper
static/js/main.js        film intro, charts, tables, explorers, lazy video loading
static/videos/           web-encoded videos (largest file 47 MB, total ≈ 100 MB)
static/images/           posters, GPU photos, favicon, social preview (og.jpg)
.nojekyll                serve files as they are on GitHub Pages
```

## Preview locally

Run this inside this folder, then open http://localhost:8765:

```bash
python3 -m http.server 8765
```

Python's built-in server can't seek inside the long videos. With the full working folder, `python3 ../project_page_tools/serve.py` serves the same page with seeking support.

## Before publishing

1. **Links.** Fill in `static/js/config.js` (`arxiv`, `pdf`, `code`, `models`, optional author homepages and `arxivId`). Empty links show as dimmed "soon" buttons, so nothing else needs editing.
2. **Social preview.** Once the Pages URL is known, make the `og:image` meta tag in `index.html` absolute (for example `https://<user>.github.io/<repo>/static/images/og.jpg`) and add `<meta property="og:url" content="…">`.
3. **BibTeX.** The entry uses `arxivId` from the config. Update the year or venue if needed.

## Deploy with GitHub Pages

1. Create a repository (e.g. `Long-WAM` or `longwam.github.io`) and push the **contents** of this folder to the `main` branch.
2. Go to *Settings → Pages → Build and deployment*, choose *Deploy from a branch*, then select `main` and `/ (root)`.
3. The page appears at `https://<user>.github.io/<repo>/` after about a minute.

Every file stays under GitHub's 100 MB limit.

## Page behaviour

- The film (2:38) fills the screen with an aperture reveal and autoplays **muted**, because browsers block autoplay with sound. *Play with sound* restarts it with audio.
- Scrolling shrinks the film away. When the film ends, the page glides to the paper header if you haven't scrolled.
- Demo clips load and play only when they are on screen.
- Charts, tables and the two explorers read from `data.js`. Best values per column are bold, including ties.
- `prefers-reduced-motion` is respected.

## Content notes

- All numbers come from the manuscript (see comments in `data.js`).
- Real-robot and simulation clips play at the labelled speed.
- *Generated* clips are LongLive2.0-Robot video predictions from one image and one instruction.
- GPU product photos © NVIDIA.
