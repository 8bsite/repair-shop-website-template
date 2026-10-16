# Free HTML repair shop website template with GSAP scroll animations — Reflow

**Website for a phone and laptop repair shop with walk-in repairs, prices and refurbished devices: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/repair-shop-website-template/)** · **[Use this template](https://github.com/new?template_name=repair-shop-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/repair-shop-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/repair-shop-website-template/"><img src="previews/desktop.png" alt="Reflow, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/repair-shop-website-template/"><img src="previews/phone.png" alt="Reflow, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/repair-shop-website-template/"><img src="previews/scroll.gif" alt="Reflow, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for a phone and laptop repair shop with a free diagnosis, a price list, refurbished stock, business pickups and repairs by post. Near-black and white with one electric blue; the wordmark is built from rounded dashes that stretch and flood the screen on the first scroll, and a blue selection scans the checklist, crosses the pickup schedule and reads along the reviews.

Good for: phone, laptop or computer repair shop; electronics, console or watch repair; refurbished device shop; any walk-in service with a price list and a booking form. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a site for <your repair business: what you fix, where you are, opening hours, prices, how to book>. Keep the layout, the motion and the single-file format; replace the brand name and the dash wordmark, copy, photos, prices, times, stock, links and contacts, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=repair-shop-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — top bar: dash mark and name, opening hours, section links, Book a repair button; phone menu overlay
- **Reflow: Phone and laptop repair, done at the window while you watch.** — two screens: a dash-built wordmark with headline and contact bar, then a staircase statement with three photos (demo: REFLOW, "Most broken things are fixable.")
- **Fifteen minutes, free, out loud.** — service explainer: staircase heading, paragraph and a twelve-row checklist with results and a quote (demo: the free diagnosis)
- **Price wall** — price list table grouped by device, each row with models, a time bar and a price (demo: Price wall)
- **Fixed at the window.** — how-we-work block: staircase heading over a wide photo cut into four strips, three columns of text (demo: "Fixed at the window.")
- **Three grades of part. You choose, and the receipt names the one we fitted.** — comparison table of three options with four rows and an example price (demo: Original, Certified, Value parts)
- **Second life** — horizontal shelf of numbered products with photo, specs, price and a Reserve link (demo: five refurbished devices)
- **For offices and schools: we collect on a weekly route, leave a loan device for every one we take and invoice once a month.** — business offer with a weekly schedule drawn as bars on an hour grid (demo: office and school pickups, Monday to Friday)
- **Post it.** — how it works: four steps under one dashed line and a button (demo: repair by post)
- **Reviews** — three customer quotes in large type, each with name and device
- **Before you ask.** — questions and answers (native &lt;details&gt;)
- **Come to the bench.** — contact and booking: staircase heading, address, hours, phone and email, a photo and a booking form (placeholders)
- **Footer** — dashed rule, one-line description, address, contact and page links, copyright and the Design: 8B credit

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, email, form) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, SplitText, Lenis 1.3.27 from jsDelivr. No build step, no framework, no npm. 108 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 108+, Safari 16+, Firefox 110+ (it uses container query units, cascade layers, small/dynamic viewport units).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. FAQ answers use native `<details>` and open without JavaScript. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
