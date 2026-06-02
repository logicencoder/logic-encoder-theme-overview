# LogicEncoder Enhanced — site theme

Public overview of the WordPress theme that powers [logicencoder.com](https://logicencoder.com/). **Source code is private:** [logic-encoder-theme](https://github.com/logicencoder/logic-encoder-theme).

## What this theme is

A **custom dark WordPress theme** built for a crypto/trading tools site: marketing homepage, application catalog, member account area, blog, and auth-related pages. It replaces a generic block theme with a single design system (typography, cards, navigation, footer) tuned for LogicEncoder branding.

## Who benefits

| Audience | Benefit |
|----------|---------|
| **Visitors** | Consistent homepage and app discovery; readable blog and landing pages. |
| **Members** | Dedicated login, account, and password flows with layouts that match the rest of the site. |
| **Site operator** | One theme to maintain instead of patching a stock theme; integrates with LE plugins for shop and settings. |

## Major features (what / why)

### Homepage and applications grid

**What:** Hero section, feature highlights, and a grid of trading/crypto apps (title, description, thumbnail, link).  
**Why:** The site sells and distributes multiple tools; visitors need a scannable catalog, not a single static page.  
**Who:** Prospective users browsing tools; operator updating apps from WordPress.

### Member account and authentication pages

**What:** Custom templates for login, account dashboard, forgot password, reset password, and email verification — matching site chrome (nav, footer, dark UI).  
**Why:** Default WordPress login pages break brand trust and layout; auth is central to paid/member content.  
**Who:** Registered users managing access; pairs with **logicencoder-login-system-plugin** for actual auth logic.

### Members-only content

**What:** Theme-level rules redirect or block content when the visitor is not logged in, on configured routes.  
**Why:** Protects documentation, downloads, or member areas without relying on ad-hoc page builders.  
**Who:** Paying or registered members; reduces accidental exposure of restricted material.

### Blog and content pages

**What:** Blog index and single-post layouts, standard pages, about and contact templates.  
**Why:** SEO and announcements (changelog, guides) need the same visual language as the product surface.  
**Who:** Readers and search engines; operator publishing updates.

### SEO and sitemaps

**What:** WordPress core sitemap as the canonical index; legacy/third-party sitemap URLs normalized; Rank Math sitemap generation disabled to avoid duplicates.  
**Why:** Search engines must see one clean sitemap; duplicate XML hurts indexing on a plugin-heavy site.  
**Who:** Operator and SEO; indirect benefit to visitors finding pages in search.

### Design system

**What:** Shared CSS variables (brand blue–mint gradient, card shadows, button styles, responsive grids).  
**Why:** Keeps login, shop wrappers, and marketing pages visually aligned as plugins evolve.  
**Who:** Everyone using the site; reduces “Frankenstein” UI across plugins.

## Related repositories

| Repo | Role |
|------|------|
| [logic-encoder-theme](https://github.com/logicencoder/logic-encoder-theme) | Private theme source |
| [le-settings-plugin](https://github.com/logicencoder/le-settings-plugin) | Site features and Telegram |
| [le-shop-plugin](https://github.com/logicencoder/le-shop-plugin) | Shop |
| [logicencoder-login-system-plugin](https://github.com/logicencoder/logicencoder-login-system-plugin) | Login and registration |

See [REPOS.md](REPOS.md) in this repository.

## Licensing

GPL v2 or later (WordPress theme standard). Copyright LogicEncoder.
