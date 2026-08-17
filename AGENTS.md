# DMI Calamba City Teachings

## Site setup

- This is a static Astro site deployed from `main` by `.github/workflows/deploy.yml` to GitHub Pages.
- Production is `https://dmicalambacity.org/`. In `astro.config.mjs`, keep `site: 'https://dmicalambacity.org'` and `base: '/'`; never restore the old `github.io/teachings` base.
- Build internal URLs and public asset paths from `import.meta.env.BASE_URL`. Canonical and social metadata come from `BaseLayout.astro`.
- A `CNAME` file is not required because Pages is deployed by GitHub Actions.

## Study article contract

- Put each study at `src/pages/YYYY-MM-DD-slug/index.astro`; use the newest study as the template.
- Import and use `BaseLayout`, `LanguageToggle`, and `SocialLinks`. Reuse the shared classes in `src/styles/global.css`; keep article-specific styling out of the page.
- Preserve this layout: study hero/nav and Scripture; summary aside; article introduction and numbered teaching sections with discussion prompts; response; closing prayer; takeaway; QR sharing block; site footer.
- Use `${base}...` for home, logo, QR, and internal links. Set the public article URL under `https://dmicalambacity.org/`, and add its QR image at `public/qr/YYYY-MM-DD-slug.png`.
- Add the new study to `src/pages/index.astro`, keeping the newest study featured and older studies in reverse chronological order.

## English / Taglish

- Every study must offer complete English and Taglish versions through `LanguageToggle.astro`; do not add page-specific toggle scripts.
- English is the HTML default. Put Taglish strings in the page's `translations` object, with one matching key for every translatable `data-i18n` element.
- Translate accessibility metadata with `data-i18n-aria-label` and `data-i18n-alt`; use `data-i18n-lang` where the element's `lang` must switch.
- The shared toggle uses `en` and `fil`, updates the document language, and remembers the choice in `dmi-study-language`. Missing Taglish keys are not acceptable.

## Required article links

- Every study summary must include its article-specific Canva presentation link and YouTube preaching/service link. Do not publish placeholders or reuse a previous study's URLs.
- Open external links in a new tab with `target="_blank" rel="noreferrer"`. Keep the shared YouTube channel and other social URLs in `SocialLinks.astro`.

## Before publishing

- Remove old `dmicalambaworship.github.io/teachings` URLs and confirm generated links do not contain `/teachings/`.
- Run `npm run check` and `npm run build`; verify the homepage, both languages, Canva/YouTube links, article route, logo, stylesheet, and QR code.
