# Mason Jar Films — Site

## File Structure

```
masonjarfilms/
├── index.html          ← Home
├── films.html          ← Films
├── about.html          ← About
├── contact.html        ← Get in Touch
├── netlify.toml        ← Hosting config
├── css/
│   └── main.css        ← All styles
├── fonts/
│   ├── Delicious-Roman.woff2
│   ├── Delicious-Bold.woff2
│   ├── Delicious-BoldItalic.woff2
│   └── Delicious-Italic.woff2
└── assets/
    ├── logos/
    │   ├── mjf-logo-horizontal.svg   ← Nav logo (85px tall)
    │   └── mjf-monogram.svg          ← Footer seal (40px)
    ├── images/
    │   ├── chris-1976.jpg            ← About page top image
    │   └── chris-austin-bw.jpg       ← About page bottom image
    └── video/
        └── homepage-loop.mp4         ← 8-12 sec autoplay clip
```

## Assets to Drop In

### Fonts (required)
Copy your Delicious WOFF2 files into `/fonts/`. The fallback (Libre Baskerville) 
will load from Google Fonts until these are in place.

### Logos (required)
Copy `mjf-logo-horizontal.svg` and `mjf-monogram.svg` into `/assets/logos/`.
Text fallbacks are built in until these are placed.

### Video (home page)
Copy your upscaled homepage clip to `/assets/video/homepage-loop.mp4`.
The dark gradient overlay will show until the file is in place.

### Images (about page)
- `/assets/images/chris-1976.jpg` — color still, top right
- `/assets/images/chris-austin-bw.jpg` — B&W, bottom right
Instructions in `about.html` comments show how to uncomment the `<img>` tags.

### Mediazilla Embeds (films page)
Open `films.html` and replace the embed comments with your Mediazilla iframe code.
When an embed is added, add the class `has-embed` to the parent `.featured-film` 
or `.grid-film` to hide the placeholder play button.

## GitHub Setup

1. Go to github.com → Sign Up (free account)
2. Create a new repository named `masonjarfilms`
3. Set to Public, no README (we have one)
4. Follow GitHub's instructions to push this folder

## Netlify Setup

1. Go to netlify.com → Sign Up with GitHub
2. "Add new site" → "Import an existing project" → GitHub
3. Select your `masonjarfilms` repo
4. Build settings: leave all blank (static site, no build step)
5. Deploy — your site will be live at a random `.netlify.app` URL
6. In Netlify dashboard → Forms → configure email notification for "contact" form

## Domain Migration (after site is confirmed live)

1. In Netlify → Site settings → Domain management → Add custom domain → `masonjarfilms.com`
2. In Squarespace → Domains → masonjarfilms.com → DNS Settings
3. Update nameservers to Netlify's (shown in Netlify dashboard)
4. Wait 24-48 hours for propagation
5. Confirm live at masonjarfilms.com, then cancel Squarespace
