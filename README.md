# FS HAIMAN — Cinematic Artist Website

A premium, cinematic, single-page website for the rapper **FS HAIMAN** (Kashmir / Hip-Hop).

The experience is designed to feel like the opening of a music documentary — a black
cinema screen, letterbox title credits, film grain, drifting Chinar leaves, crimson
highlights and oversized editorial typography. Album artwork is treated like film
stills; the artist is emerging, and the site is built to make that feel intentional
and exciting.

Built as a **single HTML file with no build step**. It deploys directly to Netlify,
Vercel or GitHub Pages.

---

## File structure

```
/
├── index.html      # The entire site — inline CSS + inline JavaScript, no dependencies
├── README.md       # This file
└── img/
    └── covers/     # Drop album cover images here (initially empty)
```

- **`index.html`** — All markup, styles and scripts live here. The only external
  resources are Google Fonts (Archivo, Space Grotesk, Space Mono), the Spotify embed,
  and two real Apple Music CDN images (artist portrait + *There Will Be Blood* cover).
- **`img/covers/`** — Optional local album covers. Any file you add here is used
  automatically; anything missing is replaced by a designed title-card placeholder
  (never a broken image).

---

## Album covers

The release catalogue lives in a single JavaScript array in `index.html`
(`var releases = [...]`). Each release looks for a local cover image at
`img/covers/<slug>.jpg`. If the file is present it is used; if not, a designed
title-card placeholder is rendered instead.

### Expected cover filenames

Add any of these to `img/covers/` to replace the placeholder for that release:

```
intro-spect.jpg
baatein.jpg
j-to-k.jpg
takda-reha.jpg
therapy.jpg
boo.jpg
homicide.jpg
not-the-last-drop-cry.jpg
ykwid.jpg
bond.jpg
konsi-beef.jpg
warning.jpg
```

> **Note:** `there-will-be-blood` does **not** need a local file — it uses the
> supplied Apple Music CDN image directly.

### Adding album covers

1. Add the image to `img/covers/`.
2. Use the **exact filename** from the list above.
3. **JPG** is preferred.
4. Recommended aspect ratio: **1:1** (square).
5. Recommended source size: at least **1000×1000**.
6. The website automatically uses the image when present.
7. If it is absent, the designed title-card fallback appears instead.

---

## Replacing placeholders

All placeholders are marked in `index.html` with `<!-- PLACEHOLDER: ... -->`
comments and grouped in a summary comment near the footer. Do **not** invent any of
these values — replace them only when confirmed.

| Placeholder      | Where in `index.html`                              | Current value                     |
|------------------|----------------------------------------------------|-----------------------------------|
| Booking email    | Footer → `Booking` column (`mailto:`)              | `your@email.com`                  |
| City             | Footer → `Location` column                         | `Kashmir` / `CITY — TO BE CONFIRMED` |
| Longer bio       | Reel 03 → `The Story` section                      | `LONGER BIO — TO BE CONFIRMED`    |
| Hero photo       | Hero `.hero__bg` + `.artist__img` (uses artwork)   | `HERO PHOTO — OPTIONAL`           |
| YouTube links    | Not present                                        | `YOUTUBE LINKS — TO BE CONFIRMED` |
| `og:url`         | `<head>` Open Graph block (commented out)          | Set once deployment URL is known  |

**To replace the booking email:** search `index.html` for
`PLACEHOLDER: Replace with confirmed booking email` and update the `mailto:` link.

**To add a longer bio:** edit the paragraphs inside the `#story` section (Reel 03).
Keep it honest — do not add facts that have not been supplied.

**To use a dedicated hero photo:** replace the image URL in `.hero__bg` (CSS) and,
optionally, the `.artist__img` portrait in the Reel 01 section.

**To add YouTube:** add a link in the "Listen Everywhere" list and/or the footer,
following the same `target="_blank" rel="noopener noreferrer"` pattern.

---

## Facts used

Only supplied, factual information is used. Nothing is inflated or invented:

- Artist: **FS HAIMAN**, from **Kashmir**, genre **Hip-Hop / Rap**.
- Languages: **English, Urdu, Koshur**.
- ~**13 releases** across **2025–2026**; first release **WARNING (2025)**.
- Spotify monthly listeners: **~200** (stated as-is, not inflated).
- Status: emerging / ground floor / still climbing.

No fake streams, sold-out shows, awards, chart positions, biography, age or real name
appear anywhere.

---

## Deployment

This is a static single-file site — **no build command is required** for any host.

### Netlify

**Netlify Drop (easiest):** open <https://app.netlify.com/drop> and drag the project
folder (the one containing `index.html`) into the page. It deploys instantly.

**Netlify CLI (optional):**

```bash
npm i -g netlify-cli
netlify deploy            # draft preview
netlify deploy --prod     # production
```

No build command and no publish subdirectory are needed — the site root **is** the
publish directory.

### Vercel

Deploy straight from the folder with the Vercel CLI:

```bash
npx vercel          # preview deployment
npx vercel --prod   # production deployment
```

Because this is a static site, **no build command is required** — accept the
defaults when prompted.

### GitHub Pages

1. Push the files to a GitHub repository.
2. Open the repository **Settings**.
3. Open **Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch** (or a GitHub
   Actions static workflow, as appropriate).
5. Select the branch and the **repository root** (the folder containing `index.html`).

Because this is a static single-file website, **no build process is necessary**.

---

## Accessibility & performance notes

- Semantic HTML, proper heading hierarchy, descriptive `alt` text, visible
  `:focus-visible` states, and `aria-label`s where needed.
- No autoplay audio. The Spotify embed uses `loading="lazy"`.
- Fully honours `prefers-reduced-motion: reduce` — the intro, Ken Burns zoom,
  parallax, leaf particles, marquee, tilt and cursor spotlight are all disabled while
  the page stays attractive and usable.
- No heavy libraries (no GSAP, Three.js, frameworks). Only a lightweight canvas is
  used for the Chinar leaves; scroll and pointer handlers are `requestAnimationFrame`
  throttled. `localStorage` is not used.
- The site remains usable with JavaScript disabled, and never shows a broken image —
  missing covers become designed title cards, and a Spotify failure shows a visible
  "Open FS HAIMAN on Spotify" fallback link.

---

## Links

- Spotify: <https://open.spotify.com/artist/7tPPD8p96vh0tED64DVWJD>
- Apple Music: <https://music.apple.com/us/artist/fs-haiman/1805456783>
- Instagram: <https://www.instagram.com/fs_haiman>

---

*FS HAIMAN — Kashmir / Hip-Hop — 2025—2026. Ground floor. Still climbing.*
