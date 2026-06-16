# Logic Encoder Enhanced — site theme

Custom WordPress theme powering [logicencoder.com](https://logicencoder.com/), designed as the shared presentation layer for marketing pages, app discovery, blog content, and member-facing account/auth pages. Theme behavior is largely controlled through Customizer panels so operators can update site structure and copy without deploying PHP for every content change.

## Tech stack

| Layer | Technologies |
|-------|--------------|
| Platform | WordPress theme (PHP templates + hooks) |
| Styling | Custom CSS design system and token variables |
| Customization | WordPress Customizer (`theme_mod` pipeline) |
| Content surfaces | Homepage, app cards, blog index, single posts, auth/account templates |
| Quality checks | Playwright E2E tests in private repo |

## Homepage and catalogue

WordPress Customizer exposes 20+ sections for homepage blocks, colors, typography, effects, footer content, app card slots, and auth/account layout choices. Operators can adjust structure and text without code deployments.

The applications surface is powered by `[le_app_cards]`, which keeps tool discovery consistent with the rest of the site design system.

## Blog experience

The theme includes a two-mode blog index and long-form single-post layout with sticky sidebar, reading progress, share controls, and related post sections. This keeps technical articles readable while preserving the same visual identity as product pages.

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
