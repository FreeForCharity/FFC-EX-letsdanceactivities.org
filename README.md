# FFC-EX-letsdanceactivities.org

Static GitHub Pages site for **Let's Dance** (letsdanceactivities.org), migrated from a
live Hostinger WordPress site as part of the Free For Charity WordPress-to-Pages
migration (Wave 1, epic
[FFC-Cloudflare-Automation#702](https://github.com/FreeForCharity/FFC-Cloudflare-Automation/issues/702)).

## What this is

- A full static capture of the WordPress site (257 pages + all media), taken 2026-07-12
  with `FFC-Static-Site-Capture-Tools`.
- **Fully localized assets**: Google Fonts, WordPress.com-hosted images, PayPal button
  images, and all same-domain media are served from this repository
  (`public/external-assets/` holds former third-party assets). CI enforces this via
  `scripts/check_assets.py`.
- **Stripped**: WordPress REST/oEmbed/xmlrpc discovery links, emoji script,
  analytics/tracking scripts, search forms, and POST forms (comments, MailChimp signup) —
  none of which can function on a static host. YouTube content embeds are intentionally
  kept (documented exception in `scripts/check_assets.py`).
- **FFC standard footer** injected on every page (attribution, hub login, copyright).

## Deployment

Deployed to the **default GitHub Pages URL**
(https://freeforcharity.github.io/FFC-EX-letsdanceactivities.org/) — no custom domain,
no DNS changes. Cutover is separately gated.

- `CI - Build and Test` validates structure and asset localization on every PR/push.
- `Deploy to GitHub Pages` runs after CI succeeds on `main` (static upload of `public/`).
- `Lighthouse CI` audits the deployed structure, staged under the repo subpath
  (pattern from FFC-EX-catnipandcattitude.org).

## Notes

- `letsdanceactivities.com` (sibling domain) is a 301 redirect to this site — it is not
  migrated separately.
- The site asserts 501(c)(3) status in its own content but publishes no EIN; the footer
  therefore carries the charity name only (never fabricate EIN/status).
