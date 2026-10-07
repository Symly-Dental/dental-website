# Project

- Plain HTML/CSS; GitHub Pages serves the repository root from `main`. Keep it build-free unless requested otherwise.
- `index.html` is the marketing page, `privacy.html` is the privacy notice, and `styles.css` contains shared styles.
- Keep changes scoped and preserve unrelated work. Remove obsolete markup/styles when replacing them.
- Update the `styles.css?v=` hash in both pages after CSS changes, and update references when moving assets.

## Design and content

- Reuse CSS variables and shared styles. Keep the warm paper, plum and mint palette, system fonts and responsive product illustrations consistent.
- Use `favicon.svg` for the purple brand mark and `assets/symly-wordmark.svg` for the wordmark. Keep other artwork in `assets/`.
- Regenerate the 1200×630 sharing PNG when editing `assets/symly-dental-social.svg`.
- Keep illustrations faithful to the app and use fictional data only. Never include secrets or real patient data.
- The primary action is “Book a demo” via `hello@symlydental.com`; pricing is by enquiry.
- Verify new product claims against `../dental-practice` and release availability. Do not invent prices, testimonials, guarantees or certifications.
- Preserve company details and the privacy link. Update the privacy notice when data collection or providers change.
- Keep metadata, canonical URLs and the sitemap consistent with `https://symlydental.com/`. Preserve `data-nosnippet` on fictional previews.

## Verification

- Check affected layouts at desktop and mobile widths, plus links and assets.
- Run `git diff --check`. Documentation-only changes need only a diff review.
