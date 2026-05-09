# Benjamin Kgosiesele — Portfolio

Multi-page portfolio site. Eight HTML files, no build step, no frameworks. Hosts anywhere.

---

## What's in the box

```
index.html                       ← Work page: hero + tile grid
about.html                       ← Info page: about, approach, competencies, tools, education, contact
case-multi-product.html          ← Case 01: Multi-product platform (BTC, Orange, BOTUBS, MPI)
case-sovereign-cloud.html        ← Case 02: Sovereign cloud research
case-she-compliance.html         ← Case 03: SHE Compliance digitisation
case-micro-lender.html           ← Case 04: Ipachi Capital onboarding
case-bsb-cards.html              ← Case 05: BSB three-tier debit cards
case-stanbic.html                ← Case 06: Stanbic Accelerate
styles.css                       ← Shared stylesheet (all design tokens, layouts, components)
README.md                        ← This file
```

Eight HTML files plus one shared `styles.css`. Drop the folder anywhere and it works — locally by double-clicking `index.html`, or hosted on any static web host. No build tools, no npm, no frameworks.

---

## Quick deploy in 5 minutes (recommended path)

The fastest way to get a live URL:

1. Open **netlify.com** and sign up with email or GitHub.
2. Click **Sites → Add new site → Deploy manually**.
3. Drag the entire portfolio folder onto the drop zone.
4. Netlify gives you a URL like `https://stunning-jellyfish-12345.netlify.app` immediately.
5. (Optional) **Site settings → Change site name** to something like `benjaminkgosiesele`. You now have `https://benjaminkgosiesele.netlify.app`.
6. (Strongly recommended) Buy a real domain (~USD $12/year on Namecheap or Cloudflare). In Netlify: **Domain management → Add custom domain**.

GitHub Pages and Vercel work identically. The site is static — anywhere static hosting works will host this site.

---

## Before you deploy: one thing to update

Drop your CV PDF into the folder as `cv.pdf`. The download link in the About page points to it. If you don't add a `cv.pdf`, the link will 404 — fine for now, but worth catching before launch.

Everything else (LinkedIn, email, phone, WhatsApp) is already wired up.

---

## Adding images later

Each case study and the home page have placeholder image slots styled with a diagonal stripe pattern. They look intentional, so the site looks finished even without real images.

### Tile images on the home page

Each tile in the grid has an empty placeholder. To add a real tile image:

```html
<a href="case-multi-product.html" class="tile featured empty reveal" ...>
  <span class="tile-placeholder">Tile image — multi-product platform hero</span>
  ...
</a>
```

Replace with:

```html
<a href="case-multi-product.html" class="tile featured reveal" ...>
  <img class="tile-img" src="images/tile-01.jpg" alt="">
  ...
</a>
```

Two changes: remove `empty` from the class list, replace the `<span class="tile-placeholder">` line with an `<img class="tile-img">` tag.

### Hero images on case study pages

Each case study has one main hero image (16:9 landscape) plus three supporting images (two side-by-side process shots and one full-width detail shot). Same swap pattern:

```html
<div class="case-hero-img empty" data-label="...">
  <!-- <img src="images/case-01-hero.jpg" alt="..."> -->
</div>
```

Becomes:

```html
<div class="case-hero-img" data-label="...">
  <img src="images/case-01-hero.jpg" alt="...">
</div>
```

Remove `empty` from class, uncomment the `<img>` tag.

### Portrait photo on the About page

Same pattern — find `class="about-portrait empty"`, remove `empty`, uncomment the `<img>`.

### Recommended specs

- **Tile images:** match the tile aspect ratio (4:3 standard, 16:9 featured, 5:3 wide). At least 1600px wide.
- **Case hero images:** 16:9 landscape, minimum 1600×900px (2400×1350px for Retina sharpness).
- **Process detail images:** 4:3 or 16:9, minimum 1280×800px.
- **Portrait photo:** 4:5 portrait crop, minimum 800×1000px.

JPEG for photos and rendered UI. PNG for high-contrast UI screenshots and pure graphics. WebP works too if your design tool exports it.

### Where to put images

Create an `images/` folder next to the HTML files:

```
portfolio/
├── index.html
├── case-multi-product.html
├── ...
└── images/
    ├── tile-01.jpg
    ├── case-multi-product-hero.jpg
    ├── portrait.jpg
    └── ...
```

The image references in the HTML files all use this `images/...` pattern.

---

## A word on client images

Before publishing screenshots from BTC, Orange Botswana, Stanbic, BSB, or the mining client — confirm you have permission, or pick screens that don't reveal NDA-covered material, real customer data, or internal-only views. The captions intentionally say "illustrative excerpt only" for this reason.

---

## Customising the design

All design tokens live at the top of `styles.css`:

```css
:root {
  --bg: #F4EFE6;            /* warm cream background */
  --ink: #1C1814;           /* primary text */
  --accent: #B05421;        /* burnt sienna accent */
  --font-display: 'Fraunces', ...;
  --font-body: 'Manrope', ...;
}
```

Edit those once and every page picks up the change. To change the accent colour across the whole site, just update `--accent` in `styles.css`.

---

## Local preview

Double-click `index.html` to open in your browser, or for a proper local server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`. The local server is recommended because some browsers restrict `file://` cross-page navigation.

---

## A note on the design

Set in **Fraunces** (serif display) and **Manrope** (sans body). Warm cream palette with burnt sienna accent. Editorial aesthetic — magazine-flavoured rather than tech-flavoured — chosen to read as confident and mature without being trendy.

Tile grid uses asymmetric sizing: the multi-product platform is the featured (large) tile because it's your strongest project. The other tiles vary by sector and weight.

Sections fade in on scroll. Animations respect `prefers-reduced-motion`. Everything is responsive down to mobile. Everything works without JavaScript (progressive enhancement).
