# minhazda.github.io

Portfolio of **MD Minhazur Rahman** — machine-learning engineer & automation specialist.

Live at **https://minhazda.github.io**

## What this is

A dossier rather than a pitch. The design follows one rule, stated on the page itself:

> No number appears without a named baseline and a public source.

Every metric on the site links to the repository and run that produced it. The two
headline services are deployed and answering, not screenshotted:

| Service | Endpoint | Source |
| --- | --- | --- |
| Card-fraud scoring | `fraud-detection-api-…run.app` | [fraud-detection-mlops](https://github.com/minhazda/fraud-detection-mlops) |
| Retail demand forecasting | `retail-forecasting-api-…run.app` | [synthetic-retail-mlops-pipeline](https://github.com/minhazda/synthetic-retail-mlops-pipeline) |

## Build

Plain HTML, CSS and vanilla JS. No framework, no build step, no dependencies —
a single `index.html` with inline styles and one inline script.

```bash
python -m http.server 4173
# open http://localhost:4173
```

## Design notes

- **Editorial dossier structure** — Exhibits A–E, an appendix of numbered footnotes,
  and a colophon. Claims in the body, evidence in the notes.
- **Dark "desk" with paper "sheets"** — sections sit on the desk as separate sheets
  with real shadows, so the page reads as documents laid out rather than a scroll.
- **Type** — Besley (serif display), Schibsted Grotesk (UI), Spline Sans Mono
  (endpoints, dates, footnote markers). Ten font variants, subset to only what the
  stylesheet actually uses.
- **Motion is decorative and optional** — scroll reveals, a count-up metric, cursor
  spotlight, headshot parallax and tilt, drifting aurora. All of it is gated behind
  `html.js` so the page is fully readable without JavaScript, and every animation
  is disabled under `prefers-reduced-motion: reduce`.

## Cold-start handling

Both Cloud Run services run at `min-instances = 0` — a deliberate $0/month
deployment. That normally means a ~30 second cold start on the first request, which
is a poor experience for anyone clicking "live demo".

The page therefore pings both `/health` endpoints on load, so the containers are
warm before a visitor clicks, and reports the real wake time in the live-services
footer. The requests are `mode: 'no-cors'` and fire-and-forget: the response body is
irrelevant, reaching the server is the whole point, and a failure leaves the page
exactly as it was.

## Accessibility

- Skip link to the main content
- Semantic landmarks and `aria-label`s on every section
- `prefers-reduced-motion` respected throughout
- Explicit `width`/`height` and `fetchpriority` on the hero image to avoid layout shift
- Live-services status uses `aria-live="polite"` so the wake-up result is announced

## Structure

```
index.html      the whole site
favicon.svg
og.png          social preview card
assets/         headshot in webp + jpg, 440w and 880w
blog/           engineering write-ups
PRODUCT.md      design intent and content rules
```

## Availability

Bangladeshi citizen, based in Chattogram. Open to on-site or hybrid work in
Dhaka and Chattogram, remote work with any team whose day overlaps UTC+6, and
relocation with sponsorship (EU Blue Card / Netherlands HSM eligible).

- Email — minhazurrahman.ds@gmail.com
- CV — https://github.com/minhazda/cv
- ORCID — https://orcid.org/0009-0008-9418-6614
