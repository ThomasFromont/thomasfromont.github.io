# IceCode design system — "Glace & granit"

Ice white, granite text, a deep glacier blue for action, copper for rare details.
Light first; the dark theme (`prefers-color-scheme: dark`) is a fjord at night.
Everything lives in [`style.css`](style.css). The live reference page is
[`/design-system/`](https://www.icecode.fr/design-system/) (not indexed).

## Colour tokens

Pick by role, never by hue.

| Token | Light | Dark | Role |
|---|---|---|---|
| `--ice` | `#F4F7F8` | `#10181D` | Page background |
| `--snow` | `#FFFFFF` | `#18232A` | Raised surfaces (cards, panels) |
| `--frost` | `#EAF1F4` | `#141E24` | Tinted zones, footer, identity cards |
| `--frost-strong` | `#DDEBF2` | `#1B3240` | Pills, selected states |
| `--line` | `#D9E2E6` | `#26343C` | 1px borders and rules |
| `--granite-deep` | `#141C21` | `#F5F8F9` | Headings |
| `--granite` | `#1F2A30` | `#E6ECEF` | Body text |
| `--stone` | `#5A6972` | `#93A3AC` | Secondary text (AA on `--ice`) |
| `--glacier` | `#2A6888` | `#8CC0DA` | Buttons, links, eyebrows (AA on `--ice`) |
| `--glacier-deep` | `#215572` | `#B0D5E7` | Hover / pressed |
| `--copper` | `#B8703F` | `#D88B5A` | Rare detail (status dot). **Never text.** |
| `--bezel` | `#141C21` | `#2B3A43` | Phone frame around screenshots |

App pages add `--app` (My Caps `#DE8D0A`, Ranker `#2E7294`) through `body_class`
(`app-my-caps`, `app-ranker`). It is used for decoration only (the halo behind screenshots).

## Typography

- **Display:** Schibsted Grotesk 500–800, tight tracking (−0.03 em on headings). Designed for a
  Norwegian news group; it carries the "nordic" voice.
- **Body:** Hanken Grotesk 400–600.
- **Utility:** system monospace for eyebrows and labels (uppercase, +0.12 em).
- Fonts are **self-hosted** in `assets/fonts/` (SIL OFL), so visitors' browsers make no request
  to Google. The legal notice states this; keep it true.
- Scale: `--step--1` … `--step-4` (fluid with `clamp()`).

## Logo

A six-armed ice crystal whose branches are code chevrons: `_includes/logo.svg` (stroke in
`currentColor`) and `assets/favicon.svg` (white on glacier).

## Components (all in `style.css`)

`btn-primary`, `btn-ghost`, `pill` (`pill-dot` for "coming soon"), `eyebrow`, `lede`, `ticks`
(chevron list), `phone` / `phones` (screenshot frames), `store-badges`, `app-showcase`,
`app-hero`, `feature-grid`, `panel`, `principles`, `facts`, `faq` (`<details>`), `identity`
(definition-list card), `contact-band`, `prose` (long documents).

## Site structure

| Page | EN | FR |
|---|---|---|
| Home | `/` | `/fr/` |
| My Caps | `/my-caps/` | `/fr/my-caps/` |
| Ranker | `/ranker/` | `/fr/ranker/` |
| Support | `/support/` | `/fr/support/` |
| Legal notice | `/legal/` | `/fr/mentions-legales/` |
| My Caps privacy | `/privacy` | — |
| Ranker privacy / terms | `/ranker/privacy-en`, `/ranker/terms-en` | `/ranker/privacy`, `/ranker/terms` |

**Stable URLs.** App Store Connect, the Play Console and the apps themselves link to `/privacy`,
`/ranker/`, `/ranker/privacy(-en)` and `/ranker/terms(-en)`. Never move them.

- Layout: `_layouts/default.html` (header + footer), `doc.html`, `ranker-privacy.html`.
- Shared strings: `_data/i18n.yml`. Company facts (SIREN, address, capital…): `_data/company.yml`.
  Store links: `_data/apps.yml` — filling `ranker.app_store` / `google_play` makes the badges
  appear wherever `store-badges.html` is included for Ranker.
- Each page sets `lang`, `alternate_lang` and `alternate_url` so the FR/EN switch and
  `hreflang` work.

## Adding an app

1. Add its store links to `_data/apps.yml` and an icon + WebP screenshots (540 px wide) under
   `assets/img/<app>/`.
2. Copy `my-caps/index.html` and `fr/my-caps/index.html`, then add an `app-showcase` block on
   both home pages, a line in the hero shelf, the footer and the support page.
3. Add `.app-<name> { --app: … }` in `style.css`.

## Local preview

```sh
bundle exec jekyll serve
```
