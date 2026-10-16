# Reflow — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger and SplitText, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/repair-shop-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `scene:opening`: `.op-stage` `.op-wm` `.op-flood` `.op-second` `.op-copy` `.op-bar` `.op-wm__row` `data-r` `.op-stair__word` `.op-tile` `.m-select`
  - `scene:diagnosis-scan`: `.dg-inner` `.dg-list` `.dg-band`
  - `scene:bench-strips`: `.bn-photo` `.bn-strip` `.bn-w`
  - `scene:refurb-shelf`: `.rf-pin` `.rf-track`
  - `scene:fleet-cursor`: `.fl-board` `.fl-cursor` `.fl-track` `.fl-win` `.fl-bar`
  - `scene:reviews-read`: `.rv-quote` `.rv-sel`
  - `scene:visit-grow`: `.vs-title` `.vs-w`
  - `section-script:navigation`: `.nav__bar` `.nav__menu` `.nav__toggle` `.nav__menu-close`
  - `section-script:opening`: `.op-stage`
  - `section-script:visit`: `.vs-form` `.vs-status` `data-ok` `data-error`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- Keep the header comment and `<meta name="generator">`; the "Design: 8B" footer link is optional.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, email, form); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- Book a repair buttons in the nav, the first screen and the footer: link to #visit now; point them to your booking page, or keep #visit if the form on the page is connected.
- Reserve links on the five refurbished devices: link to #visit now; point them to each device's product or checkout page in your shop.
- Request a box button in the repair-by-post section: link to #visit now; point them to your mail-in request form or booking page.
- Open an account button in the business section: link to mailto:fleet@reflow.example now; point them to your business-accounts email or sign-up form.
- **The form sends nothing.** `section-script:visit` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Address and area: "23 Tib Street, Northern Quarter, Manchester M4 1LX" and "on Tib Street" (nav menu, opening bar and paragraph, bench caption, visit, footer, meta description); directions "Four minutes from the Market Street tram stop. Bike rack outside the window." (visit). The street is real; the shop and the number are invented.
  - Phone 0161 000 0000 and emails bench@reflow.example, fleet@reflow.example (replaced placeholders: nav menu, opening bar, refurb note, fleet button, visit, footer).
  - Hours: "Mon–Sat 09:00–19:00", "Walk-ins until 18:00", "Sunday closed", "Walk-ins welcome" (nav, opening bar, visit, footer, booking form option "Today, walk-in").
  - "Since 2014" (opening paragraph) and the company "Reflow Repair Ltd · Registered in England" (footer).
  - Service promises: a free fifteen-minute diagnosis, twelve checks, a fixed price before work starts, most screens and batteries back "within the hour", the bench in the shop window with a magnifier camera, nothing goes to a back room (opening, diagnosis, bench, meta description).
  - The example diagnosis: battery at 71%, "Quote £129, ready in 50 minutes" (diagnosis).
  - Every price and time on the price wall: phones £89, £49, £45, £69, £35; laptops £179, £99, £119, £59, £79; tablets and consoles £79, £35, £85; bench times 20 min to 3 h; the model ranges (iPhone 11–16, Pixel 6–9, Galaxy S21–S24, "since 2018", "since 2016" and so on); water damage and data recovery "from £59", "usually a day" (prices).
  - Warranty: 12 months on repairs and refurbished devices, 6 months on Value parts, VAT included, "you pay the cheaper price" (prices, parts, refurb, faq, reviews, meta description).
  - Parts grades and the iPhone 13 screen prices £189 / £129 / £89, "True Tone moved over by us" (parts).
  - Refurbished stock: iPhone 11 Pro £329, MacBook Air 13" M2 £749, MacBook Pro 16" M1 Pro £1,190, iPhone Air £699, MacBook Pro 14" M2 Pro £1,050 with their specs and grades; "New stock lands every Thursday", devices held for two days (refurb).
  - Business service: weekly pickup route Monday–Friday with the areas (Northern Quarter, Ancoats, Salford Quays, MediaCity, Spinningfields, Deansgate, Oxford Road universities, Didsbury, Stockport) and every time window, loan devices, monthly invoice, accounts from five devices (fleet).
  - Repair by post: price range reply the same day, a padded box and prepaid label, a video call diagnosis, back "usually within three working days", free return postage on repairs over £60 (mailin).
  - Reviews by Priya (Pixel 7), Tom (MacBook Pro 13") and Aisha (iPad Air) (reviews).
  - FAQ answers: passcode handling, ultrasonic board cleaning with an answer within a day, what the warranty covers, buying broken devices (faq).
  - Booking: "We will confirm your slot by text or email within the hour" (the form's data-ok message in visit).
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- The REFLOW wordmark on the first screen is not a font: each letter is a 5-column grid of rounded dashes in the markup (.op-wm__letter, .op-wm__row, <i style="grid-column:…">). For another name, redraw the letters in the same way, or replace the block with text.
- The time bars on the price wall (style="--m:<minutes>") and the pickup windows (style="--a:<hour>;--b:<hour>") are sized from those numbers: update them together with the visible times.
- Lighthouse lists gsap and ScrollTrigger as render-blocking; they sit at the end of body and the motion scripts after them need them loaded.
- The diagnosis checklist pins only on desktops at least 760 px tall; on phones and shorter screens the band runs while the list scrolls past.
- Without JavaScript the phone menu button cannot open the overlay; the links stay reachable in the footer.

## Common edits
- Rebrand: search the old name (`Reflow`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
