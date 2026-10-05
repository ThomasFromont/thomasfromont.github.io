# icecode.fr

Company website of ICECODE SASU (brand IceCode), publisher of the My Caps and Ranker apps.
Jekyll site served by GitHub Pages from `main`; pushing to `main` deploys it.

**Read [DESIGN.md](DESIGN.md) before changing anything**: design tokens ("Glace & granit"),
components, page map (EN at `/`, FR at `/fr/`) and how to add an app.

## Rules

- **Never move these URLs.** App Store Connect, the Play Console and the apps link to them:
  `/privacy`, `/ranker/`, `/ranker/privacy`, `/ranker/privacy-en`, `/ranker/terms`, `/ranker/terms-en`.
- **Ranker notices are verbatim copies** of the in-app texts (`ranker/*.md`, below the front matter).
  Change them only when the app's text changes.
- **Keep the company identity visible and consistent** (footer + legal notice), from
  `_data/company.yml`. The site exists in part to pass Apple's organization review.
- **Every page exists in English and French.** Each sets `lang`, `alternate_lang`,
  `alternate_url`; shared strings are in `_data/i18n.yml`.
- **Colours come from the tokens in `style.css`**, never literals; check light and dark mode.
- **Fonts are self-hosted** (`assets/fonts/`). Do not add Google Fonts or any third-party
  request: the legal notice says the site makes none.
- **Only state facts about the apps that are true**: take them from the store metadata and
  privacy notices in the app repos (`../MyCaps`, `../Ranker`).
- Store links: `_data/apps.yml`. Link-preview images: `assets/og/<name>-<lang>.jpg`
  (1200×630), chosen per page with `og_image`.

## Preview

```sh
bundle exec jekyll serve
```
