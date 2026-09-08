# Street Music — Live Street Band Landing Page

A single-page marketing site for a Moscow-based street music act, built to book
performances for corporate events, weddings, and birthdays. The pitch: not a
rehearsed cover band from a catalog, but an interactive live-music act where
guests are invited up to sing and play along.

**Live copy:** [`street-band-landing.html`](./street-band-landing.html)

## Features

- Single self-contained HTML file — no build step, no dependencies, no server
  required. Open it directly in a browser or drop it on any static host.
- Sections: hero, differentiators, video/photo proof, "how it works" timeline,
  formats & lineup options, pricing packages, social proof (stats + quotes),
  FAQ accordion, and a lead-capture form.
- Scroll-triggered reveal animations via `IntersectionObserver`, with a
  `prefers-reduced-motion` fallback.
- Sticky mobile action bar (CTA + contact link) that appears after the hero.
- Accessible lead form: inline validation errors, `aria-invalid`, and focus
  management on invalid submit — no silent failures.
- Dark, high-contrast "street poster" visual style (black asphalt + acid
  yellow accent) built with plain CSS custom properties, no framework.

## Tech stack

Plain HTML5, CSS3 (custom properties, `clamp()`, `clip-path`), and vanilla
JavaScript (ES5-ish, no libraries). Fonts are loaded from Google Fonts
(Oswald, IBM Plex Sans, IBM Plex Mono).

## Getting started

No installation needed — it's a static file.

```bash
# open directly
open street-band-landing.html        # macOS
xdg-open street-band-landing.html    # Linux

# or serve it locally
python3 -m http.server 8000
# then visit http://localhost:8000/street-band-landing.html
```

To deploy, upload `street-band-landing.html` to any static host (GitHub
Pages, Netlify, Vercel, S3, etc.) as `index.html`.

## Customization

The file is intentionally content-first: business details are marked with
`TODO` comments directly in the HTML/CSS so they're easy to find and replace
before going live. Search for `TODO` to find all of them, including:

- Real phone number and messenger links (Telegram, WhatsApp, VK)
- Hero background photo/video and gallery photos
- Embedded video (YouTube/VK/Rutube `<iframe>`) in place of the video
  placeholder
- Pricing figures in the packages section
- Real testimonials and performance stats
- FAQ answers (booking terms, travel fees, equipment requirements)
- Lead form submission handling — the form currently only validates input
  client-side and logs to the console; wire it up to a backend, form service,
  or messenger bot before shipping

## Project structure

```
.
├── README.md
└── street-band-landing.html   # entire site: markup, styles, and scripts
```

## Author

**Alexandra Yurdanova**
GitHub: [@alwaterloo](https://github.com/alwaterloo)
