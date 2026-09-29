# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A single-page marketing site (in Russian) for a Moscow-based street music act, used to book performances for corporate events, weddings, and birthdays. See `README.md` for the full feature list and customization notes.

## Development commands

There is no build system, package manager, linter, or test suite in this repo — the entire site is one static HTML file (`street-band-landing.html`) with inline CSS and JavaScript.

To preview changes:

```bash
open street-band-landing.html        # macOS
xdg-open street-band-landing.html    # Linux
# or
python3 -m http.server 8000          # then open http://localhost:8000/street-band-landing.html
```

There is nothing to compile, lint, or run as an automated test — verify changes by opening the file in a browser.

## Architecture

Everything lives in `street-band-landing.html`, laid out top to bottom as `<style>` → `<body>` (one `<section id="...">` per page block) → `<script>`.

- **Design tokens**: all colors, fonts, and layout constants are CSS custom properties on `:root` (`--ink`, `--acid`, `--paper`, `--smoke`, `--display`, `--body`, `--mono`, `--wrap`, `--gap`). Every component style builds on these — change the palette/typography in `:root`, not in individual selectors.
- **Section IDs are load-bearing**: CTAs throughout the page (`<a href="#zayavka">`, nav links, sticky bar) anchor-link to section IDs (`#otlichie`, `#video`, `#kak`, `#formaty`, `#ceny`, `#opyt`, `#faq`, `#zayavka`). Keep IDs stable when restructuring sections.
- **Scroll-reveal**: any element with class `.rv` is animated in via `IntersectionObserver` (script at the bottom of the file), with a no-JS/no-IO fallback that just shows everything. New sections that should animate in need the `.rv` class, not new script.
- **Four independent JS behaviors**, all in the single `<script>` block: FAQ accordion (toggle `.open` + inline `maxHeight`), scroll-reveal (above), sticky mobile CTA bar (toggled by `scrollY` vs. hero height), and lead-form validation (client-side only — see below).
- **Lead form has no backend**: `#leadForm`'s submit handler validates `name`/`contact` client-side (inline error messages, `aria-invalid`, focus-management on invalid submit) and on success only `console.log`s the payload and shows a static "success" message. Wiring it to a real backend/messenger bot is an explicit `TODO` in the code, not a bug to silently fix.
- **Business content is placeholder data**: phone number, social links, photos, embedded video, prices, testimonials, and FAQ answers are all marked `TODO` directly in the markup (see README "Customization" section for the full list) and are expected to stay that way until real business details are supplied.

## Documentation conventions

When writing or editing `README.md` (or any new docs), prefer a simple ASCII diagram over a prose paragraph when describing:

- the page's section-by-section scroll order (a linear user flow)
- the internal structure of the single HTML file (style/body/script breakdown)
- where `TODO` placeholders live relative to page sections
- multi-step client-side logic (e.g., the form validation states)

Keep diagrams plain box/arrow or tree-style ASCII (no external diagram tools/renderers), consistent with the tree already used in README's "Project structure" section.
