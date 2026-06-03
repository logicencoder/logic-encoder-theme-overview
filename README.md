# LogicEncoder Enhanced — site theme

Public overview of the WordPress theme that powers [logicencoder.com](https://logicencoder.com/). **Source code is private:** [logic-encoder-theme](https://github.com/logicencoder/logic-encoder-theme). **Current release:** 2.8.9 (see private `style.css` header).

## What this theme is

A **custom dark WordPress theme** built for a crypto/trading tools site: marketing homepage with configurable sections, application catalog, member account area, blog (index + single posts), and auth-related pages. It replaces a generic block theme with one design system (CSS variables, cards, navigation, footer) tuned for LogicEncoder branding. Most marketing copy, colors, and layout toggles are editable in **Appearance → Customize** without redeploying PHP.

## Who benefits

| Audience | Benefit |
|----------|---------|
| **Visitors** | Consistent homepage and app discovery; readable blog with sticky sidebar and reading progress on long posts. |
| **Members** | Dedicated login, account, and password flows that match site chrome; members-only routes gated at the theme layer. |
| **Site operator** | One theme + Customizer to tune hero, app cards, footer, effects, and SEO strings; integrates with LE plugins for shop and auth. |

---

## WordPress Customizer (operator-facing)

All settings live under **Appearance → Customize**. Values are stored as `theme_mod` entries with defaults in code (`inc/theme-mods/defaults.php`). Live preview uses `inc/customizer/preview.js` and color presets via `preset-controls.js`.

### Brand & colors (`le_colors`)

**What:** Color preset dropdown (applies a full palette at once) plus individual tokens: primary/secondary, dark surfaces, text, links, buttons, crypto green/red, border radii.  
**Why:** Rebrand or A/B accents without editing CSS; presets keep tokens consistent.  
**Who:** Operator; visitors see updated colors on next page load (inline CSS from `le_theme_mod_css()`).

### Homepage visibility (`le_home_visibility`)

**What:** Checkboxes to show/hide homepage sections (hero, approach, capabilities, apps, blog preview, stack, about, CTA).  
**Why:** Launch partial homepages or hide sections during maintenance without template edits.  
**Who:** Operator.

### Homepage content sections

| Section | What you edit |
|---------|----------------|
| **Hero** (`le_home_hero`) | Eyebrow, three-part H1, description, terminal typewriter lines, feature pills, up to three CTAs (label, URL, style). |
| **Engineering approach** (`le_home_approach`) | Label, title, subtitle, three icon/title/text items. |
| **Capabilities** (`le_home_capabilities`) | Label, title, subtitle, six capability cards. |
| **Applications block** (`le_home_apps`) | Section copy, “view all” link, grid columns (2–4), default CTA text on cards. |
| **Application cards** (`le_app_cards`) | Up to eight cards: enable, tag, title, description, URL/path, image URL, alt text. Empty set falls back to built-in defaults on new sites. |
| **Blog preview** (`le_home_blog`) | Labels, title, subtitle, post count, excerpt word count, view-all link. |
| **Stack / About / CTA** (`le_home_stack`, `le_home_about`, `le_home_cta`) | Section titles and body copy for lower homepage blocks. |

**Why:** Marketing homepage is the main product funnel; operators need copy and card changes without deployments.  
**Who:** Operator; visitors and SEO crawlers consume the rendered homepage.

### Footer (`le_footer`)

**What:** Brand name, description, copyright template, “built with” line, contact email, three link lists (nav, tools, extra contact) as `Label|/path` lines per row.  
**Why:** Legal/footer links change often; logged-in users automatically lose redundant Login/Register footer links (`le_filter_footer_nav_links`).  
**Who:** Operator; all visitors see footer; members get a cleaner nav column.

### Layout & spacing (`le_layout`)

**What:** Content top margin (guest and admin-bar variants), max content width for wraps.  
**Why:** Fixed nav and admin bar need different offsets; wide monitors need a readable max width.  
**Who:** Operator; affects all `hp-wrap` / `hp-bpage-wrap` pages.

### Typography (`le_typography`)

**What:** Heading, body, logo, and base font size (Google Font choices).  
**Why:** Brand typography without loading unused font families.  
**Who:** Operator; `le_google_fonts_href()` enqueues only selected families.

### Effects (`le_effects`)

| Setting | What | Default |
|---------|------|---------|
| Dot grid background | Radial dot layer + vignette (`le_render_dot_grid_layers`) | On |
| Background animation | `.bg-animation` motion layer | On |
| Scroll reveal | Intersection observer on `.hp-reveal` elements | On |
| Label dashes | Decorative `::before` bars on section labels | On |
| Back to top | Floating button; resets sidebar scroll on single posts | On |
| Reading progress | Gradient bar on single posts tied to `#hp-spost-main` scroll | **On** |

**Why:** Motion and layers look great on marketing pages but can distract on long-form blog reading; single posts also use a flatter card style (`body.single`) so backgrounds do not “double spotlight” through glassmorphism.  
**Who:** Operator toggles; readers get calmer single-post UX when effects are off.

### Navigation (`le_navigation`)

**What:** Nav font; logout link normal and hover colors (theme avoids default WP blue on logout).  
**Why:** Logout must read as a deliberate action (often red), separate from primary nav links.  
**Who:** Logged-in members.

### Homepage SEO (`le_seo`)

**What:** Custom home `<title>` and meta description (also fed to Rank Math filters on front page).  
**Why:** Homepage is the highest-traffic URL; operator-controlled SERP snippet.  
**Who:** Operator; search visitors.

### Login page (`le_auth`)

**What:** Split vs centered layout; brand panel title and subtitle on `page-login.php`.  
**Why:** Auth is high-trust UI; layout choice fits campaign landing vs minimal login.  
**Who:** Guests logging in; pairs with **logicencoder-login-system-plugin** for form handling.

### Account page (`le_account`)

**What:** Desktop column counts for overview stat cards and settings cards on `page-account.php`.  
**Why:** Dashboard density varies by how many stats the operator surfaces.  
**Who:** Logged-in members.

---

## Homepage and applications grid

**What:** `front-page.php` renders enabled sections from Customizer. App grid uses shortcode `[le_app_cards]` (`inc/app-cards.php`) — cards from Customizer slots or legacy JSON fallback.  
**Why:** The site distributes many trading/crypto tools; visitors need a scannable catalog with thumbnails and deep links.  
**Who:** Prospective users; operator updates cards in Customizer or on the Applications page.

**How it fits:** Card URLs often point to app routes or external tools; commerce and Telegram settings remain in **le-shop-plugin** and **le-settings-plugin**.

---

## Blog index (`page-blog.php`)

**What:** Breadcrumb, stats row (posts, categories, tags), **2-column / 1-column layout switcher** (localStorage-persisted), optional **featured post** (`featured_post` post meta = `yes`), card grid, pagination, sticky right sidebar (`blog-sidebar` widget area or Search / Categories / Recent Posts fallbacks). Dot grid layers render when enabled.  
**Why:** Technical blog needs scan-friendly grids and operator-chosen hero post without a separate “featured” plugin.  
**Who:** Readers and SEO; operator marks featured posts in the editor.

---

## Single blog posts (`single.php`, v2.8.x)

**What:**

- Breadcrumb: Home → Blog → category  
- Meta: date, author, estimated read time, comment count (only if &gt; 0)  
- Featured image, content card, paginated pages  
- **Share:** Twitter, Facebook, LinkedIn popups; copy link; native `navigator.share` when available  
- Tags, author blurb, prev/next posts, **related posts** (2 random same-category)  
- **Sidebar:** `hp-spost-sidebar-track` + **sticky** `aside.leb-sidebar` with separate widget cards (Search, Categories, Recent Posts) — not one merged panel  
- **Reading progress** bar (`#hp-read-progress`) when Customizer effect is on  
- **Copy code** buttons injected on `pre.wp-block-code` blocks  
- Comments block only when `get_comments_number() > 0` (avoids empty card for logged-in users when comments template is unused)  
- `body.single`: flat cards, no dot grid call in template, background animation hidden for even tone  

**Why:** Long technical posts need progress feedback, sidebar navigation, and share/copy affordances; earlier layout hacks (multi-thousand-pixel spacers) broke sticky behavior and hid widgets — current layout uses CSS grid + sticky track aligned to content height.  
**Who:** Readers; logged-in admins get admin-bar-aware sticky offsets (`--le-sticky-below-nav`, `--le-sidebar-max-h`).

---

## Member account and authentication pages

**What:** Custom templates: login (split or centered), account dashboard, forgot/reset password, verify email, legacy dashboard — shared `hp-bpage` chrome via `le_auth_page_open()` / `le_auth_page_close()`.  
**Why:** Default `wp-login.php` breaks brand; members expect the same nav/footer as the rest of the site.  
**Who:** Registered users; **logicencoder-login-system-plugin** owns credentials, sessions, and verification URLs.

---

## Members-only content

**What:** `logicencoder_protect_member_pages` on `template_redirect` and `logicencoder_filter_protected_content` on `the_content` — redirect or mask content for configured protected pages when logged out.  
**Why:** Documentation and member areas must not leak via direct URLs or excerpts.  
**Who:** Paying or registered members; reduces accidental exposure.

---

## SEO and sitemaps

**What:** Rank Math XML sitemap disabled; legacy sitemap URLs redirected to WordPress core `/wp-sitemap.xml`; LiteSpeed nocache on sitemap requests; daily regeneration hook; front-page JSON-LD and OG tags from Customizer SEO fields.  
**Why:** One canonical sitemap on a plugin-heavy site avoids duplicate XML and stale indexes.  
**Who:** Operator and search engines.

---

## Design system and navigation

**What:** Shared tokens in `style.css` (`--hp-*`, `--primary`, crypto accents). Fixed nav with mobile menu; hover uses brand blue **without** duplicate glow `text-shadow`. App-route pages can show breadcrumbs per page meta.  
**Why:** Plugins and auth pages must not look like a different site; nav hover had been rendering “two blues” from text-shadow — removed in 2.8.7+.  
**Who:** All visitors.

---

## Quality checks (private repo)

**What:** Playwright E2E specs under `tests/e2e/` (homepage, fonts/nav, visual regression) — run against staging or local, not Hostinger prod by default.  
**Why:** Catch layout regressions on homepage and navigation before deploy.  
**Who:** Developer/operator in CI or local WSL.

---

## Related repositories

| Repo | Role |
|------|------|
| [logic-encoder-theme](https://github.com/logicencoder/logic-encoder-theme) | Private theme source |
| [le-settings-plugin](https://github.com/logicencoder/le-settings-plugin) | Site features and Telegram |
| [le-shop-plugin](https://github.com/logicencoder/le-shop-plugin) | Shop |
| [logicencoder-login-system-plugin](https://github.com/logicencoder/logicencoder-login-system-plugin) | Login and registration |

See [REPOS.md](REPOS.md).

## Licensing

GPL v2 or later (WordPress theme standard). Copyright LogicEncoder.
