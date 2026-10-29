# ICN NP/APN Network Conference 2028

Marketing website for the **ICN Nurse Practitioner / Advanced Practice Nurse Network Conference 2028**, hosted by **New Zealand Nurses Organisation (NZNO)** in Te Whanganui-a-Tara (Wellington), Aotearoa — **3 to 6 September 2028**.

> **Titiro Whakamuri. Arataki Whakamua.** — Look Back. Lean Forward.

Built with Astro + Tailwind v4. Design authored in Paper and translated to code one page at a time.

## Pages

| Route        | What it is                                                                                                                         |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| `/`          | Home — hero, embedded bid film, whakataukī intro, Aotearoa image, four section tiles                                               |
| `/theme`     | The 2028 Conference theme — maunga image moment, kaupapa explainer, four contribution pillars                                      |
| `/journey`   | NZNO's Journey to 2028 — timeline, taonga story, Whakapūmau ceremony image, koha narrative, poetic callout, NZNO media release     |
| `/travel`    | Your Journey to Aotearoa — Wellington image, entry info, four resource tiles (Visa, Tourism NZ, WellingtonNZ, Tākina)              |
| `/register`  | Register your interest — two-column form with promise bullets                                                                       |

Every page is responsive. The `lg:` breakpoint (1024px) is where the layout flips to desktop; below that it collapses to the single-column mobile artboards from the Paper file.

## Stack

- **[Astro](https://astro.build)** 5 (static output)
- **[Tailwind CSS](https://tailwindcss.com)** v4 via `@tailwindcss/vite`
- **TypeScript** (strict)
- **Fraunces** (display serif) + **Inter** (body sans) via Google Fonts
- **Node** 22 (pinned via `.nvmrc`; use [fnm](https://github.com/Schniz/fnm) or similar to auto-switch)

## Local development

```bash
# auto-switches to Node 22 via .nvmrc if you have fnm/nvm installed
cd icn
npm install
npm run dev
```

Open <http://localhost:4321>. Astro's dev server hot-reloads on save.

### Scripts

| Command           | Does                                              |
| ----------------- | ------------------------------------------------- |
| `npm run dev`     | Dev server at `localhost:4321`                    |
| `npm run build`   | Static build into `dist/`                         |
| `npm run preview` | Preview the built output locally                  |
| `npm run astro`   | Astro CLI (`astro add`, `astro check`, etc.)      |

## Project layout

```
icn/
├── public/
│   └── assets/           # brand marks, film poster, bid-film.mp4, imagery
├── src/
│   ├── components/
│   │   ├── TopNav.astro          # sticky dark header, desktop + mobile hamburger
│   │   ├── MobileNavDrawer.astro # full-screen nav, vanilla JS toggle
│   │   └── Footer.astro          # dark indigo footer with brand marks
│   ├── layouts/
│   │   └── Layout.astro          # wraps every page (nav + slot + footer + drawer)
│   ├── pages/
│   │   ├── index.astro           # Home
│   │   ├── theme.astro
│   │   ├── journey.astro
│   │   ├── travel.astro
│   │   └── register.astro
│   └── styles/
│       └── global.css            # Tailwind v4 @theme block, font imports, base styles
└── astro.config.mjs
```

## Design system

The 67 design tokens from Paper are expressed in `src/styles/global.css` under `@theme { … }`. Tailwind v4 picks these up and generates utility classes automatically.

Semantic colours used throughout:

| Token                     | Value       | Role                                              |
| ------------------------- | ----------- | ------------------------------------------------- |
| `--color-background`      | `#FFFFFF`   | Page ground                                       |
| `--color-ink`             | `#221E52`   | Body ink (deep indigo, 274 C)                     |
| `--color-ink-muted`       | `#595766`   | Muted body copy                                   |
| `--color-primary`         | `#2A3583`   | Primary accent (Klein-ish cobalt)                 |
| `--color-primary-strong`  | `#221E52`   | Deep brand surface (nav, footer, dark sections)   |
| `--color-secondary`       | `#7CAB97`   | Sage accent (narrative sections)                  |
| `--color-accent`          | `#D1C05E`   | Mustard — used sparingly for emphasis             |
| `--color-link`            | `#0074BC`   | Inline links                                      |
| `--color-surface-soft`    | `#F6F2E8`   | Warm off-white for section breaks                 |

Fonts: **Fraunces** for display headings and pull quotes; **Inter** for body copy, labels, UI. Māori terms with macrons use Inter — Fraunces at display weights drops some macron glyphs in the current Google Fonts subset.

## Assets

Everything in `public/assets/` is served directly:

- **Logos** — ICN (colour + white), NZNO (landscape + white square)
- **Motif01** — kōwhaiwhai pattern used behind the home hero
- **Film stills** — Aotearoa coastline, maunga, Whakapūmau ceremony, Wellington harbour — stills captured from NZNO's bid film
- **`bid-film.mp4`** — the full bid film NZNO presented to ICN. Re-encoded (h.264, CRF 27, 30fps, faststart) for progressive streaming on web; ~55MB. The original 1080p/50fps source is held outside the repo.
- **`video-poster.jpg`** — poster frame used on the `<video>` element before playback

## Cultural notes

Te reo Māori appears throughout the site with equal typographic weight to English. Content follows the kaupapa shared by NZNO's design reference:

- Macrons are preserved on te reo Māori terms (ā, ē, ī, ō, ū)
- Tāniko and kōwhaiwhai motifs are used in deliberate orientations per the brand reference, never flipped or on angles
- The whakataukī *Ka mua, ka muri* grounds the entire narrative

## Deploy

The site is static — `npm run build` outputs to `dist/` which can be served by any static host (Netlify, Vercel, Cloudflare Pages, S3 + CloudFront). No server-side runtime required.

## Credits

- **Hosting**: New Zealand Nurses Organisation (NZNO)
- **Taonga carver**: Wiremu Barriball — patu pounamu in tōtara case
- **Bid film**: produced by NZNO, 2025
- **Design & build**: this repo

> *Me mihi ki ngā mana whenua o Te Whanganui-a-Tara.*
