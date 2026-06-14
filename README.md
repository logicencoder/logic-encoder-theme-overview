# Logic Encoder Theme

Dark **presentation layer** for logicencoder.com — Customizer-driven homepage, application cards, blog, auth page templates, members-only routing, and SEO coordination with Logic Encoder plugins.

Private theme: [logicencoder/logic-encoder-theme](https://github.com/logicencoder/logic-encoder-theme).

## The problem it solves

A product site needs consistent branding across marketing homepage, app catalogue, blog, and member auth — without hard-coding layout in every plugin. The theme owns visual language; plugins own features.

## Homepage and catalogue

Customizer sections for colors, typography, effects, homepage blocks, and up to **eight app card slots** via **`[le_app_cards]`**. Footer, dot-grid and scroll-reveal effects, back-to-top control.

## Blog

Reading progress, share controls, sticky sidebar, featured-post meta — tuned for long-form Logic Encoder articles.

## Auth pages

Templates for login, account, forgot/reset/verify, dashboard, about, and contact — wired to [logicencoder-login-system-plugin](https://github.com/logicencoder/logicencoder-login-system-plugin-overview). Members-only routes via `template_redirect` + content filters.

## SEO and sitemap

Rank Math sitemap coordination, daily sitemap regen hook, homepage meta via [le-settings-plugin](https://github.com/logicencoder/le-settings-plugin-overview). Playwright E2E tests under `tests/e2e/`.

## Ecosystem

Works with LE Shop, Login System, Settings, MEXC/Gate/Gas plugins — theme provides shells; plugins inject shortcodes and REST-driven UI.

See [REPOS.md](REPOS.md).

---

**Made by [Logic Encoder](https://logicencoder.com)** · [GitHub](https://github.com/logicencoder) · [Contact](https://logicencoder.com/contact/)
