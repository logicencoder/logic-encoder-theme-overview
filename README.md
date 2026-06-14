# Logic Encoder Theme

Dark **presentation layer** for logicencoder.com — Customizer-driven homepage, application catalogue cards, blog layout, auth page templates, members-only routing, and SEO coordination with Logic Encoder plugins.

Private theme: [logicencoder/logic-encoder-theme](https://github.com/logicencoder/logic-encoder-theme) (v2.8.x).

## Homepage and catalogue

WordPress **Customizer** with 20+ sections:

- Global colors, typography, footer, visual effects (dot grid, scroll reveal, back-to-top)
- Homepage hero and content blocks
- Up to **eight application card slots** rendered via **`[le_app_cards]`**
- Auth page layout options (cooperates with login plugin)

## Blog

Reading progress indicator, share controls, sticky sidebar, featured-post meta box. Optimized for long-form Logic Encoder articles and release notes.

## Auth and members-only routes

Dedicated templates: login, account, forgot password, reset, verify email, dashboard, about, contact. **`template_redirect`** and content filters enforce members-only pages when configured. Integrates with [logicencoder-login-system-plugin](https://github.com/logicencoder/logicencoder-login-system-plugin-overview).

## SEO integration

Disables conflicting Rank Math sitemap generation (dedicated [sitemap manager plugin](https://github.com/logicencoder/logicencoder-sitemap-manager-plugin-overview) owns XML). Daily sitemap regen hook. Homepage meta via [le-settings-plugin](https://github.com/logicencoder/le-settings-plugin-overview). **`logicencoder_login_redirect`** filter for post-auth navigation.

## Plugin ecosystem

Theme provides shells; feature plugins inject behavior:

| Plugin | Theme cooperation |
|--------|-------------------|
| LE Shop | `application` post type archives |
| MEXC / Gate / Gas | Shortcode pages inherit dark layout |
| Login System | Auth template routing |
| LE Settings | CSS variables from Customizer + settings API |

## Quality

Playwright E2E tests under `tests/e2e/` in the private repo — homepage, auth flows, app cards regression.

See [REPOS.md](REPOS.md).

---

**Made by [Logic Encoder](https://logicencoder.com)** · [GitHub](https://github.com/logicencoder) · [Contact](https://logicencoder.com/contact/)
