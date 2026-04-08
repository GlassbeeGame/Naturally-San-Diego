# Technical Specs — Naturally San Diego

> Technical decisions and deployment setup for the website build.

---

## Framework & Stack

| Component | Choice | Notes |
|-----------|--------|-------|
| Framework | **Astro** | Static-first, fast, component-friendly |
| Hosting | **Vercel** | Free tier, GitHub integration, fast deploys |
| Version Control | **GitHub** | Standard repo for all code |
| Styling | TBD | Tailwind CSS recommended for utility-first approach |

---

## Deployment Pipeline

1. Code lives in GitHub repository
2. Vercel connects to GitHub repo
3. Push to main branch triggers auto-deploy
4. Preview deployments on pull requests

---

## External Integrations

### GlueUp (Keep existing — do not rebuild)
- **Organization ID**: 1739
- **Base URL**: naturallysandiego.glueup.com
- **Member Portal Login**: Login widget embed (or external link)
- **Event Calendar Widget**: Full-view event list iframe
- **Member Directory**: Corporate membership directory iframe
- **Membership Types**: Membership type list iframe (for pricing page)
- **Newsletter/Subscription**: Subscription list iframe
- All embed codes documented in [[architecture/glueup-widgets]]

### Forms
- **Contact Us**: Simple form → client email
- **Sponsor Inquiry**: Simple form → client email
- **Submit News + Events**: Simple form → client email
- **Newsletter Signup**: Footer on all pages → email service TBD
- Handler options: Formspree, Astro server endpoints, or similar

### External Links
- Naturally Network Job Board
- Slack Community
- Social media profiles

---

## Performance Requirements

- WebP images with lazy loading
- Critical CSS for above-fold content
- Core Web Vitals optimized
- Mobile-first responsive design
- Fast load times (target < 2s)

---

## SEO Note

SEO is **not** a priority for this project. No keyword research, location pages, or search optimization strategy needed. Basic meta tags and proper semantic HTML are sufficient — standard good practices, nothing more.

---

## Domain

- Current: naturallysandiego.org
- DNS will need to be pointed to Vercel after build

---

## Current WordPress Site (Being Replaced)

| Item | Detail |
|------|--------|
| CMS | WordPress with Enfold theme (Advanced Layout Builder) |
| Current hosting | SiteGround |
| Page builder | LayerSlider + Enfold Advanced Layout Builder |
| SEO plugin | Yoast SEO |
| E-commerce | WooCommerce (active but unused — shopping cart appears on all pages but has no products) |

> ⚠️ **WooCommerce is active on the current site.** The shopping cart link appears in the nav on every page. Confirm with client that this is not needed before launch — if any WooCommerce orders exist, they should be migrated or closed out before the WordPress site is retired.

> ⚠️ **All WordPress-hosted images must be preserved before WordPress is retired.** All team headshots, sponsor logos, and event photos have been downloaded to `assets/` — see `assets/logo-reference.md` for the full inventory.
